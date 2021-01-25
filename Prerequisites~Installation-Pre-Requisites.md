# **Pre-requisites:**
1. **## Install Java JDK**
*  **IMPORTANT NOTE:** You must request the “Java Uninstall Exception 1.0” software or else
java may be uninstalled from your computer by EY
*  In order to request the exception follow the following directions:
* *  Go to the self service portal (https://ey.service-now.com/ey/) → Go to ab
“Order Something”—> click “Get Software” → Search “Java Uninstall Exception
1.0” → click “request”
* *  Or go to
https://ey.servicenow.com/ey?id=ey_kb_article_view&sys_kb_id=d04da78cdb5
80c10403289070596199a and click on the link “Click here to add your machine
to the Java Removal Initiative exception list”
*  Install JDK 1.8 from https://www.oracle.com/java/technologies/javase-downloads.html
* JDK 8 or above will be the most compatible. Always use Long Term Support (LTS)
versions (JDK8)
2. **## Install Maven**
*  Download Maven version 3.6.1 or later https://maven.apache.org/download.cgi
* Versions as old as 2.2 have been tested and work correctly. Newer versions should
also work
3. **## Setup Environment Variables**
*  Open “File Explorer” --> Right click “This PC” --> Click “Properties” --> Click “Advanced
System Settings” --> Confirm elevation with credentials --> Click “Environment
Variables”
* Add the following to your Path system variable if not present already (Left click “Path” --
> click “Edit”)
* * Java Bin folder – e.g: C:\Program Files\Java\jdk1.8.0_144\bin
* Setup new system variables (Click “New”)
* * JAVA_HOME: - e.g C:\Program Files\Java\jdk1.8.0_144
* * CLASSPATH: %JAVA_HOME%\lib\tools.jar (as
* To test if everything is working go to command prompt and type the following
commands to verify the installation and versions are all correct:
* * `where java`
* * `java -version`
* * `where maven`
* * `maven -version`
4. **## Download and setup IntelliJ Community Version and its dependencies**
* Download IntelliJ Community Version and its dependencies from
https://www.jetbrains.com/idea/download/#section=windows
*  Click next through all the setup instructions. Click finish at the end. Required version:
2019.2.2 or later
*  In order for NG Testing Platform to run correctly in your IntelliJ environment, be sure to
install the following plugins from the IntelliJ Marketplace:
* * Cucumber for Java Plugin for IntelliJ (IntelliJ Idea Marketplace, Open IntelliJ->
File-> Settings -> Plugins)
* * * Recommended Version: 2019
* * Gherkin Plugin for IntelliJ (IntelliJ Idea Marketplace, Open IntelliJ-> File->
Settings -> Plugins)
* * * Recommended Version: v183.5429.1 or latest
* * YAML Plugin for IntelliJ (IntelliJ Idea Marketplace, Open IntelliJ-> File-> Settings -
> Plugins)
* * * Latest Version




