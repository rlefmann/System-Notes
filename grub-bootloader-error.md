# Grub error console

If grub opens an error console (e.g. after reinstalling Linux), the bootloader has been corrupted. To fix this, do the following:

1. Start live CD or USB
2. Mount Linux partition, e.g. `sudo mount /dev/sda5 /mnt`
3. `sudo grub-install --root-directory=/mnt /dev/sda` (use `sda` even if linux is installed on `sdb` or elsewhere)
