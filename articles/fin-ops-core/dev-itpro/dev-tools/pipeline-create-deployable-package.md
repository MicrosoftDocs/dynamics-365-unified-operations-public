---
title: Create deployable packages in Azure Pipelines
description: Learn about how you can create a software deployable package when you run build automation in Microsoft Azure DevOps.
author: snamilikonda
ms.author: snamilikonda
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/12/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0
---

# Create deployable packages in Azure Pipelines

If you want to deploy customizations to an environment, a deployable package is required in Microsoft Dynamics Lifecycle Services. You can create this package by using Azure Pipelines during a build or release process.

This article assumes a working knowledge of [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> - Before you can add these steps to a pipeline, the [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps organization. For more information about how to install an extension for an organization, see [Install extensions](/azure/devops/marketplace/install-extension).
> - This Azure DevOps task requires that the X++ compiler tools be available on the agent. Either run this task on a build virtual machine (VM) agent, or use the Compiler Tools NuGet package. For more information about the NuGet package and how to install it in a pipeline, see [Build automation using Microsoft-hosted agents and Azure Pipelines](hosted-build-automation.md).

> [!NOTE]
> Versions 1.\*  and lower of the task are obsolete. Update the task version to the latest available.

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Create Deployable Package**. The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
| --- | --- | --- |
| X++ Tools Path | Yes | The path of the location of the X++ tools. This location is either the **PackagesLocalDirectory\\bin** folder location on a build VM, or the location of the extracted NuGet file of the Compiler Tools NuGet package. |
| Location of the X++ binaries to package | Yes | The path that contains the folders that contain all the binaries for the X++ packages (modules) that you want to include in the deployable package. If this task is used in a build pipeline, this folder is typically the same as the compiler output folder. |
| Search pattern for binaries to package | Yes | Provide a name matching pattern for X++ package (module) names inside the path that is specified in the **Location of the X++ binaries to package** option. You can also specify a list of names instead of search patterns, or you can specify exclusion filters so that, for example, test packages aren't included. The search pattern looks for folders and validates that they contain a `bin` subfolder with X++ assemblies. For more information, see [File matching patterns reference](/azure/devops/pipelines/tasks/file-matching-patterns).  |
| Filename and path for the deployable package | Yes | The path and file name of the deployable package. The output file is a zip file, and the file name typically includes version information to make the file easy to identify. |

> [!NOTE]
> With the introduction of the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview), a new version of this task was released that is capable of generating the package in both the Lifecycle Services and Power Platform unified package formats. To generate the package in the Power Platform unified package format at the "path for the cloud deployable package" location, select the **Create Power Platform Unified Package** checkbox, and then enter the platform and application version used. The search pattern and tools package path are still honored as before. The Lifecycle Services package creation option is selected by default and is generated the same way it was before, with the option to turn off creating the Lifecycle Services package. The **Platform** and **Application version** fields are ignored.

## NuGet dependency

When this task is run on the build VM, NuGet is already available, and no action is required. However, when this task is run on hosted agents or other private agents, NuGet must be installed. In this case, Azure DevOps has the [NuGet Tool Installer task](/azure/devops/pipelines/tasks/tool/nuget) that you can run before you run the task to create the package.

> [!NOTE]
> Because of the introduction of semantic versioning in NuGet version 3.4 and later, you must install version 3.3.0 or earlier.

## Search for binaries to package

Compared to the legacy packaging on the build virtual machine, the packaging task has to specify which modules to package and where to find them. In a standard pipeline, X++ modules under compilation are output in the binaries folder of the Azure DevOps agent. The packaging task by default looks in this folder for any X++ binaries. The search looks for folder names. The task checks inside these folders for a `/bin/` subfolder with X++ assemblies.

> [!NOTE]
> If your source control repositories include third-party binaries such as ISV modules, the packaging step includes those binaries. See the examples section of this article.

## Examples of search patterns

> [!NOTE]
> To avoid deployment issues, ensure the leaf directory names resolved in the search have unique names.

The following example assumes the **Location of the X++ binaries to package** property is set to its default value of `$(Build.BinariesDirectory)`, which is the location where the X++ compiler produces the binaries.

| Search pattern | Description |
| --- | --- |
| `*` | Find all X++ binaries in `$(Build.BinariesDirectory)`. This is the default value. |
| `*`<br/>`!*Tests` | Find all X++ binaries, and exclude any module names that end in `Tests`. |
| `MyPackage` | Find a module named `MyPackage` in the `$(Build.BinariesDirectory)` folder. |
| `*`<br/>`$(Build.SourcesDirectory)\Metadata\MyBinaryPackage` | Include all X++ binaries in `$(Build.BinariesDirectory)`, and a module named `MyBinaryPackage` in the sources directory (which is the mapped source control repository folder) inside the `Metadata` folder. |
| `*`<br/>`!*Tests`<br/>`$(Build.SourcesDirectory)\Metadata\MyISV1`<br/>`$(Build.SourcesDirectory)\Metadata\MyISV2` | Include all X++ binaries in `$(Build.BinariesDirectory)`, exclude any modules where the names end in `Tests`, and include two modules named `MyISV1` and `MyISV2` in the sources directory (which is the mapped source control repository folder) inside the `Metadata` folder. |

## Frequently asked questions

#### In the Create Deployable Package step, what is the workaround for when I get the "There is not enough space on the disk" error?

If the agent running the pipeline runs out of disk space during the **Create Deployable Package** step, the workaround is to introduce a delete files task in the pipeline just before this task to delete the contents of the `$(Build.SourcesDirectory)`. This task then creates space if no other part of the pipeline is using those files. The **Create Deployable Package** step isn't dependent on the model source files because it's dependent on the build output from the build step.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
