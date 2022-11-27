# Overview

sdrtrunk is a java application for decoding and trunk tracking multiple analog and digital radio channels across 
multiple USB dongle tuners and/or sound card inputs from scanner radios.  The application provides local monitoring of 
decoded audio, recording, and streaming of audio to local and remote streaming services.

## Radio Protocols
sdrtrunk can decode the following radio protocols:

* **AM** - AM demodulator
* **APCO-25 Phase 1 (C4FM/Simulcast)** - P25 message decoder and automatic trunked channel following.
* **APCO-25 Phase 2** - Phase 1 control channels with automatic Phase 2 trunked channel following.
* **Fleetsync II** - FM demodulator and decoder for ANI, Acknowledge, Status, Paging and GPS bursts
* **FM/NBFM** - narrow-band FM demodulator with squelch control.
* **LJ1200** - FM demodulator and decoder for LoJack data bursts on 173.075 MHz in US.
* **LTR-Net** - FM demodulator and LTR-Net trunked radio signaling decoder
* **LTR-Standard** - FM demodulator and Logic Trunked Radio (LTR) trunked radio signaling decoder
* **MDC-1200** - FM demodulator and decoder for MDC-1200 ANI bursts.
* **MPT-1327** - FM demodulator and MPT-1327 trunked radio signaling decoder and automatic trunked channel following.
* **Passport** - FM demodulator and Passport trunked radio signaling decoder.
* **Tait 1200** - FM demodulator and decoder for Tait CCDI protocol GPS location bursts.

## Documentation

Access links in the sidebar for Getting Started, User Manual and other support documentation.

## Requirements

sdrtrunk is released as a stand-alone application bundle that does not have to be installed.  Simply download and
unzip/untar the application and run the launch script.  sdrtrunk releases include a complete Java Runtime
Environment (JRE) so that you do NOT have to install Java.  The bundled OpenJDK JRE is a lightweight version of the
full JRE that has been stripped down to include only the minimum components needed to run the sdrtrunk application.

### Operating System

sdrtrunk application bundles are available for the following **64-bit** operating systems 

* Linux
* OS-X
* Windows

Note: sdrtrunk, as a Java-based application, can run on any operating system supported by Java and libusb.  However, other 
operating systems have not yet been tested.

### Software Defined Radios (SDR)

Refer to the [Tuners](Tuners.md) documentation for specific details on supported SDRs

* Airspy (Mini, R1, R2)
* Funcube Dongle (Pro, Plus)
* HackRF (HackRF One, Jawbreaker, RAD1O)
* RTL-2832 (E4000, R820T, R820T2)

Note: nomitive use of protocol names are for identification. Registered trademarks are the property of their respective owners.

This application uses some of the fantastic components available from [JIDE Software](www.jidesoft.com).
