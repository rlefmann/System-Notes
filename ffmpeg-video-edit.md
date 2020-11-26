Edit Videos with ffmpeg
=======================

## Create lossless video

Use the `huffyuv` codec, e.g.

```
ffmpeg -i input.mp4 -vcodec huffyuv output.avi
```

Warning: this can result in huge files (e.g. 12GB for a 10 minute video)


## Cut videos

You can only do this with a lossless format, because otherwise it will cut by I-Frames which is not very exact. You can probably also use `mkv` with `-c:v libx264`.

```
ffmpeg -i input.mp4 -ss 00:00:03.0 -t 00:01:00.0 -c copy output.mp4
```

* You can use `-to` instead of `-t` to specify the end of the segment instead of its length.
* The `-c copy` option copies the input to the output without re-encoding.
* If you do not specify `-t` or `-to` the segment will extend until the end of the video.
* You can alternatively use the `trim` filter (if you apply other filters anyway)


## Concatenate video parts

```
ffmpeg -f concat -i filelist -c copy output.mkv
```

where filelist looks like this:

```
file input1.mkv
file input2.mkv
```


## Add blur

```
ffmpeg -i input.mkv -vf "boxblur=4:2" -c:v libx264 output.mkv
```

## Add a title

Use the `drawtext` video filter:

```
ffmpeg -i input.mkv -vf drawtext="fontfile=/usr/share/fonts/TTF/UbuntuMono-B.ttf: text='Creating a minimal dunstrc': fontcolor=white: fontsize=40: x=(w-text_w)/2: y=(h-text_h)/2" -c:v libx264 output.mkv
```


## Speed up video (part)

This doubles the speed:
```
ffmpeg -i input.mkv -filter:v "setpts=0.5*PTS" output.mkv
```


## Soft subtitles

First, create a `srt` file for your video:

```
1
00:00:00,0 --> 00:00:10,0
This is some subtitle text

2
00:00:10,0 --> 00:00:15,0
Here is more text
```

```
ffmpeg -i infile.mp4 -i infile.srt -c copy -c:s mov_text outfile.mp4
```


## Burn subtitles into video

```
ffmpeg -i input.mkv -vf "subtitles=subtitles.srt" -c:v libx264 output.mkv
```

You can change settings such as the font size like this:

```
"subtitles=subtitles.srt:force_style='Fontsize=34,PrimaryColour=&H0000ff&'"
```

Alternatively, we can use the libass library. Convert subtitles to `ass` format:

```
ffmpeg -i subtitles.srt subtitles.ass
```

Then add them using a video filter:

```
ffmpeg -i input.mkv -vf ass=subtitles.ass output.mkv
```


## Apply multiple filters

Only one `-vf` option is allowed. Separate filters using comma, e.g.

```
ffmpeg -i input.mkv -vf "boxblur=4:2, ass=subtitles.ass" output.mkv
```
