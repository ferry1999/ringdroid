Ringdroid is implemented in pure Java, and it serves as an excellent demonstration of what is possible using the Android SDK.  It works identically on the emulator and on an HTC T-Mobile G1 handset.

Ringdroid uses the Android SDK to find media files, play and seek, and record.  However, the SDK does not include any functionality for opening and decompressing compressed audio files.  So, Ringdroid implements pure-Java audio file parsers.  These parsers do not completely decompress the audio.  Instead, they simply need to parse headers, frame headers, and just enough information from each audio frame to create a crude representation of the waveform.  When the user wants to save a file, the audio file library copies entire audio frames from the original files and assembles them into a valid file of the same format.  Thus no decompression or compression of audio ever happens in the pure Java code.  The Android SDK is used to actually play the audio.

## File formats ##

Supported file formats right now include:
  * WAV
  * MP3
  * 3GPP/AMR (this is the only format that Android records into currently)
  * AAC/MP4 (including iTunes AAC files)

## Editing and audio effects ##

Right now because the pure Java code only parses the frame structure of the audio file and cannot modify the waveform directly, it's hard to imagine doing more complicated audio effects like reverb, noise removal, etc. - however, here are some crazy ideas that might actually be possible given the significant limitations:

  * **Fade in/out**.  All we'd need to do is modify the "gain" of each audio frame.  This is potentially quite easy for MP3.  For 3GPP/AMR it's also possible but there are often only up to 6 bits of resolution to play with per frame (unless the entire waveform is decompressed).  For Ogg Vorbis it seems much harder.
  * **Speed up / slow down**.  You could create a terrible sounding speed-up or slow-down effect by skipping every other frame or doubling each frame.
  * **Silence**.  This is actually not a bad idea.  If someone wanted to insert silence at the beginning, middle, or end, it would be relatively easy to add some "blank" audio frames
  * **Pitch Change**.  You could change the sample rate from 8000 to something else, as long as the Android media player supports resampling from that new sample rate.
  * **Tones**.  People could assemble a monophonic musical ringtone by assembling prerecorded audio frames of a tone.  If we had tones fpr each audio format we could splice them into any other audio.
  * **Repeat**.  Repeating is pretty easy, if someone wants to repeat a portion of the audio with a particular delay in-between.  This potentially gives more control than just having the ringtone looped when it plays back.

## Credits ##

Ringdroid's primary developer is Dominic Mazzoni, a Google employee who was also the original author of [Audacity](http://audacity.sourceforge.net), a cross-platform audio editor for desktop computers.

Joseph Wain did the graphics and helped with the UI layout, and Eugene Koh acted as an internal advocate to make sure that Ringdroid was completed and open-sourced in time for the release of the first Android phone.

## Join the team ##

This project is open-source.  If you are a programmer, we would welcome your contributions.  Please start by following the instructions on [Building](Building.md).

If you are not a programmer, you're also welcome to contribute in other ways.  Submitting bug reports and feature requests is always welcome, although please be careful not to submit just anything as a feature request before checking to see if it's possible with Android.  For example, playing protected iTunes audio files is impossible at this time.