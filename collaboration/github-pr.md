# Creating Github Pull Requests

In order to work effectively with git and github, you must understand the philosophy of it’s development mode. Git was created by Linus Torvalds to solve the code management issues experienced by the Linux kernel team. This team is highly distributed, highly capable, and very large, so the design requirements for git were to be very fast, very flexible, and to work well with a distributed team.

GitHub adds to the core of git a web interface that makes it easy to browse code, create repository forks, and assign permissions. This combination is extremely powerful when used effectively. In order to work effectively in this model, you must be able to create independent changes to your code and submit them as a functional changeset.

## Steps

![steps](http://i.imgur.com/waNfkzN.png?1)

## Clone the repository

Before you clone the repository, get the permissions to the repository from admin.
To clone the repository, type `git clone <https_url_of_repo>` in terminal.

## Decide what to implement

Typically, in github, work is tracked via the "Issues" system. If the work you are planning to do is not represented by an issue, you should create one and assign it to yourself. This ensures that other folks know what you are intending to implement and prevents duplicated work and confusion. It also provides a convenient place to discuss your plans with other developers.

## Reset your working tree

It is very important to always start with a clean tree, so you should always run `git fetch origin && git reset --hard origin/master` prior to creating your branch. These commands will wipe away any local state and ensure you are starting fresh with the latest functional code from the origin master branch.

## Create a feature branch

Once you are know what task you are taking on, you should create a feature branch and switch to it using the `git checkout -b my_new_branch` command. The branch name, in this case `my_new_branch`, should be descriptive of the work you intend to do.

## Implement your feature

This is where development happens. You should get in the habit of checking in early and often so you can easily use the power of git to restore yourself to a functional state. You will need to use the `git add 'file'` command to stage files for committing, and use the `git commit` command to actually save the changes. While you work, the `git status` command is a good way to keep track of the files you have changed, and the `git diff` command provides invaluable insight into what changes you have made.

Since you are working in a private branch, there is no penalty for committing early and often, but you should still make your best effort to create a meaningful commit message describing your change. In addition, you should get in the habit of pushing your branch to a central repository so others can view it, again, early and often. Assuming you are operating out of a private fork of the repository, you would use the command `git push origin my_new_branch` to send all your commits to github. If your repositor is configured with continuous integration this is a convenient way to run your full testsuite without slowing down your local development environment, too.

**Tip: Commit early and often**

## Open a pull request

Once your branch has been pushed to the origin and is ready for review, you should open a pull request. To do this, browse to the github ui, find your branch, and click the "compare and create pull request" button. You should look at the changed files and make sure you have not included anything by accident, and then write a detailed commit message describing the changes implemented by your branch.

Always write unit test cases for new code and check throughly for any edge cases.

**Tip: Try to keep your pull requests short and sweet**

## Receive feedback

Once you have opened a pull request, all project "watchers" will be notified. If necessary, you may want to also connect with them out of band, via IM or email, and let them know you have submitted a pull request for review. The merge master or code reviewers should view the pull request, pull it to their local machine for testing, and add any comments to the pull request. You should respond to these comments as quickly as possible, either inline or by adding additional commits to your branch and pushing it to the origin repository.

## Rebase or merge (if necessary)

If your pull request stays open for a long time, you may find that other changes have been merged to the  master branch before your pull request has been. In order to faciliate merging your pull request, you should pull the master changes into your branch. You can do this simply by running `git fetch origin && git merge origin/master`. You may need to resolve conflicts, which you should do carefully and commit the result. After committing, push your feature branch back to origin repository in order to update your pull request.

## Start again

Once the feedback cycle is completed, the merge master will merge your code. You are now ready to start work on another feature by checking out master, resetting it, and creating a feature branch. Keep in mind that there is nothing preventing you from maintaining several feature branches and pull requests at a time. The git checkout command is extremely fast, and wherever possible independent features should be kept as independent commits so they can be referenced in the future.


