---
description: Social Coding with GitHub
---

# Social Coding

## Git Rules

1. Create a Git repository for every new project
2. Create a new branch for every new feature
3. Use Pull Requests to merge code to Master

## Source Code Management

* Source Code Management is the practice of tracking versions of source code as it is being developed.&#x20;
* A source code manager (SCM) is a software tool used by teams of programmers to manage source code
* These are also referred to as Version Control Systems (VCS)
* SCMs can be Centralized or Distribute

### Distributed or Centralized

* Distributed revision control (DRCS) takes a peer-to-peer approach, as opposed to the client-server approach of centralized systems
* Rather than a single, central repository on which clients synchronize, each peer’s working copy of the codebase is a bona-fide repository
* Distributed revision control conducts synchronization by exchanging patches (change-sets) from peer to peer

### Decentralized systems

* No canonical, reference copy of the codebase exists by default; only working copies.
* Common operations (such as commits, viewing history, and reverting changes) are fast, because there is no need to communicate with a central server.
* Communication is only necessary when pushing or pulling changes to or from other peers.
* Each working copy effectively functions as a remote backup of the codebase and of its change-history, providing natural protection against data loss.

### Git: Decentralized SCM System

* A distributed source code management (SCM) tool invented by Linus Torvalds in 2005 for Linux kernel development
* Code is kept in a repository and every developer has a full copy
* Works locally without any server
* Works remotely with GitHub, GitLab, & BitBucket

### GitHub: A website that hosts git repositories

* A web site that hosts git repositories
* Founded in 2007, has 40 million registered developers and was acquired by Microsoft for a whopping $7.5 billion in 2018
* Free and Paid accounts
* Adds ability to track Issues and Bugs
* Provides webhooks to integrate other tools

## Why You Need to Know Git?

* The use of Git and software code repositories has fundamentally changed the way enterprises do software development for proprietary code and open source code alike.
* In addition, open source software has blossomed because some of the Git repositories host open source code for free.
* Most significantly, Git and code repositories have facilitated the DevOps methodology that is so impactful to software development.

![Git Command Workflow](<.gitbook/assets/image (2).png>)

## What is Social Coding?

* In the past developers worked on **private** repositories and you had to be a member of the team to contribute
* With Social Coding, repositories are **public** and everyone is encouraged to Fork the code and contribute
* You would think that anarchy would ensue but it actually works quite well because it is controlled by the repository owner

### Code Reuse Dilemma

* You see a project that is 80% of what you need but there are some missing features
* You feel that if you make a feature request of the project owner, your request will be at the bottom of their priorities (If they get funding cuts, you know that your feature request will be cut)
* So you rebuild 100% of what you need so as not to have a dependency on another project

### Social Coding Solution

* Discuss the new feature with the repo owner and agree to develop it
* Open an **Issue** and assign it to yourself so that everyone knows what you are working on
* **Fork** the code, create a **branch**, and make your changes
* Issue a **Pull Request** when you are ready to review and merge your work back into the main project

## GitHub Is A DevOps Enabler

* [x] Open Culture: Forking and Pull Requests enable openness
* [x] Emphasize Collaboration and Sharing (no Silos): Issues and Comments invite Collaboration and Planning
* [x] Infrastructure as Code: Git the the perfect place to store all of your infrastructure scripts
* [x] Automate Everything: Git works well with Travis CI, Jenkins, and other automation tools

## Git Overview

