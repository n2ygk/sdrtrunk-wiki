# sdrtrunk User Manual
The sdrtrunk user's manual is documented across several wiki pages that are accessible from the
sidebar menu displayed alongside each wiki page.  This user's manual overview wiki page details
high-level concepts and themes and then directs the reader to the appropriate wiki page that 
details how to use the sdrtrunk application feature.

<!-- TOC -->
* [sdrtrunk User Manual](#sdrtrunk-user-manual)
  * [Getting Started](#getting-started)
  * [Concepts](#concepts)
    * [Where To Find Radio Signals](#where-to-find-radio-signals)
    * [Tuners & Software Defined Radios (SDR)](#tuners--software-defined-radios--sdr-)
    * [Channels](#channels)
    * [Decoders](#decoders)
    * [Aliases](#aliases)
    * [Audio Playback](#audio-playback)
    * [Audio Recording](#audio-recording)
    * [Audio Streaming](#audio-streaming)
<!-- TOC -->

## Getting Started
The [Getting Started](Getting-Started) wiki details the steps that you need to complete to initially setup the software 
and related SDR and tuner hardware devices.

## Concepts

### Where To Find Radio Signals
The radio frequency spectrum is very wide and diverse and it can be challenging for new users to figure out where in the
radio frequency spectrum they can find signals to decode and listen to audio.  Software Defined Radios (SDR) can tune
into most of these frequency bands across the spectrum.  However, the sdrtrunk application is designed to work with 
a small subset of these radio bands, primarily the AM and FM bands and the commercial and trunked radio bands.

* **[Radio Reference](www.radioreference.com)** - the radio reference website provides crowd-sourced observations and 
government-published details about radio systems and users around the world.  sdrtrunk's [Playlist Editor](Playlist-Editor) 
includes a plugin to browse and select radio channels and automatically setup channel configurations to to tune and
decode the channels so that you can listen to audio.  You need a [Premium Subscription](https://www.radioreference.com/premium/) 
to access the radio reference database from sdrtrunk's playlist editor. 

* **[RTL-SDR.com](https://www.rtl-sdr.com/)** - this website is geared to the SDR hobby but also includes blog entries 
* and a Signal ID wiki to help you visually identify signals you may see in the radio spectrum.
* **Other Websites/Social Media** - there are many social media and local and regional websites that contain details on 
radio systems and signals that you may encounter when using sdrtrunk and other SDR applications.
* **Just Start Exploring** - sdrtrunk allows you to manual tune and view the radio spectrum around you and then you can 
select radio channel frequencies to decode.

### Playlist Editor
The playlist editor is the central tool for configuring the sdrtrunk application to decode radio signals.  sdrtrunk uses 
the concept of playlists to organize channels and aliases.  The [Playlist Editor](Playlist-Editor) wiki contains 
information to help you understand how to configure channels, decoders and aliases.

### Tuners & Software Defined Radios (SDR)
sdrtrunk uses SDRs/Tuners to select individual radio channels for decoding.  SDRs can tune/receive a wide chunk of radio 
spectrum that contains many individual radio channels.  Unlike a traditional radio scanner, sdrtrunk can tune and decode 
all radio channels that are present in this wide tuner spectrum provided by the SDR, at the same time.  

sdrtrunk can also record the wide frequency spectrum from SDRs and then mount the wide radio band
recording as an offline tuner for decoding individual channels from the recording.

See the [Tuners](Tuners) wiki page for details on 

### Channels
sdrtrunk uses channel configurations to pull together all of the elements that are needed to decode a radio channel, 
including radio frequency, protocol decoder, logging and audio recording and streaming.  The 
[Playlist Editor](Playlist-Editor) wiki details playlists and channels and how to configure channels
to start decoding.

### Decoders
sdrtrunk includes a number of different radio protocol decoders.  You can select from several primary radio protocol
and additional secondary radio protocol decoders in each Channel configuration.  A primary protocol decoder is one that
decodes teh primary signaling on a digital radio protocol channel.  Secondary decoders work with analog (FM) radio 
channels that employ short digital bursts for Automatic Number Identificaton (ANI) and GPS position reporting and
other auxiliary radio reporting tasks.

Radio protocol decoders are specified for each Channel configuration.  The [Playlist Editor](Playlist-Editor) wiki 
details playlists and channel configurations and how to select decoders for your channel(s).

### Aliases
Modern radio protocols use radio and talkgroup identifiers, IP addresses and other numeric values to 
identify the many entities involved in radio communication.  sdrtrunk provides a rich mechanism for attaching
labels to these identifiers so that you don't have to memorize all of these number values.

However, aliases are much more than simple label substitutions that help you to easily identify radio entities.  Aliases
also control everything that you want to do with the activities and call audio that is associated with each of 
these aliases.  Aliases are a foundational aspect of the way that sdrtrunk manages the decoded 
activies and audio from radio channels and it's important for you understand Aliases and how to use them so
that you can realize the maximum value from the software.

See the [Playlist Editor](Playlist-Editor) wiki for information on using and configuring aliases.

### Audio Playback
The [User Preferences](User-Preferences) wiki describes how to setup your computer for audio playback
and listening to audio produced by each of the decoding channels.

Playback and muting of audio produced by each decoding channel is controlled by Aliases.  See the 
[Playlist Editor](Playlist-Editor) wiki for details on how to configure Aliases to control the playback and
muting of radio audio.

### Recording
Recording of audio produced by each decoding channel is controlled by Aliases.  See the
[Playlist Editor](Playlist-Editor) wiki for details on how to configure Aliases to control recording of call audio.  Additionally, 
the playlist editor wiki provides details on how to setup logging and recording of messages, events, and
baseband sample data produced by the channel decoders.

### Streaming
Streaming of audio produced by each decoding channel is controlled by Aliases.  See the [Playlist Editor](Playlist-Editor) 
wiki for details on how to configure Aliases to control streaming of call audio.
