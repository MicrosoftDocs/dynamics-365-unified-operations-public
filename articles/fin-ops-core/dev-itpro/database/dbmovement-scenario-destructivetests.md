---
# required metadata

title: Destructive testing 
description: This topic explains a destructive testing scenario for Finance and Operations.
author: LaneSwenka
ms.date: 01/28/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: 8.1.3

---

# Destructive testing 

[!include [banner](../includes/banner.md)]

Database movement operations are a suite of self-service actions that can be used as part of data application lifecycle management (DataALM). In some situations,  destructive testing must be done on an environment. In this context, destructive testing means that the environment is rendered no longer useful for continued testing. Destructive testing is typical in an implementation lifecycle during Conference Room Pilots. This tutorial shows how to use database movement operations to facilitate destructive testing.

In this tutorial, you will learn two approaches:

> [!div class="checklist"]
> * Use a database backup asset.
> * Use point-in-time restore.

As an example of this scenario, a customer wants to do a Conference Room Pilot and wants to start with an environment that has no transactions (that is, no sales orders or purchase orders). The customer will be traveling from physical warehouse to physical warehouse throughout the geographic region to do the same pilot, and wants the environment to be "reset" before each pilot is done.

## Prerequisites

To complete this tutorial, you must have a standard user acceptance testing (UAT) environment deployed in your project.

## Using a database backup

If you've prepared a database backup (.bacpac) file that is already at the starting point for the test, the easiest approach is to upload the backup file to the **Database backup** section in your LCS project's Asset Library. It can then be imported to your target environment as described here.

[!include [dbmovement-import](../includes/dbmovement-import.md)]

### Database backup pros and cons

The advantage of using backup file assets is that you can keep importing the same file to get back to the starting point for the test.

The disadvantage is that if many configurations (for example, batch jobs) must be set after the import is completed but before users can begin, more effort will be required before each destructive testing session.

## Using point-in-time restore

If you didn't start with a database backup (.bacpac) file but instead have the UAT environment in a known good state, you can just record the date and time in your time zone. You can then begin the destructive testing. Then, when the testing is completed, you can restore the environment to the previous time by using the following steps.

[!include [dbmovement-import](../includes/dbmovement-pitr.md)]

### Point-in-time restore pros and cons

The advantage of using point-in-time-restore is that you can avoid dealing with database backup (.bacpac) files and can reduce the time between destructive testing sessions.

The disadvantage is that, because of current limitations of point-in-time restore, you must record a new restore date and time in your time zone after the restore is completed. Because point-in-time restore always creates a new database, the original date and time that were used won't be available as a restore point on the new database.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]