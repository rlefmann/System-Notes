Increase size of tmp directory
==============================

I sometimes have to create large temporary files. I usually use the `/tmp` directory for those. On my system the `tmpfs` has a size of 1.8GB. You can use `df -h` to view that size. If you encounter an "No space left on device" error, you can increase the size of the tmpfs on the fly:

```
sudo mount -o remount,size=10G /tmp
```
