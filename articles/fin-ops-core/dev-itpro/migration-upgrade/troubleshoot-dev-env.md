---
# required metadata

title: Troubleshoot development environments during upgrade 
description: This topic provides troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) Tier-1 development environments.
author: ttreen 
ms.date: 04/26/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Troubleshoot development environments during upgrade

[!include[banner](../includes/banner.md)]

This topic provides troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises) Tier-1 development environments.

## Scenario 1: The data upgrade is running slowly on the Tier-1 development environment.

**Solution**

Use premium storage when you deploy the virtual machine (VM) from Microsoft Dynamics Lifecycle Services (LCS).

## Scenario 2: Log files on Dynamics AX 2012 SQL database AX fill up the disk.

**Solution**

Set the recovery mode on the database to **Simple**.

## Scenario 3: A "Failed to create a session" error is generated during a prerequisite step.

During the additive or partial synchronization that is done as part of the prerequisite steps for the upgrade, you might receive an error that resembles the following example in the downloaded synchronization log:

> Stopped DBSync monitoring. Microsot.Dynamics.Ax.Xpp.ErrorException: Failed to create a session; confirm that the user has the proper privileges to log on to Microsoft Dynamics 365 for Finance and Operations.

**Possible causes**

- There might be a customization to extend the **Application** or **Info** classes, and that customization might cause Application Object Server (AOS) to stop responding.
- There might be old or corrupted sessions in the **SysClientSessions** table.

**Solution**

1. Make sure that the custom code base for the "customer validate" customization extensions around the **Application** or **Info** classes works against a demo database.
2. Truncate the records from the **SysClientSessions** table by using the following SQL command, and then try again.

    ```SQL
    TRUNCATE TABLE SYSCLIENTSESSIONS;
    ```
