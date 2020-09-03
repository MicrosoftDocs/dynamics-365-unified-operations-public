---
# required metadata

title: Downloading assets in Azure Pipelines
description: The topic explains how you can download assets from the LCS asset library using Azure Pipelines.
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

# Asset Download in Azure Pipelines

You can automate downloading assets from the **Lifecycle Services Asset Library** by using the **Deploy Lifecycle Services (LCS) Asset Download** task in Azure DevOps.

This topic assumes a working knowledge of [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](https://docs.microsoft.com/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser).

## Add the task to a pipeline

To add the task to the build of your YML or Classic pipeline, search the task list for **Dynamics Lifecycle Services (LCS) Asset Download**.

The following table describes the options that are available for this task.

| Input name | Mandatory | Description |
| --- | --- | --- |
| LCS Connection | Yes | Select or create a service connection to Dynamics Lifecycle Services (LCS). For more information, see [Creating an LCS connection in Azure Pipelines](pipeline-lcs-connection.md). |
| LCS Project Id | Yes | Enter the project ID identifying the project in LCS that contains both the asset to be deployed, and the target environment. The project ID can be found at the end of the URL of your project's dashboard. |
| Path to download to | Yes | Enter the path to download the asset into. |
| Search Pattern | Yes | Select how to find the assets in the **Asset Library**. |

Depending on the type of **Search Pattern** that you selected, the following options are available.

* When selecting **Asset ID (guid)**, provide a GUID or a semi-colon separated list of GUIDs of asset IDs in the **LCS File Asset Id(s)** field.
* When selecting **Name**, select the asset type from the **LCS File Asset Type** dropdown, and a name to search for in the **LCS File Asset Name** field. You can use a wildcard in the name using the asterisk (*) symbol, for example **MyPackage\***.

After a successful download, a list of the file paths can be captured with an output variable. In case of multiple files, a semi-colon separated list of file paths is assigned to the output variable. For more information about output variables in **Azure DevOps**, see [Use output variables from tasks](https://docs.microsoft.com/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch#use-output-variables-from-tasks)
