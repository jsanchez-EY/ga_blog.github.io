# NGTP User Interface
## Product Summary
The Next Gen Testing Platform UI is a desktop application which can be set up with user’s existing NGTP (also known as Next Gen Testing Platform) project to allow them to design, execute and report test cases from a UI interface instead of having to use a developer-centric IDEs like Eclipse, IntelliJ etc.
This product is a cross platform desktop application that is easy to install and intuitive to work with.

## Minimum System Requirements
1. OS: Windows 10 or macOS
1. RAM: 8 GB
1. Disk Space: 1GB

## Software Requirements
* Java 11 or higher - https://jdk.java.net/
* Maven 3.6.3 or higher - https://maven.apache.org/download.cgi
* Next Gen Testing Platform - https://github.com/ey-advisory-technology-testing/Trunk 
* Node.js 12.18.3 or higher - https://nodejs.org/en/

## Setup Instructions
1. Follow all steps to set up any version of Next Gen Testing Platform framework (including setting up Java and Maven as defined in the document) – Windows Next-Gen Testing Platform Installation Procedure
1. Use the installer “NGTP Setup 0.0.1.exe” to set up the UI application
1. Your antivirus may flag this installation. Please ignore the warnings and allow the installation to proceed
1. Open the NGTP.exe file
1. Once the above application is open, go to Settings > Path and make sure that the correct back-end framework is selected

## Product Understanding
### What the UI is
1. The UI is a supplement on top of existing BDD framework, so testers need not deal with a Developer IDE
1. It can create new tests and execute tests that exist
### What the UI is not
1. It is not a replacement for a test automation framework
1. It is not a coding platform to develop new business code that does not exist in your framework

## Scope for MVP
NGTP UI has four tabs, each having the following functionality:
### Dashboard
Dashboard tab is landing page for our application. First time users need to select their default framework directory before using any other tab or features available.  Dashboard, as the name implies, is available to present the user with information and shows the reports available in the framework from previous test runs.  
1. User can load test reports and view reports for previous runs
1. User can download all reports 

### Test Design
Test Design tab is place where users can create their own steps and scenarios under feature files. Users can also edit available features from the chosen framework workspace. The tab is split into three sections- Feature files (Left menu). Canvas area (middle) and Page objects (right menu)
#### Feature File - Create/Upload/Edit
1. User can select any project (Henceforth referred to as workspace) to work on. This will be the project name from NGTP framework (e.g. AmazonDemo, PolicyCenter etc.)
1. User can directly upload valid feature files
1. User can create a new feature file in the canvas and save it
1. User can load an existing feature file to the canvas to edit it
#### Building a Scenario 
1. User can add, delete or edit Scenarios within the canvas or clear the canvas itself
1. User can search the list of Step Definitions in the left menu and add a step definition to the scenario
1. User can rearrange, delete added steps
1. User can add names to the feature and/or scenarios
1. User can add any tags to the Scenarios
1. User can switch to raw mode to edit the feature file as raw text
1. User can switch from raw mode back to UI mode (only if its tested before UAT)
1. Once a step is added to the scenario, users can fill-in data to the empty input boxes either by typing a value or by dragging and dropping data from the right pane. The data can either be a test data (e.g. Addresses, names etc.) or a screen element (e.g. Submit button, username text box)

### Execute
Execute tab is the place where users can execute feature files that already exists in the project or created in the Design tab. Users can choose the scenarios from the feature files explorer section, with the help of search and filter functionality. There is a Run configuration drop down area where users can change basic and most used test configurations that are available in settings tab.
1. User can select a workspace to work on. This will be the project name from NGTP framework
1. User can select one or multiple feature files from the left menu to add them to the canvas area
1. User can select any combination of scenarios to run from the canvas area
1. User can change basic settings from Run Configuration menu
1. User can execute selected scenarios. The results will be available in the Dashboard tab

### Settings
Settings tab is the space where users can configure the settings needed for the framework. It contains 8 sub-tabs or sections categorized based on functionality.
1. In the settings tab, a user is presented with all the available settings in Next Gen Testing Platform
1. User can choose to reset all settings which will change all settings back to default values

