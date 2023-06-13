---
title: Database and environment movements when Power Platform Integration is enabled
description: This article explains how to perform database and environment movements when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: article
---

# Database and environment movements when Power Platform Integration is enabled

When the Power Platform Integration is enabled, the finance and operations apps  and the customer engagements apps environments are tightly connected. The administrators should look at these two platforms as a one single environment, with multiple apps. In this article, we highlight the environment lifecycle scenarios impacted by the Power Platform Integration.

> [!IMPORTANT]
> The Power Platform Integration is not affected by the environment lifecycle scenarios described in this article, besides when the environments are deleted.

## Backup and database export

Automatic and manual backups are options for both [Power Platform](/power-platform/admin/backup-restore-environments) and [finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/database/export-database). The main difference between the two platforms is that both code and data are backed-up for Power Platform, while only the database is applicable for finance and operations apps.

> [!NOTE]
> Perform manual backups at the same time for both platforms.

## Restore and point-in-time restore

In Power Platform, it's possible to restore a [system backup](/power-platform/admin/backup-restore-environments#restore-a-system-backup) or a [manual backup](/power-platform/admin/backup-restore-environments#manual-backups), which restores both code and database into the environment. For finance and operations apps, it's possible to do a [database point-in-time restore (PITR)](/dynamics365/fin-ops-core/dev-itpro/database/database-point-in-time-restore).

> [!NOTE]
> Perform the restore and point-in-time restore in parallel, starting from the same point in time.

Elements to pay attention after the restore and point-in-time restore are complete:

- The environment administrators need to ensure the two environments are aligned from a code perspective:
  - Option 1: After restore, install in Dataverse the solutions prior to restore
  - Option 2: Deploy to the finance and operations apps environment the code package corresponding to the time of the backup used for PITR.

- The restore and point-in-time restore might impact [dual-write](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page), [virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/virtual-entities-overview) and [business and data events](/dynamics365/fin-ops-core/dev-itpro/business-events/home-page) frameworks. Carefully review their documentation and always test the steps in a sandbox before applying them to production.

## Copy and database refresh

In Power Platform, it's possible to [copy an environment](/power-platform/admin/copy-environment) while for finance and operations apps, it's possible to [refresh a database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh) from another environment or to [import a database](/dynamics365/fin-ops-core/dev-itpro/database/import-database) from the LCS asset library.

> [!NOTE]
> Perform the copy and database refreshes in parallel, when both the source environments and the target environments are linked.

Elements to pay attention after the restore and point-in-time restore are complete:

- The environment administrators need to ensure the target environments are aligned from a code perspective:
  - Option 1: After copy, install in Dataverse the solutions prior to the copy
  - Option 2: Deploy to the finance and operations apps environment the code package installed in the source environment.

- The [dual-write](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page), [virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/virtual-entities-overview) and [business and data events](/dynamics365/fin-ops-core/dev-itpro/business-events/home-page) frameworks might be impacted by the copy and database movement activities. Carefully review their documentation and always test the steps in a sandbox before applying them to production.
