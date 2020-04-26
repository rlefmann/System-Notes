# Split audio files

Audio players sometimes have trouble playing long `mp3` files.

It therefore makes sense to split those files. For this task, we are using the program `mp3splt`.

In this example, we split a file into pieces of 10 minutes length each:

```
mp3splt -f -t 10.0 -a -d <destfoldername> inputfile.mp3
```

Further information can be found here:

[HOW TO split an audio file into equal sections??](https://ubuntuforums.org/showthread.php?t=1960479)
