---
# required metadata

title: Database Movement Operations - Destructive Testing Scenario
description: This topic explains a destructive testing scenario for Microsoft Dynamics 365 for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 1/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2019-01-22
ms.dyn365.ops.version: AX 7.0.0

---

# Tutorial: Destructive testing 

[!include [banner](../includes/banner.md)]

Database Movement operations are a suite of self-service actions that can be used as part of Data Application Lifecycle Management ( also referred to as 'DataALM' ).  In some situations it is required to perform destructive testing on an environment, which in this context means rendering an environment no longer useful for continued testing.  This is common in an implementation lifecycle during Conference Room Pilots.  This tutorial shows how to use database movement operations to facilitate destructive testing.

In this tutorial, you will learn 2 approaches:
>[!div class="checklist"]
> * Use a database backup asset
> * Use point-in-time restore

An example of this scenario is a customer who wishes to perform Conference Room Pilot starting with an environment that has no transactions ( ie - no sales orders, no purchase orders ).  The customer will be traveling from physical warehouse to physical warehouse across their geographic region to perform the same Pilot and wish for the environment to be 'reset' prior to each.

## Prerequisites
To complete this tutorial you must have a Standard User Acceptance Test (UAT) environment deployed in your project.  

## Using a database backup
If you have prepared a database backup (.bacpac) file that is already at the starting point for the test, it is simplest to upload this to your LCS Project's Asset Library under the **Database backup** section.  This can then be imported to your target environment as per below:

[!include [dbmovement-import](../includes/dbmovement-import.md)]

### Backup pros and cons
The advantage of using backup file assets is that you can continually import the same file to get back to your starting point.  

The disadvantage is that if there are many configurations that must be set after the import completes ( such as batch jobs for exmaple ) but before users can begin it will take more effort prior to each destructive testing session.

## Using point-in-time restore
If you did not start with a database backup (.bacpac) file but have instead have the UAT environment in a known good state, you can simply record the date and time in your timezone.  You can then begin the destructive testing and when finished can restore the environment back to the previous time using the below steps:

[!include [dbmovement-import](../includes/dbmovement-pitr.md)]

### Point-in-time restore pros and cons
The advantage of point-in-time-restore is that you can avoid dealing with database backup (.bacpac) files and can reduce the time between destructive testing sessions.  

The disadvantage is that due to current limitations of point-in-time restore you will need to mark down a new restore date and time in your timezone after the restore is complete.  That is because point-in-time restore always creates a new database and therefore the original date and time used will not be available as a restore point on the new database.




