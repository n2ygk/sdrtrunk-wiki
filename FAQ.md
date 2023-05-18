# sdtrunk - Frequency Asked Questions (FAQ)

## Tuners

### How can I use SDRPlay receivers on a Mac OS Computer?
A: Java is unable to use the SDRPlay API installed driver as it is named, so you have to create a symbolic link to the driver that uses the filename that sdrtrunk is expecting.  The SDRPlay folks are going to update the installer in a future release to use the *.dylib file extension for their Mac OS driver.

Type the following in a console window and then start/restart sdrtrunk:

```
sudo ln -s /usr/local/lib/libsdrplay_api.so /usr/local/lib/libsdrplay_api.dylib
```