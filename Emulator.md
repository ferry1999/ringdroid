This page contains step-by-step instructions for people who want to try Ringdroid but don't have access to an Android-compatible handset such as the HTC T-Mobile G1.  The emulator that comes with the free Android SDK works perfectly and you can get a great idea of how to use Ringdroid without ever seeing it on a phone.

**Note**: while you do not need to be a programmer in order to follow these instructions, they are still a bit tricky; they're recommended for power users only.

_This wiki page is a work in progress.  Please contribute by helping to make it more clear, or add detailed instructions for other operating systems!_

# Mac OS X (Intel) #

  * Go to the SDK download page here: http://code.google.com/android/download.html - click "I agree to the terms of the SDK License", and click "Continue".
  * Click on the link to the package android-sdk-mac\_x86-1.0\_r1.zip, next to "Mac OS X (Intel)"
  * Put the folder somewhere you can find it, like under your home directory
  * Open the Terminal (in Applications => Utlities)
  * Use the "cd" command to change the directory to the location of the Android SDK that you just downloaded.  One way to do this is to drag the folder icon into the Terminal window.  For example: `cd /Users/dmazzoni/android-sdk-mac_x86-1.0_r1/`
  * Now use the "cd" command to go into the "tools" directory within this directory: {{cd tools}}}
  * Create an sdcard with this command: `./mksdcard 256M sdcard1.iso`
  * Type "open sdcard1.iso", and your SD card will be mounted just like any other volume or disk.  Copy files to it, and then eject it from the Finder.
  * Start the emulator with this command: `./emulator -sdcard sdcard1.iso &`
    * If it complains "Cannot create data directory", type "mkdir -p " followed by the directory it wanted, then try again.
  * Wait for the emulator to start up and make sure it's working
  * Download the Ringdroid APK from the "Downloads" section of this site, and put it in the same directory (tools), or somewhere else where you can find it.
  * Run `./adb install -r Ringdroid.apk` to install Ringdroid into this emulator
  * A useful command if you're having SD card trouble: adb remount

# Windows #

See user-submitted comment below.

# Linux (i386) #

  * Go to the SDK download page here: http://code.google.com/android/download.html - click "I agree to the terms of the SDK License", and click "Continue".
  * Click on the link to the package android-sdk-linux\_x86-1.0\_r1.zip, next to "Linux (i386)"
  * Unzip the directory somewhere you can find it, like under your home directory
  * Open a new shell window and "cd" into the "tools" directory inside of the SDK directory you just unzipped.
  * Create an sdcard with this command: `./mksdcard 256M sdcard1.iso`
  * Start the emulator with this command: `./emulator -sdcard sdcard1.iso &`
  * Wait for the emulator to start up and make sure it's working
  * Download the Ringdroid APK from the "Downloads" section of this site, and put it in the same directory (tools), or somewhere else where you can find it.
  * Run `./adb install -r Ringdroid.apk` to install Ringdroid into this emulator
  * Put sound files onto the sdcard using the "adb push" command: `adb push Song.mp3 /sdcard/Song.mp3`, but you may need to restart the emulator with -wipe-data in order for these to be recognized.
  * Another useful command if you're having SD card trouble: adb remount