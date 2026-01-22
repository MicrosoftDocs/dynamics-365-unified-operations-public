---
title: Database and environment movements when Power Platform Integration is enabled
description: Learn about how to perform database and environment movements when finance and operations apps are integrated with Microsoft Power Platform.
author: abunduc-ms
ms.author: johnmichalak
ms.topic: article
ms.date: 01/22/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Database and environment movements when Power Platform Integration is enabled

When you enable Microsoft Power Platform Integration, you connect the finance and operations apps environment and the customer engagements apps environment. Administrators should regard these two platforms as one environment that has multiple apps. This article describes the environment lifecycle scenarios that Power Platform Integration affects.

> [!IMPORTANT]
> - Perform the activities that this article describes in parallel on both platforms. To find terminology that's specific to each platform, see [Environment lifecycle operations - Core concepts](environment-lifecycle-core-concepts.md).
> - Power Platform Integration isn't affected by the environment lifecycle scenarios that this article describes, except when the environments are deleted.

## Environment actions available in Power Platform admin center

This section describes the environment actions that are available in Power Platform admin center.

### Back up environments

The procedure for backing up environments in Microsoft Power Platform doesn't change for connected environments. Remember that Microsoft Power Platform backs up both code and data. For finance and operations apps, only the system backs up the database. For more information about how to back up Microsoft Power Platform, see [Back up and restore environments](/power-platform/admin/backup-restore-environments).

### Restore environments

You can use Microsoft Power Platform to [restore a system backup](/power-platform/admin/backup-restore-environments#restore-a-system-backup) or do a [manual backup](/power-platform/admin/backup-restore-environments#manual-backups). Both methods restore code and the database into the environment. For more information, see the [Considerations before and after database and environment movements](#considerations-before-and-after-database-and-environment-movements) section of this article.

### Copy environments

You can use Microsoft Power Platform to [copy an environment](/power-platform/admin/copy-environment). For more information, see the [Considerations before and after database and environment movements](#considerations-before-and-after-database-and-environment-movements) section of this article.

## Environment actions available in Lifecycle Services

This section describes the environment actions that are available in Microsoft Dynamics Lifecycle Services.

### Export a database

The procedure for using Lifecycle Services to export a database doesn't change for connected environments. Remember that only the database is backed up for finance and operations apps, whereas both code and data are backed up in Microsoft Power Platform. For more information about how to export a database, see [Export a database](/dynamics365/fin-ops-core/dev-itpro/database/export-database).

> [!NOTE]
> Perform manual backups at the same time for both platforms.

### Do a point-in-time restore

You can use Lifecycle Services to do a [database point-in-time restore (PITR)](/dynamics365/fin-ops-core/dev-itpro/database/database-point-in-time-restore).

> [!NOTE] 
> To ensure data consistency, perform the restores in parallel for both platforms, and choose the same point in time value.

### Refresh a database

You can use Lifecycle Services to [refresh a database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh) from another environment or [import a database](/dynamics365/fin-ops-core/dev-itpro/database/import-database) from the Lifecycle Services Asset library.

> [!NOTE]
> Perform the copy and database refreshes in parallel when both the source environments and the target environments are linked.

## Considerations before and after database and environment movements

- Some add-ins require cleanup before you restore a database. Carefully review the documentation that's specific to the add-ins that you're using.
- After the database and environment movements, environment administrators must ensure that the target environments on both platforms align from a code perspective:

    - **Option 1:** After a restore or copy activity, redeploy, in Dataverse, the solutions before the restore or copy activity.
    - **Option 2:** Redeploy, to the finance and operations apps environment, either the code package that corresponds to the time of the PITR or the code package in the source environment for database refreshes.

- The copy and database movement activities might affect the [dual-write](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page), [virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/virtual-entities-overview), and [business and data events](/dynamics365/fin-ops-core/dev-itpro/business-events/home-page) frameworks. Carefully review their documentation, and always test the steps in a sandbox before you apply them to production.
