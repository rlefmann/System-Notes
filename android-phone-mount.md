# How to mount Android phones on Linux computers

## Install programs

* libmtp
* simple-mtpfs

## Prepare phone

* Connect the phone via USB
* Select `Transfer files (MTP)`

## Mounting phone

First, create a mount directory, e.g. `mkdir ~/Phone`.

To get a list of the attached MTP devices, run `simple-mtpfs -l`: 

```
$ simple-mtpfs -l
1: XiaomiMi-2s (id2) (MTP)
```

To mount the phone filesystem to the previously created directory, use:

```
simple-mtpfs --device <number> ~/Phone
```

where `<number>` is the order number of your device displayed by the `simple-mtpfs -l` command. You can now access the contents of your phone's memory by browsing the `~/Phone` directory.

To unmount the phone, run `fusermount -u ~/Phone`.

## Fixing permission issues

I was having problems accessing my Xiaomi Redmi 2s phone on my Void Linux computer. simple-mtpfs shows the error message

```
LIBMTP PANIC: Trying to dump the error stack of a NULL device!
```

when I try to mount my phone. This is a rather strange error message as it turned out to be related to permission issues.

Running the command using sudo works:

```
sudo simple-mtpfs -o allow_other --device 1 ~/phone
```

The `allow_other` option permits access for users other than the root user.

If you do not want to mount the phone using `sudo` you can edit the file

```
/lib64/udev/rules.d/69-libmtp.rules
```

Find the line corresponding to your phone (search for the name listed when running `simple-mtpfs -l`) and add `GROUP="username"`, obviously replacing `username` with your own username. For me this looks as follows:

```
# Xiaomi Mi-2s (id2) (MTP)
ATTR{idVendor}=="2717", ATTR{idProduct}=="ff40", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1", GROUP="lefmann"
```

After a system restart, you can mount your phone without root privileges.

## Resources

* https://www.youtube.com/watch?v=lcmJg4OfKzs
* https://gist.github.com/rolfn/7345cf7094bfe9cf16f5586b69b8d593
* https://askubuntu.com/questions/87667/getting-mtp-enabled-devices-to-work-with-ubuntu
* http://murga-linux.com/puppy/viewtopic.php?p=1010512&sid=d47cb179362e6b02b25feed26193497e
