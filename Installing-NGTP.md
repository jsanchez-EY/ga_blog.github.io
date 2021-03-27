# Setting up NGTP
## Understanding the NGTP layout
As mentioned earlier, Next Gen Testing Platform is a modular test harness: it needs the following to function:
* Atleast 1 core library (etaf-core-library, etl-core-libraries etc)
* The corresponding step-definitions library (etaf-step-definitions, etl-step-definitions etc)
* And the cherry-on-top, the actual test automation framework which in itself is essentially a shell which needs its above libraries to be fully-functional. There are different libraries for doing different things with this framework. Namely,
- etaf-step-definitions: Provides all the reusable steps needed for functional, UI and system testing of web applications
  - etaf-core-libraries: Provides the capabilities required by etaf-step-definitions to enable Web app testing
- etl-step-definitions: Provides all the reusable steps needed for data and ETL testing
  - etl-core-libraries: Provides the capabilities required by etl-step-definitions to enable data and ETL testing

and many more. Please refer the [wiki](List-of-NGTP-libraries) links for other such component libraries.

To configure your project to consume these libraries you need to add either the library dependencies to your pom.xml and cofiguring your maven settings.xml or, their library jars directly to your project and adding it to your pom.xml. This is what will be covered in the next sections.

But once completed your pom.xml will essentially contain these

```xml
            <dependency>
                <groupId>com.ey</groupId>
                <artifactId>etaf-step-definitions</artifactId>
                <version>1.1.1</version>
                <!--<systemPath>${project.basedir}/src/main/resources/JARs/etaf-step-definitions-1.1.1.jar</systemPath>-->
            </dependency>
            <dependency>
                <groupId>com.ey</groupId>
                <artifactId>etaf-core-library</artifactId>
                <version>1.1.1</version>
                <!--<systemPath>${project.basedir}/src/main/resources/JARs/etaf-core-library-1.1.1.jar</systemPath>-->
            </dependency>
            <dependency>
                <groupId>com.ey</groupId>
                <artifactId>license-validator</artifactId>
                <version>1.0.7</version>
                <!--<systemPath>${project.basedir}/src/main/resources/JARs/license-validator-1.0.7.jar</systemPath>-->
            </dependency>
            <dependency>
                <groupId>com.ey</groupId>
                <artifactId>etl-step-definitions</artifactId>
                <version>1.0.2</version>
                <!--<systemPath>${project.basedir}/src/main/resources/JARs/etl-step-definitions-1.0.2.jar</systemPath>-->
            </dependency>
            <dependency>
                <groupId>com.ey</groupId>
                <artifactId>etl-core-libraries</artifactId>
                <version>1.0.3</version>
                <!--<systemPath>${project.basedir}/src/main/resources/JARs/etl-core-libraries-1.0.3.jar</systemPath>-->
            </dependency>
```
Uncomment the <systemPath></systemPath> tags above if you have downloaded the dependency jars and are storing them under `src/main/resources/JARs/` folder of your project

**Note:** Don't panic if you do not see xxx-core-library dependencies. As long as you find xxx-step-definitions, its libraries will already be included. You are covered.

## Inside EY Network
Within EY Testing I&A, we use GitHub as our tool of choice for version control and collaborative programming. If you are unfamiliar with Git and have not used GitHub before, you must review the GitHub user guides here: https://guides.github.com/

If you are tasked with working on any internal development, get access to our ey-advisory-technology-testing organization within GitHub. Refer the link for directions

1. Once inside the organization, you need to navigate to the [NGTP](https://github.com/ey-advisory-technology-testing/Trunk) project and click on the `Code` button. 
2. Select SSH option and Copy the SSH URL from the GitHub project’s web page
3. Open IntelliJ and then do a ```File -> New -> Project from Version Control ```
4. Paste the URL in the modal dialog that pops open and hit clone.
5. If you have setup your installation prerequisites correctly (SSH, Settings file, environment variables etc.) you should see that the dependencies will auto-resolve and the project will build smoothly.
6. And your pom.xml will contain the `com.ey` dependencies

**Trouble-shooting hints:**
* If you are prompted to select a Project SDK, then open `File -> Project Structure`. In the left pane, select `Project Settings -> Project` and select the installed JDK from the Project SDK drop down.

**Note:** The same process of cloning the project can also be done using GitHub desktop. Read its documentation for that.

## Inside Client Network
This will be a little different than what we do internally. Here we need to migrate approved components of NGTP to the client systems. We recommend a single person migrating the NGTP to client network, setting it up, committing and pushing to their version control software. Other team members who intend to use the NGTP can pull it from the VCS.

### Migrating key software to client network
1. Once inside our ey-advisory-technology-testing organization, you need to navigate to the [NGTP](https://github.com/ey-advisory-technology-testing/ngtp-base) project.
1. Mirror the repository to create an ngtp-<client-name>. Refer steps in [GitHub Guidelines](GitHub-Guidelines#mirroring-repositories)
1. Now that we have established a repository for your specific client work, this will serve as the key connection between your client work and EY NGTP.
1. Open the ngtp-<client-name> project and click on the `Code` button. 
1. Click `Download as zip` button and download it to your folder. Let's call that folder `to-client`.
1. Obtain a license file from one of our license administrators, stating the business reason and giving the engagement end date. Every person who is intending to setup and use NGTP must obtain their license.
1. Add your license file to your migration folder above.
1. Zip the entire contents and open [Media Shuttle](https://filetransfer.mediashuttle.com/) from your browser
1. Attach the zipped folder and send it to your EY email address (Yes, EY email address. This will be obvious in the next couple of steps). Wait for confirmation email from portals@mediashuttle.com
1. Now, Open your client laptop and navigate to the same [Media Shuttle](https://filetransfer.mediashuttle.com/) link.
1. Login with your EY credentials as this is limited to EY employees and contractors (This is the reason we sent the files to EY email address) 
1. Once inside, click on the `My Transfers` button on the top right of the ribbon.
1. Download the zip folder you sent to yourself.
1. Unzip the contents and save the license file to a secure location in your system.
1. Unzip the NGTP to a location of your preference.

### Setting up the pre-requisites
Follow the steps outlined in the installation prerequisites page

### Setting up the NGTP
1. Open IntelliJ and `File -> New -> Project from Existing Sources` and browse and select the pom.xml file inside the NGTP folder unzipped above.
1. You will be prompted with a message box. 
1. Click the ` Open as a Project` button
1. If you have setup your installation prerequisites correctly (SSH, Settings file, environment variables etc.) you should see that the dependencies will auto-resolve and the project will build smoothly.


**Note:** It is recommended that no matter how you choose to download your repository (GitHub
Desktop, IntelliJ integration, or simply downloading from GitHub) that you connect your
repository to GitHub Desktop to take advantage of the UI when merging. You can add any
downloaded GitHub project stored on your computer to GitHub Desktop by clicking file/add
a local repository and then pathing to that repository’s location on your computer

**Important**
* All users of NGTP must have knowledge of GitHub before being granted a license.
Learning to use GitHub desktop and the IntelliJ GitHub plugin are key to keeping a healthy and maintainable code base.

***
