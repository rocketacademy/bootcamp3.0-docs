# Project 2: Server-Side App

## Introduction

This app is a culmination of everything we've learned about server-side web applications. It is an open-ended project, meaning you will build something based on your unique needs.

As much as possible, create milestones so you know whether you are on track, and to prioritise features when you are short on time. We expect half or more of our time to be spent on polish after finishing our apps' core functionalities. We encourage refactoring or rewriting some or most of the app for clear communication. Treat this as a portfolio project that you would show to prospective employers.

## Requirements

Your app must have the following requirements.

1. Render HTML
2. Use CSS
3. Serve webpages with Express.js and EJS
4. At least 1 full set of CRUD routes (create, retrieve, update, delete)
5. At least 3 SQL tables
6. At least 1 one-to-many and 1 many-to-many SQL relationship
7. Username and password login
8. Session authentication for login-only pages

To start, create a new repo without cloning any other repo. Feel free to copy any starter code you would like. Your app must be complete in the sense that it cannot rely on the theoretical existence of another system, e.g. an API that doesn't exist. Feel free to use any 3rd-party APIs available on the internet, e.g. NPM libraries.

You are responsible for any seed data your app would need to run. The final version of your app must be populated with data that looks at least semi-realistic. For example, a social media app would have more than 1 post, 1 comment and 1 like in the system.

See the example user login app for login starter code: [https://github.com/rocketacademy/userauth-express-bootcamp](https://github.com/rocketacademy/userauth-express-bootcamp)

## App Ideas

### General Ideas

In [Module 3](../3-backend-applications/3.0-module-3-overview.md) we covered general mechanics of web applications that store, update, and retrieve data using HTTP and HTML. These mechanics are part of virtually every app on the internet.

* Google stores websites and users retrieve those websites
* Uber stores drivers and their availability and users retrieve available drivers nearby
* Telegram stores messages between users and users retrieve and create those messages
* EBay stores auction data and users retrieve products for auction

While we may not yet have the power to index websites like Google, we know enough to build prototypes of similar applications. The role of a web application is not just to make GET and POST requests, but to store and retrieve data related to its core functionality, e.g. search, ride sharing, messaging, auctions.

Your app idea is more compelling if its purpose is for something specific and realistic. The best case is if it's actually something you yourself would use. Consider Module 3 PCE and ICE exercises as inspiration.

### Frontend Limitations

Given the relative restrictions of a server-side app that renders HTML pages, there are certain ideas that will be more easily accomplished when we include more modern technologies. In later Coding Bootcamp modules we will learn how to incorporate 3rd-party JS libraries into our frontends to accomplish some of the following. No worries if you don't have these for now.

* Date or date-time input fields for scheduling or calendars.
* User location using maps.
* Anything involving a [typeahead UI](https://dribbble.com/tags/typeahead).
* Anything where the user might have to drag or draw something.

### File Uploading

If your app idea involves file uploading, [3.5.11: File Uploads](../3-backend-applications/3.4-sql-applications/3.4.11-file-uploads.md) is a primer on how to accomplish this using the technologies we have learned so far.

### 3rd-Party APIs

The following are some ideas for 3rd-party APIs that we can use in our apps.

* [Google Vision API](https://www.npmjs.com/package/@google-cloud/vision)
* [Data.gov.sg APIs](https://data.gov.sg)

## General Tips

### Separating Logic and UI Concerns

In general, our Express middleware should handle all business logic, for example determining whether a user is authenticated, or querying the DB, making calculations for any data that should be rendered. Our EJS templates should be focused on the UI, i.e. displaying the data passed to it.

## Project Timeline

### Summary

| Course Day | Deliverable                                                                                                                                                                            | Instructor Feedback                                                                 |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| CD6.1      | **Start: Ideation Phase 1.** Introduce project, post project ideas in Slack for feedback                                                                                               | Instructor to share feedback on project ideas in Slack.                             |
| CD6.4      | <p><strong>Start: Ideation Phase 2.</strong></p><p>Create planning docs: user stories, wireframes, and DB ERD.</p>                                                                     | \*\*\*\*                                                                            |
| CD7.1      | <p><strong>Due: Ideation Phase 2.</strong></p><p>Finalise project idea and share planning docs in GitHub repo over Slack.</p>                                                          | Instructor to review planning docs over Slack and over Zoom if necessary.           |
| CD7.1      | **Peer Planning Review**                                                                                                                                                               | \*\*\*\*                                                                            |
| CD7.1      | **Start: Project Start**                                                                                                                                                               | Begin Project Implementation                                                        |
| CD8.1      | <p><strong>Due: MVP deadline.</strong></p><p>Users should be able to perform the primary user story. Please deploy your app to EC2. Students to review code in pairs during class.</p> | Instructor to review code on GitHub, share feedback in Slack and Zoom if necessary. |
| CD8.4      | <p><strong>Due: Feature freeze.</strong></p><p>No more developing new app functionality. Use remaining time to focus on polish, i.e. fixing UX/UI, refactoring code.</p>               | Quick project review in class to discuss improvements post-feature freeze.          |
| CD8.5      | **Due: Project presentations.**                                                                                                                                                        | 30-minute post-mortem with instructor. Instructor to review code in PR on GitHub.   |
| CD9.1      | **Project Peer Review exercise.**                                                                                                                                                      | \*\*\*\*                                                                            |
| CD9.3      | **Due: Video demo.**                                                                                                                                                                   |                                                                                     |

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

1. \~45 minutes on each partner's project (\~30 minutes if in a group of 3)
2. Share any challenges you've faced on your project
3. Partners can critique each others' work and clarify gaps in knowledge
4. By the end, students should have a clear idea on what improvements to make by project deadline.

### Deployment

Please deploy your app to EC2 \*before\* feature freeze. You may find the following resources helpful when deploying.

1. [3.POCE.10: EC2 Deployment with Postgres](../3-backend-applications/3.poce-post-class-exercises/3.poce.10-ec2-deployment-with-postgres.md) (culmination of the following 2 modules)
2. [2.11: Deploy Server to Cloud](../2-backend-basics/2.11-deploy-server-to-cloud.md)
3. [3.4.1: PostgreSQL, psql (psql Setup)](../3-backend-applications/3.4-sql-applications/3.4.1-postgresql-psql.md#ubuntu-for-windows-users-in-wsl-and-ec2-installation)

### Refactoring

We will be learning more ways to decompose our Express apps into logical files and folders in Module 4. For Project 2, feel free to decompose and organise functions within index.js.

## Feature Freeze

The app and all its features should run without errors. Brief demo in class to demonstrate user experience and clarify work to do before presentations. Latest app should be deployed.

## Project Presentations

Presentations should cover the [topics in this list](../course-logistics/course-methodology.md#project-presentations).

## Post-Mortem Meeting

Please answer the [project post-mortem questions](../course-logistics/course-methodology.md#project-post-mortem-meeting) before the post-mortem meeting with your instructor. These questions will be similar to the presentation questions, but we will dig deeper into your code.

## Video Demo

Please follow [video demo guidelines here](../course-logistics/course-methodology.md#project-videos).

## Project Submission and Past Student Projects

Once done with your project, please submit it by adding it to the [Rocket Bootcamp Projects spreadsheet](https://docs.google.com/spreadsheets/d/1YZ39naj5E6mNNkQ1akR\_FgeFO\_kM6aWCAr8zqrFOkt4/edit?usp=sharing) in your batch-specific sheet. Feel free to view past student projects in previous batches' sheets.
