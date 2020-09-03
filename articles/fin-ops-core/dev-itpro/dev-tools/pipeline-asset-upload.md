---
# required metadata

title: Uploading assets in Azure Pipelines
description: The topic explains how you can upload assets to the LCS asset library using Azure Pipelines.
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
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0

---

# Asset Upload in Azure Pipelines

You can automate uploading assets to the **Lifecycle Services Asset Library** by using the **Deploy Lifecycle Services (LCS) Asset Upload** task in Azure DevOps. The task is only available in **Releases** pipelines.

This topic assumes you have a working knowledge of [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](https://docs.microsoft.com/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Dynamics Lifecycle Services (LCS) Asset Upload**.

The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
| --- | --- | --- |
| LCS Connection | Yes | Select or create a service connection to Dynamics Lifecycle Services (LCS). For more information, see [Creating an LCS connection in Azure Pipelines](pipeline-lcs-connection.md). |
| LCS Project ID | Yes | Enter the project ID identifying the project in LCS that contains both the asset to be deployed, and the target environment. The project ID can be found at the end of the URL of your project's dashboard. |
| Type of asset | Yes | Select the type of asset you wish to upload. |
| File to upload | Yes | Enter the path to the file to upload into the LCS **Asset Library**. |
| LCS Asset Name | No | Enter a name for the asset to be shown in the **Asset Library**. If no name is specified, the file name will be used. |
| LCS Description | No | Enter a description for the asset to be shown in the asset details. |
| Wait for Validation | No | For asset types that require validation, this checkbox instructs the task to wait until the validation of the asset has either succeeded or failed. |
