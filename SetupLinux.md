1. Install Java JRE version 7 or newer from http://www.oracle.com/java.  Note: if you are using airspy or hackrf, your computer should have 8GB or more of memory and you should use the 64-bit (x64) version of the java JRE.

2. Verify java installation:

```
console: java -version

java version "1.7.0_55"
Java(TM) SE Runtime Environment (build 1.7.0_55)
Java HotSpot (TM) 64-bit Server VM
```

3. Download the sdrtrunk application and decompress the file.

4. Install udev rules file for any tuners you'll be using into the /etc/udev/rules.d/ directory.  The **funcube-dongle.rules**, **52-airspy.rules**, **53-hackrf.rules**, and **rtl-sdr.rules** files are included in the /config folder

5. Run the SDRTrunk start script:

```
console: cd (unzip folder)/sdrtrunk
console: ./run_sdrtrunk_linux.sh
```