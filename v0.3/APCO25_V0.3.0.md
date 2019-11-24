# APCO-25 Decoder #

The P25 decoder processes all voice, trunking, and data messages and provides
traffic/voice/data call following when a tuner is available that can monitor
both the control channel and any traffic channels within the available bandwidth
of the tuner, or across multiple tuners.

## P-25 Phase I
Decodes FDMA Common Air Interface (CAI) C4FM modulation and Linear Simulcast 
Modulation (LSM).

## P-25 Phase II
Phase II TDMA (2 timeslot) traffic channel decoding.

## P-25 Phase I/II
P25 Phase II systems use both a Phase 1 control channel and Phase I and Phase II
traffic channels, providing transition support for users with a combination of
Phase I and Phase II radios.

## Audio Vocoders 

### IMBE ###
APCO-25 Phase I audio calls use the IMBE vocoder for digital audio.

### AMBE ###
APCO-25 Phase II audio calls use the AMBE vocoder for digital audio.

SDRTrunk supports the JMBE library for decoding both IMBE and AMBE digital 
audio, but DOES NOT include the jmbe library in the normal application download.
You must download and compile the library and use the **View >> Preferences** menu
to specify the location of the compiled JMBE library (jmbe-x.x.x.jar).

[JMBE library](https://github.com/DSheirer/jmbe)

[How To Setup JMBE](JMBE)

### VSELP ###
SDRTrunk recognizes VSELP audio CODEC messages and will display them in the
messages tab during decoding.  However, it will not decode the audio.

## Traffic Channel Following ##
The P25 decoder provides full traffic channel following when monitoring a P25
control channel.  You can optionally select to not follow data calls in the 
decoder configuration when setting up the channel for decoding.

## Talkgroups and Addresses ##

All talkgroups and radio addresses are presented in decimal or hexadecimal 
(base-16) notation (see Preferences).  

### **Talkgroups**: 1 - 65,535
### **Individual Radio Identifiers**: 65,636 - 16,777,211

Packet data IP Version 4 addresses will normally show in the from column of the
events window and the Logical Link ID (radio address) will show in the from
column with the radio's IP Version 4 address listed in the details column. If
the data contains UDP over IP protocol, the UDP source and destination ports
will be appended to the IP address.

## Aliases ##

You can create an Alias List and attach it to your P25 decoder in the channel
configuration window.

When aliasing talkgroups and radio addresses, you can use either a single talkgroup decimal value, or you can enter a range of talkgroup decimal values.

Optionally, add these trunking system unit ID values to your alias list:

16,777,212 = (Trunking) System Controller.  
16,777,213 = Registration Controller
16,777,215 = All Call 

## Modulation ##

Choose either C4FM or LSM Simulcast (CQPSK) modulation for Phase 1 channels in the channel configuration
decoder tab.  When you select the P25 Decoder from the drop-down list, the
modulation selector list will appear.

## Monitoring a P25 Trunked System ##

Setup a channel to decode the trunked system's control channel only.  The decoder 
will automatically detect when additional traffic channels are allocated for 
calls and will create temporary decoding channels in the application to process 
each of these calls.  

You do NOT need to create decoding channel configurations for each of the 
traffic channel frequencies used by the system because the control channel will 
tell the sdrtrunk application every thing that it needs to know in order to 
setup a temporary decoding channel.

**Note**: Phase 2 capable trunked systems will use a Phase 1 control channel
with Phase 2 traffic channels.  You only have to setup one channel configuation
for the Phase 1 control channel.  The Phase 2 traffic channels will be
automatically created by sdrtrunk as each call occurs.

### Traffic Channel Pool Size ###

When configuring the P25 control channel decode configuration, use the Traffic
Channel Pool setting to set the maximum number of temporary traffic channels 
that can be running at the same time.  The sdrtrunk application will create
channel configurations up to this maximum number and reuse the channel 
configurations for subsequent calls.

The default value of 4 traffic channels in the pool is suitable for a modern
powerful processor.  You can increase this value to match the number of traffic
channel frequencies for the system your are monitoring, provided your computer
is capable of running that many channels at the same time.  You may have to reduce 
this pool size if you are using a lower powered CPU.  Monitor the computer's CPU 
and memory consumption and adjust this value as needed.  Note: you'll have to 
stop and restart the decoding after you change the traffic channel pool size 
value and save it.

## P25 Decoding Example ##

The following screenshot shows the application configured to decode one P25
control channel.  It also shows 3 traffic channels being decoded where the 
call event was decoded on the control channel and sdrtrunk automatically 
created the 3 decoder channels to follow the calls.

