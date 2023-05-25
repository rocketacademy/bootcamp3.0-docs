# 4.2: Continuous Integration

## Learning Objectives

1. Continuous integration (aka CI) means automatically running tests when there have been any changes to our code
2. Every tech company relies on CI to verify their systems are operational
3. CI is often referred to together with "CD" or continuous deployment
4. CI is typically integrated into the development workflow, running tests on pull requests and merges

## Introduction

Continuous integration (aka CI) means automatically running tests when there have been any changes to our code, and notifying engineers when any tests fail. This helps engineers know proactively when their changes have broken existing functionality without having to manually run tests.

Every tech company relies on CI to verify their systems are operational. Testing culture varies across tech teams, and some teams will have more robust test coverage than others. Skipping writing tests may speed up development in the short term but slow down development in the longer term when new changes introduce unexpected and undetected bugs.

CI is often referred to together with CD, which stands for continuous deployment. This is because the same tools that allow us to run tests on code changes can also allow us to deploy our apps on code changes after tests pass. Because both are often used together, we often refer to them as "CI/CD".

CI is typically integrated into the development workflow, running tests on pull requests and merges. We will demonstrate how to use CI with [GitHub Actions](https://github.com/features/actions) below, but there are other popular CI alternatives such as CircleCI, Travis CI, GitLab CI and Jenkins.

## GitHub Actions

GitHub Actions are sequences of command line commands we can run automatically on specific triggers such as pull requests or pushes to specific branches. GitHub Actions allow us to run command line commands in an environment of our choice (e.g. Ubuntu, Windows, MacOS), and on triggers of our choice (e.g. on specific branches but not others). These features and their usage are similar across most CI software.

GitHub Actions (and most cloud infrastructure automation) are typically configured using [YAML](https://en.wikipedia.org/wiki/YAML), a language similar to JSON except with the option to add comments for explanations. To create a new "workflow" or sequence of commands, we create a new YAML file in a `.github/workflows` folder in the root of our repo. Once we commit a new workflow to our repo, GitHub Actions can execute it if our subsequent actions match the triggers we specified in our workflow, such as pushing to the `main` branch. GitHub has comprehensive docs on the [various options developers have to configure GitHub Actions](https://docs.github.com/en/actions) and the [specific YAML syntax for workflow files](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions).

Rocket has created a [simple CI workflow](https://github.com/rocketacademy/unit-test-bootcamp/blob/main/.github/workflows/ci.yml) using the `unit-test-bootcamp` repo we introduced in the Testing submodule, copied below. Rocket's GitHub Actions workflow is modelled after the [GitHub Actions Node.js starter workflow template](https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-nodejs).

{% code title=".github/workflows/ci.yml" %}
```yaml
# This workflow will launch a clean Ubuntu OS, install app dependencies and run tests
name: CI

# Run on push or PR to main branch
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    # Specify which OS to run this workflow on
    runs-on: ubuntu-latest

    strategy:
      matrix:
        # Specify Node version
        node-version: [16.x]

    steps:
      - uses: actions/checkout@v3
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
      # npm ci is a built-in script to install dependencies from package-lock.json
      - run: npm ci
      # Run tests
      - run: npm test
```
{% endcode %}

After pushing the above workflow to `main`, we can observe this workflow in the [Actions tab](https://github.com/rocketacademy/unit-test-bootcamp/actions) in the GitHub console.

![GitHub Actions tab in GitHub console](<../../.gitbook/assets/4.2 - CI - Actions Tab.png>)

We can inspect what happened in this workflow by clicking into it.

![GitHub shows us each stage of the GitHub Action workflow](<../../.gitbook/assets/4.2 - CI - CI Workflow.png>)

For more detailed analysis of the workflow, we can click on each of the workflow stages to observe what happened in that stage. For example, we can click into the "Run npm test" stage to verify the correct tests ran.

![GitHub allows us to view exact command line output from each workflow stage](<../../.gitbook/assets/4.2 - CI - CI Workflow Tests.png>)

In addition to running CI, GitHub Actions also allows us to deploy our apps automatically with continuous deployment (aka CD). Read about [GitHub Actions' Deploy to Heroku library](https://github.com/marketplace/actions/deploy-to-heroku) for a convenient way to deploy our apps to Heroku on GitHub pull requests and merges.

## Additional Resources

1. GitLab provides a [simple yet comprehensive introduction to CI/CD concepts](https://docs.gitlab.com/ee/ci/introduction/)
