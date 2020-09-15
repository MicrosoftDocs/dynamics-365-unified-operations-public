---
# required metadata

title: Download assets by using Azure Pipelines
description: This topic explains how you can download assets from the Asset library in Microsoft Dynamics Lifecycle Services (LCS) by using Azure Pipelines.
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

# Download assets by using Azure Pipelines

You can automate the download of assets from the Asset library in Microsoft Dynamics Lifecycle Services (LCS) by using the **Deploy Lifecycle Services (LCS) Asset Download** task in Azure DevOps.

This topic assumes that you have a working knowledge of [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](https://docs.microsoft.com/azure/devops/marketplace/install-extension).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Dynamics Lifecycle Services (LCS) Asset Download**.

The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
|---|---|---|
| LCS Connection | Yes | Select or create a service connection to LCS. For more information, see [Create an LCS connection in Azure Pipelines](pipeline-lcs-connection.md). |
| LCS Project ID | Yes | Enter the ID of the project in LCS that contains both the asset to deploy and the target environment. You can find the project ID at the end of the URL of your project's dashboard. |
| Path to download to | Yes | Enter the path to download the asset to. |
| Search Pattern | Yes | Select the type of search pattern that should be used to find the asset in the Asset library in LCS. Depending on the value that you select, the following options are available:<ul><li>**Asset ID (guid)** – If you select this value, in the **LCS File Asset Id(s)** field, enter the asset ID or a semicolon-separated list of asset IDs. Asset IDs are globally unique identifiers (GUIDs).</li><li>**Name** – If you select this value, in the **LCS File Asset Type** field, select the asset type. Then, in the **LCS File Asset Name** field, specify the name to search for. You can use an asterisk (\*) as a wildcard character in the name. For example, you might enter **MyPackage\***.</li></ul> |

After a successful download, an output variable can be used to capture a list of the file paths. If there are multiple files, a semicolon-separated list of file paths is assigned to the output variable. For more information about output variables in Azure DevOps, see [Use output variables from tasks](https://docs.microsoft.com/azure/devops/pipelines/process/variables#use-output-variables-from-tasks).
