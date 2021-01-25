# **Process to create and use forks effectively**
* To create your fork, navigate to the trunk/master in GitHub and select the Fork button on the top right
corner
* Fork the project into your personal space. Fork should be created under your user name
* Next, Change the name of your repository in settings tab
* Clone this repo on your local system
* Or in Terminal/Git Bash as:
* * `$ git clone <clone path> e.g. $ git clone`
* * `git@github.com:<your_username>/<your_fork_name>.git`
* * `$ cd <project root folder>`
* Next, you need to add a reference back to the original repo by adding a secondary remote called
upstream. Execute the following:
* * `$ git remote add upstream <master/trunk path>`
* * e.g.
* *` $ git remote add upstream git@github.com:ey-advisory-technologytesting/Trunk.git`
* Once this is set up, you can work with the repo from this point forward. Any time before beginning
work, however, sync your local repo with the original repo by executing the following:
* * `$ git checkout master` checks out your fork master to your local
workspace
* * `$ git fetch upstream` Tunes into your original master (for lack
of a better term)
* * `$ git pull upstream master` Pulls changes from Original master
* *  `$ git commit -m “<message>”` Commits changes
* * `$ git push` Push changes to the Fork master ( You
will follow all outlined rules regarding PR processes, of course)
* Your local master is now in sync with the upstream master and also has the changes you pushed in now.
You can now create a branch and make changes, and commit and push your branch to your personal
fork. When you are ready to push some functionalities back to the original repo, select that as your
target branch
* Click New Pull Request and select the base repository(the one you forked) and the head repository(the
fork) and select master on both ends for branches since you want your fork master changes to be
merged with your Original repo
* **Caution: Commit only the things that are additional capabilities which are generic enough to be**
**merged upstream. Reviewers need to exercise caution.**
