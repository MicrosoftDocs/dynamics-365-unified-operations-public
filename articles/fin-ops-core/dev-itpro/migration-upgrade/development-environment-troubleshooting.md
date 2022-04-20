---
# required metadata

title: Development environment troubleshooting
description: An overview sentence that describes what this article is all about.
author: ttreen 
ms.date: 04/08/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Development Environments Troubleshooting

[!include[banner](../includes/banner.md)]

This topic provides troubleshooting information for upgrades of Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations Development Environments (Tier 1)

## Scenario 1: The data upgrade is running slowly on the Development (Tier 1) Environment

**Solution:** Use premium storage when deploying the Virtual Machine (VM) from Dynamics Lifecycle Services (LCS)

## Scenario 2: Logs files on SQL Database AX fill up disk

**Solution:** Set the recovery mode on the database to Simple

## Scenario 3: Error on Pre-Reqs step "Failed to create a session"
During the pre-reqs, during the additive or partial sync you see an error in the downloaded sync log similar to the following:
 > _Stopped DBSync monitoring. Microsot.Dynamics.Ax.Xpp.ErrorException: Failed to create a session; confirm that the user has the proper privileges to log on to Microsoft Dynamics 365 for Finance and Operations._

**Cause:**
There can be a few issues for this issue, see below:
1. There could be customization to extend the **Application** or **Info** classes, that causes the AOS to crash.
2. There are old or corrupted sessions in the **SysClientSessions** table.
**Solution:**
1. Get the customer validate customization extensions around the **Application** or **Info** classes. Check that the custom code base works against a demo database. 
2. Truncate the records from the SysClientSessions table a try again.
```SQL
TRUNCATE TABLE SYSCLIENTSESSIONS;
```

