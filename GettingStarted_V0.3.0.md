**Version:** 0.3.x

## Getting started with SDRTrunk ##

SDRtrunk is an integrated application for demodulating radio signals and 
decoding trunked radio network protocols and some related radio signal formats.  The 
application does NOT require a discriminator tapped scanner and it does NOT
require the use of audio piping applications like Virtual Audio Cable.  All
connections between the tuner or sound card and the decoders is provided by the
sdrtrunk application.

SDRTrunk uses channel definitions to configure and setup each demodulation and decoder
processing sequence.  In order to successfully decode radio signals, each channel configuration requires:

* **Source** - specifies where to get the radio samples from (tuner or sound card)
* **Decoder** - which demodulator or decoder to use in processing the source samples

Each channel definition allows you to optionally configure:

* **Aux Decoder** - additional in-band audio digital signal protocol decoding
* **Logging** - log decoded messages or events
* **Recording** - record audio calls or digitized baseband samples

The SDRTrunk application is programmed in Java and can run on any computer where Java is supported
for the operating system and where the computer hardware (processor/memory) is sufficient for the 
processing workload.

### Setup ###

  * [Linux](SetupLinux_V0.3.0.md)
  * [Windows](SetupWindows_V0.3.0.md)

### Application Overview ###

The [application overview](v0.3/ApplicationOverview_V0.3.0.md) article describes the various
components in the sdrtrunk application

### Configuration ###

The Channels tab at the center of the application is the central control for configuring and 
managing channel definitions.  Please refer to the [Channels](Channels_V0.3.0.md) wiki page for
instructions on creating channel definitions and starting channels decoding.

