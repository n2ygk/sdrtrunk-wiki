1. Install Java JRE version 7 or newer from http://www.oracle.com/java

2. Verify java installation:

```
console: java -version

java version "1.7.0_55"
Java(TM) SE Runtime Environment (build 1.7.0_55)
Java HotSpot (TM) 64-bit Server VM
```

3. Install udev rules file for any tuners you'll be using into the /etc/udev/rules.d/ directory.  The **funcube-dongle.rules**, **52-airspy.rules**, **53-hackrf.rules**, and **rtl-sdr.rules** files are included.

4. Download the sdrtrunk application and uncompress the file.

5. Run the SDRTrunk start script:

```
console: ./run_sdrtrunk_linux.sh
```