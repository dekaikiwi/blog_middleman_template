---
title: Chrome Remote Desktop on Steam Deck
date: 1671794606
---

# Chrome Remote Desktop on Steam Deck

If you're like me and dont want to go throught the bother of setting up a 
keyboard and mouse to control the Steam Deck, consider setting up [Chrome Remote Desktop](https://remotedesktop.google.com/) 
for remote access.

The CRD site implies that CRD is only available on Debian but there it also works on Arch with a little terminal wizardry.

## Preparation

Make sure that your deck is configured to install Arch packages. This [Reddit Thread] is a good place to start.

## Install

The following snippet, should pull the [CRD package](https://aur.archlinux.org/packages/chrome-remote-desktop) for Arch and Install.

```
mkdir ~/packages
cd packages
git clone https://aur.archlinux.org/chrome-remote-desktop.git
cd chrome-remote-desktop
sudo pacman -S --needed base-devel
makepkg
```

As the CRD binary relies on a Debian file system structure, 
you may also need to create a symbolic link between the installed location of `Xorg` on Arch 
and the Debian location that CRD is expecting. 

```
sudo ln -s /usr/lib/Xorg /usr/lib/xorg/Xorg
```

Next go through the setup process

```
crd --setup
```

After following the on-screen instructions you should be good to go. Here's a few useful commands for debugging issues

```
crd --restart
```

Check the logs for the CRD service.

```
sudo journalctl -u chrome-remote-desktop@deck.service -r
```
