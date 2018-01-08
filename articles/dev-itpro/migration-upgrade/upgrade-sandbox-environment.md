---
# required metadata

title: Process for upgrading a sandbox environment
description: This topic describes the steps for deploying an upgrade to a non-production sandbox or standalone sandbox environment. 
author: tariqbell
manager: AnnBe

ms.date: 11/20/2017

ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 269234
ms.assetid: feb8ca24-e86d-4101-b77f-c04137e176d0
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Process for upgrading a sandbox environment

[!include[banner](../includes/banner.md)]

This topic describes the steps for performing a data upgrade to a Tier 2 or higher sandbox environment.

In some environments, the Microsoft Service Engineering Team (DSE) will run the data upgrade for you. For more information, see the end-to-end upgrade process in [Overview of moving to the latest update of Microsoft Dynamics 365 for Finance and Operations](upgrade-latest-update.md#scenario-3-upgrade-to-the-latest-application-release).

## Prerequisites

If you have any customizations or any solutions from independent software vendors (ISVs), you must complete a [code upgrade](upgrade-latest-update.md#scenario-2-upgrade-your-custom-code) before you begin. Your upgraded deployable packages must also be ready in your Asset library in Microsoft Dynamics Lifecycle Services (LCS).

We strongly recommend that you do the data upgrade in a development environment before you upgrade in a sandbox environment. It's much faster to make corrections and rerun the process in a development environment. Therefore, by working in a development environment first, you can reduce the overall time that is required for the upgrade.

## Export the database

Export the database from the existing sandbox environment that you want to upgrade to a bacpac file. For more information, see [Copy a Finance and Operations database to restore later](../database/copy-operations-database.md).

### Additional steps for Management Reporter

Export your report definitions, or building block groups, from the Report designer. Then move the exported file to a secure location, so that you can use the file later to reimport the report definitions. For more information, see [Building block group](https://msdn.microsoft.com/en-us/library/dn464326.aspx#Exportabuildingblockgroup). By copying or uploading the exported file to a secure location, you can import it into a different environment later. For more information, see [Transfer data with the AzCopy on Windows](https://azure.microsoft.com/en-gb/documentation/articles/storage-use-azcopy/).

> [!NOTE]
> Microsoft doesn't provide a storage account as part of your agreement for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. You must either purchase a storage account or use a storage account from a separate Microsoft Azure subscription.

> [!IMPORTANT]
> Be aware of the behavior of drive D on Azure virtual machines (VMs). Don't try to permanently store your exported building block groups on drive D, because you might lose them. For more information, see the [Understanding the temporary drive on Windows Azure Virtual Machines](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/) blog post.

## Redeploy the sandbox environment

In your LCS implementation project, follow these steps.

1. Find the sandbox environment that you want to upgrade, and delete it.

    1. On the **Environment** page, select **Deallocate**. After a few minutes, the environment status is updated to **Deallocated**.
    2. Select **Delete**, and then enter the environment name to confirm deletion. After a few minutes, the environment is deleted.

2. On the main LCS project page, in the **Environments** section, the deleted environment shows options for requesting a deployment. Select an option, and request that a new version be deployed in the environment. Select the upgraded custom deployable packages in your Asset library as the packages that should be deployed in the environment.

## Import the database

Import the database from a bacpac file into the newly redeployed sandbox environment. For more information, see [Copy a Finance and Operations database to restore later](../database/copy-operations-database.md).

## Run the data upgrade package

Run the data upgrade by following the steps in [Upgrade data in development, demo or sandbox environments](upgrade-data-to-latest-update.md).

## Update additional components

If any additional components are used in your environment, you might have to complete additional steps to upgrade them.

### Additional steps for Management Reporter

Reset the Management Reporter database by following the steps in [Resetting the financial reporting data mart after restoring a database](../analytics/reset-financial-reporting-datamart-after-restore.md). Then reimport the building block groups that you exported earlier.

## Limitations

During this upgrade process, you will lose any existing document handling documents that are stored in Azure blob storage. (When a sandbox database is imported, the documents aren't brought over.) If you have custom code that uses the X++ **FileUpload** class to put documents in blob storage, you will also lose those documents.
