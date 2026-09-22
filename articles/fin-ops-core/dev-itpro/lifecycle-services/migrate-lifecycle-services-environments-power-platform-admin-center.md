---
title: Migrate finance and operations environments from Lifecycle Services to Power Platform admin center (preview)
description: Learn how to prepare for and migrate finance and operations environments from Microsoft Dynamics Lifecycle Services to the Microsoft Power Platform admin center.
author: laneswenka
ms.author: laswenka
ms.topic: how-to
ms.date: 09/22/2026
ms.reviewer: johnmichalak
ms.search.region: Global
---

# Migrate finance and operations environments from Lifecycle Services to Power Platform admin center (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE [LCS freeze](../../../includes/lcs-freeze-banner.md)]

The self-service environment migration feature moves management of an existing finance and operations apps environment from Microsoft Dynamics Lifecycle Services to the Microsoft Power Platform admin center. Migration is performed separately for each environment in a Lifecycle Services project. It doesn't migrate the Lifecycle Services project itself.

> [!IMPORTANT]
> This feature is in public preview. During public preview, Microsoft recommends that you migrate sandbox environments first and don't use the feature for production environments. Validate your migrated sandboxes and the Power Platform application lifecycle management (ALM) process before you plan a production migration.

**Migration is a one-way operation. After an environment is migrated, its management experience is read-only in Lifecycle Services, and you can't move its management back to Lifecycle Services through a customer-initiated operation.**

## What happens during migration

Migration changes the control plane that manages the environment. The process updates environment metadata across Microsoft services so that lifecycle operations are managed through the Power Platform admin center instead of Lifecycle Services. The database isn't moved, and the environment infrastructure isn't materially changed.

The finance and operations apps environment is unavailable during part of the migration. Plan for approximately 15 minutes of downtime for each Application Object Server (AOS) instance. Environments that have more AOS instances take longer. Schedule the migration outside business hours and reserve extra time in the maintenance window in case the operation takes longer than the estimate.

After migration:

