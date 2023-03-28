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

[Git](/devops/develop/git/what-is-git) is the modern standard for version control and [Microsoft's default Version Control System](/azure/devops/repos/tfvc/comparison-git-tfvc?view=azure-devops&preserve-view=true#which-version-control-system-should-i-use) provider recommended for general development. X++ developers may already be familiar with the [existing guidance](version-control-metadata-navigation.md) to set up Team Foundation Version Control (TFVC) for X++, but many organizations are standardizing on Git. This article introduces some of the key considerations for teams looking to utilize Git tools for X++ development.

## Considerations and limitations

Below are the known limitations and workarounds required to configure a Git repo for X++ and set up developer environments for X++ development with Git:

- The [Dynamics 365 Finance and Operations build tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) are offered exclusively as an Azure DevOps extension, so for full CI/CD support, consider using Azure DevOps for your Git repo.
- Additional configuration steps are required to successfully map a Git version control system to the PackagesLocalDirectory directory in a development environment, as is also the case with TFVC. One way to perform this configuration is documented in the [Microsoft Developer Blog](https://devblogs.microsoft.com/cse/2022/06/14/xpp-and-git/).
- Dynamics Lifecycle Services (LCS) checks for a TFVC repository during the deployment of build environments, so if your team uses build environments, you will need to initialize a TFVC repository [and connect to it from LCS](../perf-test/continuous-build-test-automation#azure-devops-credential-setup-and-linking-to-lcs-project), even if you're not actively using it for code management.
- [Branching strategies in TFVC](/azure/devops/repos/tfvc/branching-strategies-with-tfvc) often differ from [branching strategies in Git](/azure/devops/repos/git/branch-policies-overview). Common Git-based branching strategies include [Trunk-based](/devops/develop/how-microsoft-develops-devops) management and [GitFlow or GitHub Flow](/devops/develop/how-microsoft-develops-devops). Read about [branching strategies when doing X++ development](branching.md).

## Resources

- [Migrating from TFVC to Git](/devops/develop/git/migrate-from-tfvc-to-git)
- [Feature comparison between Git and TFVC](/azure/devops/repos/tfvc/comparison-git-tfvc?view=azure-devops&preserve-view=true)
