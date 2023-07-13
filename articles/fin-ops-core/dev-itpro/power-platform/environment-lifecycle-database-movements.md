---
title: Database and environment movements when Power Platform Integration is enabled
description: This article explains how to perform database and environment movements when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: article
---

# Database and environment movements when Power Platform Integration is enabled

When the Power Platform Integration is enabled, the finance and operations apps  and the customer engagements apps environments are tightly connected. The administrators should look at these two platforms as a one single environment, with multiple apps. In this article, we highlight environment lifecycle scenarios impacted by the Power Platform Integration.

> [!IMPORTANT]
>
> - It is recommended to perform the activities in this article in parallel on both platforms, in parallel. In article [Environment lifecycle operations - Core concepts](environment-lifecycle-core-concepts.md) you can find the terminology specific to each platform.
> - The Power Platform Integration is not affected by the environment lifecycle scenarios described in this article, besides when the environments are deleted.

## Environment actions in Power Platform admin center (PPAC)

### Back up environments

The procedure to back up environments in [Power Platform](/power-platform/admin/backup-restore-environments) does not change for connected environments. Remember that both code and data are backed up in Power Platform, while only the database is backed up for finance and operations apps.

### Restore environments

In Power Platform, it's possible to restore a [system backup](/power-platform/admin/backup-restore-environments#restore-a-system-backup) or a [manual backup](/power-platform/admin/backup-restore-environments#manual-backups), which restores both code and database into the environment. See [Elements to pay attention after the restore and point-in-time restore are complete](environment-lifecycle-database-movements#elements-to-consider-before-and-after-database-and-environments-movements)

## Copy environments

In Power Platform, it's possible to [copy an environment](/power-platform/admin/copy-environment). See [Elements to pay attention after the copy in PPAC and database refresh in LCS are complete](environment-lifecycle-database-movements#elements-to-consider-before-and-after-database-and-environments-movements).

## Environment actions in Lifecycle services (LCS)

### Export a database

The procedure to export a database in [LCS](/dynamics365/fin-ops-core/dev-itpro/database/export-database) does not change for connected environments. Remember that only the database is backed up for finance and operations apps, while both code and data are backed up in Power Platform.

> [!NOTE]
> Perform manual backups at the same time for both platforms.

### Point-in-time restore

It's possible in LCS to do a [database point-in-time restore (PITR)](/dynamics365/fin-ops-core/dev-itpro/database/database-point-in-time-restore).

> [!NOTE]
> Perform the restore and point-in-time restore in parallel, starting from the same point in time.

### Database refresh

In LCS it's possible to [refresh a database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh) from another environment or to [import a database](/dynamics365/fin-ops-core/dev-itpro/database/import-database) from the LCS asset library.

> [!NOTE]
> Perform the copy and database refreshes in parallel, when both the source environments and the target environments are linked.

## Elements to consider before and after database and environments movements

- Some add-ins might require cleanup before a database restore. Carefully review the documentation specific to the add-ins you are using.

- After the database and environment movements, environment administrators need to ensure the target environments on both platforms are aligned from a code perspective:
  - Option 1: After restore or copy, re-deploy in Dataverse the solutions prior to the restore or copy
  - Option 2: Deploy to the finance and operations apps environment the code package corresponding to the time of the point in time restore or the one in the source environment for database refreshes.

- The [dual-write](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page), [virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/virtual-entities-overview) and [business and data events](/dynamics365/fin-ops-core/dev-itpro/business-events/home-page) frameworks might be impacted by the copy and database movement activities. Carefully review their documentation and always test the steps in a sandbox before applying them to production.
