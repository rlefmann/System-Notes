# Audio not working in void linux

* Install `alsa-utils`
* Set the sound settings in `alsamixer`
* This seems to be enough (at least when using `chromium`)
* If not, you might additionally need `alsa-tools` (or even `sox`)

You might also have to add your user to the audio group in `/etc/group`:

```
usermod -a -G audio <username>
```

## Further troubleshooting tips

alsa service not started?

```
sudo sv status alsa
ln -s /etc/sv/alsa /var/service
```

Consider temporarily removing `/etc/asound.conf` alltogether, as well as `~/.asoundrc`, if present. (Reboot to check). Try:

```
aplay -l
aplay -L
speaker-test
lspci -knn | grep -iA2 audio
```

## /etc/modprobe.d/default.conf

If `speaker-test` returns the error

```
ALSA lib pcm_dmix.c:1089:(snd_pcm_dmix_open) unable to open slave
```
create a file `/etc/modprobe.d/default.conf` with this content:

```
options snd_hda_intel index=1
```

## References

https://www.reddit.com/r/voidlinux/comments/ej8o5z/no_audio_on_fresh_new_installation/
