---
title: Debug data upgrade scripts 
description: Learn how to debug data upgrade scripts for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) Tier-1 development environments.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 11/08/2024
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
ms.service: dynamics-365-op
---

# Debug data upgrade scripts 

[!include[banner](../includes/banner.md)]

This article provides guidance on how to debug data upgrade scripts.

## Background
During the presync and post-sync steps of the data upgrade, a high number of upgrade class methods are scheduled and run in batch. These methods can be scheduled to execute once, for global scripts, or multiple times for each legal entity. The data upgrade methods are used to transform and update the table data from Microsoft AX 2012 to the version of Dynamics 365 finance and operations you're upgrading to. 

Occasionally, during an upgrade you may experience that the data method has errors. Errors can be due to data quality issues in the source AX 2012 database. Customizations and data from earlier versions of AX 2012 or prior releases can cause these symptoms. 

If the upgrade failed, the errors for the presync and post-sync jobs can be checked by using the following SQL statement:
```SQL
--Shows upgrade jobs that were in error, including error messages
select * from RELEASEUPDATESCRIPTSERRORLOG
```
Depending on the error message, you may need to debug the class method during the upgrade testing to determine the cause. For more information on how to monitor the upgrade, see: [Monitor the upgrade](monitor-upgrade.md)

## Debugging steps
To debug a presync or post-sync upgrade class\method, follow these steps:
1. Open Visual Studio on the development virtual machine (Cloud Hosted Environment or VHD) where you're running the data upgrade. For more information, see [Upgrade from AX 2012 - Data upgrade in development environments]( data-upgrade-2012.md)
2. Create a new empty Dynamics 365 finance and operations solution. This helps when debugging and drilling into sub methods. You don’t need to add any objects to the solution and project.
3. Select the Dynamics 365 menu, and select **Options**. Under the **Dynamics 365 > Debugging**, select the following options:
   - Debug items in the solution and items in specific packages. Limiting the number of items being debugged provides a better debugging experience.
   - Include packages [Models] – (Select all)
4. From the Application explorer, locate and open the class and method you need to debug and set break points as required.
5. Go to **Debug**, select **Attach To Process**, and set the following.
   - Check the **Show processes for all users**.
   - Enter **DataUpgradeBatch.exe** in the filter.
   - Check **Automatic refresh**.
6. Open a PowerShell prompt and change the path to the folder where you're running the Data Upgrade deployable package.
7. Rerun the failed data upgrade runbook. For more information, see [Rerun the runbook after a failure](data-upgrade-2012.md#rerun-the-runbook-after-a-failure)
8. When the data upgrade runbook has resumed, go back to your Visual Studio session, and monitor the processes in the **Attach to Process** window. Attach to the **DataUpgradeBatch.exe** as soon as you see it appear. 
   > [!NOTE]
   > You need to attach quickly to avoid missing the point in the pre-sync/post-sync batch process step where the class is executed. Otherwise, you might not hit the breakpoint. You may also need to disable the **Automatic Refresh** option and manually click the **Refresh** button to ensure you capture the start of the batch executable. 
9. You should then hit the breakpoint(s) set, and begin debugging. 

