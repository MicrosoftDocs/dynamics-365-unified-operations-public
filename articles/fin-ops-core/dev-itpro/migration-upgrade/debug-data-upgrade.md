---
title: Debug data upgrade scripts
description: Learn how to debug data upgrade scripts for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) Tier-1 development environments.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 11/18/2024
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
ms.service: dynamics-365-op
---

# Debug data upgrade scripts 

[!include[banner](../includes/banner.md)]

This article provides guidance about how to debug data upgrade scripts.

## Background

During the PreSync and PostSync steps of a data upgrade, a large number of upgrade class methods are scheduled and run in batch mode. Those methods can be scheduled to run once in the case of global scripts or multiple times for each legal entity. The data upgrade methods are used to transform and update the table data from Microsoft AX 2012 to the version of Dynamics 365 finance and operations apps that you're upgrading to.

Occasionally, during an upgrade, you might find that the data method has errors. Errors can be the result of data quality issues in the source AX 2012 database. Customizations and data from previous versions of AX 2012 or earlier releases can cause these symptoms.

If an upgrade fails, you can use the following SQL statement to review the errors for the PreSync and PostSync jobs.

```SQL
--Shows upgrade jobs that were in error, including error messages
select * from RELEASEUPDATESCRIPTSERRORLOG
```

Depending on the error message, you might have to debug the class method during upgrade testing to determine the cause. Learn how to monitor an upgrade in [Monitor the upgrade](monitor-upgrade.md).

## Debugging steps

To debug a PreSync or PostSync upgrade class/method, follow these steps.

1. On the development virtual machine (VM) where you're running the data upgrade, open Visual Studio. (The VM can be in a cloud hosted environment or on a virtual hard disk \[VHD\].) Learn more in [Upgrade from AX 2012 - Data upgrade in development environments]( data-upgrade-2012.md).
2. Create a new, empty Dynamics 365 finance and operations solution. This step is useful when you debug and drill into sub-methods. You don't have to add any objects to the solution and project.
3. On the **Dynamics 365** menu, select **Options**. Then, under **Dynamics 365** \> **Debugging**, select the following options:

    - Debug the items in the solution and in specific packages. Limiting the number of items being debugged provides a better debugging experience.
    - Include packages \[Models\] – select all.

4. In Application Explorer, find and open the class and method that you must debug, and set break points as required.
5. Go to **Debug**, select **Attach To Process**, and set the following values:

    - Select the **Show processes for all users** checkbox.
    - Enter **DataUpgradeBatch.exe** in the filter.
    - Select the **Automatic refresh** checkbox.

6. Open a PowerShell prompt, and change the path to the folder where you're running the Data Upgrade deployable package.
7. Rerun the data upgrade runbook that failed. Learn more in [Rerun the runbook after a failure](data-upgrade-2012.md#rerun-the-runbook-after-a-failure).
8. After the data upgrade runbook resumes, go back to your Visual Studio session, and monitor the processes in the **Attach to Process** window. As soon as **DataUpgradeBatch.exe** appears, attach to it.

    > [!IMPORTANT]
    > You must attach quickly to avoid missing the point in the PreSync/PostSync batch process step where the class is run. Otherwise, you might not hit the breakpoint. You might also have to disable the **Automatic Refresh** option and manually select the **Refresh** button to ensure that you capture the start of the batch executable file.

9. You should hit the breakpoints that you set. You can then begin debugging.
