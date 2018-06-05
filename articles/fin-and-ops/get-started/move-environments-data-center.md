---
# required metadata

title: Move environments between data centers
description: 
author: ClaudiaBetz-Haubold 
manager: AnnBe
ms.date: 06/04/2018
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

# Move environments between data centers
[!include [banner](../includes/banner.md)]

There are times when you are required to move Microsoft Dynamics 365 for Finance and Operations environments that are managed by Microsoft to a different Azure data center. Scenarios where this could be required include:

- The data center you planned to use was not available when the environments were initially deployed.
- The project creators did not conduct enough research to determine the best data center before the environments were initially deployed.
- The customer moves the physical location of their operations and in this move the WAN connection is closer to a data center which provides lower latency. 

Microsoft asks that you keep all environments within the same data center. When moving environments to a different data center, plan to have all environments eventually deployed in the same data center.
You can verify the data center that an environment is deployed to in LCS on the **Manage environments** page.

To change the Azure data center, you must redeploy all environments. The process differs between sandbox environments (sandbox, standard acceptance test and sandbox, develop and test environments) and production environments. 

## Move sandbox environments
Because this is a self-service action, the partner and/or customer must move the existing sandbox environments without Microsoft involvement. This activity requires little effort of the partner or customer resources, though it might take a few days to complete end-to-end. To streamline the data movement between environments, prior to starting the move, develop a plan to determine the best sequence.

### Save data
Before you begin the move, you must save your data. 

- Tier 1 environments database (based on Microsoft SQL Server) - Make a backup of the database
- Tier 2 and higher environments (based on Azure SQL Database) - Choose from one of the following options:

  - Option 1: Follow the process described in [Copy a Finance and Operations database from Azure SQL Database to a SQL Server environment](../../dev-itpro/database/copy-database-from-azure-sql-to-sql-server.md) 
  - Option 2: If you have an Azure subscription, save a copy of the Azure SQL database under that subscription.
  - Option 3: If you have multiple Azure SQL database environments, redeploy one environment, leave remaining environments on the old data center, and then request a database refresh between the environments.
  - Option 4: Save data as data packages and then import the packages after the redeployment is complete.

After you have saved your data, complete the following steps.

1. Validate that all code packages have been uploaded to the Asset library in LCS.
2. For each environment: 
  
    a. Click **Full details** in LCS.
    
    b. Stop the environment, and when the environment has stopped, click **Deallocate**.
    
    c. After the deallocation is complete, click **Delete**.
    
    d. When the environment is deleted, click **Configure** to redeploy the environment.
    
    
    e. In the **Geography/location** drop-down, select the data center that you want to use. 
    
    f. After the environment is deployed, apply the code packages. 
    
    g. If the redeployed environment is used as the build environment, complete the required configurations as described in [Deployment with continuous build and test automation](../../dev-itpro/perf-test/continuous-build-test-automation,md). 
    
    h.	Restore the data. 

  > [!NOTE] 
  > Moving files stored in the Azure Blob Storage is not supported in sandbox environments. 
  
  > [!NOTE]
  > Retail customers should be aware that for Retail components to function correctly after the move, extra steps are required. For more information, see [Data management](../../dev-itpro/data-entities/data-entities-data-packages.md).
  

## Move production
If you already have a production environment deployed, you must open a Support request to have it moved to another data center after you have moved all sandbox environments. This is not a common scenario. There is no automated/self-service action to complete this task. In the scenario, files stored in Azure Blob Storage will be moved as well. For the maintenance window and downtime required to move a Production environment to a different data center, see the [Service Description](https://go.microsoft.com/fwlink/?LinkId=867755&clcid=0x409) document and the related SLA documents. 

