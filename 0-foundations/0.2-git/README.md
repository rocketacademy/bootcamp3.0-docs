# 0.2: Git

## Learning Objectives

1. All software engineers use version control, and Git is the most popular version control system
2. Version control allows us to track which versions of our code have which features, and to write code in teams while avoiding potential conflicts.
3. Know how to add, and commit, files to "commits", i.e. versions of our code
4. Know when to commit changes during project development

## Introduction

All software engineers use version control to manage and review project versions and to write code in teams. Git is the most popular version control system.

Version control is not strictly necessary to create programs, but it makes software development easier by reducing the fear of breaking code. If we break code when using version control, we can compare our changes to the last working version, easily find bugs to fix, or even rolling back to the last working version if needed.

In this submodule we will learn how to create code versions, more commonly known as "commits".&#x20;

We will continue to learn Git techniques as we progress through Bootcamp.

## Git Terminology

| Term         | What it is                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Repository   | A Git repository, also known as a "repo", is a folder that contains code for a given project. We typically have separate repos for each project, such that each repo only tracks changes to the code for its own project.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Commit       | A Git "commit" is a version of our code that records a set of changes to 1 or more files. These changes can include changes within existing files, but also include addition, deletion, renaming and moving of files. Each Git repo stores a time series of commits since the creation of the repo.                                                                                                                                                                                                                                                                                                                                                                |
| Staging area | <p>Git requires us to "stage" changes before we commit them. This allows us to easier control which changes go in which commit, especially if we have made multiple changes that belong to multiple features.<br><br>For example, I may have renamed a word across my app for a branding change (Feature A) and added payment functionality (Feature B) all at once, but I do not wish to commit them together because they are separate features. With Git's staging area I would be able to only stage and commit the changes for 1 feature at a time, allowing me to keep Feature A if there is a bug that requires rollback with Feature B and vice versa.</p> |

## Git Commands

The command line is the most common and canonical way to manipulate Git. There are GUI tools, but software engineers often work with Git on remote servers that are only accessible via command line.

The following are common Git commands we will use as software engineers.

| Command                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `git clone <target-repo-url>`    | Download a copy of the target repo into the current folder.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `git status`                     | View which files have changed since the latest commit, and which files are in the staging area.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `git diff <filepath>`            | <p>Review changes made in each file at given file path since latest commit. If file path not specified, show changes made to all files in repo.</p><p>This allows us to verify we made intended changes. If changes are longer than window height, use <code>Enter</code> to browse downward. Press <code>q</code> to exit.</p>                                                                                                                                                                                                                    |
| `git add <filepath>`             | <p>Stage files in specified file path for commit by adding them to the staging area. Files added to staging are not committed yet.<br><br>Often (but not always) we will want to add all changed files to staging. We can do this with <code>git add .</code>, where <code>.</code> is an alias for the current folder.</p>                                                                                                                                                                                                                        |
| `git commit -m <commit-message>` | <p>Commit all files in staging to a new Git commit. The <code>-m</code> flag, which stands for "message", allows us to enter a mandatory commit message in the command line instead of in an editor. Commit messages should be short and descriptive, describing what changed and why.<br><br>Running <code>git commit</code> without the <code>-m</code> flag may bring us to Git's default editor, which we should have set to VS Code. If we get stuck in a command line editor, type <code>:q</code> and press <code>Enter</code> to exit.</p> |
| `git log`                        | <p>View a list of all commits in this repo. Use <code>Enter</code> to scroll downward and <code>q</code> to exit if output longer than screen height. <br><br>You can use the <code>--oneline</code> flag for a more concise list of commits.</p>                                                                                                                                                                                                                                                                                                  |

## When to commit changes?

1. We should strive to keep commits relatively small so it is easy for our team to review the changes in each commit
2. We should strive to only commit code when it is in a state that others would find useful; not in a broken state or with commented-out scratch code

## Exercise: Git Poetry

The following exercises should help familiarise you with Git. We use text instead of code, but the Git functionality is the same. You may wish to have 3 windows open on your screen: VS Code, the Git Commands table above, and the following instructions.

1. Open today's folder in terminal and create a folder with the command `mkdir`
2. `cd` into the folder, and initialise it as a git repo using the command `git init`
3. Create a text file in the command line using `touch spring-poem.txt` and open it in VS Code with `code spring-poem.txt`
4. Write a poem about spring (or anything) in `spring-poem.txt` and save the file
5. Stage and commit `spring-poem.txt` with `git add .` and `git commit -m`
6. Edit our poem to reference leaves (or anything). Stage and commit the edits
7. Add a 2nd poem about winter (or anything) in a new file `winter-poem.txt`
8. Add a title to our spring poem above the poem in the file
9. Commit the latest changes to `winter-poem.txt` and `spring-poem.txt` in 2 commits by adding 1 of them to the staging area and committing before adding the other
10. Use `git log` to review commits in our repo

## Additional Resources

1. [Intro to Version Control by Git](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
2. (Below): Intro to Git video from a prior version of Rocket Academy's Coding Basics course

{% embed url="https://youtu.be/GudllO59HJQ" %}
Intro to Git video from a prior version of Rocket's Coding Basics course
{% endembed %}
