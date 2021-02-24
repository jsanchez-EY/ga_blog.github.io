# **Forking your Branch**
*  Moving forward, all product teams will work on a forking structure with NGeTAF
* There will be a main repository located on the Organization repo that will be called Trunk.
  This repository will have branches for all internal development projects but branches for
  any product or team-specific work.
* In order to ensure repo maintenance, only those with organizational owner roles will be
  allowed to push to these branches. Product team leaders will instead make a forked
  repository on their own GitHub account for their product team to work in.
*  In order to do this simply click the fork button while viewing the repository
*  This will create a forked copy of the entire repository on your own GitHub Account which
   you will have control over.
* Once you have forked the repo you will have full control over your forked repository and be
  able to share the repository with your team as long as they are registered members of the
  EY Advisory Technology Testing GitHub organization (restrictions to organization members
  and requirement of two factor authentication will still be enforced through forks, however
  you can grant all team members write access to your forked version of the repo)
*  Once your fork is set up, you can branch off of one of the internal branches and begin
   building your product/team specific branch
*  You may also rebase your project to your team branch if you so desire and create your own
   merging strategy within your forked repository
*  rebase function of GitHub allows you to change which branch is considered the main branch
   of your repo. In a single step,
* * 1. First, it saves all your changes in your branch (If you have any)
* * 2. It brings all the contents of the master branch into your branch
* * 3. If there are no merge conflicts, then it will put all your changes on top of the changes
       from master
* * 4. If there are conflicts, it will ask you resolve them file by file.
*  Essentially this will allow you to turn your product branch into your “master” branch
*  An example of how to do this follows:
*  **First:** Rebase your master branch to whatever product branch your team is working on. This
   can be easily done in GitHub by going to settings/branch and then switching the default
   branch to your product branch
* After you have rebased your project you will be free to delete all branches that do not
  pertain to your team (you can do this by clicking on code and then branch or branches in the
  top bar where it tells you the number of branches)
* For example, keeping the product branch from source as your master, each analyst you give
  permissions to can create their own branches as shown in below example
  Finally, Setup branch protection rules to ensure analysts cannot push directly to master and
  for every PR to have 2 required reviews before merge. Follow the below link to know how
  https://help.github.com/en/github/administering-a-repository/enabling-required-reviewsfor-pull-requests
* For Further forking Guidance refer to next section "Process to Create and Use Forks Effectively"
