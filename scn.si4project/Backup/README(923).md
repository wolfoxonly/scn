
Debian
====================
This directory contains files used to package StarChaind/StarChain-qt
for Debian-based Linux systems. If you compile StarChaind/StarChain-qt yourself, there are some useful files here.

## StarChain: URI support ##


StarChain-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install StarChain-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your StarChain-qt binary to `/usr/bin`
and the `../../share/pixmaps/StarChain128.png` to `/usr/share/pixmaps`

StarChain-qt.protocol (KDE)

