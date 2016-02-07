# Downloading and Compiling sdrtrunk #

The sdrtrunk source code is hosted on github.com and the repository can be 
downloaded as a compressed archive or cloned using GIT.

[sdrtrunk repository on github](https://github.com/DSheirer/sdrtrunk)

## Eclipse IDE ##

If you use the [Eclipse IDE for Java](http://www.eclipse.org/downloads/), you 
can clone the github source code repository and import the sdrtrunk project 
directly into Eclipse using either the EGit or JGit plugins.

## Manually ##

  1. Install the Java JDK version 1.7 or higher and create a JAVA\_HOME 
  environment variable pointing to the JDK installation folder
  1. Install the latest version of [Ant](http://ant.apache.org/) and follow the 
  installation instructions in the [manual](http://ant.apache.org/manual/index.html)
  1. Click the 'Download Zip' button to download the source code from 
  https://github.com/DSheirer/sdrtrunk and unzip the code
  1. Change to the sdrtrunk build directory ( sdrtrunk/build )
  1. Execute the ant command.

Ant will look for a file named build.xml in the current folder and will run the 
default build target.  The compiled and zipped output program file will be 
located in the sdrtrunk/product/xxx.zip folder.