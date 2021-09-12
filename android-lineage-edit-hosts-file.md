Edit Hosts File in Lineage OS
=============================

* Install `adb`
* Enable `Android debugging` and set `root access` to `ADB only`
* In a shell, run `adb root`, followed by `adb remount`

You can now download the hosts file to your computer:

```
adb pull /system/etc/hosts
```

edit it and than push the modified file to your phone

```
adb push ./hosts /system/etc
```

Alternatively, you can edit it directly on your phone:

```
adb shell
nano /etc/hosts
```

Do not forget to turn `root access` back off after you are done editing the file.
