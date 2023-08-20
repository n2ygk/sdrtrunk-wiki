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

## Launching sdrtrunk Application

### MacOS

Version 13.5.1+

1) download the zip file, unzip if needed
2) use Terminal, cd to the bin directory
3) run: ./java
4) it will "fail"
5) Open up Privacy & Security settings, scroll all the way down
6) There will be a small notice - *"java" was blocked from use because it is not from an identified developer. *. Press the "Allow Anyway" button and authenticate
7) Repeat the same steps for ./sdr-trunk; you may see *another* notice about Java not being verified, press Open

Up to Version 13.4

1) download the zip file, unzip if needed
2) In the /bin directory of the application 
3) Right click > Open on java and accept the prompt