- The Power Platform admin center is the management experience for environment lifecycle operations such as copy, backup, restore, servicing, updates, and monitoring.
- Use Azure Pipelines and Power Platform deployment capabilities for ALM and code deployment.
- The environment consumes capacity under the [Power Platform capacity model](/power-platform/admin/unified-experience/finance-operations-apps-overview#transition-from-an-environment-slot-purchasing-model-to-a-capacity-based-model).
- The Lifecycle Services environment slot isn't returned or made available for another environment. Future environment provisioning is based on available Power Platform capacity instead of Lifecycle Services environment slots.

## Supported environments and limitations

| Environment or workload | Migration support |
| --- | --- |
| Self-service sandbox | Supported. Migrate and validate sandboxes before you plan a production migration. |
| Self-service production | The migration action might be available, but production migration isn't recommended during public preview. |
| Cloud-hosted developer environment | Not supported. Deploy a [Unified Developer Environment](/power-platform/developer/unified-experience/finance-operations-dev-overview) or use a [downloadable virtual hard disk (VHD)](../dev-tools/access-instances.md#vm-that-is-running-locally) for local development. |
| Environment that uses Dynamics 365 Commerce functionality | Not supported during public preview. The migration prerequisite check doesn't currently detect Commerce usage. Don't migrate an environment that uses Commerce functionality. |

## Prerequisites

Before you migrate an environment, complete the following preparation steps:

1. Confirm that the environment doesn't use Commerce functionality.
1. Ensure that the environment is healthy and has a status of **Deployed** in Lifecycle Services.
1. Link the environment to a Power Platform environment. For more information, see [Enable the Power Platform integration](../power-platform/enable-power-platform-integration.md).
1. Resolve any [Power Platform storage capacity deficit](/power-platform/admin/finance-operations-storage-capacity). Available database capacity is validated before migration.
1. Ensure that the person who starts the migration is an administrator of the linked Power Platform environment.
1. Prepare your development and ALM processes in parallel:
   - Deploy Unified Developer Environments to replace cloud-hosted developer environments that you won't migrate.
   - Create and test Azure Pipelines that produce Power Platform unified packages and deploy them to unified environments. For more information, see [Continuous integration and deployment](/power-platform/developer/unified-experience/finance-operations-pipelines).
   - Review the [unified admin experience overview](https://aka.ms/oneadmin-overview) and its related environment-management articles.
1. Plan a maintenance window based on the number of AOS instances. Allow approximately 15 minutes per AOS instance, and reserve extra time.
1. Notify users that the environment is unavailable during migration and that the migration can't be reversed through Lifecycle Services.

You don't have to enable dual-write to migrate an environment.

## Recommended migration sequence

Use the following sequence to reduce risk and validate the new management and ALM experiences before production:

1. Deploy Unified Developer Environments and create Power Platform and Azure Pipelines in parallel with your existing Lifecycle Services processes.
1. Migrate a less critical sandbox environment.
1. Validate sign-in, environment operations, custom code deployment, integrations, and add-ins in the migrated sandbox.
1. Perform an environment copy in the Power Platform admin center to validate the lifecycle operation.
1. Migrate and validate the remaining sandbox environments.
1. Plan production last, after sandbox validation is complete and production migration is recommended for your release stage.

Coordinate the last sandbox migrations with your ALM cutover. After a sandbox is migrated, Lifecycle Services deployment and promotion workflows no longer manage that environment. Use the Power Platform and Azure Pipelines that you prepared before migration.

## Migrate an environment

Complete these steps separately for every environment that you want to migrate. To migrate an environment, follow these steps:

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com) and open the project that contains the environment.
1. In the **Environments** section, find the sandbox that you want to migrate, and then select **Full details**.
1. On the environment details page, expand **Power Platform migration (Preview)**.
1. Verify that all the following prerequisite checks have a green check mark:
   - **Environment is in Deployed status**.
   - **Power Platform environment is linked**.
   - **Database storage capacity is available**.
   - **You are an administrator of the linked Power Platform environment**.

    :::image type="content" source="media/lifecycle-services-power-platform-admin-center-migration-prerequisites.png" alt-text="Screenshot of the Power Platform migration section in Lifecycle Services, showing the four completed prerequisite checks and a Not started migration status.":::

1. Select **Migrate to Power Platform Admin Center**.
1. In the **Confirm environment migration** dialog, review the downtime and one-way migration warning.
1. Enter the environment name exactly as shown, and then select **Start migration**.

    :::image type="content" source="media/lifecycle-services-power-platform-admin-center-migration-confirmation.png" alt-text="Screenshot of the environment migration confirmation dialog, showing the downtime and one-way migration warning and the environment-name confirmation field.":::

1. Keep the maintenance window open while the migration runs. Don't start other lifecycle operations for the environment.
1. Wait until **Migration status** is **Migrated**, and then select **Open in Power Platform Admin Center**.

    :::image type="content" source="media/lifecycle-services-power-platform-admin-center-migration-complete.png" alt-text="Screenshot of the Power Platform migration section in Lifecycle Services after migration, showing a Migrated status and a link to open the environment in Power Platform admin center.":::

## Validate the migrated environment

Before you migrate another environment, complete the following validation in the migrated sandbox:

1. Confirm that users can sign in to finance and operations apps.
1. In the Power Platform admin center, verify that environment details, monitoring, backup, restore, copy, and update operations are available as expected.
1. Deploy a validated customization by using the Azure DevOps and Power Platform ALM process that you prepared before migration.
1. Verify integrations, add-ins, and business processes that are critical to the environment.
1. Perform an environment copy and validate the target environment.

If validation identifies an issue, don't migrate another environment until you resolve the issue. Because migration is one-way, you can't return environment management to Lifecycle Services as a rollback action.

## Resolve prerequisite check failures

| Failed check | Resolution |
| --- | --- |
| **Environment is in Deployed status** | Wait for any lifecycle operation to finish, and resolve environment health issues until the status returns to **Deployed**. |
| **Power Platform environment is linked** | Complete [Power Platform integration](../power-platform/enable-power-platform-integration.md) for the environment. |
| **Database storage capacity is available** | Review [finance and operations storage capacity](/power-platform/admin/finance-operations-storage-capacity), and free or purchase enough capacity to clear the deficit. |
| **You are an administrator of the linked Power Platform environment** | Have an existing administrator assign you an appropriate environment admin role, and then refresh the Lifecycle Services page. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
