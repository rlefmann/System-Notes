# Audio not working in void linux

* Install `alsa-utils`
* Set the sound settings in `alsamixer`
* This seems to be enough (at least when using `chromium`)
* If not, you might additionally need `alsa-tools` (or even `sox`)

You might also have to add your user to the audio group in `/etc/group`:

```
usermod -a -G audio <username>
```
