# Airspy #

### Configuration ###

  * **Name** - tuner configuration name.
  * **Sample Rate** - select from 10.00 or 2.50 MHz sample rates. Note: the
  additional decimation option is not currently supported in sdrtrunk. 
  * **Gain Mode** - select from LINEARITY, SENSITIVITY, or CUSTOM.  Linearity
  and sensitivity modes provide a single gain adjustment value that automatically
  configures the IF, Mixer and LNA gains for each master gain setting.  The
  Custom mode disables the single gain adjustment slider and provides access to
  each of the IF, Mixer and LNA gain sliders so that you can manually adjust
  each gain value to meet your specific needs.

### Info Tab ###
The info tab displays information about the tuner:

  * **Serial** - serial number of the Airspy tuner.
  * **Firmware** - version number of the firmware loaded in the airspy
  * **Part** - airspy part number
  * **Board ID** - airspy board identifier

## Using the Airspy ##

![Figure 1: Airspy Tuner Configuration](v0.3/images/Airspy_V0.3.0.png)

## Updating Firmware ##

The firmware label shown on the Info tab is the GIT revision label that was
tagged against the software release.  SDRTrunk does not support
flashing the Airspy with new firmware.  Use the Airspy tools to update the
tuner.

## Using Airspy With Linux ##

If you've never setup your airspy for linux, you'll need to add permissions to allow users to access the airspy:

Download the file [52-airspy.rules](https://github.com/DSheirer/sdrtrunk/blob/master/src/main/resources/52-airspy.rules) and copy to your **\etc\udev\rules.d** folder.
 
    sudo cp 52-airspy.rules \etc\udev\rules.d

Set file permissions.

    sudo chmod u=rw,g=r,o=r 52-airspy.rules

Refresh the udev rules

    sudo udevadm control --reload-rules
