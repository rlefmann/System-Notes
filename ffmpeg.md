ffmpeg
======

## Convert wav to mp3

For voice recordings a bitrate of 64k is perfect.

```
ffmpeg -i input.wav -vn -ar 44100 -ac 2 -b:a 64k output.mp3
```

Use `find` in combination with `ffmpeg` to convert all files in a directory:

```
find -name "*.wav" -exec ffmpeg -i {} -vn -ar 44100 -ac 2 -b:a 64k {}.mp3
```

## Split audio file

Segment the input file into a set of tracks of equal length. For example:

```
ffmpeg -i input.mp3 -f segment -segment_time 600 -c copy output-%03d.mp3
```
