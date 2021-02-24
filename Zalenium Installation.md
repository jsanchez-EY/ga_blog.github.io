# Zalenium in NG eTAF for Windows

### Software Requirements
* Java 11 or higher - https://jdk.java.net/
* Maven 3.6.3 or higher - https://maven.apache.org/download.cgi
* Next Gen Testing Platform - https://github.com/ey-advisory-technology-testing/Trunk
* Docker for windows

### Installing Docker for Windows
1. Go to https://hub.docker.com/editions/community/docker-ce-desktop-windows and click on “Get Docker Desktop for Windows”
1. When the installation finishes, Docker starts automatically. The whale in the notification area indicates that Docker is running, and accessible from a terminal.
    1. Restart your pc if Docker does not start automatically after installation.
1. Open Windows PowerShell and run "docker version" to check the version
    1. Run "docker info" and make sure it works without error

### Setting up Zalenium
1. Go to https://opensource.zalando.com/zalenium/\
1. Open Windows PowerShell and run the following commands (one line for each bullet)
    1. docker pull elgalu/selenium
    1. docker pull dosel/Zalenium
    1. Windows OS : docker run --rm -ti --name zalenium -p 4444:4444 -v /var/run/docker.sock:/var/run/docker.sock -v /c/Users/your_user_name/temp/videos:/home/seluser/videos --privileged dosel/zalenium start
    1. MAC OS : docker run --rm -ti --name zalenium -p 4444:4444 -v /var/run/docker.sock:/var/run/docker.sock -v /tmp/videos:/home/seluser/videos --privileged dosel/zalenium start

### NG eTAF Configuration for Zalenium
1. Open cucumber.properties. (\eTAF\project_name\src\main\resources\cucumber.properties)
1. Change the grid and gridURL values as below
    1. grid=true
    1. gridURL= http://localhost:4444/wd/hub
1. Open the pom.xml file (\eTAF\project_name\pom.xml) and make below changes.
    1. Update the application name as the relevent test name
        1. <.application>amazonDemo</application.>
    1. Make sure source.feature has the below entry
        1. <source.feature>${project.basedir}/src/test/resources/${application}/features</source.feature>

1.	Scroll down to the cucable-plugin block in pom.xml and crosscheck the entries


        <plugin>
            <groupId>com.trivago.rta</groupId>
            <artifactId>cucable-plugin</artifactId>
            <version>1.8.0</version>
            <executions>
               <execution>
                  <id>generate-test-resources</id>
                  <phase>generate-test-resources</phase>
                  <goals>
                     <goal>parallel</goal>
                  </goals>
               </execution>
            </executions>
            <configuration>
               <!-- This can be either a Java class file or a text based template -->
               <sourceRunnerTemplateFile>${project.basedir}/src/test/java/methods/CucableJavaTemplate.java</sourceRunnerTemplateFile>
               <!--<sourceRunnerTemplateFile>src/test/resources/cucable.template</sourceRunnerTemplateFile>-->

               <!-- process all tests in the given directory -->
               <sourceFeatures>${source.feature}</sourceFeatures>

               <!-- process a specific feature file in the given directory -->
               <!--<sourceFeatures>${project.basedir}/src/test/resources/amazonDemo/features</sourceFeatures>-->

               <!-- process multiple feature files -->
               <!--<sourceFeatures>-->
               <!--src/test/resources/features/testfeature2,-->
               <!--src/test/resources/features/testfeature/MyTest8.feature-->
               <!--</sourceFeatures>-->

               <!-- process a specific feature file and specific line numbers in the given directory -->
               <!--<sourceFeatures>src/test/resources/features/testfeature/MyTest1.feature:8:19</sourceFeatures>-->

               <generatedFeatureDirectory>${generated.feature.directory}</generatedFeatureDirectory>
               <generatedRunnerDirectory>${generated.runner.directory}</generatedRunnerDirectory>

               <!-- optional: custom data that is available in Cucable placeholders in a template -->
               <!--<customPlaceholders>-->
               <!--<comment>This should appear inside the template</comment>-->
               <!--</customPlaceholders>-->

               <!-- optional: Cucumber tag expression to include or exclude scenarios with certain tags (see https://docs.cucumber.io/cucumber/api/#tag-expressions) -->
               <!--<includeScenarioTags>${tags}</includeScenarioTags>-->
               <includeScenarioTags>@grid</includeScenarioTags>
               <!--<includeScenarioTags>(@scenario1Tag1 or @scenario1Tag2) and not @skipMe</includeScenarioTags>-->

               <!-- optional: change parallelization mode of Cucable (default: 'scenarios')-->
               <!-- <parallelizationMode>scenarios</parallelizationMode>-->
               <parallelizationMode>scenarios</parallelizationMode>

               <!-- optional: number of test runs to create runners and features multiple times
                         if set to a number greater than 1 -->
               <!--<numberOfTestRuns>1</numberOfTestRuns>-->

               <!-- optional: generate a fixed number of runners and distribute all features round-robin.
                     This can only be used if desiredNumberOfFeaturesPerRunner is NOT used! -->
               <!--<desiredNumberOfRunners>2</desiredNumberOfRunners>-->

               <!-- optional: distribute a fixed number features per runner round-robin.
                    This can only be used if desiredNumberOfRunners is NOT used! -->
               <!--<desiredNumberOfFeaturesPerRunner>4</desiredNumberOfFeaturesPerRunner>-->

               <!-- optional: Cucable log level -->
               <logLevel>default</logLevel>
               <!--<logLevel>compact</logLevel>-->
               <!--<logLevel>minimal</logLevel>-->
               <!--<logLevel>off</logLevel>-->
            </configuration>
         </plugin>









