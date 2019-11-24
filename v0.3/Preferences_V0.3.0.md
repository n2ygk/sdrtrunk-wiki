Preferences
---
The preferences dialog allows you to change settings that affect the way
that sdrtrunk operates and displays decoded data.

![Figure 1: Preferences Dialog](v0.3/images/Preferences_V0.4.0.png)

**Figure 1:** Preferences Dialog

Each section of the preferences dialog is detailed below.

Decoder
---
#### JMBE Audio Library
Use the **Change...** button to specify the location for the optional JMBE audio 
library that can be used for decoding digital audio like P25 Phase 1 and 2.

Display
---
Settings to change the way that decoded values are displayed in the application.

#### Channel Events
Choose the timestamp format that is used in the Events tab.

#### Talkgroups
Customize the display format for talkgroup values produced by each of the decoders.

**Decimal** - Base 10 decimal format (0 - 9)
**Hexadecimal** - Base 16 format (0 - 9 and A - F)
**Formatted** - default format for the decoder (either Decimal or Hexadecimal)
**Fixed Width** - when checked, adds leading zeros to make all of the displayed values have the same width

File Storage
---
Customize the file system directories and locations used by sdrtrunk.  

By default, a base folder **SDRTrunk** is created in your user directory and all
other folders are created below that folder.  You can use the **Change ...## button
to customize any of the locations.

**Application Root** - base directory for all sdrtrunk generated data and logging folders 
**Application Logs** - log files that are created each time the application runs
**Event Logs** - event logs produced by each decoder channel when you enable event logging.
**Playlists** - playlist configuration file(s)
**Recordings** - all audio, baseband and MBE recordings are stored here
**Screen Captures** - screen capture pictures created by the user
**Streaming** - temporary streaming audio file queue.

Source
---
Settings for application data sources like tuners and wideband recordings.

#### Channel - Multiple Frequency
The multiple frequency tuner source feature allows you to specify multiple frequencies
to monitor for a system that uses rotating control channels.  The **Rotation Delay** value
indicates the number of seconds that sdrtrunk should remain on a channel that has
stopped decoding before moving to the next frequency in the list.  The application will
continue to try each frequency in the list until it discovers an active signal
to decode.

#### Tuner Channelizer
This setting allows you to choose which channelizer sdrtrunk should use.  The channelizer
is used to breakup a wide signal that you normally see from a tuner into a number
of smaller channels that are used by each of the decoders.

**Channelizer Type** - choose between **Polyphase** and **Heterodyne**

**Polyphase** is the default type and provides the best channelization with minimal to 
no bleed over from adjacent channels.  

**Heterodyne** is less processor intensive and may be appropriate for lower powered
processors.  However, this channelizer does not provide the best filtering and
some bleed over from adjacent channels can impact the performance of decoders.  This
bleed over is only an issue if you have strong signals on adjacent channels next
to the channel that you are decoding.

