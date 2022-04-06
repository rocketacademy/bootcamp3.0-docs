# Course Methodology

## General

### Difficulty Levels

To accommodate individual learning speeds and levels of experience, exercises and projects in Coding Bootcamp may be divided into sections that demarcate the levels of difficulty.

#### Base section

Everything in the Base section must be completed in order to have an adequate grasp of the concepts being taught. It is the bare minimum that needs to be done.

#### Comfortable

The Comfortable section is for students who have completed the Base section and wish to reinforce what they have learnt before moving on to more complex and challenging exercises.

#### More Comfortable

The More Comfortable section is for students who have completed the Base and Comfortable sections, and wish to push their boundaries.

Students can complete Coding Bootcamp successfully without ever attempting problems in the More Comfortable section, but students that complete More Comfortable exercises may be more valuable in the job market.

### Exercise / Project Strategies

#### Read full project page before starting

Please read through projects requirements thoroughly, and take all of them into consideration before starting work on your project. Different parts of the project might require different code architecture and starting without taking all factors into account might result in a lengthy code refactor.

#### Separate UI code from logic code

Whenever possible, keep UI and logic code separate. This makes your code easier to debug as you only have to worry about one section at a time. For example, code to manipulate the DOM can be separated from code that determines rules of a game.

#### Use a project management tool

Project management tools are often used in managing longer-term projects involving multiple people. They can also be used in individual projects to help with things like prioritizing certain tasks and organizing workflow, among other things.

