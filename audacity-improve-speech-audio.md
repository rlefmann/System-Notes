# Improving Audio

We use Audacity to edit the audio. We assume that we have our raw video in `mp4` format.

Audacity is an audio editor. Therefore you cannot edit the audio track of a video file directly. Fortunately Audacity lets you import the audio from a video file easily by just importing the video file.

1. Import video in Audacity: File -> Import -> Audio
2. Edit audio track
3. File -> Export Audio -> Save in MP3 format
4. Set the MP3 file as audio track for the video file using
```
ffmpeg -i video.mp4 -i audio.mp3 -map 0:v -map 1:a -c:v copy -c:a copy output.mp4 -y
```


## Noise Removal

* While recording, record 5 seconds of silence (best at the beginning)
* Select the 5 seconds of silence
* Effect -> Noise Reduction -> Get Noise Profile
* Select your whole audio recording
* Effect -> Noise Reduction -> Ok
* Good settings might be `Noise reduction`: 48, `Sensitivity`: 0, `Frequency smoothing`: 150, `Attack/decay time`: 0.15


## Silence parts of the video

Remove parts of the audio like deep breaths by selecting them and then pressing the `Silence audio` button in the toolbar. You can also go to Edit -> Remove Special -> Silence Audio or use the shortcut `Ctrl`+`L`.

Note:
You have to stop the audio playback by pressing the stop button before you can remove silence.

To detect breaths more easily you can set the display from `Waveform` to `Waveform (dB)` by clicking on `output` left to the visualization of the sound file.


## Remove Breathing with Noise Gate

The Noise Gate plugin lets you easily remove breathing. To install it:

1. Download the `.ny` file http://wiki.audacityteam.org/wiki/Nyquist_Effect_Plug-ins#Noise_Gate[here].
2. Move the `.ny` file in the Audacity "Plug-ins" folder `~/.audacity-data/Plug-Ins`.
3. Effect -> Add / Remove Plug-ins -> New Radio Button -> Select Noise Gate -> Enable

Search for a breath in the timeline (set the display from `Waveform` to `Waveform (dB)`). Memorize the to dB value of your breath (something like -30).

Then go to Effect -> Noise Gate and use the settings:

* `Gate`
* `Link Stereo Tracks`
* `No`
* `Gate frequencies above`: 0kHz
* `Level reduction`: between -30 and -12 dB. The lower the more completely the breath is removed
* `Gate threshold`: insert the value you memorized
* `Attack/decay` determines the minimum gate time. Set it to somewhere between 50 and 250, higher is usually better.


## Equalization

* Effects -> Equalization -> Select Curve -> Bass Boost
* Bis 100Hz etwa +10db, dann runter auf 0 bei 500dB
* Effects -> Equalization -> Select Curve -> Treble Boost

You can also manually adjust the equalizer curve: +9 from 0 to 60, then down to 0 and a small peak at 5000/6000 (you can use graphic equalizer)


## Compressor

Makes the voice easier to understand by reducing the loudest parts of the waveform, i.e. it evens out the waveform.

* Threshold: -12
* Noise Floor: -20
* Ratio: 2:1
* Attack: 0.2
* Decay: 1.0
* Make up gain for 0dB after compressing


## Hard Limiter

To cut off parts where you are speaking too loud

* Effect -> Limiter -> Hard Limit
* dB limit: between -2 and -5

## Normalize at the end

After the editing steps, perform normalize with the default values
