---
layout: doc
title: Lucy
permalink: /docs/lucy
repo: https://codeberg.org/notsludgebomb/lucy
logo: https://codeberg.org/NotSludgeBomb/Lucy/raw/branch/main/branding/lucy_logo_dark.png
---

<p align="center">
<br>**Note: Lucy is very early in development and currently only supports deb and rpm.<br>
</p>

<p align="center">
Lucy is a build system for deb, rpm, and pacman packages. It takes input in just one file (package.lucy),<br>
and generates a file in the specified format. It's a convienent tool for quickly packaging your software to Linux's
major traditional package managers.<br>
<br>
Lucy is available as open source software under the GNU GPLv3 license.<br>
<br>
<br>
</p>

# Getting Started

To start using Lucy, we first need to create a text file. This can be called anything, though *package.lucy* is the default name that Lucy will use, and it's more recognizable. So, for convenience sake, we'll use that. This is what's called a *spec file*, short for *specification file*. Open the file in whatever text editor you please.

A package contains two things; metadata, which is information such as it's name, version, dependencies, etc., and data/contents, which is the files that are actually installed to the user's system. *package.lucy* contains all the packages metadata, as well as two shell scripts for packaging the contents.

# Inside package.lucy

All of the values are declared through **macros**. These are always prefixed with a percent sign (%). After a macro is a value, or for some, a set of values. Each macro or value should be in a newline. Let's look through all the basic macro's, using Lucy's own *package.lucy* file as an example.

<p class="tip">
Tip!<br>
All of the stuff we're about to go through is covered in Lucy's manual page. If you ever need to quick refresher, you can run `man lucy` in a terminal to read through it.<br>
</p>

```
%name
    lucy

%version
    0.2.0

%release
    1

%architecture
    x86_64

%description
    all-in-one build system for Linux packages
```

`%name` is, of course, the package's name. This is what your package will be referred to as by the package manager. The `%version` macro refers to the program's version. This is used by the package manager to check for updates. The `%release` is like `%version`, but it refers to the package rather than the program. This should always but a single number (no decimal points), and should go up linearly whenever you update the scripts, which we'll get in later. `%architecture` is the CPU architecture the package is made for. As of now, only `any` and `x86_64` are officially support (meaning their names are corrected to the format you're building if they go by something else). `%description` is a short description of the program. This is given to the user by the package manager to tell them about what they're installing.

```
%maintainers
    NotSludgeBomb <notsludgebomb@protonmail.com>
```

`%maintainers` is a newline seperated list of people responsible for maintaining the package. The people updating the metadata and scripts to keep up with the software. Preferably, you should give this in the format of `NAME <EMAIL>`. Additionally, you can use the `%contributers` macro for people who have contributed to the package, but don't do active upkeep

```
%sources
    https://codeberg.org/NotSludgeBomb/lucy/archive/v0.2.0.tar.gz

%sha256sums
    SKIP
```

`%sources` is a list of source files for the package. In the example, we see it uses a URL to download from, but this can also be a local file path, or a git repository (prefixed with `git+`). Lucy will automatically uncompress tarballs and zip archives, so don't worry about doing that yourself. These will go in the **srcdir** (more on that later).

`%sha256sums` is a list of checksums for the sources files. This is optional, though if you use it, it must be the same length as the `%sources` list. Each item in `%sha256sums` correlates directly to one in `%sources`. The first item in `sha256sums` is the checksum for the first item in `%sources`, the second item is the checksum for the second source, so on. You can get the checksum for a file by running `sha256sum path/to/file` in a terminal. In the example, we use `SKIP`, which will skip past one of the sources.

```
%depends
    bash
    binutils
    coreutils
    curl
    git
    tar
    unzip
    zstd

%build depends
    cargo
    pandoc
```

`%depends` is a list of packages that your package requires to run. You can also use `%deb depends`, `%rpm depends`, or `%pacman depends` for dependencies specific to a particular format. This is helpful in case something has a different name on different platforms.

`%build depends` is a list of dependencies required to build the package. These aren't included in the final package, but are installed when Lucy is executed.

You can also use `%optional depends`, which is a list of packages that the program doesn't *require*, but unlock some feature of the program.

```
%build script
    cd ${srcdir}/${pkgname}/
    make build

%package script
    cd ${srcdir}/${pkgname}/
    make DESTDIR=${pkgdir} PREFIX=/usr install
```

Finally, we're onto the shell scripts. These are run when Lucy is executed, and are used for two different purposes. The `%build script` contains instructions for building the packages contents. The `%package script` includes code to package the contents into the final build.

There are a handful of useful variables you can use inside these scripts.

* `$pkgname` is the name of the package
* `$pkgver` is the version of the package
* `$pkgrel` is the release of the package
* `$srcdir` is a path to the **srcdir**, more on this in a bit.
* `$pkgdir` is a path to the **pkgdir**, more on this in a bit.

The `%build script` will usually start with a `cd` command to `${srcdir}/${pkgname}`. The **srcdir**, or **source directory**, contains all the source files from the `%sources` macro. If you've downloaded from or cloned a git repo, then the program's source code will always be in `${srcdir}/${pkgname}`, unless you've named your package something different from the repository. Once inside the directory, you can run any commands you need to build the program. Most will do this via **make**. This is where you'll need to know what you're doing with compiling software, as Lucy won't hold your hand.

The `%package script` is the final step in *package.lucy*. This contains instructions for installing the built software into the **pkgdir**, or **package directory**. The **pkgdir** contains the package's contents; the files to be installed. It's treated as a system's root directory. So, in the Lucy example, the compiled `lucy` executable would go to `${pkgdir}/usr/bin/lucy`. Similarly to building, most program's will have an install script using **make**.

Lucy supports two optional script macros: `%preinstall script`, and `%postinstall script`. These are scripts that, respectively, run before and after the package is installed. These are useful for configuring the system or the program if needed for it to run.

# Building the Package

Once you have *package.lucy* setup, you can build the package.

```
lucy build
```

This will build the package to the format used by your current system. You can specify a different format with the `-t` argument.

```
lucy build -t ( deb | rpm | pacman )
```

You can specify a different spec file with the `-S` argument.

```
lucy build -S path/to/file
```

You can use the `--override` argument to override certain values within the spec file.

```
lucy build --override arch=example
```

Only a handful of values are allowed to be overwritten: the name, the version, the release, and the architecture. This is mainly useful for two things:

* Changing the release for distros like Fedora Linux, which include the OS's version in the release (ex: `1.fc37`)
* Changing the architecture to easily build for more platforms, assuming the build script is able to conform to that.

# Supported Features

### Legend


| Symbol | Meaning                                                 |
| :------- | --------------------------------------------------------- |
| ✓     | Supported by package format and implemented in Lucy     |
| ⃝     | Supported by package format but not implemented in Lucy |
| —ⁿ   | Partially supported by package format (with note below) |
|        | Unsupported by package format                           |

### Table


| Feature             | .deb | .rpm |
| :-------------------- | ------ | ------ |
| Name                | ✓   | ✓   |
| Version             | ✓   | ✓   |
| Release             | —¹ | ✓   |
| Architecture        | ✓   | ✓   |
| Description         | ✓   | ✓   |
| Maintainers         | —² |      |
| Contributers        |      |      |
| Depends             | ✓   | ✓   |
| Optional Depends    | ✓   | ✓   |
| Pre Install Script  | ✓   | ✓   |
| Post Install Script | ✓   | ✓   |

1. Not supported by dpkg, but still included in the output file's name
2. Only supports one maintainer (first one in list is used)
