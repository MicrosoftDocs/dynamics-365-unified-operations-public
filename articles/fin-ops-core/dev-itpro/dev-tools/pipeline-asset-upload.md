---
title: Upload assets by using Azure Pipelines
description: Learn about how you can upload assets to the Asset library in Microsoft Dynamics Lifecycle Services by using Azure Pipelines.
author: snamilikonda
ms.author: snamilikonda
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/12/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0
---

# Upload assets by using Azure Pipelines

You can automate the upload of assets to the Asset library in Microsoft Dynamics Lifecycle Services by using the **Dynamics Lifecycle Services Asset Upload** task in Azure DevOps. This task is available only in **Releases** pipelines.

This article assumes you have a working knowledge of [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps organization. For more information about how to install an extension for an organization, see [Install extensions](/azure/devops/marketplace/install-extension).

> [!NOTE]
> Versions 1.\*  and lower of the task are obsolete. Update the task version to the latest available.

> [!NOTE]
> (Not required for Version 2.\* and later.) Version 1.\* of the upload task requires availability of the MSAL.PS PowerShell library. A task is available to automatically install the tools during pipeline execution. This task can be added anywhere in the stage before the upload task. For more information, see [Add the MSAL.PS install task to a pipeline](pipeline-lcs-connection-update.md#add-the-msalps-install-task-to-a-pipeline).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Dynamics Lifecycle Services Asset Upload**.

The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
|---|---|---|
| Lifecycle Services Connection | Yes | Select or create a service connection to Lifecycle Services. For more information, see [Create an Lifecycle Services connection in Azure Pipelines](pipeline-lcs-connection.md). |
| Lifecycle Services Project ID | Yes | Enter the ID of the project in Lifecycle Services that contains both the asset to deploy and the target environment. You can find the project ID at the end of the URL of your project's dashboard. |
| Type of asset | Yes | Select the type of asset to upload. |
| File to upload | Yes | Enter the path of the file that you want to upload into the Asset library in Lifecycle Services. |
| Lifecycle Services Asset Name | No | Enter the name to show for the asset in the Asset library. If you don't enter a name here, the file name is used. |
| Lifecycle Services Description | No | Enter the description to show for the asset in the asset details. |
| Wait for Validation | No | For asset types that require validation, use this check box to instruct the task to wait until validation of the asset succeeds or fails. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

