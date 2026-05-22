---
title: Destructive testing 
description: Learn about a destructive testing scenario for finance and operations, including prerequisites and an overview of using a backup database.
author: LaneSwenka
ms.author: laswenka
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: johnmichalak
audience: IT Pro, Developer
ms.search.region: Global 
ms.search.validFrom: 2019-01-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.3
---

# Destructive testing 

[!include [banner](../includes/banner.md)]

Database movement operations are a suite of self-service actions that you can use as part of data application lifecycle management (DataALM). In some situations, you need to perform destructive testing on an environment. In this context, destructive testing means that the environment is no longer useful for continued testing. Destructive testing is typical in an implementation lifecycle during Conference Room Pilots. This tutorial shows how to use database movement operations to facilitate destructive testing.

In this tutorial, you learn two approaches:

> [!div class="checklist"]
>
> - Use a database backup asset.
> - Use point-in-time restore.

As an example of this scenario, a customer wants to do a Conference Room Pilot and wants to start with an environment that has no transactions (that is, no sales orders or purchase orders). The customer travels from physical warehouse to physical warehouse throughout the geographic region to do the same pilot, and wants the environment to be "reset" before each pilot is done.

## Prerequisites

To complete this tutorial, you must deploy a standard user acceptance testing (UAT) environment in your project.

## Using a database backup

If you prepare a database backup (.bacpac) file that's already at the starting point for the test, the easiest approach is to upload the backup file to the **Database backup** section in your LCS project's Asset Library. You can then import it to your target environment as described in the following section.

[!include [dbmovement-import](../includes/dbmovement-import.md)]

### Database backup pros and cons

When you use backup file assets, you can keep importing the same file to return to the starting point for the test.

If you need to set many configurations (for example, batch jobs) after the import but before users can begin, each destructive testing session requires more effort.

## Using point-in-time restore

If you don't start with a database backup (.bacpac) file but instead have the UAT environment in a known good state, you can just record the date and time in your time zone. You can then begin the destructive testing. When the testing is completed, you can restore the environment to the previous time by using the following steps.

[!include [dbmovement-import](../includes/dbmovement-pitr.md)]

### Point-in-time restore pros and cons

When you use point-in-time restore, you avoid dealing with database backup (.bacpac) files and reduce the time between destructive testing sessions.

Because of current limitations of point-in-time restore, you must record a new restore date and time in your time zone after the restore is completed. Because point-in-time restore always creates a new database, the original date and time that you used aren't available as a restore point on the new database.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
