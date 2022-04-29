---
# required metadata

title: Move environments between data centers
description: This topic explains how to move environments that are managed by Microsoft to a different Microsoft Azure data center.
author: ClaudiaBetz-Haubold 
ms.date: 04/29/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
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

Occasionally, you must move environments that are managed by Microsoft to a different Microsoft Azure data center. Here are some scenarios where this move might be required:

- The data center that you planned to use wasn't available when the environments were originally deployed.
- The project creators didn't do enough research to determine the best data center before the environments were originally deployed.
- The customer moves the physical location of its operations, and the wide area network (WAN) connection is now closer to a data center that provides lower latency.

Microsoft asks that you keep all your environments in the same data center. When you move environments to a different data center, you should plan to eventually have all environments deployed in the same data center.

You can verify the data center that an environment is deployed to on the **Manage environments** page in Microsoft Dynamics Lifecycle Services (LCS).

To change the data center, you must redeploy all environments. The process differs for sandbox environments (sandbox standard acceptance test environments, and sandbox develop and test environments) and production environments.

## Move sandbox environments

Because this move is a self-service action, the partner and/or customer must move the existing sandbox environments without Microsoft involvement. Although this action requires little effort on the part of the partner or customer resources, completion of the end-to-end process might require a few days. To streamline the data movement between environments, you should develop a plan to determine the best sequence before you begin the move.

### Save data

Before you begin the move, you must save your data.

- **Tier 1 environment database that is based on Microsoft SQL Server:** Make a backup of the database.
- **Tier 2 and higher environments that are based on Azure SQL Database:** Choose one of the following options:

    - **Option 1:** Review the processes that are listed in the [Database movement operations home page](../../dev-itpro/database/dbmovement-operations.md) topic.
    - **Option 2:** If you have an Azure subscription, save a copy of the Azure SQL database under that subscription.
    - **Option 3:** If you have multiple Azure SQL database environments, redeploy one environment, leave the remaining environments in the old data center, and then request a database refresh between the environments.
    - **Option 4:** Save data as data packages, and then import the packages after the redeployment is completed.

### Move the environments

After you've saved your data, follow these steps.

1. Verify that all code packages have been uploaded to the Asset library in LCS.
2. For each environment, follow these steps:

    1. In LCS, select **Full details**.
    2. Stop the environment, and then, when the environment has stopped, select **Deallocate**.
    3. After the deallocation is completed, select **Delete**.
    4. After the environment is deleted, select **Configure** to redeploy the environment.
    5. In the **Geography/location** field, select the data center to use.
    6. After the environment is deployed, apply the code packages.
    7. If the redeployed environment is used as the build environment, complete the required configurations that are described in [Deploy and use an environment that supports continuous build and test automation](../../dev-itpro/perf-test/continuous-build-test-automation.md).
    8. Restore the data.

> [!NOTE]
> - The movement of files that are stored in Azure Blob Storage isn't supported in sandbox environments.
> - Commerce customers should be aware that extra steps are required for components to work correctly after a move. For more information, see [Data management overview](../../dev-itpro/data-entities/data-entities-data-packages.md).

## Move production environments

If you already have a production environment deployed, you must open a Support request to move the production environment to another data center after you've finished moving all the sandbox environments. This scenario is rare, and there is no automated/self-service action to complete the move. In this scenario, files that are stored in Azure Blob Storage will also be moved. For information about the maintenance window and downtime that are required in order to move a production environment to a different data center, see [Service Description](https://go.microsoft.com/fwlink/?LinkId=867755&clcid=0x409) and the related service-level agreement (SLA) documents.

> [!NOTE]
> There are several LCS instances available to enable the [Sovereign and local cloud deployment options](../../dev-itpro/deployment/deployment-options-geo.md). Movement of production environments between these different LCS instances is not supported. 
 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
