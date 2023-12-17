# User Preferences Editor
You can access the User Preferences editor from the main application window via the **View** menu.

The user preferences editor contains sdrtrunk application settings that the user can customize.  These
settings are organized by category.

## Audio
The audio tab contains settings for audio playback, recording and call handling.

### Call Management
The call management editor contains settings for managing patch group streaming and duplicate call audio that can occur when 
you are decoding multiple sites or control channels from the same trunked system.  In order for this
duplicate call feature to work you must ensure that each of the decoding channels share a common
**System** name.

![Image of the user preferences editor with the Audio category and Calls Management editor pane showing](https://github.com/DSheirer/sdrtrunk/assets/4079756/65986c06-116b-40f5-8f5d-20a133496032)

#### Duplicate Call Detection
This section contains settings for enabling various methods of duplicate call detection.

* **Talkgroup** - enables duplicate call detection by called talkgroup.  This is the most-common method for
duplicate call detection and handling.
* **Radio ID** - enables duplicate call detection by calling radio ID.  This method of duplicate call 
detection is disabled by default because it can have unintended side-effects as documented in the 
preference editor pane.

#### Duplicate Call Suppression
The settings in this section determines how duplicate call suppression is applied.

* **Listening** - suppress monitoring of duplicate call audio.
* **Recording** - suppress recording of duplicate call audio.
* **Streaming** - suppress streaming of duplicate call audio.

#### Patch Group Streaming.

This setting controls how patch group audio calls are managed for streaming.  The default **Patch Group** setting will stream each patch group call just once using the patch group identifier.  The **Individual Talkgroups** setting will cause the single patch group call to be streamed multiple times, once for each patched talkgroup or radio identifier that is combined within the patch group.  

Note: the **Individual Talkgroups** setting can cause the same call audio to be streamed multiple times where each time the audio is streamed for each distinct talkgroup or radio identifier.  Use caution when assigning talkgroups or radios for streaming to avoid situations where a patched audio call is sent multiple times over the same stream. 

### MP3
The MP3 preference editor contains settings that control the conversion/encoding of decoded audio to MP3
audio format.
![Image of the user preferences editor with the audio category and the MP3 editor pane showing](images/user_preferences_audio_mp3.png "User Preferences Editor - MP3 Audio")

* **Normalize Audio Before Encoding** - enables a process that attempts to normalize the audio volume
before it is encoded to MP3.
* **LAME Encoder Setting** - identifies the MP3 encoding format to use
* **Input Audio Sample Rate** - identifies the input audio format to the MP3 encoder.  sdtrunk uses
an application default of 8kHz sample rate with 32-bit sample size when generating audio.  Selecting
another input sample rate will cause sdrtrunk to resample the audio from the system default format
before it is sent to the MP3 encoder and incur additional CPU processing workload.

### Output / Tones
The output/tones editor controls audio playback device selection and playback tones insertion.
![Image of the user preferences editor with the Audio category and the Output/Tones editor pane showing](images/user_preferences_audio_output_tones.png "User Preferences Editor - Audio Output / Tones")

#### Audio Output Device
* **Audio Output Device** - selects the audio output to use for audio playback.  sdrtrunk attempts
to use the system default audio device which is generally correct for most users.  However, users
with alternate audio hardware configurations can select from among the audio playback devices
provided by the operating system. Click the **Test** button to generate a short tone on the selected
audio output device to verify that sdrtrunk audio playback is configured correctly.

#### Audio Playback Insert Tones
This feature inserts short tones during audio playback to indicate audio playback events.  sdrtrunk
can insert these tones before audio playback to let you know what's going on with audio playback.
* **Start Tone** - a short tone is injected before playback of each audio call.
* **Priority PreemptTone** - a short one is injected when a higher priority call interrupts
playback of the current audio call and starts playback of the higher priority call.
* **Drop Tone** - a short tone is inserted when playback of a call is interrupted and dropped because
an alias associated with the call indicates Do Not Monitor the audio.

You can select from among several tones and tone volumes for each of these tone insert events:
* **Frequency** - controls the frequency of the generated insert tone.
* **Volume** - controls the volume of the generated insert tone.
* **Test** - the selected frequency and volume settings by clicking the test button.

### Record
This preference editor allows you to select the default format for audio recordings.
* **MP3** - the default recording format for all audio recordings.
* **WAVE** - an alternate recording format.

## CPU
![Image of the user preferences editor with the CPU category and the Vector Calibration editor pane showing](images/user_preferences_cpu_vector_calibration.png "User Preferences Editor - CPU Vector Calibration")
### Vector Calibration
The sdrtrunk application can take advantage of advanced CPU processing capabilities called Single
Instruction Multiple Data (SIMD) that enables the CPU to efficiently execute several calculations in parallel
during the same CPU cycle.  The Java runtime was updated starting in JDK 17 to enable Java applications
to use these CPU SIMD instructions.  However, as of Java 19 this SIMD support continues to be in a 
preview status and has not been finalized yet.  Despite this preview status, the capability is 
stable enough for use in the sdrtrunk application.

You may or may not notice any change in the processing workload on your computer with SIMD enabled
or disabled.  Sometimes the performance impacts are minimal.  However, SIMD does speed up some of the
data processing intensive operations by 4x or 8x.

SIMD feature support across CPUs is not consistent and sometimes the SIMD operations can actually run slower
than the non-SIMD operations.  Depending on the CPU, SIMD operations can process 2, 4, 8 or 16 operations
at the same time. For these reasons, the sdrtrunk application has several options available to choose from for various
processing-intensive tasks and the application must choose which SIMD option performs the best on 
your computer.  The best SIMD processing option is determined through the vector calibraton process.

The Vector Calibration feature runs by default the first time that you launch the 
application.  You can choose to cancel this calibration and run it at a later time by clicking the
**Calibrate** button in this editor.

Additional SIMD processing options will be added to the application over time.  As these options
are included in releases, the vector calibration dialog will appear on application startup and 
automatically run the calibration routines for only the newly added processing options.

* **Enable SIMD Vector Operations** - enables using SIMD processing when your CPU supports it.  You
must run the vector calibrations for this to have an effect.
* **Don't Show Calibration Dialog** - disables automatic vector calibration dialog on application startup.
* **Calibrations To Perform** - indicates the number of calibrations that will be run when you click the **Calibrate** 
button
* **Calibrate** - starts the calibration process.
* **Reset All Calibrations** - resets all calibrations to default (ie not calibrated) so that they can be run again.

## Decoder
![Image of the user preferences editor with the Decoder category and the JMBE Audio Library editor pane showing](images/user_preferences_jmbe.png "User Preferences Editor - JMBE Audio Library")
### JMBE Audio Library
The JMBE audio library can be used to decode digital audio frames for some decoders like APCO25 and DMR.  The
sdrtrunk application bundle does not include the JMBE library.  However, you can download the source code for the
JMBE library and compile it yourself and then update sdrtrunk to use that library.

* **Current Version** - displays the current version of the library that's being used by sdrtrunk.
* **File** - file location for the user-created JMBE library.
* **Create Library** - opens a dialog to download the JMBE source code and compile the JMBE Audio Library.
* **Check For Library Updates** - checks to see if there is a newer version of the JMBE library source code.
* **Select** - allows you to select a compiled JMBE library file to use.
* **Reset** - clears the currently selected JMBE library file.
* **Alert when decoder requires missing JMBE library** - when selected, alerts you when you start a channel
with a decoder that requires the JMBE audio library to produce audio, whenever the library is missing.

## Display
### Channel Events
* **Timestamp Format** - selects the display format for timestamps in the Events tab for a decoding channel.

![Image of the user preferences editor with the Display category and the Talkgroup and Radio ID editor pane showing](images/user_preferences_talkgroup_radio_format.png "User Preferences Editor - Talkgroup & Radio ID Formats")
### Talkgroup & Radio ID
Select the display format for talkgroups and radio identifiers for each of the radio protocols 
supported by the sdtrunk application.

* **Decimal** - decimal (base-10) format.
* **Hexadecimal** - hexadecimal (base-16) format
* **Formatted** - custom format generally used for identifiers in that protocol.
* **Fixed Width** - formats all values to the same number of digits, using zero prefix padding as necessary.

## File Storage
### Directories
![Image of the user preferences editor with the File Storage category and the Directories editor pane showing](images/user_preferences_file_directories.png "User Preferences Editor - File Storage Directories")
Select default or alternate file storage locations that sdtrunk uses to store file artifacts.

* **Application Root** - the root folder for all application folders.  When you change this, it changes all of
the other folder preferences to set the root for each of them.  However, you can override these changes
for each of the child folders.
* **Application Logs** - application log files.
* **Configuration** - configuration files used by sdrtrunk
* **Event Logs** - event logs generated by the channel decoders when event logging is enabled.
* **JMBE Libraries** - location where sdrtrunk looks for the JMBE library on startup and the location
where the JMBE audio library will be stored when the user downloads and compiles the library.
* **PLaylists** - sdtrunk playlist directory.
* **Recordings** - folder where channel recordings, tuner wideband recordings, demodulated bit stream
recordings, and MBE frame recordings are stored.
* **Screen Captures** - storage for screen captures generated by the user.
* **Streaming** - temporary folder used for storing audio recordings awaiting streaming.  

## Source
### Tuner Channelizer
SDR tuners capture a broad swath of the frequency spectrum containing multiple radio channels.  sdrtrunk 
employs a channelizer to extract each radio channel for decoding.  sdrtrunk provides two channelizers to choose from.
![Image of the user preferences editor with the Source category and the Tuner Channelizer editor pane showing](images/user_preferences_tuner_channelizer.png "User Preferences Editor - Tuner Channelizer")

* **Heterdyne** - the heterdyne channelizer applies a mixing frequency to mix the channel of interest
down to the zero frequency and then it uses a sequence of half-band decimation filters to incrementally
divide the sample rate and bandwidth in half.  These half-band decimation filters are computationally
efficient.  However, the filters do not provide a sharp cutoff at the channel band edges and this can sometimes 
allow bleedover from strong adjacent channels.  Use this channelizer if you are only decoding a few channels to
reduce the processing workload.
* **Polyphase** - the polyphase channelizer uses a single filter and an FFT to break the entire bandwidth of the SDR
into equal bandwidth channels.  This channelizer is more efficient than the heterodyne channelizer when you are decoding 
three or more channels at the same time.  This is the default channelizer.
