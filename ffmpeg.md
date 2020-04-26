# ffmpeg

## Convert wav to mp3

For voice recordings a bitrate of 64k is perfect.

```
ffmpeg -i input.wav -vn -ar 44100 -ac 2 -b:a 64k output.mp3
```

To convert all files in a directory:

```
find -name "*.wav" -exec ffmpeg -i {} -vn -ar 44100 -ac 2 -b:a 64k {}.mp3
```
