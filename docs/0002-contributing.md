# Contribution Guidelines

## Contents

1. Overview
2. Workflow
    1. [Local Development](#local-development)
    2. [Pushing Changes](#pushing-changes)
    3. [Pull Requests](#pull-requests)
    4. [Deployment](#deployment)
3. Best Practices
    1. [Code Style](#code-style)
    2. [Linting](#linting)

## Overview

Developers are expected to follow the guidelines outlined in this document when contributing to the project. This document is subject to change at any time, and it is the responsibility of the developer to keep up to date with the latest changes.

In general, developers should keep an open mind when contributing to the project. We encourage the discussion of ideas amongst the team, and should be open to criticism and feedback.

## Workflow

We will be making use of the GitHub Flow workflow for this project. This means that we will be using the `main` branch as the primary branch for development, and will be using feature branches for new features and bug fixes.

### Local Development

Local development is left primarily up to the developer's discretion. We would recommend using VSCode plus the necessary CLI tools to develop the project. Another option would be to use DevContainers to avoid having to install the necessary tools on your local machine.

### Pushing Changes

All changes should be pushed to a personalized feature branch following the naming convention outlined below:

-   All branches should be prefixed with a type, such as `feat/` or `fix/`.
-   All branches should then include the name of the developer who is working on the branch.
-   All branches should be suffixed with a single or multiple words describing the feature or fix being implemented.

For example, a branch implementing a new feature by a developer named John Smith would be named `feat/john-smith/new-feature`.

> **Note:** Changes should never be pushed directly to the `main` branch. This branch is automatically deployed to production, and should only be updated with working code.

### Pull Requests

Developers should open pull requests to the `main` branch when they feel that their feature or fix is close to completion. This allows developers to make use of the automatic CI/CD pipelines built into the majority of the project.

#### Reviews

Pull requests should be reviewed by at least two other developers before being merged into the `main` branch. Most of the repositories have been configured to require this, but a few may be lacking - please let us know if you notice this!

Please be mindful of the following when reviewing a pull request:

-   We all have different styles of writing code, and that's okay! As long as the code is readable, consistent, and meets the automatic style enforcement, it's fine.
-   We all have different skill levels and some of us will need more help than others. If you notice something that could be improved, please let the developer know in a constructive manner.
-   Take the time to understand the code being written. If you don't understand something, ask the developer to explain it to you. This will help you learn, and will help the developer understand what they are doing better.

We want to avoid the classic "LGTM" review, as it doesn't help anyone. If you don't have the time to review a pull request, feel free to remove yourself from the review and request someone else to take over.

#### Staging

Pull requests made to frontend repositories will automatically be deployed to a staging environment for testing, with the relevant details being posted in the pull request.

### Deployment

The `main` branch is automatically deployed to production using Vercel, Terraform, and a variety of other pipelines.

#### Mobile

Since mobile apps tend to follow a more traditional release cycle, we will be using the `main` branch as the primary branch for development, then creating a release branch when we are ready to release a new version of the app.

## Best Practices

We should be mindful to follow a common set of best practices when developing a project part of fur.ink. This will ensure that our code is consistent and easy to read, although it is important to keep in mind we all have our own ways of doing things that are all equally valid. For example, some of us may prefer to use tabs over spaces, or vice versa. To avoid these kinds of inconsequential arguments, we will be using a set of tools to enforce a common set of rules.

### Commit Hooks

Most repositories make use of a set of commit hooks to ensure that our code is formatted consistently. Using the `lint-staged` package, we run the linters and formatters outlined below on all staged files.

### Code Style

For TypeScript and ECMAScript, we will be using the [Prettier](https://prettier.io) code formatter to ensure that our code is formatted consistently. Specifically, we will be using the [`prettier-config-infernal`](https://github.com/kaylendog/prettier-config-infernal) configuration.

### Linting

For TypeScript and ECMAScript, we will be using [ESLint](https://eslint.org) to ensure that our code is free of errors and follows a common set of rules. We will be using the [`eslint-config-infernal`](https://github.com/kaylendog/eslint-config-infernal) configuration for this.
