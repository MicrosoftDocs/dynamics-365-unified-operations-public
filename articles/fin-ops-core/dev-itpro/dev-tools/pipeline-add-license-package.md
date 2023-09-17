---
title: Add license files to a deployable package in Azure Pipelines
description: The article explains how you can add license files to an existing software deployable package when you run build automation in Microsoft Azure DevOps.
author: gianugo
ms.date: 03/05/2020
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 
---

# Add license files to a deployable package in Azure Pipelines

[!include [banner](../includes/banner.md)]

When you update an environment by using a deployable package, a license might be required for independent software vendor (ISV) or partner X++ solutions. ISVs can create pipelines to automatically include licenses in release or build pipelines. Customers can create their own pipelines to combine the ISV deployable package and the license file.

This article assumes a working knowledge of [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](/azure/devops/marketplace/install-extension).

## Adding the task to a pipeline

To add the task to your build for the YML or Classic pipeline, search the task list for **Add Licenses to Deployable Package**. The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
| --- | --- | --- |
| Search pattern for license files to add to the package | Yes | A list of license files on the build agent, or a search pattern for files on the build agent. To make the license files available on the build agent, you can add them to source control. Alternatively, they can be downloaded or generated in an earlier step of the pipeline. For more information, see [File matching patterns reference](/azure/devops/pipelines/tasks/file-matching-patterns). |
| Filename and path of the deployable package to update | Yes | The path and file name of an existing deployable package zip file that the license files should be added to. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
