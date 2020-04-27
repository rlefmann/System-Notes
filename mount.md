# Mounting hard drives in void linux

* Install `udevil` to mount hard drives without permission
* To get read permissions for NTFS drives, also install `ntfs-3g`

## Mounting and unmounting

* `lsblk`to list hard drives
* `udevil mount /dev/sdb1`
* `udevil unmount /dev/sdb1`

## Automatic mounting

* To start watch for hard drives: `devmon &`
* You may want to put this in your `.xinitrc`
