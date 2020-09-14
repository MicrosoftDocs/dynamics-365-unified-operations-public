---
# required metadata

title: Deploy assets by using Azure Pipelines
description: This topic explains how you can deploy assets from the LCS asset library using pipelines in Microsoft Azure DevOps.
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
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0

---

# Deploy assets by using Azure Pipelines

You can automate deploying assets stored in the **Lifecycle Services Asset Library** to specific environments by using the **Deploy Lifecycle Services (LCS) Asset Deployment** task in Azure DevOps. There are some limitations to this task that you should consider.

* The task is only available in **Releases** pipelines.
* The task does not allow automation of deploying software deployable packages to production environments.
* The task does not allow deploying software deployable packages to build environments.
* The task does not allow deploying software deployable packages to **Local Business Data** (LBD) environments on premises.

This topic assumes that you have a working knowledge of [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](https://docs.microsoft.com/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Dynamics Lifecycle Services (LCS) Asset Deployment**. If your target environments include self-service environments, ensure you select **Task version** 1.\* or later.

The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
| --- | --- | --- |
| LCS Connection | Yes | Select or create a service connection to Dynamics Lifecycle Services (LCS). For more information, see [Creating an LCS connection in Azure Pipelines](pipeline-lcs-connection.md). |
| LCS Project ID | Yes | Enter the project ID identifying the project in LCS that contains both the asset to be deployed, and the target environment. You can find project ID at the end of the URL of your project's dashboard. |
| LCS Environment ID | Yes | Enter the ID of the target environment. The environment ID is a GUID that you can find on the environment's details page under **Environment Details** > **Environment ID**. |
| LCS File Asset ID | Yes | Enter the asset ID of the software deployable package to deploy. The asset ID is a GUID that you can find in the asset library. Select the row of the asset you wish to deploy, and find the **Asset ID** under **Additional Details**. Typically, this ID will dynamically come from other pipeline steps, such as the [Dynamics Lifecycle Services (LCS) Asset Upload task](pipeline-asset-upload.md). |
| Name for the update | Yes | This name is a name for the update that will be shown in the LCS environment history. |
| Wait for Completion | No | This checkbox instructs the task to wait until the deployment of the asset has either succeeded or failed. If set to **No**, the task will only start the deployment. Long-running deployments may result in a pipeline time-out if the task is instructed to wait. For more information on time-out options, see [Specify jobs in your pipeline](https://docs.microsoft.com/azure/devops/pipelines/process/phases?view=azure-devops&tabs=classic&viewFallbackFrom=vsts#timeouts). |
