---
title: Update LCS Connection authentication tasks to MSAL in Azure Pipelines
description: This topic explains how to update Azure Pipelines to use MSAL for authentication.
author: jorisdg
ms.date: 11/30/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.custom:
ms.search.region: Global
ms.author: jorisde
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0
---

# Overview

The Azure DevOps tasks for Dynamics 365 now support and default to using the [Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-overview#languages-and-frameworks) for authentication. To support these new versions, the MSAL PowerShell libraries (MSAL.PS) have to be installed on any agent running these tasks. On self-hosted agents, the MSAL.PS library can be [manually installed from the PowerShell Gallery](https://github.com/AzureAD/MSAL.PS/#msalps). For any agent, including Azure DevOps hosted agents, we've provided a task that installs the MSAL PowerShell library for you every time the pipeline is run.

## Update existing service connections

For any existing service connections, the setting **Authentication Endpoint** has to be updated to `https://login.microsoftonline.com/organizations`. If you're using a national cloud, see [National clouds](/azure/active-directory/develop/authentication-national-cloud) to find your relevant endpoint. When creating a new service connection, the **Authentication Endpoint** will default in correctly, and only needs to be updated for national clouds.

For more information about setting up a connection, see [Create an LCS connection in Azure Pipelines](pipeline-lcs-connection.md).

## Add the MSAL.PS install task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Install MSAL.PS to enable authentication**. There are no options or settings for this task. Ensure this install step is executed on every agent at any time prior to executing a task that requires authentication with LCS.

> [!NOTE]
> Any and all agents executing tasks that require authentication with LCS will require the MSAL.PS libraries to be installed. If your pipeline consists of multiple stages, each stage may be executed on a different agent. This means each stage has to ensure the libraries are installed.

## Update existing tasks

To update the existing tasks to use the new MSAL authentication, the task versions need to be updated. For more information on updating tasks versions, see [Task types & usage](/azure/devops/pipelines/process/tasks?view=azure-devops&tabs=classic#task-versions). The following table lists tasks that use authentication, along with the minimum version of each task that uses MSAL.

| Task name | Minimum version that uses MSAL |
| --- | --- |
| [Dynamics Lifecycle Services (LCS) Asset Download](pipeline-asset-download.md) | 2.* or higher |
| [Dynamics Lifecycle Services (LCS) Asset Upload](pipeline-asset-upload.md) | 1.* or higher |
| [Dynamics Lifecycle Services (LCS) Asset Deployment]()(pipeline-deploy-asset.md) | 1.* or higher |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]