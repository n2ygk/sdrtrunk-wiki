# sdtrunk - Frequency Asked Questions (FAQ)

## Decoders

### MPT-1327

***

#### How do I recover the channel map for an MPT1327 system if I only know the control channel frequency?

Setup a channel configuration to monitor the control channel frequency for a period of time.  Using the events tab, catalog all of the logical channel numbers that are referenced for call events.  sdrtrunk will tell you that it doesn't know the frequency, but that's ok, we just want the channel numbers being used by the system for traffic channels.

Next, you'll need to discover which additional frequencies are being used by the system.  There are two potential options:

**Option 1** - Lookup the frequencies from the license

1. Find the government (FCC?) issued license for the system operator and catalog all of the frequencies that they're authorized to use, including the one you already know (ie control channel).  
1. Create MPT1327 decoder channels on each of these additional frequencies and run those channels.  
1. At the end of each call the system will transmit a series of CLEAR messages that tell the radio(s) to return to the control channel, using the logical channel number for the control channel.  From there you have your first confirmed logical channel to frequency mapping, for the control channel. 
1. Continue monitoring the control channel activity to correlate the call event channel numbers to the channel frequency that becomes active for each call event to recover the logical channel number to frequency mappings for the traffic channels.

**Option 2** - Watch the spectrum for traffic channels to become active.

1. Monitor the control channel events tab and watch for channel grant events.
2. Watch the spectral display to see when a channel becomes active at the same time as the control channel call grant.
3. Create an MPT1327 channel to decode that traffic channel frequency so that you can capture the CLEAR messages transmitted at the end of the call.
4. When you're successful, you'll have the channel number to frequency map recovered for the traffic channel where the call occurred, and also the channel number and frequency for the control channel.

**Option 3** - Find the Neighbor Control Channels.
Larger MPT1327 systems can have several sites.  Each site will have a control channel.  The system will (generally) use the same channel map across all of the sites.
1. Catalog all of the control channel frequencies that you can find.
2. Decode the control channel messages and watch for Neighbor site announcements and catalog the neighbor control channel numbers.
3. Sort the control channel numbers and the control channel frequencies in numeric order
4. Your lists will generally line-up and you'll end up with recovery of several channel number to frequency values.
5. If your channel numbers and frequencies don't line up, the system may be using overlapping sub-ranges and you'll need to do a bit more work.
5. Go the to the 'recover channel maps' section below. 

##### Recover The Channel Maps

UHF - 450 MHz: 

A fairly standard/common channel map to use is one that starts at 450.000 MHz with channel zero or channel 1:

* Base: 450.0000 or 450.0125
* First: 1
* Last: 1023
* Step: 12500

VHF - 150-180 MHz:

VHF frequency allocations normally don't follow a clean 12.5 kHz channel raster/spacing and MPT-1327 systems can use several channel ranges that overlap each other so that they can align the channel number ranges that follow a 12.5 kHz channel spacing with the actual licensed frequencies that don't follow a 12.5 kHz channel spacing.

There are also MPT1327 systems that use other channel spacings.  An alternate example might be 20 kHz (20000 Hz) channel spacing.

MPT1327 uses channel numbers in the range of 1 to 1023.  A channel step size (ie spacing) of 12.500 kHz is common.  System operators can segment the allowable channel number range into smaller sub-ranges with each using a different base frequency, possibly in chunks of 100 or 200, to map all of their authorized frequencies to logical channel numbers that the MPT1327 system can use.  For example:

Range 1:
* Base: 150.000000
* First: 1
* Last: 199
* Step: 12500

Range 2:
* Base: 150.006250
* First: 200
* Last: 399
* Step: 12500

From these two examples, a system could map a channel number to any frequency that is a multiple/spacing of 6.25 kHz, despite the fact that the system requires that the sequential channels in a range are spaced 12.5 kHz apart.  As an example, here are the first few frequencies for these two ranges using a 6.25 kHz channel spacing:

* 150.00000 = Channel 1
* 150.00625 = Channel 200
* 150.01250 = Channel 2
* 150.01875 = Channel 201

Once you have your first control or traffic channel number to frequency recovery, you can create your first range of your channel map.  For example, if you've discovered that channel 215 is frequency 152.6875, you can create the following channel map:

* Base: 152.6875
* First: 215
* Last: 1023
* Step: 12500

Monitor the system for a period of time using this channel map.  Watch when call events happen and listen to the call audio.  If sdrtrunk creates a traffic channel and there's nothing but static, then the mapping is incorrect for that channel number and that channel number should be excluded from your initial (first-last) channel range.  You can do this by decreasing the value for the last channel number in your channel map to just below the channel number that was incorrect.  Generally, the channel number ranges will follow a pattern like 1-199, 200-399, 400-599, etc.

You should note that the above channel map is functionally equivalent to this channel map:

