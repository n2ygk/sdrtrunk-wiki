# Fleetsync II Decoder #

Fleetsync is a digital radio identifier, status, GPS, and data protocol that is normally used in addition to other trunked radio protocols and/or on conventional radio channels. The decoder decodes Automatic Number Identification (ANI), Acknowledgements, Status and GPS messages.  If you discover additional message types, please share them with the author for inclusion in the decoder.

## GPS ##

GPS data bursts normally occur on a conventional radio channel, separate from normal voice communications.  Each mobile radio has a unique timestamp that tells it when to broadcast, so that users don't broadcast on top of each other.  In addition to the defined time to transmit, radios are told how often to broadcast.  Broadcast updates of 1, 3, 5 and 6 minute intervals have been observed.

Smaller fleets may broadcast more often.  Larger fleets will broadcast less often, because each radio must have an opportunity to broadcast at least once within the repeat interval.

## Status ##

Mobile radios are programmed with a pre-defined list of canned status messages.  The decoder will display the status number received.  If you can determine the meaning of each status number, you can alias the status number with a status alias identifier so that the meaning is displayed, instead of the status number.

## Acknowledge ##

Some radio networks will acknowledge status messages.  When this happens, the mobile radio will broadcast a status message, and the network will immediately respond with an acknowledgement.

## Aliases ##

Add the following aliases to each alias list you are using for Fleetsync:

  * 099-0999 Broadcast Call
  * `*``*``*`-0999 Fleet Call
  * 099-`*``*``*``*` Supervisor Call
  
## Decoder Setup - Conventional or Repeater Network ##

Setup a decoding channel with a NBFM decoder and select MDC1200 in the aux
decoder configuration tab.

## Decoder Setup - Analog Trunked Network ##

Setup a decoding channel with one of the analog trunked radio decoders (LTR,
LTRNet, Passport, etc) and select MDC1200 in the aux decoder configuration tab.  