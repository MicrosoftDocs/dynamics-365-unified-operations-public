--- 
# required metadata 
 
title: ER Import a configuration from Lifecycle Services
description: The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can import a new version of an Electronic reporting (ER) configuration from Microsoft Lifecycle Services (LCS). 
author: NickSelin
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  

# optional metadata 

ms.search.form: ERWorkspace, ERSolutionTable,  ERSolutionRepositoryTable, ERSolutionImport   
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

# ER Import a configuration from Lifecycle Services

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can import a new version of an Electronic reporting (ER) configuration from Microsoft Lifecycle Services (LCS).

In this example, you will select the desired version of the ER configuration and import it for sample company, Litware, Inc. These steps can be performed in any company as ER configurations are shared among companies. To complete these steps, you must first complete the steps in the "Upload an ER configuration into Lifecycle Services" procedure. Access to LCS is also required for completion of these steps.

1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Configurations.

## Delete a shared version of data model configuration
1. In the tree, select 'Sample model configuration'.
    * The first version of a sample data model configuration has been created and published to LCS during the "Upload an ER configuration into Lifecycle Services" procedure. In this procedure, you will delete this version of the ER configuration. This version of a sample data model configuration will be imported later from LCS.  
2. In the list, find and select the desired record.
    * Select the version of this configuration that is in the 'Shared' status. This status indicates that the configuration has been published to LCS.  
3. Click Change status.
4. Click Discontinue.
    * Change the status of the selected version from 'Shared' to 'Discontinued' to make it available for deletion.  
5. Click OK.
6. In the list, find and select the desired record.
    * Select the version of this configuration that has a status of 'Discontinued'.  
7. Click Delete.
8. Click Yes.
    * Note that the only draft version 2 of the selected data model configuration is available.  
9. Close the page.

## Import a shared version of data model configuration from LCS
1. In the list, mark the selected row.
    * Open the list of repositories for the 'Litware, Inc.' configuration provider.  
2. Click Repositories.
3. Click Open.
    * Select the LCS repository and open it.  
4. In the list, mark the selected row.
    * Select the first version of the 'Sample model configuration' in the versions list.  
5. Click Import.
6. Click Yes.
    * Confirm the import of the selected version from LCS .  
    * Note that the information message (above the form) confirms the successful completion of the import of the selected version.  
7. Close the page.
8. Close the page.
9. Click Configurations.
10. In the tree, select 'Sample model configuration'.
11. In the list, find and select the desired record.
    * Select the version of this configuration that has a status of 'Shared'.  
    * Note that the shared version 1 of the selected data model configuration is available now as well.  

