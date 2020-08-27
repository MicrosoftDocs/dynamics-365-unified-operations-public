--- 
# required metadata 
 
title: ER Upload a configuration into Lifecycle Services
description: The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration and upload it into Microsoft Lifecycle Services (LCS). 
author: NickSelin
manager: AnnBe 
ms.date: 08/27/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, ERDataModelDesigner, ERDataModelContentsItemCreationDialog, ERSolutionRepositoryTable, ERSolutionRepositoryCreateDropDialog, ERSolutionImport   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# ER Upload a configuration into Lifecycle Services

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new [Electronic reporting (ER) configuration](../general-electronic-reporting.md#configuration) and upload it into the [project-level asset library](../../lifecycle-services/asset-library.md) of Microsoft Lifecycle Services (LCS).

In this example, you will create a configuration and upload it to LCS for sample company, Litware, Inc. These steps can be performed in any company as ER configurations are shared among companies. To complete these steps, you must first complete the steps in the procedure, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). Access to LCS is also required to complete these steps.

1. Sign in to the application by using one of the following roles:
    - Electronic reporting developer
    - System administrator
2. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
3. Select **Litware, Inc.** and mark it as **Active**.
4. Click **Configurations**.

<a name="accessconditions"></a>
> [!NOTE]
> Make sure that the current Dynamics 365 Finance user is a member of the LCS project that contains the [asset library](../../lifecycle-services/asset-library#asset-library-support.md) for importing ER configurations.

> [!NOTE]
> You can't access an LCS project from an ER repository that represents a different domain than the domain used in Finance. If you do try this, an empty list of LCS projects will be shown and you won't be able to import ER configurations from the LCS project-level asset library. To access LCS project-level asset libraries from an ER repository for importing ER configurations, sign in to the Finance application with the credentials of a user that belongs to the tenant (domain) for which the current Finance instance has been provisioned.

## Create a new data model configuration
1. Click Create configuration to open the drop dialog.
    * You will create a configuration that contains a sample data model for electronic documents. This data model configuration will be uploaded into LCS later.  
2. In the Name field, type 'Sample model configuration'.
    * Sample model configuration  
3. In the Description field, type 'Sample model configuration'.
    * Sample model configuration  
4. Click Create configuration.
5. Click Model designer.
6. Click New.
7. In the Name field, type 'Entry point'.
    * Entry point  
8. Click Add.
9. Click Save.
10. Close the page.
11. Click Change status.
12. Click Complete.
13. Click OK.

## Register a new  repository
1. Close the page.
2. Click Repositories.
    * This enables you to open the list of repositories for the Litware, Inc. configuration provider.  
3. Click Add to open the drop dialog.
    * This allows you to add a new repository.  
4. In the Configuration repository type field, select LCS.
5. Click Create repository.
6. In the Project field, enter or select a value.
    * Select the desired LCS project. You must have [access](#accessconditions) to the project.  
7. Click OK.
    * Complete a new repository entry.  
8. In the list, mark the selected row.
    * Select the LCS repository record.  
    * Note that a registered repository is marked by the current provider meaning that the only configurations owned by that provider can be placed to this repository and, consequently, uploaded into the selected LCS project.  
9. Click Open.
    * Open the repository to view the list of ER configurations. It will be empty if this project has not yet been used for ER configurations sharing.  
10. Close the page.
11. Close the page.

## Upload configuration into LCS
1. Click Configurations.
2. In the tree, select 'Sample model configuration'.
    * Select a created configuration that has been already completed.  
3. In the list, find and select the desired record.
    * Select the version of the selected configuration with the status of 'Completed'.  
4. Click Change status.
5. Click Share.
    * The configuration status will change from 'Completed' to 'Shared' when it is published in LCS.  
6. Click OK.
7. In the list, find and select the desired record.
    * Select the configuration version with the status of 'Shared'.  
    * Note that the status of the selected version has changed from 'Completed' to 'Shared'.  
8. Close the page.
9. Click Repositories.
    * This enables you to open the list of repositories for the Litware, Inc. configuration provider.  
10. Click Open.
    * Select the LCS repository and open it.  
    * Note that the selected configuration is shown as an asset of the selected LCS project.  
11. Open LCS using https://lcs.dynamics.com.
    * Open a project that was used earlier for repository registration.
    * Open the 'Asset library' of this project.
    * Expand the content of the 'GER configuration' asset type – the uploaded ER configuration will be available.
    * Note that the uploaded LCS configuration can be imported to another instance if providers have access to this LCS project.  
