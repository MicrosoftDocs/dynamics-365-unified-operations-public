---
# required metadata

title: Process for upgrading a sandbox environment
description: This topic describes the steps for deploying an upgrade to a non-production sandbox or stand-alone sandbox environment. 
author: MargoC
manager: AnnBe
ms.date: 06/20/2017
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
ms.search.scope: Operations, Platform, UnifiedOperations
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

[!include[upgrade banner](../includes/upgrade-banner.md)]

This topic describes the steps for performing a data upgrade to a Tier 2 or higher sandbox environment.

In some environments the Microsoft Service Engineering Team (DSE) will execute the data upgrade for you, for more information see the end to end upgrade process here: [Overview of moving to the latest update of Microsoft Dynamics 365 for Finance and Operations](upgrade-latest-update.md#scenario-3-upgrade-to-the-most-current-application-update).

## Prerequisites
If you have any customizations or ISV solutions you must have already completed [code upgrade](upgrade-latest-update.md#scenario-2-upgrade-your-custom-code) and have your upgraded deployable packages ready in your asset library in Lifecycle Services. We strongly recommend that you perform the data upgrade on a development environment before upgrading in a sandbox environment. It is much faster to make corrections and re-run the process in a development environment, so you can reduce the overall time to upgrade by working in a development environment first.

## Export the database
Follow the steps in this article to export the database to a bacpac file from the existing sandbox environment you wish to upgrade: [Copy a Finance and Operations database to restore later](../database/copy-operations-database.md).

#### Additional steps for Management Reporter

Export your report designs, known as building block groups, from the Report Designer. Transfer the exported file to a secure location so that you can use it later to reimport the report definitions. Detailed instructions for exporting: [Building block](https://msdn.microsoft.com/en-us/library/dn464326.aspx#Exportabuildingblockgroup). You can take this file and copy or upload it to secure location such that it may be imported into a different environment at another time. See [Upload the file to an Azure storage account, by using the AzCopy Command-Line Utility.](https://azure.microsoft.com/en-gb/documentation/articles/storage-use-azcopy/) **Note:** Microsoft doesn’t provide a storage account as part of your Finance and Operations agreement. You must either purchase a storage account or use a storage account from a separate Azure subscription. **Important:** Be aware of the behavior of the D drive on Azure Virtual Machines, do not keep your exported building block groups here permanently unless you are prepared to lose them. For details see: [Understanding the temporary drive on Windows Azure virtual machines (blog post)](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/).

## Redeploy sandbox environment
In your Lifecycle Services implementation project:

1.  Locate the sandbox environment that you wish to upgrade and delete it.
    1.  Click Deallocate on the toolbar in the Environment page. After a few minutes the environment status will change to Deallocated
    2.  Click Delete on the toolbar and type the environment name to confirm deletion. After a few minutes the environment will be deleted

2.  In the main LCS Project page, in the Environments pane, the deleted environment will display the options to request a deployment – click and request the environment to be deployed with the new version and select your upgraded custom deployable packages from your asset library to be deployed to the environment.

## Import the database
Follow the steps in this article to import the database from a bacpac file into the newly redeployed sandbox environment: [Copy a Finance and Operations database to restore later](../database/copy-operations-database.md).

## Run the data upgrade package
Execute the data upgrade as described in this article: [Upgrade data in development, demo or sandbox environments.](upgrade-data-to-latest-update.md)

## Update additional components
There may be additional components in use in your environment which require further steps to upgrade.

#### Additional steps for Management Reporter

Reset the management reporter database by following the steps in this topic [Resetting the financial reporting data mart after restoring a database](../analytics/reset-financial-reporting-datamart-after-restore.md) and then reimport the building block groups you exported in an earlier step.

## Limitations
Existing document handling documents which are stored in Azure blob storage will be lost during this upgrade process. If you have custom code which utilises the X++ class FileUpload to place files in blob storage, these documents will also be lost.



