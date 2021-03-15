Filesystem location for manually installed software
===================================================

Move such software to the directory `/opt`.

## Scripts

Move scripts that are a single file to `/usr/local/bin`. Better yet move the script to `/opt` and create a link to there:

```
mv script.py /opt
ln -s /opt/script.py /usr/local/bin/script
```
