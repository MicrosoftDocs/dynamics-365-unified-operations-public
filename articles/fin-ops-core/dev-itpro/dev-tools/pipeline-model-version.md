---
title: X++ model-versioning in Azure Pipelines
description: Learn about how you can automatically version X++ models when you run build automation in Microsoft Azure DevOps.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: AX 7.0.0
---

# X++ model versioning in Azure Pipelines

[!include [banner](../includes/banner.md)]

During build automation, update X++ model versions so they match or link to the build number of the pipeline. These updates make it easier for customers to identify the version of the X++ packages that they're running. They also let developers track versions back to the build pipeline and the version of the source code files.

This article assumes a working knowledge of [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> Before you can add these steps to a pipeline, you must enable and install the [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps in your Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](/azure/devops/marketplace/install-extension).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Update Model Version**. The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
| --- | --- | --- |
| X++ Source Location | Yes | The path of a parent folder that contains X++ source code. The **Descriptor Search Pattern** option runs in this path and subfolders. The default value, **$(Build.SourcesDirectory)**, points to the root of the source code repository. |
| Descriptor Search Pattern | Yes | Provide a file matching pattern to find the descriptor files inside the path that you specify in the **X++ Source Location** option. You can also specify a list of full paths of descriptor files instead of search patterns. For more information, see [File matching patterns reference](/azure/devops/pipelines/tasks/file-matching-patterns). |
| Lowest Layer to Update | Yes | When using search patterns, this task might find descriptors for ISV or partner code in your source control. You likely shouldn't update those descriptor versions. This option allows you to define an additional filter to define the lowest layer that the task updates. |
| Version number in format #.#.#.# to update | Yes | The version number to write into the descriptors. The format must consist of four digits that are separated by periods (.). By using the build ID or build number, you allow for traceability. The default build number isn't in the correct format. You can change the format in the classic editor, under **Options** \> **Build number format**. You can also change it by adding a `name:` tag at the top of the YML file. An example of a valid build number that uses the year, month, and date, and also the build count revision number, is `$(Date:yy.MM.dd)$(Rev:.r)`. For more information, see [Configure run or build numbers](/azure/devops/pipelines/process/run-number). |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
