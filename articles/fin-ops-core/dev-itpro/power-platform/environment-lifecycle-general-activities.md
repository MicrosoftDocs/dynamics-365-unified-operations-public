---
title: Environment lifecycle management when Power Platform Integration is enabled
description: This article explains how to handle environment lifecyle management when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: article
---

# Environment lifecycle management when Power Platform Integration is enabled

When the Power Platform Integration is enabled, the finance and operations apps  and the customer engagements apps environments are tightly connected. The administrators should look at these two platforms as a one single environment, with multiple apps. In this article, we highlight the environment lifecycle scenarios impacted by the Power Platform Integration.

> [!IMPORTANT]
> The Power Platform Integration is not affected by the environment lifecycle scenarios described in this article, besides when the environments are deleted.

## Edit the properties of an environment in Power Platform admin center

Article [Edit properties of an environment](/power-platform/admin/edit-properties-environment), highlights how administrators can edit properties of an environment in Power Platform Admin center when there is no link with finance and operations app. Most of these actions are still possible, with one notable restriction, the **URL**. Once a Dataverse environment is linked to finance and operations apps, the URL cannot be updated anymore, the error below is thrown:

:::image type="content" source="media/ppi-edit-URL.png" alt-text="Editing the URL of a linked Dataverse environment." lightbox="media/ppi-edit-URL.png":::

> [!TIP]
> If you need a different URL for your Dataverse environment, consider deploying a  separate one from Power Platform Admin center and updating the URL there. Afterwards follow the steps in article [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).

## Delete an environment from Power Platform admin center

It it not possible to delete a linked environment from Power Platform admin center, the following error is shown:

:::image type="content" source="media/ppi-delete-ppac.png" alt-text="Delete an environemnt from Power Platform admin center." lightbox="media/ppi-delete-ppac.png":::

## Delete an environment from Lifecycle services

The Lifecycle services (LCS) portal can still be used to delete a finance and operations apps environment, the process is not changed.

> [!NOTE]
> When the finance and operations apps environment is deleted, the linked Dateverse environment is **not** automatically deleted. However, the link is removed and the environment can be further deleted from [Power Platform admin center](/power-platform/admin/delete-environment).

## Reset an environment from Power Platform admin center

It is not possible to Reset a linked environment from Power Platform admin center, the Reset button is not available.

:::image type="content" source="media/ppi-reset.png" alt-text="Reset option not available in Power Platform admin center." lightbox="media/ppi-reset.png":::

## Change the environment type from Power Platform admin center

It is possible to [convert a Power Platform admin center environment](/power-platform/admin/switch-environment) from sandbox to production or from production to sandbox, but it is **not recommended** for linked environments as this option is not available for finance and operations apps.

Aspects to consider when changing the environment type:

- **Sandbox to production**: The Dataverse environment becomes of type production, while the linked finance and operations apps remains of sandbox type. To link your Dataverse environment to a production finance and operations environment, the following steps need to be done:
  - Step 1: Deploy the finance and operations production environment without enabling the Power Platform Integration.
  - Step 2: [Refresh the database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh) from the finance and operations environment linked to the production Dataverse environment
  - Step 3: Delete the finance and operations sandbox environment to remove the link with the production Dataverse environment
  - Step 4: Apply the steps in [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md) to link the production finance and operations apps environment to the production dataverse environment.

- **Production to sandbox**: The Dataverse environment becomes of type sandbox, while the linked finance and operations apps remains of type production. This configuration is not recommended. Since the Power Platform Integration link is irreversible, the customer cannot link the production finance and operations apps environment to another production Dataverse environment without deletion.

> [!IMPORTANT]
> It is highly **not recommended** to run production workloads in a sandbox environment. Sandbox environments do not benefit from the same level of SLAs as production ones.

## Backup and database export

Automated backups as well as the option to perform manual backups are in place for both [Power Platform](/power-platform/admin/backup-restore-environments) and [finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/database/export-database), with the notable difference that both code and data are backed-up for Power Platform, while only the database is applicable for finance and operations apps.

> [!NOTE]
> Perform manual backups at the same time for both platforms.

## Restore and point-in-time restore

In Power Platform, it is possible to restore [system backup](/power-platform/admin/backup-restore-environments#restore-a-system-backup) or a [manual backup](/power-platform/admin/backup-restore-environments#manual-backups) which will restore both code and database into the environment. For finance and operations apps, it is possible to do a [database point-in-time restore (PITR)](/dynamics365/fin-ops-core/dev-itpro/database/database-point-in-time-restore).

> [!NOTE]
> Perform the restore and point-in-time restore in parallel, starting from the same point in time.

Elements to pay attention after the restore and point-in-time restore are complete:

- Since a Power Platform restore includes also the underlying codebase, while PITR is only for the database, the admins need to ensure the two environments are re-alligned from a code perspective. This implies:
  - Option 1: After restore, install in Dataverse the solutions prior to restore
  - Option 2: Deploy to the finance and operations apps environment the code package corresponding to the time of the backup used for PITR.

- The [dual-write](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page), [virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/virtual-entities-overview) and [business and data events](/dynamics365/fin-ops-core/dev-itpro/business-events/home-page) frameworks might be impacted by the restore and point-in-time restore. Carefully review their documentation and always test the steps in a sandbox before applying them to production.

## Copy and database refresh

In Power Platform, it is possible to [copy an environment](/power-platform/admin/copy-environment) while for finance and operations apps, it is possible to [refresh a database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh) from another environment or to [import a database](/dynamics365/fin-ops-core/dev-itpro/database/import-database) from the LCS asset library.

> [!NOTE]
> Perform the copy and database refreshes in parallel, when both the source environments and the target environments are linked.

Elements to pay attention after the restore and point-in-time restore are complete:

- Since a Power Platform copy includes also the underlying codebase, while finance and operations apps actions target only the database, the admins need to ensure the target environments are re-alligned from a code perspective. This implies:
  - Option 1: After copy, install in Dataverse the solutions prior to the copy
  - Option 2: Deploy to the finance and operations apps environment the code package installed in the source environment.

- The [dual-write](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page), [virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/virtual-entities-overview) and [business and data events](/dynamics365/fin-ops-core/dev-itpro/business-events/home-page) frameworks might be impacted by the copy and database movement activities. Carefully review their documentation and always test the steps in a sandbox before applying them to production.
