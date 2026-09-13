# zfs-openrc



# Getting started

This package contains the zfs init scripts for OpenRC.
You MUST install [zfs-utils](https://aur.archlinux.org/packages/zfs-utils) and [zfs-dkms](https://aur.archlinux.org/packages/zfs-dkms) or [zfs-utils-git](https://aur.archlinux.org/packages/zfs-utils-git) and [zfs-dkms-git](https://aur.archlinux.org/packages/zfs-dkms-git) from the AUR or the [chaotic-aur](https://aur.chaotic.cx/).

# Warning
This is my first AUR package.
To use this just clone this repository and run:

    makepkg -sri 

Then you must enable the services that you need with:

    sudo rc-update add zfs-import sysinit ## (This is needed!)
    sudo rc-update add zfs-load-key sysinit ## (Only if you need it: it runs between import and mount)
    sudo rc-update add zfs-mount sysinit ## (THIS IS IMPORTANT!! Otherwise the zpool(s) will be imported but not mounted!)
    sudo rc-update add zfs-zed default ## (This is needed!)
    sudo rc-update add zfs-share default ## (Only if you need it!)

Import and mount belong in `sysinit`, as on Gentoo, so the pools are mounted
before anything in `boot` (localmount included) or `default` starts.
