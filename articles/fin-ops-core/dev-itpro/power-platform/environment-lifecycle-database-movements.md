---
title: Database and environment movements when Power Platform Integration is enabled
description: This article explains how to perform database and environment movements when finance and operations apps are integrated with Power Platform.
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: conceptual
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Database and environment movements when Power Platform Integration is enabled

When Microsoft Power Platform Integration is enabled, the finance and operations apps and the customer engagements apps environments are tightly connected. Administrators should look at these two platforms as a one environment with multiple apps. This article highlights the environment lifecycle scenarios that are impacted by the Power Platform Integration.

> [!IMPORTANT]
>
> - It's recommended to perform the activities described in this article in parallel on both platforms. To find terminology specific to each platform, see [Environment lifecycle operations - Core concepts](environment-lifecycle-core-concepts.md).
> - Power Platform Integration isn't affected by the environment lifecycle scenarios that are described in this article, except when the environments are deleted.

## Environment actions available in Power Platform admin center (PPAC)

This section describes the environment actions that are available in Power Platform admin center (PPAC).

### Back up environments

The procedure to back up environments in Power Platform doesn't change for connected environments. Remember that both code and data are backed up in Power Platform. Only the database is backed up for finance and operations apps. For more information on backing up Power Platform, see [Back up and restore environments](/power-platform/admin/backup-restore-environments).

### Restore environments

Using Power Platform, it's possible to [restore a system backup](/power-platform/admin/backup-restore-environments#restore-a-system-backup) or performa a [manual backup](/power-platform/admin/backup-restore-environments#manual-backups), which restores both code and database into the environment. For more information, see [Elements to pay attention after the restore and point-in-time restore are complete](environment-lifecycle-database-movements.md#elements-to-consider-before-and-after-database-and-environments-movements)

### Copy environments

Using Power Platform, it's possible to [copy an environment](/power-platform/admin/copy-environment). For more information, see [Elements to pay attention after the copy in PPAC and database refresh in Lifecycle Services are complete](environment-lifecycle-database-movements.md#elements-to-consider-before-and-after-database-and-environments-movements).

## Environment actions available in Lifecycle services

This section describes the environment actions that are available in Lifecycle services.

### Export a database

The procedure to export a database using Lifecycle Services doesn't change for connected environments. Remember that only the database is backed up for finance and operations apps, while both code and data are backed up in Power Platform. For more information about exporting a database, see [Export a database](/dynamics365/fin-ops-core/dev-itpro/database/export-database).

> [!NOTE]
> Perform manual backups at the same time for both platforms.

### Point-in-time restore

It's possible to use Lifecycle Services todo a [database point-in-time restore (PITR)](/dynamics365/fin-ops-core/dev-itpro/database/database-point-in-time-restore).

> [!NOTE] 
> Perform the restore and point-in-time restore in parallel, starting from the same point in time.

### Database refresh

In Lifecycle Services it's possible to [refresh a database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh) from another environment or [import a database](/dynamics365/fin-ops-core/dev-itpro/database/import-database) from the Lifecycle Services asset library.

> [!NOTE]
> Perform the copy and database refreshes in parallel when both the source environments and the target environments are linked.

## Elements to consider before and after database and environments movements

- Some add-ins might require cleanup before a database restore. Carefully review the documentation specific to the add-ins you're using.

- After the database and environment movements, environment administrators need to ensure the target environments on both platforms are aligned from a code perspective:
  - Option 1: After restore or copy, redeploy in Microsoft Dataverse the solutions prior to the restore or copy
  - Option 2: Deploy to the finance and operations apps environment the code package corresponding to the time of the point in time restore or the one in the source environment for database refreshes.

- The copy and database movement activities may impact the [dual-write](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page), [virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/virtual-entities-overview) and [business and data events](/dynamics365/fin-ops-core/dev-itpro/business-events/home-page) frameworks. Carefully review their documentation and always test the steps in a sandbox before applying them to production.