Brief introduction [up here](social-coding.md#git-decentralized-scm-system).

* Git works well with Travis CI, Jenkins, and other automation tools
* Developers work in their own BRANCHES (even in FORKS)
* The MASTER branch should always be ready to deploy
* PULL REQUESTS are used to MERGE code BRANCHES into MASTER

### Detailed Feature Branch Workflow

* CLONE a Repository (FORK first if not part of Dev Team)
* Assign the ISSUE for your work to yourself and place it in working status
* Create a BRANCH to work on an ISSUE
* Run the Test suite to make sure you can run the code
* Make changes to code and test cases and COMMIT to local BRANCH
* Run the Test suite early and often to make sure you didn’t break anything
* PUSH changes to remote BRANCH
* Did we mention testing the code early and often?
* Create PULL REQUEST when all tests pass and code is ready for review / MERGE

### Why is Testing So Important?

* Automated testing must pass before your Pull Request will be accepted
* Automated testing is your guarantee that you didn’t break anything
* Without automated testing you cannot fully automate the DevOps pipeline

## Guidelines for Contributing: \`CONTRIBUTION.md\`

To help your project contributors do good work, you can add a file with contribution guidelines to the root of your project's repository. Then, whenever someone opens a pull request or creates an issue, they will see a link to that file. Good Social Coding requires that everyone know and follow the guidelines.

As you can imagine, with outside contributors there must be coding standards. Use a `CONTRIBUTION.md` file to document how to contribute. It’s a good idea to publish your coding standards on your GitHub Wiki or other public place and point to them in your `CONTRIBUTION.md` file. When a Pull Request is made, you should also check that the standards have been followed.

## Issues: Tacking What You Do

* When a Pull Request is made, you should also check that the standards have been followed
* ISSUES can be features or defects or pull requests or …
* You should not be working on code without an open ISSUE
* You should not be working on code without an open ISSUE

## Branches

* Branching is a core concept in Git: Branching is a core concept in Git
* The only rule: Anything in the **master**/**main** branch must always be deployable
* It's extremely important that your new branch is created off of master when working on a feature or a fix

## Pull Request Workflow

Use a PULL REQUEST to notify the team that you changes are ready to be reviewed and merged into the MASTER branch. The pull request workflow helps us to share information.

Benefits:

* A second set of eyes: Sometimes you may have solved a problem, but when someone reviews it they pointed out a subtle flaw, or perhaps a way you could solve it more elegantly. It also helps identify things like security exposures. This results in a much cleaner codebase.
* Knowledge sharing: It is dangerous to only have one developer that understands the code. Having another developer review the code allows for shared understanding and protects against one developer leaving the project.
* Allows automation of unit testing: You setup your GitHub project to run unit tests on pull requests so that we can verify that everything works before merging.

### Prepare for Pull Request

* You want to make sure that you are using the latest code before you make a pull request
* The remote master branch has probably moved on since you created your branch
* Therefore it is necessary "rebase to" or "merge with" the current master

## Fetch vs Pull

* Fetch will bring down all of the changes from the remote repository
* Pull will merge the changes from the current branch with your local workspace

Note: Pull does a fetch so if you just want to pull there is no need to fetch.

## Merge vs Rebase

**Merge** joins two branches together, usually your branch and master but it can be any two branches only changing the checked out branch. If there are no conflicts and the current HEAD is an ancestor of the merge branch, git will fast-forward the merge by moving the pointer forward. Merge retains all the history as it happened chronologically

**Rebase** will replay your changes on top of the current version of master. It will look as if your branch was created from the current state of master. It will look as if your branch was created from the current state of master. You can optionally do this before pushing/creating to remote branch otherwise use merge. **Never rebase once you have pushed to a remote**. It will mess everyone else up because it changes history in a way that is incompatible.

## Reset vs Revert

### Reset: Rewind the Mistakes Before Push

If you have NOT pushed to a remote branch, you can use `reset` to go back to a previous commit. Reset rewinds the commits as if they never happened.

* To get rid of the last two commits

```bash
git reset --soft HEAD~2
git reset --hard master@{1}
```

* `--soft` will undo the commit history and leave the files staged
* `--mixed` will undo the history and the staging so the files are untracked (default)
* `--hard` will undo and **delete** your files!

### Revert: Rewind the Mistakes After Push

If you made a commit and pushed it to the remote, how to do undo it because other people may have access to the remote?

```bash
git revert <sha1>
```

Revert is the only **safe** undo for a commit that has a remote push.

Note: revert will not remove files that are pushed remotely.

### Comparison

**Reset** will alter history as if it never existed. This will confuse remote repos so once you push a commit you should not reset it.

**Revert** will undo history by adding a commit that reverses the changes. This is remote repo friendly.

## Merge Conflicts

Git cannot merge code that has the **same line** of code changed in two **different branches**. This requires **manual intervention** and probably collaboration with the developer who made the other changes.

#### Resolution

For pull requests, you should merge from the master branch first. If there were conflicts, they would appear in the current branch.&#x20;

* Edit the file in conflict and commit. (If is during a rebase, you should `git rebase --continue`).

```bash
git commit -am "Fix: Resolve conflicts"
```

* Then you can proceed to merge the pull requests into the master branch.

### Abort a Merge or Rebase

Never leave a merge or rebase in an unfinished state!

* For merge, you can abort it with: `git merge --abort`
* For rebase, you can abort it with: `git rebase --abort`
