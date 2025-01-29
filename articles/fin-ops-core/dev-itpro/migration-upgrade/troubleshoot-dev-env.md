---
title: Troubleshoot development environments during upgrade 
description: Access troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) Tier-1 development environments.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 08/08/2024
ms.reviewer: johnmichalak
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

Ensure that your cloud-hosted environment is a suitably scaled Azure virtual machine (VM) stock keeping unit (SKU). Also ensure that you use premium storage when the VM is deployed from Microsoft Dynamics Lifecycle Services.

## Scenario 2: Log files on Dynamics AX 2012 SQL database AX fill up the disk.

**Solution**

Set the recovery mode on the database to **Simple**. Confirm that there's enough free disk space for the upgrade database to grow.

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

## Scenario 4: When you run the upgrade deployable package, you receive the following error: "The term 'new' is not recognized as the name of a cmdlet."

When you run the upgrade deployable package on a cloud-hosted environment or virtual hard disk (VHD), you receive the following error:

> GlobalUpdate script for service mode: AOSService on machine: localhost  
> perform data upgrade, sync AX database and deploy SSRS report  
> The term 'new' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling...

**Cause**

An environment variable that the *AutoDataUpgradeOperations.ps1* PowerShell script references is missing.

**Solution**

1. In Windows, select **Start**, enter *Environment Variables* in the search field, and then select to open **Edit the system environment variables**.
2. In the **System Properties** dialog box, select **Environment Variables**.
3. In the upper half of the **Environment Variables** dialog box, select **New** to add the following user variable if it doesn't already exist.

    - **Variable name:** *SERVICEDRIVE*
    - **Variable value:** *C:*

    > [!NOTE]
    > For this environment variable, the **Variable value** field specifies the letter of the drive that has the *AOSService* folder. Edit the value as required for your service drive. For VHDs, it's *C:*. For cloud-hosted environments, it's *J:*.

4. Select **OK**.
5. Select **OK** to close all dialog boxes.
6. Open a new PowerShell prompt to ensure that the new environment variable is loaded into the session.
7. Start the runbook again by using the `-rerunstep` option.
