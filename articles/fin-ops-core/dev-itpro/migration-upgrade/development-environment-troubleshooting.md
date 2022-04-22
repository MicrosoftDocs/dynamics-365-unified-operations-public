---
# required metadata

title: Troubleshoot Tier-1 development environments during upgrade 
description: This topic provides troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations development environments (Tier 1).
author: ttreen 
ms.date: 04/22/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Troubleshoot Tier-1 development environments during upgrade

[!include[banner](../includes/banner.md)]

This topic provides troubleshooting guidance for upgrades of Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations development environments (Tier 1).

## Scenario 1: The data upgrade is running slowly on the Tier 1 development environment.

**Solution:** Use premium storage when deploying the virtual machine (VM) from Microsoft Dynamics Lifecycle Services (LCS).

## Scenario 2: Log files on Dynamics AX 2012 SQL database AX fill up disk

**Solution:** Set the recovery mode on the database to **Simple**.

## Scenario 3: "Failed to create a session" error generated during prerequisite step 

During the prerequisite steps to upgrading, during the additive or partial sync you may see an error in the downloaded sync log similar to the following:
 `> _Stopped DBSync monitoring. Microsot.Dynamics.Ax.Xpp.ErrorException: Failed to create a session; confirm that the user has the proper privileges to log on to Microsoft Dynamics 365 for Finance and Operations._`

**Possible causes:**

- There could be a customization to extend the **Application** or **Info** classes that causes the Application Object Server (AOS) to crash.
- There are old or corrupted sessions in the **SysClientSessions** table.

**Solution:**

1. Check that the custom code base for the customer validate customization extensions around the **Application** or **Info** classes works against a demo database. 
2. Truncate the records from the **SysClientSessions** table using the following SQL command, and then try again.
```SQL
TRUNCATE TABLE SYSCLIENTSESSIONS;
```

