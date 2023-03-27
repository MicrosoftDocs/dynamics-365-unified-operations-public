---
title: Branching
description: This article discuss branching strategy considerations for X++ development.
author: skaue-ms
ms.date: 01/04/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: toskaue
ms.search.validFrom: 2023-01-01
ms.dyn365.ops.version: 10.0.30
---
# Branching

Branching configurations for X++ repositories vary depending on the development team preference and the finance and operations apps lifecycle. If the implementation already has a preferred branching structure and it meets the [minimum branching criteria](#minimum-branching-criteria) outlined below, you could use it to manage new development. Alternatively, you can evaluate the branching structure options in this article.

## Considerations

You'll find that a few elements of the X++ development cycle differ from general application development. Keep the following items in mind as you consider how to structure your branches:

- ERP systems are business-critical environments. When designing your code management infrastructure, you should prioritize design elements that minimize both the risk of major production issues and the disaster recovery timeline.
- Due the he complexity of and the interdependency on the standard system code, it's generally a good idea to perform automated and manual testing of **all critical business processes** after each code update. This testing can take days to complete, so plan for a branch to contain this in-test code for long spans of time while it is being validated.
- Merge conflicts are relatively frequent with X++ due to the pattern of dev teams frequently focusing their collective attention on enhancing specific modules and areas of the product. Plan a branching strategy that reduces the frequency of collisions and eases the resolution of collisions when they do occur.

## Minimum Branching Criteria

Any X++ repo branching strategy should support, at a minimum:

- The isolation of un-tested development code or code in development. Developers should be protected from teammates accidentally breaking any active development branch. If there's only one DEV branch shared, each developer would need to ensure they don't commit code that breaks teammates. Additional configuration of the version control capabilities should be leveraged. Otherwise, isolating untested code from in-development code is an ideal way to provide this protection. 
- The isolation of in-development code from test-eligible code. A code change may pass unit testing or manual developer testing but the associated task may still not be ready for functional testing. Any X++ branching structure should clearly notate when a collection of changes is ready for functional testing.
- The isolation if in-test code from production code. This is the fundamental purpose of all version control: avoiding code releases to production environments until code changes have been fully validated.
- Relatively long (weeks) functional testing cycles. See the [Considerations](#considerations) section for more details on why finance and operations apps customizations take longer to validate.

## Branch Policy Guidance

Below are some branch policy best practices we recommend regardless of which branching strategy you choose:

- The live/production code branch should be locked to prevent direct editing; changes should only be made via merge from other branches.
- Before functional testing begins, all code changes should be reviewed by at least one reviewer.

## Branching strategies

### Branching in TFVC

A commonly used branching for teams using TFVC is combining a Trunk-based approach with Developer isolation and Release isolation. This approach also attempts to mirror the phases of the development cycle as code progresses chronologically from active development to functional testing to the live production environment.

When a developer believes their work item is ready for functional testing, they merge or "promote" all changes associated with their work from a dedicated development branch to a dedicated testing branch. The testing branch contains all code awaiting functional validation. After the changes associated with a work item pass functional validation, they are promoted to the dedicated branch holding production ready code. The Production branch contains the code running on (or soon to be deployed to) the live environment.

### Branching in Git

Git works very well with both a [Trunk-based approach](/devops/develop/how-microsoft-develops-devops) and [GitFlow approach](/devops/develop/how-microsoft-develops-devops#differences-from-github-flow). One of the strong recommendations using Git branching is to keep branches short-lived and sync often to reduce the risk of merge conflicts.

When a developer starts a new work, a new branch can be created to hold the changes. The developer would make sure to keep the branch in sync with its originated branch and do pull requests often to validate their changes through the build and test validation. At the completion of the development, the changes can be easily merged back with a [squash and merge operation](azure/devops/repos/git/merging-with-squash?view=azure-devops&preserve-view=true). 

## Resources

- [Branching strategies in TFVC](/azure/devops/repos/tfvc/branching-strategies-with-tfvc?view=azure-devops&preserve-view=true)
- [Branching strategies in Git](/azure/devops/repos/tfvc/branching-strategies-with-tfvc?view=azure-devops&preserve-view=true)

