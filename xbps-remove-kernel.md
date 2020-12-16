Remove Kernels
==============

## Removing old kernels


## Removing kernel series

If you try to remove a kernel package like `linux5.9`, it will fail because of unresolved dependencies.

You have to create a file `kernel.conf` (the file name does not matter) in
`/etc/xbps.d/` and add the line

```
ignorepkg=linux5.9
```

to it. Afterwards you can remove the package with `xbps-remove`
