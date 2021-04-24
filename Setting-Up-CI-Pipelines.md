# **Setting up CI Pipelines**
Every library must have a `.github/workflows` package with predefined workflows for PR merge request and Release process. Reach out to the Build & Implementation team to get the workflows. This will be run automatically in GitHub actions everytime you push a code to a branch or merge a code with the master, automatically releasing a new version of the project

There are two workflow jobs `Pre-merge check` and `release` that should be added to all repositories. You can find them in your repository under `Actions` tab. All that is needed to do is, navigate to action and apply these generic workflows. Pre-merge Check will monitor any pushes to any branch or master and run the pipeline activities such as verifying all the quality gates passed and prevent the merging of any non-compliant code. Ensure these 2 workflows are successful after push.

![custom actions](images/resources/github/actions.jpg)

Pre-merge check  job will be run when code is pushed to other than Master and Main branch  on the following folders
- '/src/**'
- 'pom.xml'
- '.github/**'

Release job will be run when a pull request is merged to Master or Main branch. A release jar will be created with updated version mentioned in POM.xml.  Whenever you push changes in one of the locations mentioned above, ENSURE YOU ARE UPDATING THE YOUR REPOSITORY VERSION in the POM.XML.-v

![pom-version](images/resources/intellij/pom-version.jpg)
