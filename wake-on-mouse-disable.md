Disable wake on mouse
=====================

`cat /proc/acpi/wakeup` returns a list of devices that are able to wake up the computer from suspend. It might look similar to this:

```
Device	S-state	  Status   Sysfs node
CIR	  S3	*disabled
PS2K	  S4	*disabled
PS2M	  S4	*disabled
USB1	  S3	*disabled
RP01	  S4	*disabled  pci:0000:00:1c.0
RP02	  S4	*disabled
RP03	  S4	*disabled  pci:0000:00:1c.2
RP04	  S4	*disabled
RP05	  S4	*disabled
RP06	  S4	*disabled
RP07	  S4	*disabled
RP08	  S4	*disabled
GLAN	  S4	*disabled
EHC1	  S4	*enabled   pci:0000:00:1d.0
EHC2	  S4	*enabled   pci:0000:00:1a.0
XHC	  S4	*enabled   pci:0000:00:14.0
HDEF	  S4	*disabled  pci:0000:00:1b.0
PEG0	  S4	*disabled
PEGP	  S4	*disabled
PEG1	  S4	*disabled
PEG2	  S4	*disabled
```

You have to disable the entry corresponding to your mouse. You set or unset the flags in the file by echoing the device name into it:

```
> sudo -i
> echo "EHC1" > /proc/acpi/wakeup
```

When you have found the correct device (e.g. `EHC1`), you can make the change permanent by putting the line `echo "EHC1" > /proc/acpi/wakeup` into the file `/etc/rc.local`.
