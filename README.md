# Arch Linux Guide

Guide and notes on my arch linux install for reference if/when things break. Configured on a Metabox P641HK / Clevo P640HK1 laptop.

## Install

Used [Antergos](https://antergos.com/) to install, did once using Arch install guide and just took less time using Antergos. Base install still gives me (almost) vanilla Arch.

If installing alongside an existing Windows install (even if it's on a second HDD, mistake I made!) important to *mount* the existing EFI partition (ESP) or you will overwrite the Windows bootloader.

Use systemd-boot for the bootloader, GRUB was a little messy to get working and unless you need the extra features GRUB provides it's not worth the hassle.

Make sure to configure systemd-boot using the [arch wiki link](https://wiki.archlinux.org/index.php/systemd-boot) or it won't work properly. Especially important was setting the correct PARTUUID in the config.

For the rest of the install follow the Arch Wiki, Chnchi takes care of most parts so only do what's needed.

## Post-Install

Work through this guide to configure the system: https://wiki.archlinux.org/index.php/General_recommendations

Post install hardware that needed attention:

* Backlight Keys
* Volume Keys
* Touchpad
* Power Saving
* Graphics Card

### Backlight Keys

https://wiki.archlinux.org/index.php/Backlight

Backlight worked after installing `xorg-backlight` package. Got an error saying "No outputs have backlight property" and followed wiki to set option in xorg.conf. 

To map brightness to Fn buttons install `xbindkeys`, then create `.xbindkeysrc` in home directory. Use `xbindkeys -k` to find out what the keycode is. More info [here](https://wiki.archlinux.org/index.php/Xbindkeys#Volume_control)

### Volume Keys

Same as above to map the keys. Follow the guide on the [wiki](https://wiki.archlinux.org/index.php/PulseAudio#Keyboard_volume_control) to figure out the correct commands to map.

### Touchpad 

Worked out of the box but had no tap to click functionality. Follow instructions [here](https://wiki.archlinux.org/index.php/Libinput#Common_options) to set it to on.

### Power saving

Installed [Laptop Mode Tools](https://wiki.archlinux.org/index.php/Laptop_Mode_Tools). Didn't configure anything.

### Graphics Card

Follow the guide [here](https://antergos.com/wiki/hardware/graphics/bumblebee-for-nvidia-optimus/) to install drivers for Optimus with Bumblebee. Locked up on boot following driver installation and trying to launch X with `startx`. Solution was [here](https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Lockup_issue_.28lspci_hangs.29)

## Software