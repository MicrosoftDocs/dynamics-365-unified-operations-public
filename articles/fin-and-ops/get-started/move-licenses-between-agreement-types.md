---
# required metadata

title: Move licenses between agreement types
description: 
author: ClaudiaBetz-Haubold 
manager: AnnBe
ms.date: 06/05/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30 
ms.dyn365.ops.version: AX 7.0
---

# Move licenses between agreement types
[!include [banner](../includes/banner.md)]

Sometimes, a customer who initially purchased subscriptions through a Cloud Service Provider (CSP) will decide to change to a Volume Licensing (VL) agreement with Microsoft after the LCS Implementation project has been created. This can happen even after the project has gone live in production. The opposite, though much less common, where a customer who initially purchased the subscriptions through a Volume Licensing (VL) agreement with Microsoft decides to change to a Cloud Service Provider (CSP), is also possible. In the latter case, the change of the agreement has to align with the renewal date of the VL agreement.
While moving subscriptions from one type of agreement to another is primarily a commercial process, the technical implications on the LCS Implementation project are minimal.

  > [!NOTE]
  > Moving subscriptions between agreement types is not the same as an Azure Active Directory (AAD) tenant move. If an AAD tenant move is required in conjunction with the contractual changes of the agreements, you must also follow the process described in the topic, [Move an LCS Implementation project to another Azure Active Directory Tenant](move-lcs-implementation-project-tenant.md). 
  
The three standard environments that come with the subscription (one production environment, one Tier-2 Standard Acceptance Test environment, and one Tier-1 developer environment) are not impacted. Actions in LCS might be required only if the customer has additional add-on environments. If action is required, the activities related to add-on environments require little effort of the partner or customer resources. Plan beforehand to determine the best sequence, specifically to streamline moving data between environments.

## Customer has only default environments
If the customer only has the three standard environments under the Microsoft managed subscription and did not purchase any add-ons through the initial CSP or VL agreement, the necessary activities are purely commercial.
1.	Customer places the order for subscriptions under the new agreement with the VL Reseller or CSP. 
  > [!IMPORTANT]
  > Make sure that the subscriptions are purchased against the same AAD tenant that is used on the original agreement.
2.	Customer activates the subscription. 
3.	Customer validates in the Microsoft Office 365 admin center that the new and existing subscriptioare are active.
4.	Only after validating that new subscriptions are available, request that the Volume Licensing Reseller or CSP suspend the existing subscriptions. There is generally an overlap to ensure continuity and avoid a disruption to service. 

## Customer has add-on environments
If the customer has purchased add-on environments through the initial CSP or VL agreement, those environments must be redeployed. 

### Pre-work
Before you begin the move, you must save your data from your existing environments. 

- Tier 1 environments database (based on Microsoft SQL Server) - Make a backup of the database
- Tier 2 and higher environments (based on Azure SQL Database) - Choose from one of the following options:

  - Option 1: Follow the process described in [Copy a Finance and Operations database from Azure SQL Database to a SQL Server environment](../../dev-itpro/database/copy-database-from-azure-sql-to-sql-server.md) 
  - Option 2: If you have an Azure subscription, save a copy of the Azure SQL database under that subscription.
  - Option 3: If you have multiple Azure SQL database environments, redeploy one environment, leave remaining environments on the old data center, and then request a database refresh between the environments.
  - Option 4: Save data as data packages and then import the packages after the redeployment is complete.

- Validate that all code packages have been uploaded to the Shared asset library in LCS.

### Commercial activities
1.	The customer places the order for the subscriptions, including the add-on environments, under the new agreement with the Volume Licensing Reseller or the CSP.
  > [!IMPORTANT]
  > Make sure that the subscriptions are purchased against the existing AAD tenant.
2.	The customer activates the subscriptions. 
3.	The customer validates in the O365 Admin Portal that the new subscriptions are active in addition to the existing subscriptions.

### Deploy new environments
1. After the new subscriptions are active, additional add-ons that you can configure will show in LCS.  
2. Deploy those new add-ons and configure as appropriate. Apply deployable the packages and restore the data. 

### Delete environments under the obsolete agreement
Complete the following steps for each environment that was deployed under the old agreement. After you have deleted the environments do not use or redeploy them again.
1. In LCS, on the **Environment details** page, click **Full details**.
3. Stop the environment, and when the environment has stopped, click **Deallocate**.
4. When the deallocation is complete, click **Delete**.
5. When the environment is deleted, click **Configure**. 


### Update environments
1. The CSP or Volume Licensing Reseller suspends the existing subscriptions.
2. Any original add-ons no longer appear in LCS.

  > [!IMPORTANT]
  > Existing subscriptions must be kept in an active state in parallel to the new subscriptions until the physical redeployment of the add-on environments has been completed. 
  
  > [!NOTE] 
  > Moving files stored in the Azure Blob Storage is not supported in sandbox environments. 
  
  > [!NOTE]
  > Retail customers should be aware that for Retail components to function correctly after the move, extra steps are required. For more information, see [Data management](../../dev-itpro/data-entities/data-entities-data-packages.md).

