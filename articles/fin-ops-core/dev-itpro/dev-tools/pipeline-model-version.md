---
# required metadata

title: X++ model-versioning in Azure Pipelines
description: The topic explains how you can automatically version X++ models when you run build automation in Microsoft Azure DevOps.
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

# X++ model-versioning in Azure Pipelines

During build automation, X++ model versions can be updated so that they match or are linked to the build number of the pipeline. These updates make it easier for customers to identify the version of the X++ packages that they are running. They also let developers track versions back to the build pipeline and the version of the source code files.

This topic assumes a working knowledge of [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](https://docs.microsoft.com/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Update Model Version**. The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
| --- | --- | --- |
| X++ Source Location | Yes | The path of a parent folder that contains X++ source code. The **Descriptor Search Pattern** option will be run in this path and subfolders. The default value, **$(Build.SourcesDirectory)**, points to the root of the source code repository. |
| Descriptor Search Pattern | Yes | Provide a file matching pattern to find the descriptor files inside the path that is specified in the **X++ Source Location** option. You can also specify a list of full paths of descriptor files instead of search patterns. For more information, see [File matching patterns reference](https://docs.microsoft.com/azure/devops/pipelines/tasks/file-matching-patterns?view=azure-devops). |
| Lowest Layer to Update | Yes | When you use search patterns descriptors for independent software vendor (ISV) or partner code might be found, the lowest layer that the versions should not be updated for. This option allows for additional filtering by updating descriptors only in the selected layer and above. |
| Version number in format #.#.#.# to update | Yes | The version number to write into the descriptors. Note that the format must consist of four digits that are separated by periods (.). By using the build ID or build number, you allow for traceability. Note that the default build number isn't in the correct format. You can change the format in the classic editor, under **Options** \> **Build number format**. You can also change it by adding a `name:` tag at the top of the YML file. An example of a valid build number that uses the year, month, and date, and also the build count revision number, is `$(Date:yy.MM.dd)$(Rev:.r)`. For more information, see [Configure run or build numbers](https://docs.microsoft.com/azure/devops/pipelines/process/run-number?view=azure-devops&tabs=classic). |
