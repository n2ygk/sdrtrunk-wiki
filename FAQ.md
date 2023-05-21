# sdtrunk - Frequency Asked Questions (FAQ)

## Tuners

### SDRPlay

#### How do I set the gain on SDRPlay RSP tuners?
A: Gain usage for the RSP tuners works differently than other tuners supported by SDRTrunk.  Per recommendation of the SDRPlay engineers, you should **Enable AGC** and **Set Gain to Maximum**.  After doing this, if you are seeing the **Gain Overload** indicator, you can reduce the gain level. 

#### How can I use SDRPlay receivers on a Mac OS Computer?
A: Java is unable to use the SDRPlay API installed driver as it is named, so you have to create a symbolic link to the driver that uses the filename that sdrtrunk is expecting.  The SDRPlay folks are going to update the installer in a future release to use the *.dylib file extension for their Mac OS driver.

Type the following in a console window and then start/restart sdrtrunk:

```
sudo ln -s /usr/local/lib/libsdrplay_api.so /usr/local/lib/libsdrplay_api.dylib
```