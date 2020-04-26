# Create a screencast

Record a video of your screen.

```
ffmpeg -f x11grab -s 1280x800 -r 25 -i :0.0 -qscale 0 /tmp/screencast.mp4
```

creates a screencast of the top left 1280x800 pixels. To stop recording, simply type `q`.

The next command records the whole screen as well as audio input:

```
ffmpeg -f x11grab -y -r 30 -s 1920x1080 -i :0.0 -vcodec huffyuv -f alsa -i default out.mkv
```

To convert a video in a smaller `FLV` file:

```
ffmpeg -i filename.mp4 filename.flv
```

See: http://ubuntuforums.org/showthread.php?t=1392026
