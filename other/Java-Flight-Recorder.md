Java Flight Recorder (JFR) can be used to create a recording of the sdrtrunk application while it is running, to capture statistics about how the application is performing.  These recordings are useful in investigating performance or memory leaks.

# Create a JFR Recording

1. Start sdrtrunk and enable any decoding channels.  Allow the application to run for at least 10 seconds.
2. Open a shell or command line
3. Get the Process ID for the sdrtrunk application

Type: ```jcmd```

This will show a list of running java applications and their Process ID.  Look for this line (the number at the beginning is your process ID):
```
212161 io.github.dsheirer.gui.SDRTrunk
```
In this example, 212161 is the process ID or PID.  We'll use the PID value in the next series of steps.  Substitute this number wherever you see PID in the next steps.

4. Start a Java Flight Recorder recording.

Type: ```jcmd PID JFR.start```

5. Wait 60 seconds and then dump the events to the recording file:

Type: ```jcmd PID JFR.dump name=1```

6. Notice the file path and name that are listed after you perform the dump.  This is your JFR recording file.

Note: you can execute this JFR.dump command multiple times.  Each time it will dump all events captured since the start of the recording.  The default max size of captured events is 250MB, but you can change that to be larger if you need to.

7. Stop the JFR recording:

Type: ```jcmd PID JFR.stop name=1```

# Example

```
denny@denny-desktop-2021:~$ jcmd
195170 org.gradle.launcher.daemon.bootstrap.GradleDaemon 7.2
1490 com.intellij.idea.Main
196705 org.gradle.launcher.daemon.bootstrap.GradleDaemon 7.2
212161 io.github.dsheirer.gui.SDRTrunk
195770 org.gradle.launcher.daemon.bootstrap.GradleDaemon 7.2
212312 jdk.jcmd/sun.tools.jcmd.JCmd
196239 org.gradle.launcher.daemon.bootstrap.GradleDaemon 7.2
2735 org.jetbrains.idea.maven.server.RemoteMavenServer36
denny@denny-desktop-2021:~$ 
denny@denny-desktop-2021:~$ jcmd 212161 JFR.start
212161:
Started recording 1. No limit specified, using maxsize=250MB as default.

Use jcmd 212161 JFR.dump name=1 filename=FILEPATH to copy recording data to file.
denny@denny-desktop-2021:~$ jcmd 212161 JFR.dump
212161:
Dumped recording, 1.6 MB written to:

/home/denny/IdeaProjects/sdrtrunk/hotspot-pid-212161-2022_01_14_05_26_45.jfr
denny@denny-desktop-2021:~$ jcmd 212161 JFR.dump
212161:
Dumped recording, 3.0 MB written to:

/home/denny/IdeaProjects/sdrtrunk/hotspot-pid-212161-2022_01_14_05_26_57.jfr
denny@denny-desktop-2021:~$ jcmd 212161 JFR.stop name=1
212161:
Stopped recording "1".
denny@denny-desktop-2021:~$ 

```



