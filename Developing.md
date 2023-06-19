# sdrtrunk - Developers/Developing

This wiki will expand to contain details about the sdrtrunk architecture and information for developers that may want 
to either contribute to the project, experiment with the source code, or use the source code in other projects.

### OpenJDK
sdrtrunk requires **Java JDK with integrated Open JavaFX** libraries. OpenJDK vendors that I use include:
* [Azul Zulu OpenJDK](https://www.azul.com/downloads/?package=jdk)
* [Bellsoft Liberica OpenJDK](https://bell-sw.com/pages/downloads/#/java-17-lts%20/%20current)
* [SDKMAN](https://sdkman.io/) - not an SDK vendor, rather an SDK selection tool.  Linux Only

Note: required Java JDK is currently locked at JDK 19.x until Gradle 8.2 is released.

Use the gradle wrapper to build the source code:

### Linux
```
./gradlew clean build
```
### Windows
```
gradlew.bat clean build
```

The **/build/distributions** folder will contain the zip file of the compiled program.  Unzip it and launch the program from the scripts in the **/bin** directory.

## Run the Application (from Gradle)

### Linux
```
./gradlew clean run
```
### Windows
```
gradlew.bat clean run
```

## Creating Release Distributions (from Gradle)

### Create Current OS Release Using Local Installed JDK
```
./gradlew runtimeZipCurrent
```
### Create Windows (x86-64 & aarch64) Releases With Automatic JDK Download
```
./gradlew runtimeZipWindows
```
### Create Linux (x86-64 & aarch64) and Mac (x86-64 & aarch64) Releases With Automatic JDK Download
```
./gradlew runtimeZipOthers
```


## Development
All dependencies/versions are controlled from build.gradle.
