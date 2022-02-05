---
title: Deploy assets by using Azure Pipelines
description: This topic explains how you can deploy assets from the Asset library in Microsoft Dynamics Lifecycle Services (LCS) by using pipelines in Azure DevOps.
author: jorisdg
ms.date: 03/05/2020
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.custom:
ms.search.region: Global
ms.author: jorisde
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0
---

# Deploy assets by using Azure Pipelines

You can use the **Dynamics Lifecycle Services (LCS) Asset Deployment** task in Microsoft Azure DevOps to automate the deployment of assets that are stored in the Asset library in Microsoft Dynamics Lifecycle Services (LCS) to specific environments. However, this task has the following limitations that you should consider:

* The task is available only in **Releases** pipelines.
* The deployment of software deployable packages to production environments can't be automated.
* Software deployable packages can't be deployed to build environments.
* Software deployable packages can't be deployed to local business data (LBD) environments on-premises.

This topic assumes that you have a working knowledge of [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](/azure/devops/marketplace/install-extension).

## Make sure that MSAL.PS is installed

Versions 2.\* and later of the deployment task require availability of the MSAL.PS PowerShell library. A task is available to automatically install the tools during pipeline execution. This task can be added anywhere in the stage before the deployment task. For more information, see [Add the MSAL.PS install task to a pipeline](pipeline-lcs-connection-update.md#add-the-msalps-install-task-to-a-pipeline).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Dynamics Lifecycle Services (LCS) Asset Deployment**. If your target environments include self-service environments, be sure to select task version 1.\* or later.

The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
|---|---|---|
| LCS Connection | Yes | Select or create a service connection to LCS. For more information, see [Create an LCS connection in Azure Pipelines](pipeline-lcs-connection.md). |
| LCS Project ID | Yes | Enter the ID of the project in LCS that contains both the asset to deploy and the target environment. You can find the project ID at the end of the URL of your project's dashboard. |
| LCS Environment ID | Yes | Enter the ID of the target environment. The environment ID is a globally unique identifier (GUID) that you can find on the environment's details page, under **Environment Details** \> **Environment ID**. |
| LCS File Asset ID | Yes | Enter the asset ID of the software deployable package to deploy. The asset ID is a GUID that you can find in the Asset library. Select the row of the asset that you want to deploy, and then, under **Additional Details**, look in the **Asset ID** field. Typically, this ID comes dynamically from other pipeline steps, such as the [Dynamics Lifecycle Services (LCS) Asset Upload](pipeline-asset-upload.md) task. |
| Name for the update | Yes | Enter the name that is shown for the update in the environment history in LCS. |
| Wait for Completion | Cleared (No) | Use this check box to instruct the task to wait until the deployment of the asset has either succeeded or failed. If it's cleared (**No**), the task will only start the deployment. If the task is instructed to wait, a pipeline time-out might occur during long-running deployments. For more information about time-out options, see [Timeouts](/azure/devops/pipelines/process/phases#timeouts). |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
