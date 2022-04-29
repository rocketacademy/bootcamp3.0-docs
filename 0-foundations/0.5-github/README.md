# 0.5: GitHub

## Learning Objectives

1. GitHub is a code-hosting website that hosts Git repos for individuals or teams to review and collaborate on
2. Know how to fork a repo on GitHub
3. Know how to clone a repo from GitHub
4. Know how to push changes to GitHub
5. Know how to pull changes from GitHub
6. Know how to view repo commit history in GitHub

## Introduction

GitHub is a code-hosting website that hosts Git repos for individuals or teams to review and collaborate on. Team members can easily review latest code changes and commit history, making software development more transparent and thorough.

## GitHub Fork

A GitHub "fork" is a copy of another GitHub repo. SWEs typically "fork" repos they do not have edit access to either to make improvements to merge back into original repos, or to create and maintain independent versions of repos. At Rocket Academy we will fork Rocket exercise repos to complete and submit assignments.&#x20;

We can fork a repo by clicking the Fork button on a GitHub repo page. Once forked, we can change our copy of the repo without affecting the original.

![Click the Fork button to fork a repo](<../../.gitbook/assets/0.5 - GitHub - 1) Fork.png>)

![Fork menu; We typically keep the same repo name for clarity](<../../.gitbook/assets/0.5 - GitHub - Fork - 2) Fork menu.png>) ![Forked repo; Notice the repo is now under my account](<../../.gitbook/assets/0.5 - GitHub - Fork - 3) Forked repo.png>)

## Git Clone

Once we have edit access to the repo we want to edit, either by forking an existing repo or [creating a new repo](https://docs.github.com/en/get-started/quickstart/create-a-repo), we can "clone" (i.e. download) that repo to our local machine to make changes to it.

Click the copy button in the Code dropdown menu on the GitHub page of the repo we wish to edit.

![Click the copy button in the Code dropdown to copy the repo link to use with git clone](<../../.gitbook/assets/0.5 - GitHub - Clone.png>)

Then go to terminal, `cd` to the relevant folder and enter the command `git clone <repo-url>`, where `<repo-url>` is the URL we just copied from GitHub. This will create a new folder named after the repo with the repo's contents inside.

```
bootcamp % git clone https://github.com/kai-rocket/react.git
Cloning into 'react'...
remote: Enumerating objects: 203678, done.
remote: Total 203678 (delta 0), reused 0 (delta 0), pack-reused 203678
Receiving objects: 100% (203678/203678), 173.82 MiB | 5.85 MiB/s, done.
Resolving deltas: 100% (144768/144768), done.
bootcamp % 
```

## Git Push

We will learn 1 new Git command `push` to send local code commits from our computers to GitHub. `push` can also be used as a general command to move code between "remote" repos, but during Coding Basics we will only be using `push` to push code to GitHub.

![The "git push" command can be used to send local code commits to GitHub.](../.gitbook/assets/github-push.png)

## Git Pull

## GitHub Workflow Summary

Here is the workflow for Coding Basics projects:

1. Go to the project repo page. Click the "Fork" button to copy the repo to our own GitHub account.
2. In the command line on our local computer, **clone the repo from our own Github account's copy of the repo.**
3. Once the repo is on our computer, make the changes we want, and follow the Git workflow to commit those changes.
4. `git push` our changes to our repo. **Refresh** the repo page to see our commits in the repo.
5. Create a [pull request](0.5.1-pull-requests.md) in GitHub. This connects our work on the repo _in our account_ to the original Rocket Academy repo. Fill in the survey and submit.

## How to view commit history in GitHub

Reviewing commit history is one of the most useful features of GitHub. For example, if we are wondering which commit changed a line of code that caused a bug, we can easily find which commits changed that line, who made those commits and what else was in those commits.

![Click the number of commits on a repo's GitHub page to view a list of all its commits](<../../.gitbook/assets/0.5 - GitHub - 1) View Commits.png>)

![Click on any commits in the repo's commit history to view the details of that commit](<../../.gitbook/assets/0.5 - GitHub - 2) Commit List.png>)

![We can review complete details of each commit in GitHub](<../../.gitbook/assets/0.5 - GitHub - 3) Commit Contents.png>)

## Exercise

1. Fork a copy of the [Basics _Beat That_! repo](https://drive.google.com/drive/u/0/folders/16hSoY\_ldzSWCWP2VaAZlcyE9np1McymR) as setup for Project 2.
2. Clone the repo into a folder on your local machine.
3. Once you start working on your project, make frequent commits and use `git push` to update your GitHub repo.

## Additional Resources

1. [Git and GitHub in Plain English](https://blog.red-badger.com/2016/11/29/gitgithub-in-plain-english) (blog post)
2. [Git and GitHub by The Coding Train](https://youtube.com/playlist?list=PLRqwX-V7Uu6ZF9C0YMKuns9sLDzK6zoiV) (video playlist)
3. (Below) Intro to GitHub video from prior version of Rocket's Coding Basics course
4. (Below) GitHub Fork video from prior version of Rocket's Coding Basics course
5. (Below) GitHub Repo Browsing video from prior version of Rocket's Coding Basics course

{% embed url="https://www.youtube.com/watch?v=dn7r4333c4g" %}
Intro to GitHub video from prior version of Rocket's Coding Basics course
{% endembed %}

{% hint style="warning" %}
In the below GitHub Fork video we demonstrate `git push origin master`, but for most purposes `git push` will suffice.
{% endhint %}

{% embed url="https://youtu.be/uMNcnLWTmZU" %}
GitHub Fork video from a prior version of Rocket's Coding Basics course
{% endembed %}

{% embed url="https://youtu.be/a-flBCpOmBU" %}
GitHub Repo Browsing video from prior version of Rocket's Coding Basics course
{% endembed %}
