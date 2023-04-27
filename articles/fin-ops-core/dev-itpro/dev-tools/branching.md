---
title: Branching overview
description: This article explains branching strategy considerations for X++ development.
author: skaue-ms
ms.date: 01/04/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: toskaue
ms.search.validFrom: 2023-01-01
ms.dyn365.ops.version: 10.0.30
---
# Branching overview

Branching configurations for X++ repositories (repos) vary, depending on the development team's preference and the finance and operations app lifecycle. If the implementation already has a preferred branching structure, and it meets the [minimum branching criteria](#minimum-branching-criteria) that are outlined later in this article, you can use it to manage new development. Alternatively, you can evaluate the other branching structure options that are explained in this article.

## Considerations

You'll find that a few elements of the X++ development cycle differ from general application development. Keep the following items in mind as you consider how to structure your branches:

- Enterprise resource planning (ERP) systems are business-critical environments. When you design your code management infrastructure, you should prioritize design elements that help minimize both the risk of major production issues and the disaster recovery timeline.
- Because of the complexity of, and interdependency on, the standard system code, it's generally a good idea to do both automated testing and manual testing of **all critical business processes** after each code update. Because this testing can be lengthy, you should plan to have a branch to contain the in-test code for long spans of time while it's being validated.
- Because dev teams frequently focus their collective attention on enhancing specific modules and areas of the product, merge conflicts are relatively frequent for X++. Therefore, you should plan a branching strategy that helps reduce the frequency of collisions and makes collisions easier to fix when they occur.

## Minimum branching criteria

At a minimum, any X++ repo branching strategy should support the following criteria:

- **Isolation of untested development code or code that's in development** – Developers should be protected from having teammates accidentally break any active development branch. If the team shares a single development branch, each developer must ensure that they don't commit code that breaks teammates' code. Additional configuration of the version control capabilities should be used for this purpose. Otherwise, isolation of untested code from in-development code is an ideal way to provide this protection. 
- **Isolation of in-development code from test-eligible code** – Although a code change might pass unit testing or manual developer testing, the associated task might not yet be ready for functional testing. Any X++ branching structure should clearly notate when a collection of changes is ready for functional testing.
- **Isolation of in-test code from production code** – The fundamental purpose of all version control is to help prevent code releases to production environments until code changes have been fully validated.
- **Relatively long functional testing cycles** – For more information about why finance and operations app customizations take longer to validate, see the [Considerations](#considerations) section of this article.

## Branch policy guidance

We recommend the following branch policy best practices, regardless of the branching strategy that you choose:

- The live/production code branch should be locked to prevent direct editing. Changes should be made only via merges from other branches.
- Before functional testing begins, developers should move their code into the corresponding branch. We recommend that you define policies to help protect branches from incomplete work. Git lets you require a [minimum number of reviewers](/azure/devops/repos/git/branch-policies?view=azure-devops&tabs=browser&preserve-view=true#require-a-minimum-number-of-reviewers) before pull requests can be completed. Team Foundation Version Control (TFVC) has mechanisms to ensure that [check-ins are gated](/azure/devops/repos/tfvc/set-enforce-quality-gates?view=azure-devops&preserve-view=true).

## Branching strategies

### Branching in TFVC

A common branching strategy for teams that use TFVC combines a trunk-based approach with developer isolation and release isolation. This strategy is an attempt to mirror the phases of the development cycle as code progresses chronologically from active development to functional testing to the live production environment. [Learn more about branching strategies in TFVC.](/azure/devops/repos/tfvc/branching-strategies-with-tfvc?view=azure-devops&preserve-view=true)

When a developer believes that their work item is ready for functional testing, they merge or "promote" all changes that are associated with their work from a dedicated development branch to a dedicated testing branch. The testing branch contains all code that's awaiting functional validation. After the changes that are associated with a work item pass functional validation, they're promoted to the dedicated branch that holds production ready code. The production branch contains the code that's running on the live environment (or that will soon be deployed to it).

### Branching in Git

Git works very well with both a [trunk-based approach](/devops/develop/how-microsoft-develops-devops) and a [GitFlow approach](/devops/develop/how-microsoft-develops-devops#differences-from-github-flow). If you use Git branching, we strongly recommend that you keep branches short-lived and sync often to help reduce the risk of merge conflicts. [Learn more about branching strategies in Git.](/azure/devops/repos/tfvc/branching-strategies-with-tfvc?view=azure-devops&preserve-view=true)

When a developer starts new work, a new branch can be created to hold the changes. The developer should be sure to keep the branch in sync with its origin branch, and they should often create pull requests to validate their changes through build and test validation. At the completion of the development, the changes can easily be merged back through a [squash and merge operation](/azure/devops/repos/git/merging-with-squash?view=azure-devops&preserve-view=true).
