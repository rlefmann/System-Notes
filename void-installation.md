# Installing Void Linux

## Programs I want to keep

* newsboat
* vim
* insync
* network-manager-applet ?
* udisks2
* unzip
* zathura

## Fonts

* Inconsolata
* nerd-fonts-terminus
* terminus-font

## Save Data

* Find HDD_: `lsblk` -> `/dev/sdb1`
* Mount hard drive:  `udisksctl mount -b /dev/sdb1`
* Save the obvious Data files to disk:
				* `cd /location/where/mounted`
				* `DEST=pwd`
				* `cd ~`
				* `mv folder $DEST`
* Save the not-so-obvious stuff, e.g.:
				* `.bashrc`
				* `.vimrc`
				* `.mozilla` folder
				* `.newsboat` folder
				* `.Xresources`
				* `.config/sxiv`
				* `.config/zathura`
* Unmount hard drive

## Create USB

* Download the `x86_64` version of the ISO of your operating system
* Insert usb drive and find its drive letter with `lsblk`
* `sudo dd bs=4M if=/path/to/iso of=/dev/sd[drive letter] status=progress`

## Boot from USB (for Lenovo Thinkpad Edge)

* Shutdown computer
* Restart and press `F12` to enter boot menu
* Select USB name (for me, this was `ubuntu`) and press enter
* You should see the void linux logo
* Enter the credentials you are told (username: `root`, password: `voidlinux`)
* `sudo -i` (the minus is on the ß key
* `void-installer`

## Installation settings

* Keyboard: `de`
* Network: nothing to do
* The other points are straightforward, too
* Because the Thinkpad has a UEFI, we have to do the following (we can see this, because GPT is mandatory and we cannot set bootable flags):
				* First partition: 100MB EFI
				* Second partition: 8GB swap
				* Third partition: the rest, Linux filesystem
* Format the first partition as `fat32` and set the mount point to `/boot/efi`
* Format the second partition as swap
* Format the third partition as `ext4` with mount point `/`
* Finish installation

## Updates

* Run `xbps-install -Suv` repeatedly until there are no more updates
* `xbps-query -l | wc -l`: 137

## Install basic software

Example `vim`:

* list packages via `xbps-query -Rs vim`
* install package: `sudo xbps-install vim`

## Install a desktop

* You will need `xorg-minimal`
* You also need a video driver. Because I have a Intel CPU, I chose `xf86-video-intel`
* You also need `xorg-fonts`
* And if you are using a german keyboard, install `setxkbmap`
* I choose `dwm` as my window manager
* `vim .xinitrc`, add `setxkbmap de` and `exec dwm`
* If you now type `startx`, `dwm` should start

## Installing st (the simple terminal)

* Note: directly install `base-devel`
* First we have to install `git`, `make`, `pkg-config`
* `st` has the dependencies `freetype-devel`, `fontconfig-devel`, `libX11-devel`, `libXft-devel`
* `mkdir Downloads`
* `cd Downloads`
* `git clone https://git.suckless.org/st`
* `cd st`
* `make`
* `sudo make install`
* Change the font in `config.h` to `"mono:pixelsize=14:antialias=true:autohint=true"`
* Install the `scrollback` patch via `patch -p1 < st-scrollback-xxx.diff`. This allows you to scroll up and down using `Shift+PgUp` and `Shift+PgDown`. `Ctrl+Shift+PgUp` increases the font size, `Ctrl+Shift+PgDown` decreases it.

## Install DMENU

* Same as `st`
* But we need additional dependency `libXinerama-devel`


## Shutdown and suspend computer without password prompt

* `sudo visudo`
* add to the end: `lefmann ALL=(ALL) NOPASSWD: /sbin/shutdown, /sbin/zzz`


## Automatically mount hard drives

* Install `udevil`
* To start watch for hard drives: `devmon &`
* You can also put this in you `.xinitrc`

## vim clipboard

* install `xsel`
