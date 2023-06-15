---
title: Deploy assets by using Azure Pipelines
description: This article explains how you can deploy assets from the Asset library in Microsoft Dynamics Lifecycle Services (LCS) by using pipelines in Azure DevOps.
author: gianugo
ms.date: 04/29/2020
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0
ms.custom: 
---

# Deploy assets by using Azure Pipelines

You can use the **Dynamics Lifecycle Services (LCS) Asset Deployment** task in Microsoft Azure DevOps to automate the deployment of assets that are stored in the Asset library in Microsoft Dynamics Lifecycle Services to specific environments. However, this task has the following limitations that you should consider:

* The task is available only in **Releases** pipelines.
* The deployment of software deployable packages to production environments can't be automated.
* Software deployable packages can't be deployed to build environments.
* Commerce Cloud Scale Unit (CSU) extension packages and e-commerce packages can't be deployed to local business data environments on-premises.

> [!NOTE]
> Commerce Cloud Scale Unit (CSU) extension or e-commerce packages can be deployed to a production, UAT, or Sandbox environment using the **Dynamics Lifecycle Services Asset Deployment**.

This article assumes that you have a working knowledge of [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 finance and operations tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](/azure/devops/marketplace/install-extension).

> [!NOTE]
> The Azure DevOps pipeline must be run by a user with the **Environment manager** [role](../lifecycle-services/configure-lcs-security.md#configuring-project-security) in the corresponding Dynamics Lifecycle Services project.

## Dynamics 365 for Finance + Operations (on-premises) package deployment

Starting with version 0.2.1239020 of the **Dynamics 365 finance and operations tools** extension, it is possible to deploy packages to local business data environments on-premises. You should use at least version 3.\* of the  **Dynamics Lifecycle Services (LCS) Asset Deployment** task. You will then be able to select **Software deployable package for on-premises environments** under the **Type of asset** field.

> [!NOTE]
> The entire pipeline run will take more than one hour, so you shouldn't use the free Microsoft-hosted agents as they will timeout.

## Dynamics 365 Commerce Cloud Scale Unit (CSU) extension and e-Commerce package deployment

Starting with version 3.\*, the **Dynamics Lifecycle Services (LCS) Asset Deployment** task supports deploying Commerce packages. A new field type called **Type of asset** has been added to select the Commerce package deployment type. The values available for this field are:

- **Software deployable package - Finance and Operation environment deployment** (default value)
- **Commerce Cloud Scale Unit Extension - CSU Extension package deployment** 
- **e-Commerce Package - e-Commerce environment deployment**.

Selecting either the **Commerce Cloud Scale Unit Extension - CSU Extension package deployment** or **e-Commerce Package - e-Commerce environment deployment** options will override previous deployments. If you have multiple CSU extensions packages, then all CSU packages must be merged as one package for deployment.

## Make sure that MSAL.PS is installed

Versions 2.\* and later of the deployment task require availability of the MSAL.PS PowerShell library. A task is available to automatically install the tools during pipeline execution. This task can be added anywhere in the stage before the deployment task. For more information, see [Add the MSAL.PS install task to a pipeline](pipeline-lcs-connection-update.md#add-the-msalps-install-task-to-a-pipeline).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Dynamics Lifecycle Services (LCS) Asset Deployment**. If your target environments include self-service environments, be sure to select task version 1.\* or later.

The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
|---|---|---|
| LCS Connection | Yes | Select or create a service connection to Dynamics Lifecycle Services. For more information, see [Create a Dynamics Lifecycle Services connection in Azure Pipelines](pipeline-lcs-connection.md). |
| LCS Project ID | Yes | Enter the ID of the project in Dynamics Lifecycle Services that contains both the asset to deploy and the target environment. You can find the project ID at the end of the URL of your project's dashboard. |
| LCS Environment ID | Yes | Enter the ID of the target environment. The environment ID is a globally unique identifier (GUID) that you can find on the environment's details page, under **Environment Details** \> **Environment ID**. |
| LCS File Asset ID | Yes | Enter the asset ID of the software deployable package to deploy. The asset ID is a GUID that you can find in the Asset library. Select the row of the asset that you want to deploy, and then, under **Additional Details**, look in the **Asset ID** field. Typically, this ID comes dynamically from other pipeline steps, such as the [Dynamics Lifecycle Services Asset Upload](pipeline-asset-upload.md) task. |
| Type of asset | Yes | Select the type of asset to be deployed to the environment in Dynamics Lifecycle Services. Options are **Software deployable package - finance and operations environment deployment**, **Software deployable package for on-premises environments - Finance + Operations (on-premises) environment deployment**, **Commerce Cloud Scale Unit Extension - CSU Extension package deployment**, and **e-Commerce package - e-Commerce environment deployment**. |
| Commerce Cloud Scale Unit Name | No | Enter the name of the Commerce Cloud Scale Unit environment, you can find the environment name in the environment's details page, under **Environment FEATURES** \> **Commerce** \> **Manage** \> **Commerce deployment & setup** \> **Commerce scale units**. If the package type is selected as **Commerce Cloud Scale Unit Extension** then the value for the field **Commerce Cloud Scale Unit Name** is mandatory. |
| e-Commerce Environment Name | No | Enter the name of the e-Commerce environment, you can find the environment name in the environment's details page, under **Environment FEATURES** \> **Commerce** \> **Manage** \> **Commerce deployment & setup** \> **e-Commerce.** If the package type is selected as **e-Commerce Package** then value for the field **e-Commerce Environment Name** is mandatory. |
| Name for the update | Yes | Enter the name that is shown for the update in the environment history in Dynamics Lifecycle Services. |
| Wait for Completion | Cleared (No) | Use this check box to instruct the task to wait until the deployment of the asset has either succeeded or failed. If it's cleared (**No**), the task will only start the deployment. If the task is instructed to wait, a pipeline time-out might occur during long-running deployments. For more information about time-out options, see [Timeouts](/azure/devops/pipelines/process/phases#timeouts). |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

