## Introduction
[GitHub](https://github.com/) is a version control service. It is backed by [git](https://git-scm.com/) - a version control system.

GitHub tracks file changes and allows to collaborate on files in a group.

## Guide summary
This guide will explain how to contribute to GitHub repository using GitHub Desktop:
1. Forking and cloning forked repository onto local drive
2. Creating a new branch
3. Making and committing changes
4. Submitting a PR (pull request) and merging process
5. Syncing fork with original repository

Repository [l4d2-community-update/contrib-test](https://github.com/l4d2-community-update/contrib-test) can be used as a testing ground and will be used as a reference.

## Simple branching model
Repository contains of branches - independent versions of repository, with commit history inherited from another branch or entirely own.

Branch contains of commits[^1] - information units containing changes[^2] to specific files in repository.

- `main` - main working branch in original repository (an `upstream` branch for forked repository)
- `feature` - a branch containing changes to contribute, originated from `main`

[^1]: Commit contains of differences between two revisions of repository.
[^2]: Change could be anything - file modifications, creations, renames, deletions.

![feature](/src/feature.png)

In this illustration, commits `B` and `C`, containing pending changes are merged into main working branch with a merge commit `D`.

Branch `feature` originates from commit `A` of main working branch.

Commits `B` and `C` will be made in branch `feature`, and after merge, these commits will be a part of main working branch.

### Setting up Git client with GUI - GitHub Desktop
#### [Download GitHub Desktop](https://desktop.github.com/)
An app designed to simplify work with GitHub.

After installation it will ask to sign in, to be able to interact with repositories.

![signin](/src/signin.png)

Clicking `Sign in to GitHub.com` will redirect to your default browser to guide through authentication process, and then back to app.

You can sign in later through `File` -> `Options` -> `Accounts` in app.

## Forking repository
Fork is an independent full copy of a repository (including branches), through forks you may contribute to original repository. Changes made in fork will not be reflected in original repository, which makes it isolated.

If you don't have write access to repository (not able to make direct changes to it), then it must be forked first[^3].

You will always have a write access to your fork.

![fork](/src/fork.png)

`Fork` button is available at repository webpage, in the top right corner. Upon clicking you will be redirected to a new forked repository.

[^3]: If you don't have write access to repository, GitHub Desktop will fork it after your GitHub account automatically before cloning.

## Cloning repository
Cloning remote repository will download it onto local drive, so then local repository can be interacted with using Explorer and `git`.

Click `Add` -> `Clone repository` in app, then choose a remote repository to clone. Choose a fork to clone (your username will be listed as owner). If it doesn't appear - click `Refresh` button.

![clone](/src/clone.png)

Specify a `Local path`, which is a path to new local folder to be created with repository contents.

![clonedialog](/src/clonedialog.png)

In case of forked repositories, a dialog window will pop up, pick `To contribute to the parent project` -> `Continue`.

![usage](/src/usage.png)

Default branch of repository will be cloned.

## Making changes
You can make changes to contribute in a new branch of repository, following model `branch per feature`.

**Do not directly commit to default branch of your forked repository** - this is bound to create merge conflicts with original repository, and to solve them you'd need to remove your forked repository and fork original anew.

![newbranch](/src/newbranch.png)

Click on `Current branch` to show branch list, then click on `New branch`.

![newbranch2](/src/newbranch2.png)

It will let you know, that new branch will originate from `upstream` default branch, which is what you need. 

Pick a name for your new branch. You should stick to something generic and simple, describing change(s) as a whole.

Click `Create branch` - app will switch local branch to a new one, which is not yet published to your remote forked repository.

![newbranch3](/src/newbranch3.png)

Your local repository folder will now mirror current branch. Make changes to that folder - add/remove/edit files.

![commit](/src/commit.png)

GitHub Desktop will notice changes made to local folder and show a list of changed files and their details.

Create a commit - a dialog box in the bottom left corner of app will contain input fields for creating a commit.

You have to enter summary, - a short sentence summarizing changes in commit, and, optionally, - a description (containing more text and allowing to use new line).

Then you can click on `Commit to ...`, to add this commit to your local branch.

![commit2](/src/commit2.png)

You can see your commit and it's details in `History`. You may edit local (= not being pushed yet to remote repository) commits, or add more changes into the branch.

After you're done making changes, make sure to click `Push origin` (or `Publish branch` if you haven't done that already), to publish changes to remote, - this will upload your local commits to remote GitHub servers, and you will be able to see new changes at webpage of your repository in corresponding branch.

## Creating a Pull Request
Pull Request (AKA PR) is a proposal to pull your remote feature branch with original repository default branch, in other words, - request to contribute.

It will pull your changes in form of commits into commit history of original repository, effectively applying changes.

![createpr](/src/createpr.png)

You can find button `Create Pull Request` on `Changes` tab in app, which will open a browser page comparing changes between two branches - original repository default and your feature branch. You may attach files or images to your messages on website and discuss proposed changes with others, as well as continue working on your feature branch by committing more changes to it.

After pull request has been merged, you can safely remove your feature branch and keep contributing through new branches and pull requests.

You can always switch between branches, as long as you don't have any uncommitted changes, and work on different features simultaneously.

![prcollab](/src/prcollab.png)

Also you can contribute to other people pull requests using an app. To see the list of active pull requests of original repository, you can click `Current branch` -> `Pull Requests` tab.

Clicking on specific pull request will switch your local branch to related remote feature branch of its owner. There you should be able to commit your changes directly into that branch, and these commits will be added to PR.

Note for PR owners accepting collaborations: app may require you to sync your local branch with remote branch (in case someone has committed something for PR) before pushing more changes, - can do so by clicking `Fetch origin` -> `Pull origin` on current feature branch.

## Merging Pull Request
Now a maintainer (has write access) of original repository may merge your changes using one of three variants:
- (default) `Create a merge commit` - adds commits from feature branch to commit history of `upstream`, along with new commit describing merge changes and referencing PR
- `Squash and merge` - combines new commits into one
- `Rebase and merge` - creates new commits with changes to be pushed into history as if changes were done directly to `upstream`

You will be able to enter summary and details for first two options.

<!-- 
## Syncing up fork's default branch
First do `Fetch origin` - that will get latest information about branches and commits from remote forked and original repositories. It may also add an `upstream` default branch into list of branches, in case it wasn't there already.

Click on `Current branch` to view branch list. Switch to main working branch of your forked repository, listed as `Default branch`, by clicking on it.

![branchupdate](/src/branchupdate.png)

Click on `Choose a branch to merge into ...` while on default branch, then select `upstream` one, then wait until it checks for any updates.

![upstreammerge](/src/upstreammerge.png)

If there were any updates on original repository, then you might want to merge it in your fork - click `Create a merge commit`. Merge commit is now local, your remote repository is not yet updated, for that click `Push origin`, - this will copy commits from original repository into your fork.
-->
