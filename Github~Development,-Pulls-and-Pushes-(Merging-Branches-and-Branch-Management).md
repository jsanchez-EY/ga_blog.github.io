# **Development, Pulls and Pushes**
* After you have created your team’s fork it will be up to you and your team to manage you
and your teams code before creating a pull request to merge your code back to your
product branch in organization’s repo
* You may create a pull or push request from any branch in your repo to any branch in the
organizations main repo as required. They will then be reviewed by the NGeTAF repo
management team for approval to ensure no code breaks occur. Once submitting a pull or
push request, email ngetaf.repo.managers@ey.com with information about your request
and someone will review the request for approval asap
* A best practice for analysts creating new functionality on a fork follows:
1. Analyst clones the master branch into his local
2. Analyst develops new code
3. **Important:** Analyst Must take updates from master before committing changes back
* **Tip:** Use rebase discussed above to do this in a single step instead of doing
git stack push and git stack pop every time.
4. Analyst commits his changes
5. Analyst pushes his changes to origin/feature/… or origin/fix… branch. The below
template must be followed for long-term maintenance reasons.
* **Important**
* * E.g. **feature/product1_trading** – If you are pushing a trading functionality for a product branch.
* * **fix/product1_trading_glue_code** – if you are fixing a glue code for
trading-functionality for a product1.
6. GitHub creates a new branch as created above
7. Analyst creates pull request of new code into master branch of fork
* **Important**
* * All Pull Requests title should be the same as the branch name created
above. This makes it easier for Owners to investigate PRs and track it down to
branches or features down the road.
* * The PR should have a description of what was changed.
* * The PR should have a screenshot of unit tests passing or some evidence
that it did not break existing code.
8. Owner and 1 peer (if team is large enough) review code and approve
* **Important**
* * The PR should be reviewed and approved only after the CI pipeline build
succeeds.
9. Owner approves pull request to merge code and the development branch (Analyst
creates new branch off master for next development effort)
* It is also worth noting that all the above repo management procedures can be conducted on
GitHub desktop as well, and it is strongly recommended to leverage GitHub Desktop to see if
your team can benefit from its use.
* Once you have your forking structure set up and have created some new functionality that
you would like to share back with the main NGeTAF repository, simply make sure the code is
pushed to the main branch of your forked repo’s origin and create a pull request between
your main branch and the product branch of NGeTAF
* Similarly, if there is an update added to NGeTAF branch from an internal project, those
updates can be aggregated to your fork either by you or the NGeTAF repo team
* All major releases will require for all product teams to push their finalized code via pull
request to their product branch on the organization’s repo for the NGeTAF internal
team to aggregate the code to all branches effectively

NG eTAF Setup

Open cucumber.properties.