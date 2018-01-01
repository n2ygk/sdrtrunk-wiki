**Version:** 0.3.x

1. Install Java JRE version 8 or newer from http://www.oracle.com/java.  Note: if you are using airspy or hackrf, your computer should have 8GB or more of memory and you should use the 64-bit (x64) version of the java JRE.

2. Verify java installation:

```
console: java -version

java version "1.8.0_91"
Java(TM) SE Runtime Environment (build 1.8.0_91-b14)
Java HotSpot (TM) 64-bit Server VM
```

3. Download the sdrtrunk application.

4. Install udev rules file for any tuners you'll be using into the /etc/udev/rules.d/ directory.  

The following udev files are available here: https://github.com/DSheirer/sdrtrunk/tree/master/src/main/resources

**funcube-dongle.rules** 
**52-airspy.rules** 
**53-hackrf.rules** 
**rtl-sdr.rules**

5. Run the SDRTrunk application:

```
console: cd (download folder)
console: java -jar sdrtrunk-release-jar-filename
```