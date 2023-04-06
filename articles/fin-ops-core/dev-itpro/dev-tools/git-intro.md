---
title: X++ in Git
description: This article introduces the concept of X++ code management in Git and outlines key considerations for teams that want to use Git tools for X++ development.
author: ianjensenisme
ms.date: 03/31/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ianjensen
ms.search.validFrom: 2023-04-01
ms.dyn365.ops.version: 10.0.31
---

# X++ in Git

[Git](/devops/develop/git/what-is-git) is the modern standard for version control. It's also [Microsoft's default version control system](/azure/devops/repos/tfvc/comparison-git-tfvc?view=azure-devops&preserve-view=true#which-version-control-system-should-i-use) provider that's recommended for general development. X++ developers might be already familiar with the [existing guidance](version-control-metadata-navigation.md) to set up Team Foundation Version Control (TFVC) for X++, but many organizations are standardizing on Git. This article introduces the concept of X++ code management in Git and outlines key considerations for teams that want to use Git tools for X++ development.

## Considerations and limitations

The following list describes known limitations and workarounds that are required to configure a Git repository (repo) for X++ and set up developer environments for X++ development via Git:

- [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) are build tools that are offered exclusively as a Microsoft Azure DevOps extension. Therefore, for full continuous integration and continuous delivery (CI/CD) support, consider using Azure DevOps for your Git repo.
- More configuration steps are required to successfully map a Git version control system to the PackagesLocalDirectory directory in a development environment, as is also the case with TFVC. The [Microsoft Developer blog](https://devblogs.microsoft.com/cse/2022/06/14/xpp-and-git/) documents one way to do this configuration.
- Dynamics Lifecycle Services checks for a TFVC repo during the deployment of build environments. Therefore, if your team uses build environments, you'll have to initialize a TFVC repo and [connect to it from Lifecycle Services](../perf-test/continuous-build-test-automation.md#azure-devops-credential-setup-and-linking-to-lcs-project), even if you aren't actively using it for code management.
- [Branching strategies in TFVC](/azure/devops/repos/tfvc/branching-strategies-with-tfvc) often differ from [branching strategies in Git](/azure/devops/repos/git/branch-policies-overview). Common Git-based branching strategies include [trunk-based](/devops/develop/how-microsoft-develops-devops) management and [GitFlow or GitHub Flow](/devops/develop/how-microsoft-develops-devops). [Learn more about branching strategies for X++ development.](branching.md)

## Resources

- [Migrating from TFVC to Git](/devops/develop/git/migrate-from-tfvc-to-git)
- [Feature comparison between Git and TFVC](/azure/devops/repos/tfvc/comparison-git-tfvc?view=azure-devops&preserve-view=true)
