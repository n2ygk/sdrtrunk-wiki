## Getting started with SDRTrunk ##

SDRtrunk is an integrated application for demodulating radio signals and 
decoding trunked radio network and some related radio signal formats.  The 
application does NOT require a discriminator tapped scanner and it does NOT
require the use of audio piping applications like Virtual Audio Cable.  All
connections between the tuner or sound card and the decoders is provided by the
sdrtrunk application.

SDRTrunk uses channel configurations to setup a demodulation and decoder
processing sequence.  In order to successfully decode radio signals, each 
channel configuration requires:

* **Source** - specifies where to get the radio samples from (tuner or sound card)
* **Decoder** - which demodulator or decoder to use in processing the source samples

Each channel configuration allows you to optionally configure:

* **Aux Decoder** - additional in-band audio protocols
* **Logging** - log decoded messages or events
* **Recording** - record audio calls or digitized baseband samples

The SDRTrunk application is programmed in Java and can run on any computer where
the there is Java available for the operating system and the computer hardware
(processor/memory) is sufficient for the processing workload.

### Setup ###

  * [Linux](SetupLinux)
  * [Windows](SetupWindows)

### Application Overview ###

The [application overview](ApplicationOverview) article describes the various
components in the sdrtrunk application

### Configuration ###

The configuration window/tab at the center of the application is the central
control for configuring tuners and creating/managing channel configurations, 
aliases and channel maps.

Channels are organized by [System](System) and [Site](Site).  The system and 
site labels can be anything that you want to name them and allow you to setup
your configurations to mirror actual radio network configurations.

### Setup a Channel for Decoding ###

In the Configuration tab at the center of the application window:

1. Click on the 'Tuners' tree branch and verify that the application recognized one or more [tuners](Tuner).
1. Right-click on 'Systems' tree branch and create a system - type a system name and click 'Save' in the editor.
1. Right-click on the system tree branch that you created and add a Site - type a site name and click 'Save' in the editor.
1. Right-click on the site tree branch that you created and add a Channel.
1. Type in the channel name.
1. In the Source tab, select Tuner from the Source drop-down menu and type in the frequency that you want to monitor
1. In the Decoder tab, select a decoder.  The default options can be changed, but should be sufficient for a quick start.
1. Click 'enabled' so that channel decoding starts when you hit save.
1. Click the save button. 

If everything is configured correctly and the application can use the tuner to
tune to the frequency that you entered, you should see a [channel](DecodingChannel) 
display appear in the lower-left corner of the application that will show the 
status of the decoding process.

Click on this [channel](DecodingChannel) to select it.  Then, click on the 
[Messages](Messages) tab or the [Events](CallEvents) tab to see the decoding
results. 

### Alternate Quick Start - SDR Dongle ###

1. In the Configuration tab, select a tuner to display in the spectral display
by right-clicking on the tuner tree branch and select 'Show in Main Spectrum'.
1. Left-click the tuner and in the [editor](Editor) window, tune to a frequency 
near the channel that you want to decode.  Do not tune the channel into the 
center of the display.  Adjust the frequency so that the channel is either to 
the left or to the right of the center of the display.
1. Right-click on the frequency in the [spectral display](SpectralDisplay) and 
choose **Add Decoder** and select the type of decoder that you want to use.
1. If a tuner is available, the channel will immediately start decoding with
default settings and a [channel](DecodingChannels) will appear in the lower-left
window of the application. Left-click the channel display to select the channel
and then click on the Messages or Events tab to see the decoding results.
