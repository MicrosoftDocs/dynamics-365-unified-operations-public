---
# required metadata

title: Add License Files to a Deployable Package in Azure DevOps Pipelines
description: The topic explains how you can add license files to an existing software deployable package when running build automation in Azure DevOps
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

# Add License Files to a Deployable Package in Azure DevOps Pipelines

When updating an environment with a deployable package, a license may be required for ISV or partner X++ solutions. ISVs can setup pipelines to automatically include these licenses in release or build pipelines, or customers can setup their own pipeline to combine the ISV deployable package and the license file.

This article assumes a working knowledge of Azure DevOps pipelines. Please review the documentation about [Aure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

> [!NOTE]
> To add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps needs to be enabled and installed in the Azure DevOps Account. Review the [Azure DevOps documentation](https://docs.microsoft.com/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser) on how to install an extension for an organization.

## Adding the task to a pipeline

To add the task to your YML or Classic Pipeline build, search the task list for **Add Licenses to Deployable Package**. The following table describes the options available for the task.

| Input Name | Mandatory | Description |
| --- | --- | --- |
| Search pattern for license files to add to the package | Yes | A list of license files or a search pattern for files, on the build agent. To make the license files available on the build agent, the files can be added to source control, or downloaded or generated in a previous step of the pipeline. |
| Filename and path of the deployable package to update | Yes | This specifies the path, including the filename, of an existing deployable package zip file to which the license file(s) should be added. |
