# Project 2: Full-Stack App (Firebase)

## Introduction

Build an app that solves a problem you have using React and Firebase. Feel free to use any 3rd-party libraries and all Firebase features beyond the ones we have learnt.

## Requirements

### App

1. React app with Create React App
2. Data storage with Firebase Realtime Database or Firebase Firestore
3. Async/await syntax to manage asynchronous functionality such as HTTP requests
4. 1 or more requests to an external API using Axios or Fetch libraries
5. `useEffect` hook to retrieve data or perform other "side effect" on component load for 1 or more components
6. File upload with Firebase Storage
7. Authentication with Firebase Authentication
8. App routing with React Router
9. At least 1 custom higher-order component
10. State management with React Context

### Other

1. Deployment with Firebase Hosting
2. Naming, casing and commenting [best practices](../general-reference/naming-casing-and-commenting-conventions.md)
3. Git commits for each feature with descriptive commit messages
4. App description in README with user stories and low-fidelity wireframes
5. Instructions in README to run app

## Ideas

TBD

## Project Timeline

### Summary

| Course Day | Deliverable                                                                                                                                                                               | Instructor Feedback                                                                 |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| CD10.3     | <p><strong>Start: Ideation Phase 1.</strong></p><p>Introduce project, post project ideas in Slack for feedback</p>                                                                        | Instructor to share feedback on project ideas in Slack.                             |
| CD11.1     | <p><strong>Start: Ideation Phase 2.</strong></p><p>Create planning docs: user stories, wireframes, and DB ERD.</p>                                                                        |                                                                                     |
| CD11.3     | <p><strong>Due: Ideation Phase 2.</strong></p><p>Finalise project idea and share planning docs in GitHub repo over Slack.</p>                                                             | Instructor to review planning docs over Slack and over Zoom if necessary.           |
| CD11.3     | **Peer Planning Review.**                                                                                                                                                                 |                                                                                     |
| CD11.3     | **Start: Project Start.**                                                                                                                                                                 | Begin Project Implementation                                                        |
| CD12.3     | <p><strong>Due: MVP deadline.</strong></p><p>Users should be able to perform the primary user story. Please deploy your app to Heroku. Students to review code in pairs during class.</p> | Instructor to review code on GitHub, share feedback in Slack and Zoom if necessary. |
| CD12.5     | <p><strong>Due: Feature freeze.</strong></p><p>No more developing new app functionality. Use remaining time to focus on polish, i.e. fixing UX/UI, refactoring code.</p>                  | Quick project review in class to discuss improvements post-feature freeze.          |
| CD13.2     | **Due: Project presentations.**                                                                                                                                                           | 30-minute post-mortem with instructor. Instructor to review code in PR on GitHub.   |
| CD13.3     | **Project Peer Review exercise.**                                                                                                                                                         |                                                                                     |
| CD13.5     | **Due: Video demo.**                                                                                                                                                                      |                                                                                     |

### Recommended Order of Implementation

Implement the core user story first. What are users coming to your app to do? Make sure they are able to accomplish that, before adding authentication and nice-to-have features.

1. CRUD functionality
2. Login functionality
3. Any stretch functionality, e.g. AI APIs or file uploading

## Ideation Phase 1

Brainstorm app ideas. What problem does the app solve, for whom? How does the app solve the problem? What data does the app handle? Feel free to use [Rocket's project planning template](https://docs.google.com/document/d/1klyi92bVHUKjxgD\_Saou\_u6yoEZFbzkvbttj2izh8xg/edit?usp=sharing), and share your ideas with your SL in Slack to get feedback.

## Ideation Phase 2

Plan the app implementation with the following planning docs.

1. [User-flow diagram](https://careerfoundry.com/en/blog/ux-design/what-are-user-flows/)
2. Wireframes of minimal UIs that enable our user flows
3. Database ERD to support our user flows and wireframes.

Save these planning docs in a project GitHub repo and share it in Slack. Instructors will review these planning documents with you before you begin implementation.

## MVP Deadline

A user should be able to play the game through once without encountering errors. App should be deployed to Heroku. Peer code review during class.

## Feature Freeze

The app and all its features should run without errors. Brief demo in class to demonstrate user experience and clarify work to do before presentations. Latest app should be deployed.

## Project Presentations

Presentations should cover the [topics in this list](../logistics/course-methodology.md#project-presentations).

## Post-Mortem Meeting

Please answer the [project post-mortem questions](../logistics/course-methodology.md#project-post-mortem-meeting) before the post-mortem meeting with your instructor. These questions will be similar to the presentation questions, but we will dig deeper into your code.

## Video Demo

Please follow [video demo guidelines here](../logistics/course-methodology.md#project-videos).

## Project Submission and Past Student Projects

Once done with your project, please submit it by adding it to the [Rocket Bootcamp Projects spreadsheet](https://docs.google.com/spreadsheets/d/1YZ39naj5E6mNNkQ1akR\_FgeFO\_kM6aWCAr8zqrFOkt4/edit?usp=sharing) in your batch-specific sheet. Feel free to view past student projects in previous batches' sheets.





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
