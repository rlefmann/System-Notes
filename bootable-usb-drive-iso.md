# Create a bootable USB drive

Identify the drive path by running `lsblk`, e.g. `/dev/sdb`. The drive path does not include a number!

Ensure the device is not mounted: `udevil unmount /dev/sdb`

Using `dd`, write the image to the device:

```
sudo dd bs=4M if=/path/to/iso of=/dev/sd[drive letter] status=progress
```
