---
title: Update LCS Connection authentication tasks to MSAL in Azure Pipelines
description: Learn about how to update Azure Pipelines so that it uses the Microsoft Authentication Library (MSAL) for authentication.
author: pathaku
ms.author: pathaku
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 10/23/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0
---

# Update LCS Connection authentication tasks to MSAL in Azure Pipelines

By default, new versions of the Microsoft Azure DevOps tasks for Dynamics 365 support the [Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-overview#languages-and-frameworks) and use it by default for authentication. To support these new versions, the MSAL PowerShell libraries (MSAL.PS) must be installed on any agent that runs the tasks. For self-hosted agents, the MSAL.PS library can be [manually installed from the PowerShell Gallery](https://github.com/AzureAD/MSAL.PS/#msalps). For any agent, including agents that are hosted in Azure DevOps, Microsoft provides a task that installs the MSAL.PS library for you every time that the pipeline is run.

## Update existing service connections

For existing service connections, the **Authentication Endpoint** setting must be updated to `https://login.microsoftonline.com/organizations`. If you're using a national cloud, see [National clouds](/azure/active-directory/develop/authentication-national-cloud) to find your relevant endpoint. The correct authentication endpoint will be set by default when you create a new service connection. The setting must be updated only for national clouds.

For more information about how to set up a connection, see [Create an LCS connection in Azure Pipelines](pipeline-lcs-connection.md).

## Add the MSAL.PS install task to a pipeline

To add the MSAL.PS install task to the build of your YML or Classic pipeline, search the task list for **Install MSAL.PS to enable authentication**. There are no options or settings for this task. Make sure that this install task is run on every agent before you run any task that requires authentication with Microsoft Dynamics Lifecycle Services (LCS),

> [!NOTE]
> The MSAL.PS libraries must be installed on every agent that runs tasks that require authentication with LCS. If your pipeline consists of multiple stages, each stage might be run on a different agent. Therefore, each stage must ensure that the libraries are installed.

## Update existing tasks

To update the existing tasks so that they use the new MSAL authentication, you must update the task versions. For more information about how to update task versions, see [Task types & usage](/azure/devops/pipelines/process/tasks?view=azure-devops). The following table shows the tasks that use authentication. It also shows the earliest version of each task that uses MSAL.

| Task name | Minimum version that uses MSAL |
| --- | --- |
| [Dynamics Lifecycle Services (LCS) Asset Download](pipeline-asset-download.md) | 1.\* or later |
| [Dynamics Lifecycle Services (LCS) Asset Upload](pipeline-asset-upload.md) | 1.\* or later |
| [Dynamics Lifecycle Services (LCS) Asset Deployment](pipeline-deploy-asset.md) | 2.\* or later |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
