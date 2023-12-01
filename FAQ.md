# sdtrunk - Frequency Asked Questions (FAQ)

## Tuners

### SDRPlay

***

#### How do I set the gain on SDRPlay RSP tuners?
A: Gain usage for the RSP tuners works differently than other tuners supported by SDRTrunk.  Per recommendation of the SDRPlay engineers, you should **Enable AGC** and **Set Gain to Maximum**.  After doing this, if you are seeing the **Gain Overload** indicator, you can reduce the gain level. 

***

#### How can I use SDRPlay receivers on a Mac OS Computer?

##### A: **SDRPlay API version 3.11 (and older) for Mac OS**

Java is unable to use the SDRPlay API installed driver as it is named, so you have to create a symbolic link to the driver that uses the filename that sdrtrunk is expecting.  The SDRPlay folks are going to update the installer in a future release to use the *.dylib file extension for their Mac OS driver.

Type the following in a console window and then start/restart sdrtrunk:
```
sudo ln -s /usr/local/lib/libsdrplay_api.so /usr/local/lib/libsdrplay_api.dylib
```

##### A: **SDRPlay API version 3.12 for Mac OS**

The installer for this version has some issues.  After installing the API, use the following (additional) instructions:

Run the following commands in an admin window:
```
sudo mkdir -p /usr/local/lib
sudo ln -s /Library/SDRplayAPI/3.12.0/lib/libsdrplay_api.3.12.0 /usr/local/lib/libsdrplay_api.so.3.12
sudo ln -s /usr/local/lib/libsdrplay_api.so.3.12 /usr/local/lib/libsdrplay_api_arm64.so.3.12
sudo ln -s /usr/local/lib/libsdrplay_api.so.3.12 /usr/local/lib/libsdrplay_api_x64.so.3.12
sudo ln -s /usr/local/lib/libsdrplay_api.so.3.12 /usr/local/lib/libsdrplay_api.so.3
sudo ln -s /usr/local/lib/libsdrplay_api.so.3 /usr/local/lib/libsdrplay_api.so
sudo ln -s /usr/local/lib/libsdrplay_api.so /usr/local/lib/libsdrplay_api.dylib
```
Try sdrtrunk.  If it doesn't work, these additional commands are known to work for Mac M1 Mini:
```
sudo cp /Applications/SDRconnect.app/Content/MacOS/libusb-1.0.0.dylib /usr/local/lib/
```
(Note this requires SDRconnect to be installed first!)

On my machine the service did not start for some reason, so the following was added:
```
sudo launchctl load -w /Library/LaunchDaemons/com.sdrplay.service.plist
sudo launchctl enable system/com.sdrplay.service
sudo launchctl start system/com.sdrplay.service
```
You can check the service is running by doing this:
```
sudo launchctl list | grep -I sdr
```
After a reboot the service should run ok without further intervention.
 
***
## Launching sdrtrunk Application

***

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

***

## General

***

### What does **Audio segment detected with NO to identifiers** mean?

This indicates that sdrtrunk decoded an audio call but it didn't detect any TO radio or talkgroup identifiers.  This can happen when the decode quality is poor and sdrtrunk decodes just enough audio frames to create an audio segment (ie a call), but didn't decode any of the messaging that carries the radio identifiers for that specific call.
