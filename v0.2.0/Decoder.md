# Decoders #

Each decoding [channel](Channel) can have one primary decoder and one or more 
auxiliary decoders.  If you want to run multiple primary decoders on the same
frequency, create separate channels for each primary decoder.

## Primary Decoders ###

  * [AM](AM) - AM demodulator
  * [LTR-Standard](LTR) - FM demodulator and Logic Trunked Radio (LTR) trunked radio signaling decoder
  * [LTR-Net](LTRNet) - FM demodulator and LTR-Net trunked radio signaling decoder
  * [MPT-1327](MPT1327) - FM demodulator and MPT-1327 trunked radio signaling decoder and automatic trunked channel following.
  * [NBFM](NBFM) - narrow-band FM demodulator.
  * [Passport](Passport) - FM demodulator and Passport trunked radio signaling decoder.
  * [P-25 Phase 1 C4FM](APCO25) - FM demodulator with P25 message decoder and automatic trunked channel following.
  * [P-25 Phase 1 LSM](APCO25) - Quadrature demodulator with P25 message decoder and automatic trunked channel following.
  
## Auxiliary Decoders ##
Auxiliary decoders are designed to process demodulated audio or in-band 
signalling that is normally layered on top of another digital protocol or FM
modulated analog repeater channel.  These layered protocols provide services 
like Automatic Number Identification (ANI), status messaging, GPS location, 
emergency notification, etc.  Auxiliary protocols may be transmitted when the 
mobile radio user keys the microphone, or in the case of GPS, they can key the 
radio and transmit the GPS location without any user actions.

How do auxiliary decoders work?  Demodulated audio from a primary decoder that uses
an FM demodulator is simultaneously routed to each of the auxiliary decoders
and the decode results and added to the Events and Messages lists, as well as
displayed in the [decoding channel](DecodingChannels) windows.

Auxiliary decoders are normally used with analog decoders like NBFM, LTR, 
LTR-Net, and Passport.

  * [Fleetsync II](Fleetsync2Decoder) - decodes ANI, Acknowledge, Status, Paging and GPS bursts
  * [LJ1200](LoJackDecoder) - decodes LoJack data bursts on 173.075 MHz in US.
  * [MDC-1200](MDC1200Decoder) - decodes MDC-1200 ANI bursts.
  * [Tait 1200](TaitDecoder) - decodes Tait CCDI protocol GPS location bursts.

**Note**: there are a wide variety of these auxiliary service protocols that can be 
easily added to SDRTrunk.  If you encounter a new audio-band protocol, collect
a number of good quality samples and send them to the author via the google 
support group for possible inclusion in the sdrtrunk application.   