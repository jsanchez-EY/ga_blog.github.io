# **Setting up CI Pipelines**
* The Trunk master branch will have a CI pipeline setup using CircleCI to make sure every PR is
tested before merged.
* Once your Fork is setup, You can add CI pipelines to automate the build process using
CircleCI as below:
    * Go here https://circleci.com/integrations/github/
    * Signup using GitHub account
    * Select the repository you want to add CI
    * Select Maven as build tool
    * Click next until Pipeline runs
    * That’s it! (These are the basics. You can read up scheduling jobs here: https://circleci.com/docs/2.0/workflows/)
