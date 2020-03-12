---
# required metadata

title: Database point-in-time restore (PITR)
description: This topic explains how to perform a point-in-time restore of a database for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 03/11/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: AX 7.0.0

---

# Database point-in-time restore (PITR)

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to perform the point-in-time restore (PITR) for a sandbox user acceptance testing (UAT) environment. Microsoft maintains [automated backups](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups) according to Microsoft Azure SQL defaults, up to a maximum of 30 days.  

## Self-service point-in-time restore
[!include [pitr](../includes/dbmovement-pitr.md)]

### Restore operation failed
In case of failure, the option to perform a **Rollback** is available.  By clicking the rollback option after the operation has initially failed, your target sandbox environment will be restored to the state it was before the restore began. Clicking the rollback option will restore the previous database from the deleted databases storage on the Azure SQL Server. A rollback is often required if a customization is present in the target sandbox that cannot complete a database synchronization with the newly-restored data.  

To determine the root cause of the failure, download the runbook logs using the available buttons before starting the rollback operation.

### Data elements that need attention after restore
When restoring a database from a previous point-in-time, keep in mind that the database is provided as-was. For example, batch jobs and other data elements in the system could be in an in-progress state. These will require manual review.

### Environment administrator
The System Administrator account in the target environment (UserId of 'Admin') is reset to the value found in the web.config file on the target.  This should be the same value as that of the Administrator from Lifecycle Services. To preview which account will be used, go to your target sandbox **Environment Details** page in LCS.  The value of the **Environment Administrator** field that was selected when the environment was first deployed is updated to be the System Administrator in the transactional database. The tenant of the environment will be that of the Environment Administrator.  

If you have used the Admin User Provisioning Tool on your environment to change the web.config file to a different value, it may not match what is in Lifecycle Services.  If you require a different account, you will need to deallocate and delete the target sandbox, and redeploy by selecting another account. Afterwards, you can perform another refresh database action to restore the data.

## Steps to complete after a database restore for environments that use Commerce functionality
[!include [environment-reprovision](../includes/environment-reprovision.md)]

## Known issues

### Breaking the chain of available restore points
Several common actions create a new database, which won't have the same restore point history built up as the previously used database.  These scenarios include point-in-time restore, database refresh, database import, point-in-time restore from Production to Sandbox. In addition, if you apply a Software Deployable Package to your environment and it fails during update of the database, using the Rollback functionality in Lifecycle Services will perform a point-in-time restore of the database which also creates a new database. 

The new database does not have any restore history, but does begin to accrue new restore points going forward. After performing any of the above actions, you will not be able to do so again using the same restore date and time.  

### Restore is denied for environments running Platform update 20 or earlier
The restore database process cannot be completed if the environment is running Platform update 3 or earlier. For more information, see the [list of currently supported Platform updates](..//migration-upgrade/versions-update-policy.md).


