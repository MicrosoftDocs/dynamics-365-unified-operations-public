---
title: Troubleshoot development environments during upgrade 
description: Access troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) Tier-1 development environments.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 04/26/2022
ms.reviewer: johnmichalakffin
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
ms.service: dynamics-365-op
---

# Troubleshoot development environments during upgrade

[!include[banner](../includes/banner.md)]

This article provides troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) Tier-1 development environments.

## Scenario 1: The data upgrade is running slowly on the Tier-1 development environment.

**Solution**

Ensure your Cloud Hosted Environment is a suitabily scaled Azure VM SKU, and that you use premium storage when you deploy the virtual machine (VM) from Microsoft Dynamics Lifecycle Services (LCS).

## Scenario 2: Log files on Dynamics AX 2012 SQL database AX fill up the disk.

**Solution**

Set the recovery mode on the database to **Simple**. Esnure you have enough free disck space for the upgrade database to grow.

## Scenario 3: A "Failed to create a session" error is generated during a prerequisite step.

During the additive or partial synchronization that is done as part of the prerequisite steps for the upgrade, you might receive an error that resembles the following example in the downloaded synchronization log:

> Stopped DBSync monitoring. Microsot.Dynamics.Ax.Xpp.ErrorException: Failed to create a session; confirm that the user has the proper privileges to log on to Microsoft Dynamics 365 Finance.

**Possible causes**

- There might be a customization to extend the **Application** or **Info** classes, and that customization might cause Application Object Server (AOS) to stop responding.
- There might be old or corrupted sessions in the **SysClientSessions** table.

**Solution**

1. Make sure that the custom code base for the "customer validate" customization extensions around the **Application** or **Info** classes works against a demo database.
2. Truncate the records from the **SysClientSessions** table by using the following SQL command, and then try again.

    ```SQL
    TRUNCATE TABLE SYSCLIENTSESSIONS;
    ```

## Scenario 4: Running upgrade deployable package you get error "The term 'new' is not recognized as the name of a cmdlet"

Whilst running the upgrade depployable package on a Cloud Hosted Environment or VHD, you get the following error:

```
GlobalUpdate script for service mode: AOSService on machine: localhost
perform data upgrade, sync AX database and deploy SSRS report
The term 'new' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling...
```
**Cause**
The cause is due to a missing environment variable that the PowerShell script **AutoDataUpgradeOperations.ps1** references.

**Solution**
1. Click on the Windows Icon, and type Environment Variables, select the Edit the system environment variables form.
2. Click the **Environment Variables...** button
3. Add in to the user variables the following if it doesn't exist. NOTE! Edit value to you service drive, for VHDs this is **C:**, for Cloud Hosted Environments it is normall **J:**. The drive letter is the drive that has the AOSService folder in. 

   Variable Name: SERVICEDRIVE

   Variable Value: C:

4. Click OK and OK to close all windows.
5. You'll need to open a new PowerShell prompt again to ensure the new environment variable is loaded into the session. 
6. Start the run book again using the -rerunstep option.


