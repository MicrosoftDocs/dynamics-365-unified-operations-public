---
# required metadata

title: Data upgrade from AX 2012 to Dynamics 365 for Operations in a development environment
description: This topic explains the end-to-end process for upgrading from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 for Operations in a development environment
author: tariqbell
manager: AnnBe
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations, Platform, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 106163
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2017-05-31
ms.dyn365.ops.version: Platform update 8

---

# Data upgrade from AX 2012 to Dynamics 365 for Operations in a development environment

[!include[banner](../includes/banner.md)]

This is an exciting moment in the upgrade project. The output of this task  provides the first upgraded dataset from Microsoft Dynamics AX 2012 in Microsoft Dynamics 365 for Operations.

Before you run this process in a shared sandbox environment, we recommend that you run it in a development environment. There are two main reasons for this approach:

- It provides local data that developers can write and test their custom data upgrade scripts against.
- It helps reduce the overall time that is spent on iterations of the data upgrade process. In a development environment, an issue can be debugged immediately, code can be adjusted, and the upgrade can be rerun within minutes. However, larger sandbox environments don’t allow for this level of agility. In those environments, a minimum of several hours will be required to debug and remediate issues, update code, deploy the updated code, and rerun the upgrade.

## End-to-end data upgrade process

![Data upgrade process](media/endToEndDataUpgradeProcess.png)

### Back up your AX 2012 database

To back up your AX 2012 database, use the standard Microsoft SQL Server process to produce a *.bak file. If you use the compression option when you create the backup, the file size will be smaller, and less time is required in order upload it to and download it from Microsoft Azure Storage.

### Upload the backup to Azure Storage

Upload your backup to Azure Storage. For more information, see UsingStorageExplorer.docx TODO

### Download and restore the backup to the development environment

When you restore the backup to your Dynamics 365 for Operations development environment, don’t overwrite the existing AXDB database. Instead, restore the AX 2012 database next to the original databases. You might also consider using drive D for the data and log files, to help improve performance. However, there is a potential downside to using drive D. If the underlying virtual machine (VM) is deallocated in Azure and then reallocated, drive D will be wiped. In practice, this scenario rarely occurs. Therefore, you might find that the risk is acceptable. To learn more about how to use drive D, see [Understanding the temporary drive on Windows Azure Virtual Machines](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/).

To speed up the database restore process, you can change the SQL Server service account to **axlocaladmin**. The restore process can then use instant file initialization. For more information, see [Database Instant File Initialization](https://docs.microsoft.com/en-us/sql/relational-databases/databases/database-instant-file-initialization).

After the database is restored, stop the following services:

- World wide web publishing service
- Dynamics 365 for Operations Batch Management service
- Management Reporter 2012 Process service

Next, rename the original AXDB database **AXDB_orig**. This database might be useful as reference later, when you develop code.

Finally, rename the newly restored AX 2012 database **AXDB**.

### Run the data upgrade

Run the data upgrade deployable package as described in [Upgrade data in development, demo, or sandbox environments](https://docs.microsoft.com/en-gb/dynamics365/operations/dev-itpro/migration-upgrade/upgrade-data-to-latest-update).

## Troubleshooting data upgrade script errors

There are options that you let you resume the data upgrade where it last stopped. You can also record any data upgrade script errors with call stacks to a table in the database. For development scenarios, you can skip failed scripts and continue to run the upgrade.

For more details, see the [main data upgrade topic](https://docs.microsoft.com/en-gb/dynamics365/operations/dev-itpro/migration-upgrade/upgrade-data-to-latest-update#troubleshoot-upgrade-script-errors).

### Recommendation for the first data upgrade run

When you run the data upgrade against your dataset for the first time, and especially when there many customizations or many custom data upgrade scripts, you might find the [feature to skip failed scripts](https://docs.microsoft.com/en-gb/dynamics365/operations/dev-itpro/migration-upgrade/upgrade-data-to-latest-update) useful. By using this feature, you gain visibility into as many errors as possible in one run. Otherwise, only one critical issue is discovered per run. Be aware that, because dependencies exist between scripts, you might receive errors in related child scripts if you skip the parent script. These errors occur only because the parent wasn’t run correctly. They will be resolved when the issue in the parent script is resolved.
