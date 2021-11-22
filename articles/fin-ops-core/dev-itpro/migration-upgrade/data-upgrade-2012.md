---
# required metadata

title: Upgrade from AX 2012 - Data upgrade in development environments
description: This topic explains the end-to-end process for upgrading from Microsoft Dynamics AX 2012 to the latest Finance and Operations development environment.
author: laneswenka
ms.date: 11/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 106163
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2017-05-31
ms.dyn365.ops.version: Platform update 8

---

# Upgrade from AX 2012 - Data upgrade in development environments

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

This is an exciting moment in the upgrade project. The output of this task provides the first upgraded dataset from Microsoft Dynamics AX 2012 to the latest Finance and Operations development environment.

Before you run this process in a shared sandbox environment, we recommend that you run it in a development environment. There are two reasons for this approach:

- It provides local data that developers can write and test their custom data upgrade scripts against.
- It helps reduce the overall time that is spent on iterations of the data upgrade process. In a development environment, an issue can be debugged immediately, code can be adjusted, and the upgrade can be rerun within minutes. However, larger sandbox environments don't allow for this level of agility. In those environments, a minimum of several hours will be required to debug and remediate issues, update code, deploy the updated code, and rerun the upgrade.

We strongly recommend that you run the [Upgrade analyzer](upgrade-analyzer-tool.md) and respond to the issues it identifies before running data upgrade - this will help ensure that your data upgrade is quicker and easier.

## End-to-end data upgrade process

![Data upgrade process.](media/endToEndDataUpgradeProcess.png)

### Back up your AX 2012 database

To back up your AX 2012 database, use the standard Microsoft SQL Server process to produce a BAK file. If you use the compression option when you create the backup, the file size will be smaller, and less time is required in order upload it to and download it from Microsoft Azure Storage.

### Upload the backup to Azure Storage

If your developer environment is hosted as a VM locally or in Azure, you will need to transfer the 2012 database backup to it. With a local VM you may be able to transfer the file directly across the network (if you have configured the virtual network to allow that) but for an Azure hosted VM we recommend that you upload your backup to Azure Storage (using your own secure file transfer service or SFTP is also a valid option). You would need to provide your own Azure storage account for this. There are free tools to help you to move files between Azure storage, from a command line you can use [Azcopy](/azure/storage/storage-use-azcopy), or for a GUI experience you can use [Microsoft Azure storage explorer](https://storageexplorer.com/). Use one of these tools to first upload the backup from your on-premises environment to Azure storage and then on your download it on your development environment.

### Download and restore the backup to the customer-managed development environment

> [!NOTE]
> Developer environments are only supported as customer-managed, [cloud-hosted environments](../dev-tools/access-instances.md). By using cloud-hosted environments, you can increase the drive space so that it meets your own specifications.  

When you restore the backup to the new development environment, don't overwrite the existing AXDB database. Instead, restore the AX 2012 database next to the original databases. You might also consider using drive D for the data and log files, to help improve performance. However, there is a potential downside to using drive D. If the underlying virtual machine (VM) is deallocated in Azure and then reallocated, drive D will be wiped. In practice, this scenario rarely occurs. Therefore, you might find that the risk is acceptable. To learn more about how to use drive D, see [Understanding the temporary drive on Windows Azure Virtual Machines](/archive/blogs/mast/understanding-the-temporary-drive-on-windows-azure-virtual-machines).

To speed up the database restore process, you can change the SQL Server service account to **axlocaladmin**. The restore process can then use instant file initialization. For more information, see [Database Instant File Initialization](/sql/relational-databases/databases/database-instant-file-initialization).

After the database is restored, stop the following services:

- World wide web publishing service
- Dynamics 365 for Finance and Operations Batch Management service
- Management Reporter 2012 Process service
- Microsoft Dynamics Lifecycle Services Diagnostic Service
- Data Import / Export service

Next, rename the original AXDB database **AXDB_orig**. This database might be useful as reference later, when you develop code.
```sql
ALTER DATABASE AXDB SET SINGLE_USER WITH ROLLBACK IMMEDIATE
GO
ALTER DATABASE AXDB MODIFY NAME = AXDB_Orig
GO
ALTER DATABASE AXDB_Orig SET MULTI_USER
GO
```

Finally, rename the newly restored AX 2012 database **AXDB**.

### Run the data upgrade deployable package 

To get the latest data upgrade deployable package for a target environment that is running the latest update, download the latest binary updates from Microsoft Dynamics Lifecycle Services (LCS) Shared asset library.

1. Sign in to [LCS](https://lcs.dynamics.com/).
2. Select the **Shared asset library** tile.
3. In the **Shared asset** library, under **Select asset type**, select **Software deployable package**.
4. In the list of deployable package files, find the data upgrade package that corresponds to your upgrade. For example, if you're upgrading from AX 2012, the package name starts with AX2012DataUpgrade. Select the package that corresponds to the release you are upgrading to. For example: AX2012DataUpgrade-July2017.

For more information, see [Upgrade data in development or demo environments](upgrade-data-to-latest-update.md). 

## Troubleshooting data upgrade script errors

There are options that let you resume the data upgrade where it last stopped. You can also record any data upgrade script errors with call stacks to a table in the database. For development scenarios, you can skip failed scripts and continue to run the upgrade.

For more details, see the [main data upgrade topic](upgrade-data-to-latest-update.md#troubleshoot-upgrade-script-errors).

### Recommendation for the first data upgrade run

When you run the data upgrade against your dataset for the first time, and especially when there many customizations or many custom data upgrade scripts, you might find the [feature to skip failed scripts](upgrade-data-to-latest-update.md) useful. By using this feature, you gain visibility into as many errors as possible in one run. Otherwise, only one critical issue is discovered per run. Be aware that, because dependencies exist between scripts, you might receive errors in related child scripts if you skip the parent script. These errors occur only because the parent wasn't run correctly. They will be resolved when the issue in the parent script is resolved.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
