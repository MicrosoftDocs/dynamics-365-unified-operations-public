---
title: X++ in Git
description: This article introduces the concept of X++ code management in Git and outlines key considerations for teams looking to utilize Git tools for X++ development.
author: ianjensenisme
ms.date: 01/04/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: ianjensen
ms.search.validFrom: 2023-04-01
ms.dyn365.ops.version: 10.0.31
---

# X++ in Git

## Introduction

[Git](https://learn.microsoft.com/en-us/devops/develop/git/what-is-git) is the modern standard for version control and Microsoft's [Microsoft's default recommendation](https://learn.microsoft.com/en-us/azure/devops/repos/tfvc/comparison-git-tfvc?view=azure-devops#which-version-control-system-should-i-use) for general development. Many X++ developers are familiar with the [existing guidance](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/version-control-metadata-navigation) to set up Team Foundation Version Control (TFVC) for X++, but for many teams, Git has already become a more flexible and powerful option for X++ development. This article introduces the concept of X++ code management in Git and outlines key considerations and resources for teams looking to utilize Git tools for X++ development.

## Considerations

Below are the known limitations and workarounds required to configure a Git repo for X++ and set up dev environments for X++ development with Git:

- The [Dynamics 365 Finance and Operations build tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) are offered exclusively as an Azure DevOps extension, so for full CI/CD support, consider using Azure DevOps for your Git repo.
- Git cannot directly map to the PackagesLocalDirectory folder on a development environment without additional configuration steps. These steps are documented in the [Microsoft Developer Blog](https://devblogs.microsoft.com/cse/2022/06/14/xpp-and-git/).

## Resources

- [Migrating from TFVC to Git](https://learn.microsoft.com/en-us/devops/develop/git/migrate-from-tfvc-to-git)
- [Feature comparison between Git and TFVC](https://learn.microsoft.com/en-us/azure/devops/repos/tfvc/comparison-git-tfvc?view=azure-devops)
- General repository branching guidance
