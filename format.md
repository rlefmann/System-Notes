# Format usb drive

## Preparation

* Plug in usb drive
* List all hard disks using `lsblk` (alternative: `sudo fdisk -l`)
* Find device name, e.g. `/dev/sdb`
* Unmount all mounted partitions


## Optional: delete all data

```
sudo dd if=/dev/zero of=/dev/sdc1
```

Takes some time, but ensures your data is overwritten!


## Format

Format usb drive with `mkfs`:

```
# FAT
sudo mkfs.vfat -n 'device name' -I /dev/sdc1

# NTFS
sudo mkfs.ntfs -I /dev/sdc1

# EXT4
sudo mkfs.ext4 /dev/sdc1
```
