---
# required metadata

title: Reset the financial reporting data mart after restoring a database
description: This topic describes how to reset the financial reporting data mart after restoring a Microsoft Dynamics 365 for Finance and Operations database. 
author: ShylaThompson
manager: AnnBe
ms.date: 08/15/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 261824
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Reset the financial reporting data mart after restoring a database

[!include[banner](../includes/banner.md)]


This topic describes how to reset the financial reporting data mart after restoring a Microsoft Dynamics 365 for Finance and Operations database.

If you ever restore your Finance and Operations database from a backup or copy the database from another environment, you must follow the steps in this topic to ensure that the financial reporting data mart is correctly using the restored Finance and Operations database. 
> [!Note] 
> The steps in this process are supported for Dynamics 365 for Operation May 2016 release (App build 7.0.1265.23014 and financial reporting build 7.0.10000.4) and newer releases. If you have an earlier release of Finance and Operations, contact our Support team for assistance.

## Export report definitions
First, export the report designs located in the Report Designer, using the following steps:

1.  In the Report Designer, go to **Company** &gt; **Building Block Groups**.
2.  Select the building block group to export, and click **Export**. 

    > [!Note] 
    > For Finance and Operations, only one building block group is supported, **Default**.
    
3.  Select the report definitions to export:
    -   To export all your report definitions and the associated building blocks, click **Select All**.
    -   To export specific reports, rows, columns, trees, or dimension sets, click the appropriate tab, and then select the items to export. Press and hold the Ctrl key to select multiple items in a tab. When you select reports to export, the associated rows, columns, trees, and dimension sets are selected.

4.  Click **Export**.
5.  Enter a file name and select a secure location where you want to save the exported report definitions.
6.  Click **Save**.

The file can be copied or uploaded to a secure location, allowing it to be imported into a different environment at another time. Information about using a Microsoft Azure storage account can be found in [Transfer data with the AzCopy Command-Line Utility](/azure/storage/storage-use-azcopy). 
> [!NOTE]
> Microsoft doesn’t provide a storage account as part of your Finance and Operations agreement. You must either purchase a storage account or use a storage account from a separate Azure subscription. 
> [!WARNING]
> Be aware of the behavior of the D drive on Azure Virtual Machines. Do not keep your exported building block groups here permanently. For more information about temporary drives, see [Understanding the temporary drive on Windows Azure Virtual Machines](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/).

## Stop services
Use Remote Desktop to connect to all the computers in the environment and stop the following Windows services by using services.msc:

-   World wide web publishing service (on all AOS computers)
-   Microsoft Dynamics 365 for Finance and Operations Batch Management Service (on non-private AOS computers only)
-   Management Reporter 2012 Process Service (on BI computers only)

These services will have open connections to the Finance and Operations database.

## Reset
### Locate and download the latest MinorVersionDataUpgrade.zip package

Locate the latest MinorVersionDataUpgrade.zip package using the directions found in [Download the latest data upgrade deployable package](..\migration-upgrade\upgrade-data-to-latest-update.md#download-the-latest-data-upgrade-deployable-packages). The directions explain how to locate and download the correct version of the data upgrade package. An upgrade is not required to download the MinorVersionDataUpgrade.zip package. You only need to complete the steps in the “Download the latest data upgrade deployable package” section without performing any of the other steps in the article to retrieve a copy of the MinorVersionDataUpgrade.zip package.

### Execute scripts against Finance and Operations database

Run the following scripts against the Finance and Operations database (not against the financial reporting database).

-   DataUpgrade.zip\\AosService\\Scripts\\ConfigureAxReportingIntegration.sql
-   DataUpgrade.zip\\AosService\\Scripts\\GrantAzViewChangeTracking.sql

These scripts ensure that the users, roles, and change tracking settings are correct.

### Execute PowerShell command to reset database

On the AOS computer, execute the following commands in PowerShell as an Administrator to reset the integration between Finance and Operations and financial reporting:

```
F:
cd F:\MRApplicationService\MRInstallDirectory
Import-Module .\Server\MRDeploy\MRDeploy.psd1
Reset-DatamartIntegration -Reason OTHER -ReasonDetail “<my reason for resetting>”

```
> [!NOTE]
> After executing the commands, you will be asked to enter “Y” to confirm.

Explanation of parameters:

-   The valid values for -Reason are: SERVICING, BADDATA, OTHER.
-   The -ReasonDetail parameter is free text.
-   The reason and reasonDetail will be recorded in telemetry/environment monitoring.

## Start services
Use services.msc to restart the services that you stopped earlier:

-   World wide web publishing service (on all AOS computers)
-   Microsoft Dynamics 365 for Finance and Operations Batch Management Service (on non-private AOS computers only)
-   Management Reporter 2012 Process Service (on BI computers only)

## Import report definitions
Import your report designs from the Report Designer, using the file created during the export:

1.  In the Report Designer, go to **Company** &gt; **Building Block Groups**.
2.  Select the building block group to export, and click **Export**. 

    > [!NOTE]
    > For Finance and Operations, only one building block group is supported, **Default**.
    
3.  Select the **Default** building block and click **Import**.
4.  Select the file containing the exported report definitions and click **Open**.
5.  In the Import dialog box, select the report definitions to import:
    -   To import all the report definitions and the supporting building blocks, click **Select All**.
    -   To import specific reports, rows, columns, trees, or dimension sets, select the reports, rows, columns, trees, or dimension sets to import.

6.  Click **Import**.




