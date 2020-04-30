---
# required metadata

title: Create deployable packages in Azure Pipelines
description: This topic explains how you can create a software deployable package when you run build automation in Microsoft Azure DevOps.
author: jorisdg
manager: AnnBe
ms.date: 03/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 26731
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0

---

# Create deployable packages in Azure Pipelines

If you want to deploy customizations to an environment, a deployable package is required in Microsoft Dynamics Lifecycle Services (LCS). You can create this package by using Azure Pipelines during a build or release process.

This topic assumes a working knowledge of [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](https://docs.microsoft.com/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser).
>
> This Azure DevOps task requires that the X++ compiler tools be available on the agent. Either run this task on a build virtual machine (VM) agent, or use the Compiler Tools NuGet package. For more information about the NuGet package and how to install it in a pipeline, see [Build automation using Microsoft-hosted agents and Azure Pipelines](hosted-build-automation.md).

## Add the task to a pipeline

To add the task to your YML or Classic pipeline build, search the task list for **Create Deployable Package**. The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
| --- | --- | --- |
| X++ Tools Path | Yes | The path of the location of the X++ tools. This location is either the **PackagesLocalDirectory\\bin** folder location on a build VM, or the location of the extracted NuGet file of the Compiler Tools NuGet package. |
| Location of the X++ binaries to package | Yes | The path that contains the folders that contain all the binaries for the X++ packages (modules) that you want to include in the deployable package. If this task is used in a build pipeline, this folder is typically the same as the compiler output folder. |
| Search pattern for binaries to package | Yes | Provide a name matching pattern for X++ package (module) names inside the path that is specified in the **Location of the X++ binaries to package** option. You can also specify a list of names instead of search patterns, or you can specify exclusion filters so that, for example, test packages aren't included. For more information, see [File matching patterns reference](https://docs.microsoft.com/azure/devops/pipelines/tasks/file-matching-patterns?view=azure-devops). |
| Filename and path for the deployable package | Yes | The path and file name of the deployable package. The output file is a zip file, and the file name typically includes version information to make the file easy to identify. |

## NuGet dependency

When this task is run on the build VM, NuGet is already available, and no action is required. However, when this task is run on hosted agents or other private agents, NuGet must be installed. In this case, Azure DevOps has the [NuGet Tool Installer task](https://docs.microsoft.com/azure/devops/pipelines/tasks/tool/nuget?view=azure-devops) that you can run before you run the task to create the package.

> [!NOTE]
> Because of the introduction of semantic versioning in NuGet version 3.4 and later, you must install version 3.3.0 or earlier.
