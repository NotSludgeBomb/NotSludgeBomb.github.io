---
layout: post
title:  "GNOME is the only desktop environment worth caring about"
permalink: "/blog/gnome-is-the-only-desktop-environment-worth-caring-about"
date:   2022-11-28 17:42:14 -0600

---
Those familiar with Linux will know there are a *lot* of desktop environments
to choose from. KDE Plasma, Cinnamon, XFCE, MATE, LXDE, Budgie, Pantheon, and, of course, GNOME.
GNOME has sort of been the default desktop environment for Linux. Many distros either
have it out-of-the-box or provide it as one of the default options. There's a lot
of discussion around GNOME. Some supportive, some not. GNOME definitely has its
critics, but I'm here right now to argue wildly in its favour.

I believe GNOME is really the only Linux desktop environment worth caring about.
Between its push for Wayland, workflow and modularity, customizability with Extensions, 
aesthetics, approachability, and just general polish, GNOME is really superior to anything 
else I've used. Let's talk about why.

# Wayland Support

GNOME was, to my knowledge, the first desktop to support Wayland, starting in
version 3.10. Other environments have since gained support as well, such as
KDE Plasma, Cinnamon (kind of), and... well, that's pretty much it.

Cinnamon supports Wayland only if you use Mutter as the window manager,
which Mint doesn't do out-of-the-box (and who else is using Cinnamon?). 
Plasma *hardly* supports Wayland, with frequent KWin krashes for, what, 
adding a widget to the panel?

GNOME is the only desktop environment I've used that not only supports Wayland
but owns it and does it well. Plasma krashes constantly on Wayland, and
Cinnamon I don't like for reasons I'll discuss later.

Now, I have been neglecting tiling window managers so far, and I have used Sway. 
But I really prefer having a full desktop environment, and Sway is just too high 
effort for me.

# Workflow and Modularity

The overview is really one of the most ingenious things to come out of
GNOME. In just a single button press, or a single hot corner, you have
a view of all your currently opened apps, pinned apps to open, a button
to view the rest of your apps, all your workspaces to organize windows,
and a search bar if you aren't sure where things are.

GNOME's use of workspaces is incredibly helpful for organizing my work.
I can keep socials, web browsing, file management, writing, photo editing,
music composing, whatever, all on different virtual desktops. It's something
other desktop environments have, but GNOME's implementation of them is
made 10x better with the overview.

One of the best aspects of GNOME, to me, is its modularity. In Plasma,
everything is on the panel. App menu, taskbar, system tray, clock, what
have ya. Similarly, in XFCE, pretty much everything has to be placed on
a panel. But in GNOME, things are spread out more. There's a panel,
dash, overview, and app grid, all as separate entites. And using
extensions, which I'll delve into in a bit, you can remove or tweak
all of them individually.

# Tweaks and Extensions

Extensions are addons to the GNOME Shell that can do, really, pretty much
whatever you want. Whether it's simply adding a dock to your desktop, or
turning GNOME into a tiling window manager, GNOME Extensions can do anything.

In combination with GNOME Tweaks, offering some extra, less supported settings,
you can turn your GNOME desktop into whatever you want. Zorin OS takes
advantage of this, with four "desktop layouts" you can switch between on the
fly (eight layouts if you buy the "Pro" version, though that's a whole 'nother
discussion).

Pretty much everyone has their own GNOME configuration utilizing extensions.
I used to use a setup using Dash-to-Panel and ArcMenu to make GNOME more like 
Windows. Or the Ubuntu layout, with Dash-to-Dock on the left side of the screen. 
GNOME is incredibly customizable with Extensions, and they're really fun to play 
around with trying to find a setup just for you.

What do other desktop environments have in this regard? Cinnamon has its own 
extensions, but I found this out like, a month ago, went "*sniff* neat" and 
never thought about it again. I don't know if anyone actually uses Cinnamon Extensions.
Or develops them, even. Maybe their site's just broken, but I'm counting 23 extensions 
total. 

