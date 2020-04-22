---
# required metadata

title: X++ Model Versioning in Azure DevOps Pipelines
description: The topic explains how you can automatically version X++ models when running build automation in Azure DevOps
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

# X++ Model Versioning in Azure DevOps Pipelines

During build automation, X++ models' versions can be updated to match or link to the build number of the pipeline. This makes it easier for users to identify the version of the X++ packages they are running, and allows developers to track versions back to the build pipeline and the version of the source code files.

This article assumes a working knowledge of Azure DevOps pipelines. Please review the documentation about [Aure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

> [!NOTE]
> To add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps needs to be enabled and installed in the Azure DevOps Account. Review the [Azure DevOps documentation](https://docs.microsoft.com/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser) on how to install an extension for an organization.

## Adding the task to a pipeline

To add the task to your YML or Classic Pipeline build, search the task list for **Update Model Version**. The following table describes the options available for the task.

| Input Name | Mandatory | Description |
| --- | --- | --- |
| X++ Source Location | Yes | The path to a parent folder containing X++ source code. The **Descriptor Search Pattern** will be run in this path and subfolders. The default value of $(Build.SourcesDirectory) points to the root of the source code repository. |
| Descriptor Search Pattern | Yes | Provide a file matching pattern to find the descriptor files inside the path specified in the **X++ Source Location**. A list of full paths to descriptor files can also be specified instead of search patterns. For more information on the file match pattern options available in Azure DevOps, review the [File matching patterns reference](https://docs.microsoft.com/azure/devops/pipelines/tasks/file-matching-patterns?view=azure-devops) in the Azure DevOps documentation. |
| Lowest Layer to Update | Yes | When using search patterns descriptors for ISV or Partner code may be found, for which the versions should not be updated. This option allows additional filtering, by only updating descriptors in the selected layer and above. |
| Version number in format #.#.#.# to update | Yes | The version to write into the descriptors. Note that the format has to consist of 4 digits separated by a period ('.'). Using the build Id or build number allows for traceability. Note that the default build number is not in the correct format. This can be changed in the classic editor under **Options** > **Build number format**, or in a YML file by adding a "name:" tag at the top of the YML file. An example of a valid build number could be using the year, month and date as well as the build count revision number: "$(Date:yy.MM.dd)$(Rev:.r)". For more information, see the Azure DevOps documentation to [Configure run or build numbers](https://docs.microsoft.com/azure/devops/pipelines/process/run-number?view=azure-devops&tabs=classic).  |