* Base: 152.6750
* First: 214
* Last: 1023
* Step: 12500

In this second channel map example, we just subtracted 12.5 kHz from the base frequency and decreased the first channel number by one.  Using this new range would still map channel 215 to 152.6875 MHz, the same as the first map.  So, in this way, you can adjust your channel map to include lower channel numbers in your range to test if those lower channel numbers are also part of this range, or if they belong in a separate channel map range.

It's best to use a spreadsheet when you're trying to recover the channel number ranges since you can create formulas to auto-calculate the frequencies from the channel numbers using different base frequencies, step-sizes, and channel number first-last ranges.  However, if you are able to recover several channel number to frequency mappings, post a new topic here on the Discussions tab, or post a question on Radio Reference and ask for help figuring out the channel map.

***

## Tuners

### Unable To Source Channel From Preferred Tuner

What does this error mean?

```
2024-12-02 21:18:21.412 INFO  i.g.d.s.t.m.TunerManager - Unable to source channel [851187500] from preferred tuner [RTL2832 SDR/R820T 00000001] - searching for another tuner  [572MB/630MB 90%]
```
It means that you have selected a preferred tuner in your channel configuration for your control channel and sdrtrunk is trying to also allocate a traffic channel for that same tuner.  However, sdrtrunk can't allocate the channnel/frequency from the preferred tuner.  There are two possible reasons why this happens:

1. The preferred tuner is already tuned to another frequency and it can't fit the new channel together with all of the current channels within the tuner's bandwidth.

2. The preferred tuner that you selected in your channel configuration is no longer available in the system. 

In the first issue, sdrtrunk will search for another tuner for the traffic channel.  If it can't find a tuner you'll see a call detected event where the details indicate NO TUNER AVAILABLE.  The solution is to add another tuner so that sdrtrunk can tune the additional traffic channel.

For the second issue, you can select another preferred tuner in the channel configuration so that sdrtrunk stops trying to find a non-existent tuner.

### SDRPlay

***

#### How do I set the gain on SDRPlay RSP tuners?
A: Gain usage for the RSP tuners works differently than other tuners supported by SDRTrunk.  Per recommendation of the SDRPlay engineers, you should **Enable AGC** and **Set Gain to Maximum**.  After doing this, if you are seeing the **Gain Overload** indicator, you can reduce the gain level. 

***

#### How can I use SDRPlay receivers on a Mac OS Computer?

##### A: **SDRPlay API version 3.12+ for Mac OS**

A new release of [API](https://www.sdrplay.com/api/) version 3.15 of the Mac OS API was published on 7-May-2024.  This release enables sdrtrunk to use the SDRPlay receivers without requiring any additional steps.  If you downloaded and installed a Mac OS API version prior to this release date, download a fresh copy and reinstall it.

You may also need to make sure the API service is loaded. If you start sdrtrunk and it reports not
finding any RSP devices yet you're sure one is plugged in then it may be because the API service
is not present:
```
INFO  i.g.d.s.t.m.TunerManager - Discovered [0] RSP devices from SDRplay API
```

You can load and check for the service with these steps:
```
$ cd /Library/SDRplayAPI/3.15.0
$ launchctl load plist/com.sdrplay.service.plist
$ launchctl list | grep sdrplay
-	78	com.sdrplay.service
```

 
##### A: **SDRPlay API version 3.11 (and older) for Mac OS**

Java is unable to use the SDRPlay API installed driver as it is named, so you have to create a symbolic link to the driver that uses the filename that sdrtrunk is expecting.  The SDRPlay folks are going to update the installer in a future release to use the *.dylib file extension for their Mac OS driver.

Type the following in a console window and then start/restart sdrtrunk:
```
sudo ln -s /usr/local/lib/libsdrplay_api.so /usr/local/lib/libsdrplay_api.dylib
```

***
## Launching sdrtrunk Application

***

### MacOS

Version 13.5.1+

1) download the zip file, unzip if needed
2) use Terminal, cd to the bin directory
3) run: ./java
4) it will "fail"
5) Open up Privacy & Security settings, scroll all the way down
6) There will be a small notice - *"java" was blocked from use because it is not from an identified developer. *. Press the "Allow Anyway" button and authenticate
7) Repeat the same steps for ./sdr-trunk; you may see *another* notice about Java not being verified, press Open

Up to Version 13.4

1) download the zip file, unzip if needed
2) In the /bin directory of the application 
3) Right click > Open on java and accept the prompt

***

## General

***

### What does **Audio segment detected with NO to identifiers** mean?

This indicates that sdrtrunk decoded an audio call but it didn't detect any TO radio or talkgroup identifiers.  This can happen when the decode quality is poor and sdrtrunk decodes just enough audio frames to create an audio segment (ie a call), but didn't decode any of the messaging that carries the radio identifiers for that specific call.
