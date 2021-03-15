Download YouTube videos with youtube-dl
=======================================

## Video download

```
youtube-dl -o "%(upload_date)s %(title)s.%(ext)s" <url to video or channel>
```

## Download audio

You can also directly download the audio of a video only. This is useful if you want to listen to it on the phone as a podcast.

```
youtube-dl --extract-audio --audio-format mp3 -o "%(upload_date)s %(title)s.%(ext)s" <url to video or channel>
```

Audio players on Android often have trouble playing long `MP3` files. It therefore makes sense to split those files using `mp3splt`. Look into the document `split-audio.md`.
