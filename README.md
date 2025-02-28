# Guidelines to dotteddev projects

There are several rules and guidelines in place, to ensure correct behavior of build process, deployment etc. This file will summarize those requirements and serve as a guide everyone working on those projects has to know.

- [Guidelines to dotteddev projects](#guidelines-to-dotteddev-projects)
  - [Documentation for the win](#documentation-for-the-win)
    - [Configuration files](#configuration-files)
    - [Readme files / documentation files](#readme-files--documentation-files)
  - [Onboarding](#onboarding)

> [!IMPORTANT]
> Each rule or guideline is __not__ meant to bother people, rather it is essential part of multi-user collaboration.

## Documentation for the win

<!-- > [!NOTE]
> Sometimes, not all guidelines and rules are a good fit. There can, and will, be places, where it does not make sense. In those cases, there has to be a document specifying what is different -->

### Configuration files

Configuration files are essential part of the development of our applications and libraries. They ensure, that our apps run flawlessly across different environments.

All configuration files are meant to be as independent as possible to allow newcomers and contributors to easily onboard the application.

> [!TIP]
> All configuration files are explained in the [onboarding](./ONBOARDING.md) document.

### Readme files / documentation files

What is in your head should probably be written somewhere for others to see. We encourage you to write documentation not only for newcomers, but also for you, when you come to the project months later. Spend time writing docs, so others do not need to.

When some workflow or process takes place, you can use Mermaid to visualize it.

> [!TIP]
> All doc and readme files are written in markdown, for more information see [Github markdown cheatsheet](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

## Onboarding

Prior to using our code, see [onboarding](./ONBOARDING.md) for you to get started.
