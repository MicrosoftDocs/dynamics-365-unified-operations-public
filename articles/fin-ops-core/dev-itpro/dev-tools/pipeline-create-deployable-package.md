---
# required metadata

title: Creating a Software Deployable Package in Azure DevOps Pipelines
description: The topic explains how you can create a software deployable package when running build automation in Azure DevOps
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

# Creating Deployable Packages in Azure DevOps Pipelines

To deploy customizations to an environment, a deployable package is required in Dynamics Lifecycle Services. This package can be created in an Azure Pipeline, during a build or release process.

This article assumes a working knowledge of Azure DevOps pipelines. Please review the documentation about [Aure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

> [!NOTE]
> To add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps needs to be enabled and installed in the Azure DevOps Account. Review the [Azure DevOps documentation](https://docs.microsoft.com/en-us/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser) on how to install an extension for an organization.

> [!NOTE]
> This Azure DevOps task requires the X++ compiler tools be available on the agent. Either run this task on a build Virtual Machine agent, or use the Compiler Tools NuGet package. For more information on the NuGet package and how to install it in the pipeline, review the documentation on [Build Automation using Azure DevOps Hosted Agents](hosted-build-automation.md).

## Adding the task to a pipeline

To add the task to your YML or Classic Pipeline build, search the task list for **Create Deployable Package**. The following table describes the options available for the task.

| Input Name | Mandatory | Description |
| --- | --- | --- |
| X++ Tools Path | Yes | The path to the location of the X++ tools, either the PackagesLocalDirectory\bin folder location on a build VM, or the path to the extracted NuGet file of the Compiler Tools NuGet package. |
| Location of the X++ binaries to package | Yes | The path containing the folders with all the binaries for the X++ packages (modules) you wish to include in the deployable package. Typically this is the same folder as the compiler output folder if this task is used in a build pipeline. |
| Search pattern for binaries to package | Yes | Provide a name matching pattern for X++ package (module) names inside the path specified in **Location of the X++ binaries to package**. A list of names can also be specified instead of search patterns, or exclusion filters for example to exclude test packages from being included. For more information on the file match pattern options available in Azure DevOps, review the [File matching patterns reference](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/file-matching-patterns?view=azure-devops) in the Azure DevOps documentation. |
| Filename and path for the deployable package | Yes | Path including filename for the deployable package. The output file is a Zip file and typically the filename includes a version to easily identify the file. |

## NuGet Dependency

When running this task on the build VM, NuGet is already available and no action is required. However, when running on hosted agents or other private agents NuGet has to installed. For this, Azure DevOps has the [NuGet Tool Installer task](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/tool/nuget?view=azure-devops) which can be run prior to running the task to create the package.

> [!NOTE]
> Due to the introduction of semantic versioning in NuGet version 3.4 and above, it is currently required to install version 3.3.0 or earlier.

