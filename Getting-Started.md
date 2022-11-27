# Getting Started
The following instructions detail how to get started with the sdrtrunk application.

sdrtrunk is released as a stand-alone application bundle that does not have to be installed.  Simply download and 
unzip/untar the application and run the launch script.  sdrtrunk releases include a complete Java Runtime 
Environment (JRE) so that you do NOT have to install Java.  The bundled OpenJDK JRE is a lightweight version of the 
full JRE that has been stripped down to include only the minimum components needed to run the sdrtrunk application.

## Download the Application Bundle
* Click the Download link in the sidebar menu to access the GitHub project Releases page.
* Select the latest release version
* Expand the 'Assets' section at the bottom of the Version release page.
* Download the appropriate application bundle as follows:

<details><summary>Linux ARM 64-bit</summary>

Select the asset that starts with: **sdr-trunk-linux-aarch64**

</details>

<details><summary>Linux x86 64-bit</summary>

Select the asset that starts with: **sdr-trunk-linux-x86_64**

</details>

<details><summary>OS-X M1/M2 (ARM) 64-bit</summary>

Select the asset that starts with: **sdr-trunk-osx-aarch64**

</details>

<details><summary>OS-X x86 64-bit</summary>

Select the asset that starts with: **sdr-trunk-osx-x86_64**

</details>

<details><summary>Windows x86 64-bit</summary>

Select the asset that starts with: **sdr-trunk-windows-x86_64**

</details>

## Unzip or Untar the Application Bundle
The application bundle is compressed as a ZIP or TAR.GZ archive.  Use any popular zip or tar application to unzip the
application bundle.

* [7-zip](https://www.7-zip.org/)

## Read the User's Manual
The user's manual is documented in this wiki.  Use the links in the sidebar to navigate to the various documentation
sections.  Please read the [Playlist Editor](Playlist-Editor) documentation so that you understand how to correctly
configure sdrtrunk.

## Setup Software Defined Radio (SDR) Dongles
See the [Tuners](Tuners) documentation for Operating System (OS) specific setup instructions for each supported SDR
dongle/tuner type. Carefully read the section on **Calibrating SDR Tuners** in the [Tuners](Tuners) section of the
user manual **BEFORE** you try to decode any signals.

## Launch the Application
<details><summary>Linux/OS-X</summary>

Open a terminal and navigate to where you unzipped the application bundle and run the following shell script:

```
(untarred application bundle file location)/bin/sdrtrunk.sh
```
Note: you can also use File Explorer and double-click on this batch file to start the application.  However, if there
are any errors in starting the application, the command prompt window will quickly disappear and the application may not
start.
</details>

<details><summary>Windows</summary>

Open a command prompt and navigate to where you unzipped the application bundle and run the following batch file:

```
(unzipped application bundle file location)/bin/sdrtrunk.bat
```
Note: you can also use File Explorer and double-click on this batch file to start the application.  However, if there 
are any errors in starting the application, the command prompt window will quickly disappear and the application may not
start.
</details>

## Configure Audio Playback
sdrtrunk attempts to select the correct (ie default) audio playback device from your computer and you may not have to 
do anything to setup your computer's audio system.  However, some computers are configured in a not-so-standard fashion 
and sdrtrunk may need your help in selecting the correct audio playback devices.

The [User Preferences Dialog](User-Preferences) documentation describes how to select alternate audio playback devices.

## Create Channels and Aliases To Start Decoding
The [Playlist Editor](Playlist-Editor) section describes how to configure channels and aliases for decoding and
also details how to setup audio monitoring, recording and streaming.
