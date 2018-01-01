# Decoders #

Each decoding [channel](Channel) requires one primary decoder and can optionally
have zero or more auxiliary decoders running at the same time.  If you want to 
run multiple primary decoders on the same frequency, create separate channels 
for each primary decoder.

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
signaling that is normally layered on top of another digital protocol or FM
modulated analog repeater channel.  These layered protocols provide services 
like Automatic Number Identification (ANI), status messaging, GPS location, 
emergency notification, etc.  Auxiliary protocols may be transmitted when the 
mobile radio user keys the microphone, or in the case of GPS, they can key the 
radio and transmit the GPS location without any user actions.

How do auxiliary decoders work?  Demodulated audio from a primary decoder's FM 
demodulator is simultaneously routed to each of the auxiliary decoders
and the decode results are added to the Events and Messages lists, as well as
displayed in the [decoding channel](DecodingChannels) windows.

Auxiliary decoders are normally used with analog decoders like NBFM, LTR, 
LTR-Net, and Passport.

  * [Fleetsync II](Fleetsync2) - decodes ANI, Acknowledge, Status, Paging and GPS bursts
  * [LJ1200](LoJack) - decodes LoJack data bursts on 173.075 MHz in US.
  * [MDC-1200](MDC1200) - decodes MDC-1200 ANI bursts.
  * [Tait 1200](Tait1200) - decodes Tait CCDI protocol GPS location bursts.

**Note**: there are a wide variety of these auxiliary service protocols that can be 
easily added to SDRTrunk.  If you encounter a new audio-band protocol, collect
a number of good quality sample recordings and contact the author via the 
google support group for possible inclusion in the sdrtrunk application.   