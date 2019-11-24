# JMBE Library #

The Java Multi-Band Excitation (JMBE) library provides decoder support for 
converting IMBE encoded audio frames to normal audio so that you can listen to 
the audio calls over your computer speakers.

Website: [JMBE](https://github.com/DSheirer/jmbe)

## Patent Warning ##

The JMBE library contains source code that may be patent protected.  Users
should check local laws before downloading, compiling, using, or DISTRIBUTING
compiled versions of the JMBE library.

## Copyright Notice ##

Copyrights for the terms MBE and IMBE are the property of their respective
owners.

## Adding JMBE to SDRTrunk for decoding MBE audio ##

* [JMBE Download Site](https://github.com/DSheirer/jmbe/releases) Follow the instructions on this site for building the JMBE library.

* You can use the compiled **jmbe-x.x.x.jar** file right where you compiled it, or it may make sense to copy it to a more permanent location on your computer that is always accessible for sdrtrunk.

* Start the SDRTrunk application.

* Open the **View >> Preferences** menu item to open the Preferences window.

* In the **Decoder >> JMBE Audio Library** section, click the **Change...** button to specify the 
location for the 'jmbe-1.0.0.jar' library is located. (or whichever version you just compiled)

* Start (or restart) any P25 decoder channels to start using the audio library.

## Troubleshooting ##

SDRTrunk will generate several log entries to let you know if it discovered the jmbe library correctly and where it was looking for the library:

> 16:59:28.404 INFO  i.g.d.a.c.m.JmbeAudioModule - Loading JMBE library from [/home/denny/JMBE/jmbe-1.0.0.jar]

> 16:59:28.415 INFO  i.g.d.a.c.m.JmbeAudioModule - JMBE audio conversion library loaded: JMBE Audio Conversion Library v1.0.0

P25 Phase 1 channels when started will log the following entry:

> 16:59:28.415 INFO  i.g.d.a.c.m.ImbeAudioModule - JMBE audio conversion library IMBE CODEC successfully loaded - P25-1 audio will be available

P25 Phase 2 channels when started will log the following entry:
> 16:59:28.415 INFO  i.g.d.a.c.m.AmbeAudioModule - AMBE CODEC successfully loaded - P25-2/DMR/NXDN audio will be available

Note: Phase 2, DMR and NXDN protocols all use the same audio codec.  Decoder support for DMR and NXDN may be added at a future time