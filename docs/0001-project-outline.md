# Project Outline

## Overview

**fur.ink** is a platform for artists to share and publish commission information, and for customers to find something that fits their tastes. The goal of this issue is to concisely outline the goals of this project in a more definitive manner, which allows us to allocate work across the team.

### Target Audience

The platform is targeted primarily at two types of users: artists and customers.

- Artists will be able to use the platform to share and publish commission information, such as commission openings, YCHs, auctions, and payment information.
- Customers will be able to browse, search, and filter the available information to find something that fits their needs, and then establish contact with the artist in question and pay them for the slot.

There is also a secondary target user who would take an interest in the platform: advertisers, either artists or external organisations. These entities could buy panels or cards on the platform dashboard to promote their products, commission slots, or similar.

### Platforms

We will be targeting two platforms during initial development: mobile and web.

- The web application will be the primary entry point for users to the platform. It will be laid out similarly to DeviantArt or FurAffinity, with an up-to-date and modern UI.
- The mobile application will enable users to browse available slots on the go, as well as allow artists to make quick fixes to information.

Since our resources are limited, we will be prioritising the development of the web application over the mobile one during the first few iterations.

### Architecture

Since our team is relatively small, we should aim to build as much of our software to support serverless environments as possible.

#### Web Application

The web application will be built in React using the [NextJS](https://nextjs.org) framework, allowing us to deploy changes continuously to production on Vercel's servers without the DevOps team having to manage a dedicated host.

#### Backend

The backend will initially be built using Node using the [NestJS framework](https://nestjs.com). As a team, we must decide on the type of architecture to go with: a monolithic API, or one built using Nest's [microservice support](https://docs.nestjs.com/microservices/basics). Regardless, it will likely be a good idea to run our services in Kubernetes to enable rolling deployments and centralised management of resources.

We will be making use of a number of service providers to aid in development:

- [Stripe](https://stripe.com) to aid in managing purchases and seller accounts.
- [Supabase](https://supabase.com) to enable seamless authentication with existing OAuth providers.
- [TypeSense](https://typesense.org/) to enable searching over our database of commission information.

### Work Allocation

It will be a good idea to split the work into a number of different teams, each working on their own slice of the project. This will also allow us to allocate code reviews amongst the team in a fashion that won't make everyone annoyed at the number of notifications they are receiving.

Here is a brief overview of the teams we will put in place:

- @furinkapp/core, responsible for the overall maintenance of the project.
- @furinkapp/design, responsible for designing the web and mobile applications.
- @furinkapp/developer, responsible for the development of the platform's code.
- @furinkapp/devops, responsible for managing the platform's infrastructure, CI, and deployments.

The developer team will be further split into two sub-teams, each managing a different environment:

- @furinkapp/backend, responsible for the development of the platform's backend services.
- @furinkapp/frontend, responsible for the development of the platform's web and mobile applications.

### Communication

As a team, we should maintain good communication with each other. We should use a platform such as Discord or Slack to keep up to date with each other.

### Social Media

It will be beneficial for us if we can receive feedback on the platform as it stands at a given point in the development process. We should begin creating a social media presence on other platforms such as Telegram, Mastodon, BlueSky, X (formerly Twitter...) so we can raise awareness for the platform and to get feedback.