[Trello](https://trello.com) is a popular, easy-to-use project management tool that we recommend for Coding Bootcamp. [Here](https://blog.trello.com/how-to-scrum-and-trello-for-teams-at-work) is a breakdown of how to get started with it.

### Recommended Daily Order of Work

On any given day in Coding Bootcamp, students will have to do post-class exercises for the current day, pre-class exercises for the upcoming day, and will possibly be working on a project on top of the usual daily exercises . RA recommends that students prioritize the material in the following order.

1. Base section of post-class exercises / project
2. Pre-class exercises
3. Comfortable and More Comfortable sections of post-class exercises / project

### Saving work from a forked copy of RA's repo to a New GitHub Repo

To save work from a forked copy of a bootcamp repo to a new repo, follow the instructions below.

1. Create a new, empty repo in GitHub
2. In your local copy of the `base-node-bootcamp` repo that you want to now link to your new repo, run the command `git remote set-url origin <NEW_REPO_HTTPS_URL>`, where `<NEW_REPO_HTTPS_URL> is https://github.com/<GITHUB_USERNAME>/<REPO_NAME>.git`. This will link your local repo to the new repo, and unlink it from `base-node-bootcamp`.
3. Run `git remote -v` to verify that our local repo is linked to the new repo in GitHub
4. Commit any desired local changes and run `git push`. This will push the current state of the repo to the `origin` remote, which should be the new repo we created.

## Peer Code Review

On days where there are longer post-class exercises or projects due, we will review each others' code in pairs during class. If there is an odd number of students in the class, the student without a partner will join a pair so that everyone gets to review someone else's code.

### Individual

1. Clone partner's code
   1. You'll be paired up so that you can exchange the links for your repos via Slack. Remember that the forked repo is the one that is under your GitHub account, not Rocket Academy's.
   2. **If you have forked the repo, but you have not pushed your latest changes to GitHub,** take a moment now to do a `git push`. Let your partner know you're updating the repo.
   3. Run `git clone <repo-url> <new-folder-name>` to clone your partner's code. You will need to rename the target folder when you clone if you already have a folder named after the repo.
2. Run partner's code
   1. Open the code in the browser and test it. What does it do? If you're not sure what it does look inside the `script.js` or relevant files to see.
3. Read partner's code
   1. How does it work?
   2. Does it have any obvious errors?
   3. Does it implement something that you were trying to do?
   4. Does it implement a feature that you haven't started yet? How does the code work?
4. Play with partner's code
   1. It may be helpful to make changes to the code to help you understand it better. Write some `console.log` that would help you figure out what the code does. Break the code in a certain way to prove how it works or doesn't work.
5. Open your partner's GitHub Pull Request and complete a code review on their code to help them improve.

### In Pairs

1. Discuss findings from individual code review
2. Pair program on 1 person's project at a time. The goal is to get working versions for each person. **The driver will be the person who is \*not\* working on their own code.**
3. Once done with 1 person's code, send the code to your pair (it's their project) via a [Slack code snippet](https://slack.com/intl/en-sg/slack-tips/share-code-snippets). Switch to work on the other person's code. If you are working on your partner's code you can't push to their repo because GitHub repos are read-only to non-owners by default.
4. Once both have working versions, implement a new feature in 1 of the repos together.

## Project Scrums

Professional tech teams typically operate using [Agile Scrum Methodology](https://www.atlassian.com/agile/scrum). This is simulated during Coding Bootcamp project weeks. Each course day during project weeks students will take turns sharing the following with each other, helping everyone stay on-track with their projects.

1. What did you do between the previous course day and today?
2. What do you plan to do between today and the next course day?
3. Do you have any blockers?

## Project Presentations

Students present projects in class on the last day of each project. Presentations should cover the following.

1. App demo
2. App development strategy
3. Biggest challenges faced
4. What they might do differently next time

## Project Post-Mortem Meeting

After each project an instructor will review your code with you 1-1. Please prepare answers to the following questions before the 1-1, and be prepared to discuss your code that relates to each answer.

{% hint style="info" %}
Please keep track of post-mortem notes because they can be helpful for compiling your project portfolio at the end of the course!
{% endhint %}

### Technical Review

"Technical" refers to software logic and syntax.

1. What went well? Please share a link to the specific code.
2. What were the biggest challenges you faced? Please share a link to the specific code.
3. What would you do differently next time?

### Process Review

"Process" refers to app development steps and strategy.

1. What went well?
2. What could have been better?
3. What would you do differently next time?

## Project Videos

Congrats on a job well done! You'll now create a short video to help showcase your hard work.

{% hint style="info" %}
No need to record a video for project 1, video poker.
{% endhint %}

### Requirements

1. Demo your app in a 1-2 minute video (brevity is best!)
2. Explain who your app is for, what your app does and how a user would use the app.
3. Explain features of the app in the context of what the user wants to accomplish and why they want to accomplish it.
4. The video _**should not go into any technical details**_ that would be incomprehensible to someone non-technical.

For example, when demoing an e-commerce app, discuss the process of the user selecting an item they want to buy and ordering it, instead of how when the button gets clicked that it creates an HTTP POST request.

### Focus On What You Did, Not What You Didn't Do

When speaking it is a common impulse to downplay what the app does. This includes statements like: "This is just a simple app". "I didn't complete this". "I didn't have time to....", "This doesn't work well/is not designed well, but..."

If you catch yourself saying any of these phrases in the video, stop and re-record it. Remember that this video is to demonstrate what the app does do, not to talk about what it doesn't do.

### How to Record the Video

Use Zoom to record the video locally on your computer. It will record you and your face in the upper right corner. Once done recording, make the video available in the following ways.

1. Upload it to YouTube. Embed the video in your project README.md file.
2. Put the video file in your project repo, commit the file and push it to GitHub.

### Previous Examples

{% hint style="info" %}
These videos are longer than 1-2 minutes, but please try to make your own videos within the 2 minute limit.
{% endhint %}

[https://www.youtube.com/watch?v=466AbXvMdzc](https://www.youtube.com/watch?v=466AbXvMdzc)\
\
[https://www.youtube.com/watch?v=JjHM96XIXjs](https://www.youtube.com/watch?v=JjHM96XIXjs)\
\
[https://www.youtube.com/watch?v=RxihjXRp7cQ](https://www.youtube.com/watch?v=RxihjXRp7cQ)
