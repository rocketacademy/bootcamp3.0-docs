# Project 1: Frontend App

## Introduction

Build an app that solves a problem you have using HTML, React and CSS. We will not be able to persist data until Module 2, but there are still many useful apps we can build.

## Requirements

### App

1. HTML, React and CSS with Create React App
2. Interactivity, e.g. at least 1 input or button that changes app state
3. `useState` to manage app state in relevant components
4. At least 2 levels of components, e.g. `App` component and 1 or more child components at least 1 level below it
5. React Bootstrap, MUI, Tailwind CSS or another modern CSS framework
6. Responsive layout that is user-friendly on desktop and mobile

### Other

1. Deployment with GitHub Pages
2. Naming, casing and commenting [best practices](../general-reference/naming-casing-and-commenting-conventions.md)
3. Git commits for each feature with descriptive commit messages
4. App description in README with user stories and low-fidelity wireframes
5. Instructions in README to run app

## Ideas

The best ideas are ones that solve our own problems. Since we cannot persist data until Module 2, consider apps that do not require us to store data beyond the current session. For example: games, calculators, guitar tuners, colour matchers, visualisers. Games may be the most engaging to implement because they typically require more logic. Consult your section leader if you are struggling to decide on an idea.

## Timeline

You will have roughly 8 course days to complete this project. We will observe the following timeline to keep us on track.

| Project Day | Checkpoint                                                                                                                                                                                                                        | Feedback                                                                                                                       |
| :---------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
|      0      | <p><strong>Ideation phase 1</strong></p><p>Post project ideas in Slack for feedback</p>                                                                                                                                           | SL to review ideas and share feedback                                                                                          |
|      1      | <p><strong>Ideation phase 2</strong><br><strong></strong>Create planning docs: user stories, wireframes, kanban board</p>                                                                                                         | SL to review planning docs and share feedback                                                                                  |
|      2      | **Start implementation**                                                                                                                                                                                                          | -                                                                                                                              |
|      3      | -                                                                                                                                                                                                                                 | -                                                                                                                              |
|      4      | -                                                                                                                                                                                                                                 | -                                                                                                                              |
|      5      | <p><strong>MVP deadline</strong><br><strong></strong>Users can complete the primary user story</p>                                                                                                                                | SL to review code in GitHub, share feedback                                                                                    |
|      6      | -                                                                                                                                                                                                                                 | -                                                                                                                              |
|      7      | <p><strong>Feature freeze</strong></p><p>No new features, focus on polishing existing features and code to be presentable</p>                                                                                                     | SL to review progress and share post-feature-freeze suggestions                                                                |
|      8      | -                                                                                                                                                                                                                                 | -                                                                                                                              |
|      9      | <p><strong>Project presentations</strong></p><p>Practise <a href="../logistics/course-methodology.md#presentations">explaining your work</a> to others. Other batches will join and we will celebrate each others' hard work.</p> | SL to review code in GitHub, share feedback in 30-minute [post-mortem meeting](../logistics/course-methodology.md#post-mortem) |
|      10     | <p><strong>Demo video</strong><br><strong></strong>Record a <a href="../logistics/course-methodology.md#demo-video">demo video</a> for employers and the public, embed in README</p>                                              |                                                                                                                                |

## Project Management Suggestions

Rocket recommends the following project management strategies and tools for all projects.

### User Stories

Start with user stories. Who is our user and what is their [job to be done](https://hbr.org/2016/09/know-your-customers-jobs-to-be-done)? Be as specific as possible. After we articulate user stories we can proceed to design our app.

Example user stories for Project 1:

* An interior designer wants to determine whether 2 or more colours match and what an optimal colour palette might be for given a base colour
* A daily commuter wishes to play Flappy Bird during his 30-minute commute
* A couple wishes to play a game of checkers against each other on their shared computer

Above user stories may not require persisting user data beyond the current session. From Project 2 onward we will learn how to persist user data for multiple users accessing our apps at multiple times on different devices.

### Wireframes

After user stories, create simple wireframes to visually describe how our users will accomplish their user stories with our app. Rocket recommends [Figma](https://www.figma.com) for user stories because it is a relatively simple tool widely used by designers in industry. Only include what is needed for the user stories, no more and no less.

[Here](https://www.figma.com/blog/how-to-wireframe/) is an introduction to wireframing with Figma. Rocket recommends only low-fidelity wireframes for our projects due to limited time. Below are example wireframes by Figma; we can visualise [user flows](https://careerfoundry.com/en/blog/ux-design/what-are-user-flows/) by navigating to the Prototype tab in the right sidebar and adding connections.

{% embed url="https://www.figma.com/file/NkdUszMYMFqhMX31HGUH0o/Wireframing-in-Figma?node-id=0%3A1" %}
Example wireframes by Figma
{% endembed %}

### Kanban Board

After user stories and wireframes, Rocket recommends using a [kanban board](https://blog.trello.com/kanban-data-nave) to track implementation progress. A kanban board is a progress-tracking board that contains broadly 3 lists of tasks: To Do, Doing and Done. Rocket recommends [Trello](https://trello.com) for its simplicity, and the [Trello Engineering Kanban Template](https://trello.com/templates/engineering/kanban-template-LGHXvZNL) for its relevance to SWE.

Each task on your board should take no more than 1 day to complete. If you think it will take longer than 1 day, break it down into smaller tasks. This will help you stay motivated and track progress more accurately. Move in-progress tasks to the Doing lists and completed tasks to Done.

## Setup

Start by forking Rocket's base CRA repo. This will make it easier for SLs to review your code via pull requests.

## Submission

Submit your project by adding it to the [Rocket Bootcamp Projects spreadsheet](https://docs.google.com/spreadsheets/d/1YZ39naj5E6mNNkQ1akR\_FgeFO\_kM6aWCAr8zqrFOkt4/edit?usp=sharing) in your batch-specific sheet. Feel free to review past student projects in previous batches' sheets.

## General Tips

### Polish

Leave sufficient time to polish your app to be presentable. Fewer, more-polished features are generally better than more, less-polished features. Below is a sample checklist to run through.

1. Are there obvious bugs?
2. Are variable names concise and precise?
3. Do we have [JSDoc comments](https://jsdoc.app/about-getting-started.html#adding-documentation-comments-to-your-code) above major functions and inline comments above code that could be confusing to others?
4. Is each function sufficiently small and modular to be easily readable?
5. Is the visual design clean?
6. Is the app layout responsive?
7. Did we update the app favicon and page title?
8. Did we populate the README?
