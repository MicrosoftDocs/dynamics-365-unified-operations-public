---
title: Add license files to a deployable package in Azure Pipelines
description: Learn about how you can add license files to an existing software deployable package when you run build automation in Microsoft Azure DevOps.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 10/03/2023
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0
---

# Add license files to a deployable package in Azure Pipelines

[!include [banner](../includes/banner.md)]

The article explains how you can add license files to an existing software deployable package when you run build automation in Microsoft Azure DevOps.

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

> [!NOTE]
> With the introduction of the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview), a new version of this task was released that is capable of adding licenses to a package in both the Microsoft Dynamics Lifecycle Services (LCS) and Power Platform unified package formats. To add licenses to a package, select the desired option from the **Package Type** dropdown menu. The LCS package creation option is selected by default and is generated the same way as before, requiring the same inputs as version 0. If you select **Power Platform Unified Package**, you must provide an additional model name to include the package in the model. You can add multiple such tasks for different models/packages. The search pattern and file path fields are still honored as before.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
