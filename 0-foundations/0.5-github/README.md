# 0.5: GitHub

## Learning Objectives

1. GitHub is a code-hosting website that hosts Git repositories for individuals or teams to review and collaborate on
2. GitHub (and other code-hosting platforms such as BitBucket, GitLab) serve as the source of truth for project repos shared among teams

## Introduction

We'll use GitHub to download starter code, and after we learn forking, pushing, pulling and pull requests, we'll use it to submit projects and store our code online.

## Additional Resources

1. [Git and GitHub in Plain English](https://blog.red-badger.com/2016/11/29/gitgithub-in-plain-english) (blog post)
2. [Git and GitHub by The Coding Train](https://youtube.com/playlist?list=PLRqwX-V7Uu6ZF9C0YMKuns9sLDzK6zoiV) (video playlist)
3. (Below) Intro to GitHub video from prior version of Rocket Academy's Coding Basics course

{% embed url="https://www.youtube.com/watch?v=dn7r4333c4g" %}
Intro to GitHub video from prior version of Rocket's Coding Basics course
{% endembed %}

# 0.5.1: Navigating GitHub

## Learning Objectives

By the end of this lesson, you should:

- Be familiar with navigating GitHub.
- Know how to view the commit history of a repo.
- Know how to navigate the Pull Requests tab in GitHub

## Introduction

{% embed url="https://youtu.be/a-flBCpOmBU" %}

One of the biggest benefits of Git is the ability to see contents of previous commits or versions. We can do this within the command line interface of Git, but it is easier on the GitHub website. Familiarise yourself with everything the GitHub website can display about your repo.

## Repo and Commit Navigation

![View a list of all commits.](../../0-foundations/.gitbook/assets/screen-shot-2020-09-22-at-9.09.22-pm.png)

![See the contents of each commit.](../../0-foundations/.gitbook/assets/screen-shot-2020-09-22-at-9.11.32-pm.png)

![Commit contents include a "diff" for every changed file.](../../0-foundations/.gitbook/assets/screen-shot-2020-09-22-at-9.12.10-pm.png)

## Pull Request Navigation

![View the full file, not just a "diff" of changes between old and new versions of the file.](../../0-foundations/.gitbook/assets/screen-shot-2020-09-22-at-9.14.16-pm.png)

![View a list of all pull requests on a repo.](../../0-foundations/.gitbook/assets/screen-shot-2020-09-22-at-9.15.17-pm.png)

![View details of a single pull request.](../../0-foundations/.gitbook/assets/screen-shot-2020-09-22-at-9.16.06-pm.png)

![View a list of all commits within this pull request.](../../0-foundations/.gitbook/assets/screen-shot-2020-09-22-at-9.18.14-pm.png)

{% hint style="info" %}
**What if I want to undo something from a previous commit?**

We can "roll back" our repos to a previous commit with the `git revert` command, but due to the small nature of our apps in Coding Basics, it may be easier to "roll forward" by copying the code we want from a previous commit in GitHub, pasting that code into our local repo, and creating a new commit for these changes.
{% endhint %}

## Exercises

### Follow Along

Follow along with the video to navigate your own repo.
