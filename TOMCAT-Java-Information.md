## CATALINA_HOME and JAVA_HOME
In v1.0.8 Migration Assistant will look for Tomcat applications based on the location specified in the CATALINA_HOME environment variable, and using the Java version found in the JAVA_HOME location. If either of these values is not found as an environment variable then you will be prompted to provide these paths. 

### LINUX
The values to use for these environment variables can be found in the Tomcat service definition file. This would usually be in a location like: /etc/systemd/system/tomcat.service and look something like:
> Environment=JAVA_HOME=**/usr/lib/jvm/java-1.11.0-openjdk-amd64**

> Environment=CATALINA_HOME=**/opt/tomcat**

### WINDOWS
The values to use for these environment variables are related to where Tomcat and Java are installed on the machine. Tomcat is typically installed in a location like "C:\Program Files (x86)\Apache Software Foundation\Tomcat 8.5". 
The Java version used by a particular Tomcat instance can be found using the Tomcat Monitor application. Go to the tomcat install location and open the 'bin' directory, look for an exe named something like "tomcat8w.exe" (basically this should be named [tomcatServiceName]w.exe) and run it, this will open a GUI. On the Java tab find the value used for Java Virtual Machine and use the first part of this path up to the \bin folder, like the bolded part of the example Java Virtual Machine value below: 

> **C:\Program Files (x86)\Java\jre1.8.0_261**\bin\client\jvm.dll


***

## Related Resources

Check out the detailed steps for manually evaluating and migrating Tomcat sites for App Service here:
https://docs.microsoft.com/en-us/azure/developer/java/migration/migrate-tomcat-to-tomcat-app-service