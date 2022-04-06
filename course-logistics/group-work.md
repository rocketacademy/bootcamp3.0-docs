# Group Work

## Introduction

The workflow when coding in a group is different from coding alone. This module describes tools and workflows to enable smooth coding in a group.

## Principles

![](../.gitbook/assets/team-comms.png)

Working closely on a technical project in a group can be challenging. Not only as a coding challenge but as an exercise in communication. As teams get bigger, the communication necessary for coordination does not grow at the same linear rate.

If you've never coded in a team setting, understand that it will feel slow compared to the working alone, due to time spent on communication overhead.

In a real team setting this coordination and communication is the most important key to the success of a project (not its technical merits).

## Communication Processes

Usually, when discussing a team's successful collaboration, a big element is the processes put in place that make it clearer how all the relevant people are doing within the project.

We will outline these processes for dividing and completing tasks, which should make it easier to coordinate all the work.

All of these things are (not strictly) derived from "agile" workflow.

You can read more about agile [here](https://en.wikipedia.org/wiki/Agile\_software\_development).

### User Stories

The user stories are the first part of planning that state what the app should give the user the ability to accomplish, and why the user wants to accomplish that task.

* The user is going on a trip. They can create it within the app.
* The user wants to invite their friends. The app allows them to enter their friend's names.
* The user wants to keep track of all the places they want to go. The app allows them to record each place.

### Wireframes

Wireframes show visually how the user will accomplish the tasks described in the users stories. If a wireframe has a UX element that is not used for a task described in a user story, it should be removed.

### Kanban Board

![](../.gitbook/assets/kanb.png)

A Kanban board is a team document that is used for planning, to show what each team member is working on, and to show what parts of the project are already done.

You'll be using Trello to hold your Kanban board. The board will have the following three sections:

#### Backlog

The backlog section is the set of tasks that have to be done. When planning, the team will break the larger features / user stories of the app into small pieces that can be completed by one person in a relatively small amount of time.

Each team member will assign themselves a task in the board and move it to "**in progress**".

When planning try to avoid adding every single task that could ever conceivably be done in the future. This should be for features that have already been planned out in the user stories and wireframes.

#### In Progress

For tasks in progress.

#### Done

For done tasks.

## Git Workflow

One member of the team will create a GitHub repo and invite the other collaborators. See [2.15 Git Branches](../0-language-and-tooling/0.5-advanced-git/0.5.2-git-branches.md) and [2.ICE.7.](../0-language-and-tooling/0.ice-in-class-exercises/0.ice.1-git-branches.md)

For each task in the Kanban board create a new feature branch by checking out from `main`. Name the branch after the task. When a feature is done, push the feature branch to GitHub, create a pull request and merge the code into `main` from the PR in GitHub.

### Pulling and Merging Latest Changes in `main` to Feature Branch

When working in a team, the `main` branch will be updated regularly and we will want to incorporate those changes to our feature branches on a regular basis to ensure new features are still compatible with `main`. The following steps walk through how to merge changes from `main` to our feature branches.

1. Save & commit all changes on the current (non-`main`) feature branch. Get latest changes on `main` with `git pull origin main`.
2. If there are changes on `main` that are needed in the feature branch, do a merge while in the feature branch: `git merge main`
   1. Even if work is not completed yet on the feature branch, it's possible to do a defensive merge of `main` into the feature branch, even if that code is not needed immediately. This best practice prevents very large changes in `main` from being merged all at once.
3. Resolve any conflicts on the feature branch. Follow instructions in the console, using `git status` to see what steps are needed.

### Pushing and Merging Latest Changes from Feature Branch to `main`

1. Once we have committed all changes and resolved any merge conflicts in feature branch, push feature branch to GitHub with `git push`, then create a PR to merge feature branch with `main` on GitHub.
2. Once PR is merged, run `git pull origin main` to get latest `main` branch changes from GitHub.
3. Delete old feature branch locally with `git branch -d <MY-FEATURE-BRANCH-NAME>`
4. Delete old feature branch on GitHub with `git push origin --delete <MY-FEATURE-BRANCH-NAME>`
5. Once ready to work on new feature, checkout new feature branch from `main` and work on new feature with `git branch <MY-NEW-FEATURE-BRANCH>`

### Avoiding Merge Conflicts

In a React full-stack app, there are a few files that might generate merge conflicts, such as `App.js` or `routes.js` on the back-end. For the most part, to avoid merge conflicts it simply takes a lot of communication when two people are both changing these centralized files. Ideally each new change would just be done one after the other, where one person waits to get the code of the second person.

### Resolving Merge Conflicts

One hard rule is, _**never merge a pull request into `main` that has a conflict.**_ If there is a merge conflict it should be resolved inside the conflicting branch first, before it's merged into `main`.

### Merge `main` into Feature Branch Regularly

The main strategy for dealing with merge conflicts and keeping the `main` branch clean is to merge `main` into the conflicting branch and make all necessary code edits in the conflicting branch. (this all happens on the local computer). Then push that (now clean) branch to GitHub.

The commands for merging `main` to our feature branch will be:

1. `git checkout <MY-FEATURE-BRANCH-NAME>` to checkout feature branch
2. `git merge main` to merge the commits from `main` to feature branch
3. Resolve any conflicts on the feature branch
4. Once all conflicts are resolved, feel free to push feature branch to GitHub with `git push`, then create a PR to merge feature branch with `main` on GitHub.
