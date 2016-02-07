#SDRTrunk#

SDRTrunk is a java application for decoding and trunk tracking multiple analog 
and digital radio channels across multiple USB dongle tuners and/or sound card 
inputs from scanner radios.

* [Getting Started](GettingStarted)
* [User's Manual](UserManual)
* [Download](https://github.com/DSheirer/sdrtrunk/releases)
* [Support](https://groups.google.com/forum/#!forum/sdrtrunk)

This application uses some of the fantastic components available from JIDE Software.

**Operating Systems**

* [Linux](SetupLinux)
* [Windows](SetupWindows)
* Any operating system supported by Java and libusb, however other systems have not yet been tested 

**Requirements**

* [Java](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html) 7 or newer

[Supported Tuners](Tuner)

  * [Airspy](Airspy)
  * [Ettus B100/WBX Daughter Card](B100)** - (planned).  SDRTrunk will recognize the B100 but it will not allow you to use or configure the B100
  * [Funcube Dongle Pro](FuncubeDonglePro) (1.0)
  * [Funcube Dongle Pro Plus](FuncubeDongleProPlus) (2.0)
  * [HackRF](HackRF)
  * [RTL-2832 with Elonics E4000](E4000)
  * [RTL-2832 with Rafael Micro R820T or R820T2](R820T)
  * [Sound card(s) connected to scanner audio output](SoundCard) 

**Decoders**

  * [AM](AM) - AM demodulator
  * [Fleetsync II](Fleetsync2) - decodes ANI, Acknowledge, Status, Paging and GPS bursts
  * [LJ1200](LoJack) - decodes LoJack data bursts on 173.075 MHz in US.
  * [LTR-Standard](LTR) - FM demodulator and Logic Trunked Radio (LTR) trunked radio signaling decoder
  * [LTR-Net](LTRNet) - FM demodulator and LTR-Net trunked radio signaling decoder
  * [MDC-1200](MDC1200) - decodes MDC-1200 ANI bursts.
  * [MPT-1327](MPT1327) - FM demodulator and MPT-1327 trunked radio signaling decoder and automatic trunked channel following.
  * [NBFM](NBFM) - narrow-band FM demodulator.
  * [Passport](Passport) - FM demodulator and Passport trunked radio signaling decoder.
  * [P-25 Phase 1 C4FM](APCO25) - FM demodulator with P25 message decoder and automatic trunked channel following.
  * [P-25 Phase 1 LSM](APCO25) - Quadrature demodulator with P25 message decoder and automatic trunked channel following.
  * [Tait 1200](Tait1200) - decodes Tait CCDI protocol GPS location bursts.

Note: nomitive use of protocol names are for identification. Registered trademarks are the property of their respective owners.

**Source Code**

Source code is available on this website

* [Downloading and Compiling sdrtrunk](Building) 