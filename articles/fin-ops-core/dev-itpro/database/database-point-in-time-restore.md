---
title: Database point-in-time restore (PITR)
description: Learn how to perform a point-in-time restore of a database for finance and operations, with steps to complete for environments with Commerce functionality.
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
ms.dyn365.ops.version: AX 7.0.0
---

# Database point-in-time restore (PITR)

[!include [banner](../includes/banner.md)]

Use Microsoft Dynamics Lifecycle Services to perform the point-in-time restore (PITR) for a sandbox user acceptance testing (UAT) environment or a production environment (live). Microsoft maintains [automated backups](/azure/sql-database/sql-database-automated-backups) of the business and financial reporting databases for 28 days for production environments and seven days for sandbox environments.

## Self-service point-in-time restore

[!include [pitr](../includes/dbmovement-pitr.md)]

### Applicable scenario for production restore

Restoring the database in production to a previous point in time isn't a common lifecycle operation. However, you might need to recover your production environment if it undergoes significant data corruption. Keep in mind that the operation can cause significant downtime and SQL data loss up to the point of time of the request.

### Restore operation failed

If the restore operation fails, it automatically rolls back. If you select the rollback option after the operation originally fails, your target sandbox environment is restored to the state that it was in before the restore began. A rollback is often required if a customization that is present in the target sandbox environment can't complete a database synchronization with the newly restored data.

To determine the root cause of the failure, use the **Environment change history** page to download the logs for the failed operation.

### Data elements that need attention after restore

When you restore a database from a previous point in time, the database is provided "as is." For example, batch jobs and other data elements in the system can be in an in-progress state. These elements require manual review.

> [!NOTE]
> Restore affects the tables that store references to files stored in Azure blob storage, like document attachments and custom Microsoft Office templates. However, because Azure blob storage itself isn't affected by this process, any files added after the restore point continue to exist in Azure blob storage but aren't reflected in the database.

### Environment administrator

The system administrator account in the target environment (that is, the account that has a **UserId** value of **Admin**) is reset to the value that is found in the web.config file in the target environment. This value should match the value of the administrator account in Lifecycle Services. To preview which account is used, go to the **Environment Details** page for your target sandbox environment in Lifecycle Services. The value that you select in the **Environment Administrator** field when you first deploy the environment updates the system administrator in the transactional database. The tenant of the environment is the tenant of the environment administrator.

If you use the Admin User Provisioning Tool in your environment to change the value in the web.config file, the value might not match the value in Lifecycle Services. If you require a different account, you must deallocate and delete the target sandbox environment, and then redeploy it by selecting another account. You can then perform another refresh database action to restore the data.

## Steps to complete after a database restore for environments that use Commerce functionality

[!include [environment-reprovision](../includes/environment-reprovision.md)]

## Known issues

### Breaking the chain of available restore points

Several frequently used actions create a new database that doesn't have the same restore point history as the previously used database. These actions include point-in-time restores, database refreshes, database imports, and point-in-time restores from the production environment to the sandbox environment. In addition, if a software deployable package that you apply to your environment fails during update of the database, and you use the rollback functionality in Lifecycle Services, the rollback functionality does a point-in-time restore of the database, and that restore also creates a new database.

Although the new database doesn't have any restore point history, it does begin to accrue new restore points from that time onward. After you perform any of the previously mentioned actions, you can't perform it again by using the same restore date and time.

### Restore is denied for environments that run Platform update 20 or earlier

The restore database process can't be completed if the environment is running Platform update 20 or earlier. For more information, see the list of currently supported Platform updates in the [Software lifecycle policy and cloud releases](../migration-upgrade/versions-update-policy.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
