# Overview

The application supports streaming of multiple audio calls to multiple remote audio streaming servers.  Audio calls are temporarily recorded to disk in MP3 audio format.  The temporary recording is then queued for broadcast with one or more audio streams.  Streaming uses aliases to identify which stream(s) will broadcast the audio recording.  Each temporary recording contains metadata about the call that is also forwarded to the streaming server.

This concept allows you to create simple single channel audio streams or very complex audio streams that are combined from multiple radio systems or radio users. For example, you could monitor a group on a P25 system and a related separate group on an LTR system and combine all calls from both systems into a single broadcast channel.

Temporary audio recordings that are queued for streaming in the order received.  When the streaming queue is empty, MP3 silence frames are streamed to maintain a consistent connection to the remote server.  When silence is streaming, the metadata is updated to read 'Scanning...'.

## Supported Servers

The following servers are supported:
* [Broadcastify](http://www.broadcastify.com/)
* Icecast Version 2.3.x (TCP connection)
* [Icecast Version 2.4.1+](http://icecast.org/) (HTTP 1.1 connection)
* Shoutcast 1.x
* [Shoutcast 2.x/Ultravox 2.1](http://wiki.shoutcast.com/wiki/SHOUTcast_Broadcaster)

## Audio Format
* MP3 lossless audio compression
* Constant Bit Rate (CBR)
* 8000 Hz Sample Rate
* 16-bit samples

## Setup an Audio Stream
1. Click the **Streaming** tab
2. Click the **New** button and select the streaming server type
3. Create a unique name for the channel (each stream requires a unique name)
4. Fill in the server-specific stream details
5. Click **Save**
6. Attach this stream to one or more Aliases.

## [Aliases](Alias) and Broadcast Channels

Aliases are used for designating specific radio users and/or groups for streaming.  You can attach one or more Broadcast Channel identifiers to each alias.  When a call occurs, it is temporarily recorded to disk in MP3 format.  Once the recording is complete, it is queued for broadcast with each broadcast channel that is listed for each and every alias involved in the call.  

For example, if you have a call from radio ID 123456 to talkgroup ABCD and the radio ID has Channel A and Channel B attached, and the talkgroup has Channel B and Channel C attached, then the call would be streamed to all three channels. 

### Attaching a Broadcast Channel to an Alias
1. Create an [Alias List](AliasList) and attach it to your decoding [Channel Configuration](Channel)
1. In the **Aliases** tab, select the alias you want to stream
1. In the Alias editor screen, switch to the **Audio/Identifier** tab
1. Click **New** and select **Audio Broadcast Channel**
1. In the drop-down list, select the Broadcast Channel that you have previously configured
1. Click **Save**
1. Repeat these steps to add additional broadcast channels for the alias.

### Viewing Streaming Status

Select the View menu at the top of the application window and click on the **Show Streaming Status** menu item to turn on the streaming status panel at the bottom of the application window.  This allows you to view the 'Now Playing' window, channel details windows, and monitor your streaming status at the same time.