## Assumptions
* The UI application is dependent on a working test automation framework
* Product can only recognize step definitions if they are in a java file ending with “StepDefinitions.java”
* Application can only read from and save feature files in the default features folder for the workspace - ~src/test/resources/{workspace}
* Some step definitions may not get recognized by the UI and send an error “Invalid Step in the file” if their regular expression is not supported. This will be fixed as the framework gets updated
* Product assumes default location of Step Definitions and Reusable Step Definitions based on Next Gen Testing Platform architecture as follows:
1. Reusable Step Definitions - `~src/main/java/seleniumutils/reusablestepdefinitions`
1. Step Definitions- `~src/test/java/{workspace}/stepdefinitions`

This will change in the next release where we can configure paths to custom step definitions

## Limitations
As this is the MVP release, the product has a few limitations and assumptions:
1. Product does not support API and ETL tests
1. Product does not support Scenario Outlines and Examples
1. Product does not support creating new Test Data or Page Objects
1. Product does not support creating new Step Definitions
1. To see all reports, leave the reports location blank in settings. Alternatively, selecting a specific html report in the Reports Location will load just this one report on the dashboard
1. If a Feature contains a Step Definition that is not recognized, the feature file will not load on the canvas

## Definitions/glossary
### Feature file
Automation tests in the UI are created using Feature Files. Features files contain a list of scenarios composed of Steps written in _Gherkin language_ which provides a way to describe your application behavior in business readable language. Each feature can have one or more scenarios, and every scenario consists of one or more _steps_.

### Scenario
Every Scenario is an individual test case. Scenario is one of the core Gherkin structures. Every scenario starts with the keyword “Scenario:” (or localized one) and is followed by an optional scenario title. Every scenario consists of a list of steps, which must start with one of the keywords Given, When, Then, But or And.

### Step or Step Definition
A step definition is a common template for a step. E.g. Given I navigate to “______”. Here you can fill any valid URLs.
A Step Definition links the java code to one or more Gherkin steps. When Cucumber executes a Gherkin step in a scenario, it will look for a matching step definition to execute.

### Tags
You can use tags to group features and scenarios together, independent of your file and directory structure. This allows you to run multiple tests at once.

## FAQs
### Q. I don’t see anything loading in the UI
A. Go to Settings>Paths and make sure that the back-end framework’s path is selected. When you click browse, the selected folder should show “src” directory and “pom.xml”
### Q. Nothing loads on the dashboard or unexpected report loads 
A. Go to Settings>path and make sure the path for reports is empty if you want the default reports to load or select a specific report (index.html) for it to be loaded on dashboard
### Q. I selected a specific report and now I can’t clear the path to load the default view
A. To clear the path, you will have to go to Settings and click on “Reset Settings” button. Please note, this will also reset all other settings
### Q. The notification says “Test execution completed” but I do not see the updated report
A. This happens if there was an error in executing the tests after build was run successfully. Make sure your back-end framework is set up correctly by running command:
* `mvn clean install` to see if all default tests
* `mvn clean install  -Dsource.feature="<path of the folder where your feature files are located> " -Dapplication="<applicationName>" -Denvironment="<environment name>`
If any one of the above commands fail, you may need to update the back-end framework’s POM.xml
### Q. I don’t know what Page Objects or Test Data values are supposed to be used when I design tests
A. This is a limitation of the UI application and we assume that the person designing tests either knows the values in Page Objects and Test Data or can edit them in the back-end framework
### Q. I made some changes and added feature files directly in the back-end but I do not see them in the UI
A. To reload the list of feature files, please switch the workspace and switch back to your workspace. You will find that the list of feature files is updated
### Q. I cannot uninstall the application using the uninstaller.exe
A. This is a known issue as the uninstaller is flagged and quarantined by EY’s antivirus. Please uninstall the application by going to Control Panel > Programs > Uninstall a Program, then look for NGTP application and double click on it. Now you can follow the on-screen prompts to uninstall the application

***