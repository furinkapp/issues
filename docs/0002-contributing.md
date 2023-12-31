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

In general, developers should keep an open mind when contributing to the project. We encourage the discussion of ideas amongst the team and should be open to criticism and feedback.

## Workflow

We will be making use of the GitHub Flow workflow for this project. This means that we will be using the `main` branch as the primary branch for development and will be using feature branches for new features and bug fixes.

### Local Development

Local development is left primarily up to the developer's discretion. We recommend using VSCode with the necessary CLI tools to develop the project. Another option would be to use DevContainers to avoid installing the tooling on your local machine.

### Pushing Changes

All changes should be pushed to a personalized feature branch following the naming convention outlined below:

-   All branches should be prefixed with a type, such as `feat/` or `fix/`.
-   All branches should then include the name of the developer working on the branch.
-   All branches should be suffixed with single or multiple words describing the feature or fix being implemented.

For example, a branch implementing a new feature by a developer named John Smith would be named `feat/john-smith/new-feature`.

> **Note:** Changes should never be pushed directly to the `main` branch. This branch is automatically deployed to production, and should only be updated with working code.

### Collaborative Development

If multiple team members are working on the same feature at the same time, they should use their own feature branches, and then merge into a shared `feat/new-feature` branch to track their shared changes. This will help to avoid conflicts when pushing to and from a single feature branch.

For example, if Doug and Harris are both working on a `cat-images` feature, they will work in their personal feature branches, `feat/doug/cat-images` and `feat/harris/cat-images`, then merge their changes into `feat/cat-images`. This can then be reviewed by other team members and merged into `main`.

### Pull Requests

Developers should open pull requests to the `main` branch when they feel that their feature or fix is close to completion. This allows developers to make use of the automatic CI/CD pipelines built into the majority of the project.

#### Reviews

Pull requests should be reviewed by at least two other developers before being merged into the `main` branch. Most of the repositories have been configured to require this, but a few may be lacking - please let us know if you notice this!

Please be mindful of the following when reviewing a pull request:

-   We all have different styles of writing code, and that's okay! As long as the code is readable, consistent, and meets the automatic style enforcement, you shouldn't be too worried.
-   We all have different skill levels so some will need more help than others. If you notice something that could be improved, let the developer know, but please remember to keep your feedback constructive.
-   Take the time to understand the code being written. If you don't understand something, ask the developer to explain it. This will help you learn and help the developer understand what they are doing better.

We want to avoid the classic "LGTM" review, as it doesn't help anyone. If you don't have the time to review a pull request, feel free to remove yourself from the review and request someone else to take over.

#### Staging

Pull requests made to frontend repositories will automatically be deployed to a staging environment for testing, with the relevant details posted in the pull request.

### Deployment

The `main` branch is automatically deployed to production using Vercel, Terraform, and a variety of other pipelines.

#### Mobile

Since mobile apps tend to follow a more traditional release cycle, we will use the `main` branch as the primary branch for development, then create a release branch when we are ready to release a new version.

## Best Practices

We should follow best practices when developing a project part of fur.ink. This will ensure that our code is consistent and easy to read, although it is important to keep in mind we all have our own ways of doing things that are all equally valid. For example, some of us may prefer tabs over spaces, or vice versa. To avoid these kinds of inconsequential arguments, we will use CI tooling to enforce these rules.

### Commit Hooks

Most repositories make use of a set of commit hooks to ensure that our code is formatted consistently. Using the `lint-staged` package, we run the linters and formatters outlined below on all staged files.

### Code Style

For TypeScript and ECMAScript, we use the [Prettier](https://prettier.io) code formatter to ensure our code is formatted consistently. Specifically, we will use the [`prettier-config-infernal`](https://github.com/kaylendog/prettier-config-infernal) configuration.

### Linting

For TypeScript and ECMAScript, we will use [ESLint](https://eslint.org) to ensure that our code is error-free and follows a set of rules. We will use the [`eslint-config-infernal`](https://github.com/kaylendog/eslint-config-infernal) configuration.
