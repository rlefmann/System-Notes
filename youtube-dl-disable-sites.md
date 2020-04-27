# Disable all sites besides youtube in youtube-dl

Use your package manager to locate the youtube-dl files.
If you are a void linux user:

```
xbps-query -f youtube-dl
```

Apparently, they are stored in

```
/usr/lib/python3.8/site-packages/youtube_dl
```

Go to that directory and edit the file `extractor/extractors.py`:

```
sudoedit extractor/extractors.py
```

Comment out all undesired imports.
