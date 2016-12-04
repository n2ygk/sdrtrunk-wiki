# Creating a java library for the Radio Reference web service

The Radio Reference API uses an older WSDL format that is not compatible with modern versions of wsimport (2.x+).  Generating a library from this WSDL requires an older version of Apache Axis.  Go to http://apache.is.co.za/axis/axis/java/1.4/ and download axis-bin-1_4.zip.

Extract axis 1.4 into a directory and you should have the following files (among others) in a /libs folder:

* axis.jar
* commons-discovery-0.2.jar
* commons-logging-1.0.4.jar
* jaxrpc.jar
* saaj.jar
* wsdl4j-1.5.1.jar

Additionally, download the following two jars and store them in the same Axis 1.4 libs folder

* http://central.maven.org/maven2/javax/activation/activation/1.1/activation-1.1.jar
* http://www.java2s.com/Code/JarDownload/java-mail/java-mail-1.4.jar.zip (and extract it)

Open a command prompt and navigate to the libs folder and execute this command:

**java -classpath commons-discovery-0.2.jar:axis.jar:commons-logging-1.0.4.jar:jaxrpc.jar:saaj.jar:wsdl4j-    1.5.1.jar:java-mail-1.4.jar:activation-1.1.jar:log4j-1.2.8.jar org.apache.axis.wsdl.WSDL2Java -B http://api.radioreference.com/soap2/?wsdl&v=latest**

This will create a folder /com in the /libs folder and will also generate (-B option) an ant build script.

Edit the build.xml file and change the jar name in this line from ?wsdl to radioreference-14.jar:
**<jar jarfile="radioreference-14.jar" basedir="${build.classes}" >**

Run ant from the same folder to create the **radioreference-14.jar** library




 