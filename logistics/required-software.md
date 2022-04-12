# Required Software

## Introduction

This document outlines required software for SWE Bootcamp. Please install this software before starting the course unless instructed otherwise.

## Complete Coding Basics Setup

1. Please install the latest version of Windows or MacOS that your computer supports.
2. If you haven't already, please obtain and install [Coding Basics required hardware, software and accounts](https://codingbasics.rocketacademy.co/logistics/required-hardware-software-and-accounts).

## Install Git

We will learn about Command Line and Git in the course. For now, install them.

{% hint style="warning" %}
_**When copying commands from the Git website, do not copy the dollar sign ($) in front of the command.**_ The dollar signs in their commands denote the starts of command lines, and are not part of the commands.
{% endhint %}

#### MacOS Instructions

1. Download and install Git for MacOS by downloading it here: [https://sourceforge.net/projects/git-osx-installer/](https://sourceforge.net/projects/git-osx-installer/)
2. Verify Git is installed by running `git --version` in the [VS Code terminal](https://code.visualstudio.com/docs/editor/integrated-terminal). This should print out a version number on the next line, e.g., `git version 2.28.0`.
3. Download and install the [Git Credential Manager](https://github.com/microsoft/Git-Credential-Manager-Core/releases/download/v2.0.498/gcmcore-osx-2.0.498.54650.pkg).

{% hint style="warning" %}
To install the Git Credential Manager you may need to allow "unidentified developer apps". Don't worry, Git Credential Manager is created by Microsoft. [Instructions here](https://support.apple.com/en-sg/guide/mac-help/mh40616/mac).

If you are using a company computer for this course you may not be able to override the security settings. You may need to [create a personal token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) instead.
{% endhint %}

#### Windows Instructions

1. Navigate to the Git download page and click the download link: [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Open the downloaded file
3. Select the below options in the install dialog
4. Follow [command line setup instructions below](../required-hardware-and-software.md#windows-command-line-setup) to set Bash as the default terminal language.
5. Verify Git is installed by running `git --version` in the [VS Code terminal](https://code.visualstudio.com/docs/editor/integrated-terminal). This should print out a version number on the next line, e.g., `git version 2.28.0`.

{% embed url="https://www.youtube.com/watch?v=7Dq_e90LqTU" %}
Install dialog options (Click "Next" to apply default option):
{% endembed %}

## Configure Git and GitHub

### Configure Git default branch

Set the default Git branch to `main` as per GitHub's (and Rocket's) latest convention. Some older versions of Git may still use `master` as the default branch name.

```bash
git config --global init.defaultBranch main
```

### Git and GitHub Credential Configuration

Set your GitHub account credentials on your computer through the command line. This will enable us to interact with GitHub via the command line, which we will do a lot. Please replace `<YOUR_GITHUB_USERNAME>` and `<YOUR_GITHUB_EMAIL>` with your GitHub username and email.

```bash
git config --global user.name "<YOUR_GITHUB_USERNAME>"
```

```bash
git config --global user.email "<YOUR_GITHUB_EMAIL>"
```

Type `git config -l` into the terminal to verify configuration success. If you see `user.name` and `user.email` in the output, we succeeded. If you see a `:` at the bottom of the output, you may need to press `Enter` until you see the lines starting with `user.name` and `user.email`.

## Install Code Formatters

### Install Prettier

Prettier is a code formatter that will auto-format our code and make it more readable when we save our files.

1. Install the Prettier extension for VS Code [here](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode).
2. Restart VS Code to activate Prettier.

### Install ESLint

ESLint is a JavaScript code formatter that helps us detect functional and stylistic errors in our code prior to running it.

1. Install ESLint on your computer by running `sudo npm i -g eslint` from the terminal in VS Code. Enter your computer's password if prompted.
2. Install the ESLint VS Code extension [here](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint).

### Set VS Code Formatting Settings

1. Open VS Code and open the command prompt with `Ctrl+Shift+P` on Windows and `Cmd+Shift+P` on Mac.
2. Start typing `Preferences: Open Settings (JSON)` and select this option when you see it in the search dropdown. A JSON settings file should open in VS Code.
3. Replace everything on the screen (in the file) with the code below.
4. Save the settings file.
5. Restart VS Code to apply our settings.
6. Open and save the settings file again and verify that Prettier auto-formats it as our default formatter.

{% tabs %}
{% tab title="MacOS" %}

#### VS Code Settings for MacOS

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint"
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint"
  },
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,
  "editor.minimap.enabled": true,
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "eslint.format.enable": true,
  "eslint.lintTask.enable": true,
  "eslint.migration.2_x": "off"
}
```

{% endtab %}

{% tab title="Windows" %}

#### VS Code Settings for Windows

{% hint style="warning" %}
Windows users: The following code assumes we installed our Git folder at the root of our C drive. Some students' installers install the Git folder elsewhere, for example in `C:\\Program Files (x86)`. You should have noted the installation location of Git when you installed it, as per the instructions above.

If your installed Git folder is not in the location as listed below, please edit the Git Bash "path" attribute to the appropriate value when you copy the configurations.
{% endhint %}

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint"
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint"
  },
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,
  "editor.minimap.enabled": true,
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "eslint.format.enable": true,
  "eslint.lintTask.enable": true,
  "eslint.migration.2_x": "off",
  "terminal.integrated.defaultProfile.windows": "Git Bash",
  "terminal.integrated.profiles.windows": {
    "Git Bash": {
      "path": "C:\\Program Files\\Git\\bin\\bash.exe",
      "icon": "terminal-bash"
    }
  }
}
```

{% endtab %}
{% endtabs %}

## Install Windows-specific software (Windows only)

### Install and setup Windows Subsystem for Linux (WSL)

WSL allows us to run the Linux operating system on Windows machines. We do this because most programming uses Unix-based operating systems, of which MacOS is a descendant. Most SWEs that use Windows do their work in WSL to maximise compatibility between their work and work done on Linux machines. Before installing WSL, update Windows to the latest version.

1. Install WSL [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
2. Install the latest version of Ubuntu [here](https://www.microsoft.com/en-sg/p/ubuntu-2004-lts/9n6svws3rx71). Ubuntu is a popular version of the Linux operating system.
3. Run `sudo apt install build-essential` in Ubuntu in WSL to install standard libraries Ubuntu needs to further install common packages.
4. Run `sudo apt-get install ca-certificates` in Ubuntu in WSL to get SSL verification certificates on Ubuntu for Ubuntu to communicate with VS Code on our computer.

### Integrate VS Code with WSL

1. Install the [VS Code Remote Development extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) to enable VS Code to integrate with WSL.
2. Click the Remote Development extension icon in the bottom left corner of VS Code. A pop up will appear with a list of options. Click the first option "Remote-WSL: New Window" for the default distro.

You will see a notification "Starting VS Code in WSL...". This means VS Code is setting up a server inside WSL for the first time. Once installed, the VS Code of your Windows OS will sync automatically with the VS Code of your Ubuntu OS, and the VS Code terminal will show the Ubuntu terminal.

{% hint style="danger" %}
If you were using the Git Bash terminal before, after following these instructions you **must only use the Ubuntu terminal** to ensure our files are saved in Ubuntu.
{% endhint %}

### Install Node.js in Ubuntu

Open an Ubuntu terminal in VS Code and follow [Node.js install instructions](https://github.com/nodesource/distributions/blob/master/README.md#installation-instructions). Read more about these install instructions [here](https://dev.to/ajeet/the-ultimate-guide-to-use-vs-code-with-windows-subsystem-for-linux-wsl-51hc).

## Install Mac-specific software (Mac only)

### Install XCode Command Line Tools

Run `xcode-select --install` to install command line tools for software engineers on MacOS.

### Install Homebrew

Follow instructions at [https://brew.sh/](https://brew.sh) to install Homebrew.

Homebrew is a package manager for MacOS that provides a single source of truth for which packages and package versions are installed. This is typically only relevant to command line packages; We typically do not install GUI applications via Homebrew.

Homebrew typically manages OS-specific packages, e.g. `node`, and not application-specific packages, e.g. `react`. Application-specific packages are typically managed by application-level package managers such as `npm` or `pip`. Application-specific packages are typically bundled and deployed together with an application, regardless of where those applications are running.

### Install Node.js

Install Node.js using Homebrew using the following commands. `install` installs the package and `link` makes the `node` command accessible in our terminal.

```
brew install node@16
brew link node@16
```

## Install other helpful VS Code extensions

Install VS Code's [Open in Browser extension](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser) to make it easier to open HTML files in our browser from VS Code.

## Setup folder structure for SWE Bootcamp

Rocket recommends the following folder structure to keep ourselves organised during Bootcamp.

{% hint style="warning" %}
Name files and folders in kebab-case, e.g. `new-file.txt`, lowercase and hyphenated for ease of use on the command line. We do not recommend naming files and folders with spaces in names because we will need to enter special characters in the terminal to escape the space character when referring to these files.
{% endhint %}

{% hint style="danger" %}
Please do not store code in folders synced to cloud storage such as Google Drive or Apple iCloud. This will cause issues during Bootcamp, such as package installations running slowly or unnecessary extra files committed to GitHub.
{% endhint %}

{% tabs %}
{% tab title="MacOS" %}

#### Mac Folder Organisation

Mac users can store all Bootcamp code in 1 place.

1. Host all SWE Bootcamp code in a folder called `bootcamp`.
2. Within the `bootcamp` folder, create a new folder for each module of the course. This means you will have 5 folders, such as `m1`, `m2`, ..., `m5`.
3. Within each module folder, create 1 folder for each day, i.e. `d1`, `d2`, ..., `d16`.
4. Within each day folder, create `prce` (pre-class), `ice` (in-class), and `poce` (post-class) folders for the respective exercises.
5. Within each PRCE, ICE and POCE folder, keep a separate folder for every exercise you do that requires a new Git repo.
6. Store projects within a `projects` folder directly within the `bootcamp` folder for easy accessibility.
   {% endtab %}

{% tab title="Windows" %}

#### Windows Folder Organisation

Windows users will need to store Bootcamp code in 2 places, 1 place for Module 1 and another place for Modules 2-5.

1. For Module 1, host code in a folder called `bootcamp`.
2. Within the `bootcamp` folder, create a new folder for Module 1, i.e. `m1`.
3. Within the `m1` folder, create 1 folder for each day, i.e. `d1`, `d2`, ..., `d16`.
4. Within each day folder, create `prce` (pre-class), `ice` (in-class), and `poce` (post-class) folders for the respective exercises.
5. Within each PRCE, ICE and POCE folder, keep a separate folder for every exercise you do that requires a new Git repo.
6. Store projects within a `projects` folder directly within the `bootcamp` folder for easy accessibility.
7. For Module 2 onward we will store files inside the WSL part of the computer. Create a directory called `bootcamp` in the home (`~`) folder of the Ubuntu system.
8. Organise modules, days, exercises and projects as above for Modules 2-5.
9. Do not save any of the files from Module 2 onward in the Windows side of the computer.
   {% endtab %}
   {% endtabs %}