Pretty much every other desktop environment just has widgets, which are items you can add
to your panel. Plasma has by far the best implementation of widgets, allowing
them on both the panel and the desktop and having a centralized store for
them where you can download widgets made by other users.

Plasma widgets are inherently more limiting than GNOME Extensions. They can
only do things when you interact with them where they lie. And where they lie
is in a fixed area; you can't just place them anywhere. There's a grid on the
desktop, and on the panel, it just pushes itself to the side automatically.
Pretty much all widgets can add are buttons.

Other desktops are even worse in this regard. XFCE doesn't have desktop widgets,
only panel ones. And there's no widget manager; you have to download and manage 
them as regular ol' packages. And everything else I know of doesn't really have
any custom widgets or extensions. Or if they do, they're so obscure that no
one makes them.

# Appearance

There isn't much to this one; GNOME is just really pretty. Using Gradience, you
can still theme it with different colours and a bit of custom CSS. I'm not good 
with colours so I just use the Monet, but if you're inclined to, you can change 
all of them yourself.

# Approachability

GNOME is, in my experience, significantly better in regards to newcomer-friendliness.
I think pretty much all of us want Linux to be approachable, and GNOME does
that well.

GNOME is incredibly stable. There isn't much that you can break by accident,
whereas Plasma has plenty of footguns to ruin your experience *quickly*, 
such as accidentaly deleting the panel. Why does it even let you do that?
There isn't even, like, a popup or anything warning you that you're... y'know,
deleting the panel. And if you're completely new to this, you might not
immediately realize that you can right click on your desktop to bring it back.

If you wanna remove something in GNOME, it's an extension, which I think is
way better. You have to go out of your way to find the extension to remove
it. If you get rid of the panel, or the dash, or whatever you want to get rid of,
you're doing it with intent. No accidents here. And if there are? Well, you
probably have the extensions app open already, just turn off the extension
that's doing it. And even if you don't, you have a super key. The app grid
and the panel are separate objects from each other, as I discussed earlier. 
If you get rid of the panel, you can still open apps. Unlike in Plasma, 
where the app menu is a widget on the panel. Just like everything else in Plasma.

GNOME also streamlines the user experience a ton. Its settings app is simple,
easy to navigate and find what you want. And the new Quick Settings menu in
GNOME 43 is incredibly useful, with quick controls for volume, brightness
(~~which i think only works on laptops~~), wifi, bluetooth, dark mode,
night light, and power options all in the same place.

Plasma system settings I could never go through without using the search bar.
I mean, good on them for having one, but it should be more of a helpful hint
rather than a borderline necessity. And everything in Plasma just feels too
spread apart. The audio controls are their own button on the panel. Brightness
is its own button on the panel. Wifi isn't even a widget, it's in the
system tray for some reason. Doesn't it feel weird having volume and brightness
as dedicated buttons, but lumping wifi next to Discord and Steam?

# Conclusion

I really don't see much reason to use GNOME over any other alternatives.
It's the only desktop I know of that compatently supports Wayland. it's workflow is super 
streamlined and modular. Extensions and Tweaks offer me way more control over my desktop 
than I've seen in other environments, and are way easier to boot. It's aesthetically way 
better, and with the adw-gtk3 theme, pretty much everything matches. And it's super 
approachable and stable for newcomers.

I know plenty of people use other desktop environments, but I believe that GNOME 
should be the one people put their focus on. If you're using something else, I
heavily recommend giving GNOME a shot. Play around with Extensions and Tweaks, I'm
sure you'll find some configuration you love. 

(Extra tip: use Extension Manager by Matt Jakeman. It's like the official GNOME 
Extensions app, but with a nicer layout and a section to download extensions 
directly from the app)

If after all you're not convinced, uh... um... erm... uhh... hm...

— NotSludgeBomb
