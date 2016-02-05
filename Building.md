This page is for developers.  You should have some Java experience and an interest in learning the Android SDK before proceeding.  You do _not_ need to own an Android-compatible mobile phone in order to develop; Ringdroid works perfectly on the emulator that's included with the SDK.

To play with Ringdroid on the Emulator if you're not a developer, see [Emulator](Emulator.md).

# Install the Android SDK #

First, download the Android SDK from this location:

http://code.google.com/android/download.html

# Option 1: Apache Ant #

There are two ways to build Android applications: using Apache Ant (a command-line tool, similar to working with a Makefile) or using an Eclipse plug-in (a full graphical IDE).  The instructions for Ant are here; for Eclipse, see below.

If you choose to use Apache Ant, put the path to the "tools" directory from the SDK into your path, and then run this command to generate a build.xml file:

`android update project -n ringdroid -t 2 -p .`

To build, just run:

`ant debug`

This will generate a debug Android package (.apk) file in the "bin" directory, which you can install on an Android emulator or on an actual handset.  Ringdroid won't work without an SD Card, so you should make sure that you create an SD Card disk image if you're going to try Ringdroid with an emulator.

For information on how to run the emulator and set up an SD card, see: http://code.google.com/android/reference/emulator.html

Once your emulator is running, use this command to install the debug APK on your emulator:

`adb install -r bin/ringdroid-debug.apk`

This same command works if you have a handset attached via USB.  Use the "-d" and "-e" commands to direct an install to the device or emulator, respectively.

# Option 2: Eclipse #

Someone who uses Eclipse should write this section specifically for Ringdroid.  In the meantime, see these links:

  * Download Eclipse: http://www.eclipse.org/downloads/

  * Installing the Eclipse plug-in: http://code.google.com/android/intro/installing.html#installingplugin

# Release #

For development team members only:

http://code.google.com/android/intro/develop-and-debug.html

```
ant release
cp bin/ringdroid-unsigned.apk bin/Ringdroid.apk
jarsigner -keystore ringdroid.keystore bin/Ringdroid.apk ringdroid
```

Initial key generated with:

`keytool -genkey -keystore ringdroid.keystore -alias ringdroid -validity 10000`