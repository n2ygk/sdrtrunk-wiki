# Tuner #

The Tuners folder contains a listing of all recognized tuners that are automatically discovered upon startup of the SDRTrunk application.  Each tuner displays the tuner type, name, serial number (if known), and the currently tuned frequency and [bandwidth/sample] rate.

![](images/Tuners.png)

## Supported Tuners ##

The following tuners are currently supported by the SDRTrunk application.  Additional tuner support will be added in the future.

  * [Airspy](Airspy)
  * [Ettus B100/WBX Daughter Card](B100)** - (planned).  SDRTrunk will recognize the B100 but it will not allow you to use or configure the B100
  * [Funcube Dongle Pro](FuncubeDonglePro) (1.0)
  * [Funcube Dongle Pro Plus](FuncubeDongleProPlus) (2.0)
  * [HackRF](HackRF)
  * [RTL-2832 with Elonics E4000](E4000)
  * [RTL-2832 with Rafael Micro R820T or R820T2](R820T)

## Tuner Management ##

SDRTrunk manages all tuners as a pooled set of resources.  As you enable channels for decoding, SDRTrunk polls each tuner to see if it can support the requested channel, and then assigns the channel to the tuner.  If no tuners can support the channel, then the channel will not start and will be disabled.

Each tuner can source one or more channel frequencies, as long as the set of channel frequencies fit within the current center tuned frequency and bandwidth (sample rate) of the tuner.  As additional channels are sourced by the tuner, the tuner controller will automatically adjust the center frequency to provide a best-fit of all of the requested channels, while ensuring that no channels overlap any DC-spike that may be present in the center of the spectrum for some types of tuners.

## Visualizing the Tuner Spectrum ##
On startup, SDRTrunk automatically displays the first discovered tuner in the [Spectral Display](SpectralDisplay).  All tuners can be displayed in the main spectral display or in additional spectral display windows.

  * **Application Spectral Display** - right-click on any of the tuners and select **Show in Main Spectrum** to show the spectral display for that tuner in the main application display.

  * **Additional Spectral Display** - right click on any of the tuners and select **New Spectrum Window** to open a new window and display the spectrum for that tuner.  You can open as many spectral display windows as you want, including multiple windows on the same tuner.