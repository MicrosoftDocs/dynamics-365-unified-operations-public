---
title: Migrate finance and operations environments from Lifecycle Services to Power Platform admin center (preview)
description: Learn how to prepare for and migrate finance and operations environments from Microsoft Dynamics Lifecycle Services to the Microsoft Power Platform admin center.
author: laneswenka
ms.author: laswenka
ms.topic: how-to
ms.date: 11/24/2026
ai-usage: ai-generated
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

> [!IMPORTANT]
> Migration is a one-way operation. After an environment is migrated, its management experience is read-only in Lifecycle Services, and you can't move its management back to Lifecycle Services through a customer-initiated operation.

## What happens during migration

Migration changes the control plane that manages the environment. The process updates environment metadata across Microsoft services so that lifecycle operations are managed through the Power Platform admin center instead of Lifecycle Services. The database isn't moved, and the environment infrastructure isn't materially changed. The environment URL and your deployed code stay the same, so users and integrations continue to connect to the same URL.

The finance and operations apps environment is unavailable during part of the migration. Plan for approximately 15 minutes of downtime for each Application Object Server (AOS) instance. Environments that have more AOS instances take longer. Schedule the migration outside business hours and reserve extra time in the maintenance window in case the operation takes longer than the estimate.

After migration:

- The Power Platform admin center is the management experience for environment lifecycle operations such as copy, backup, restore, servicing, updates, and monitoring.
- Use Azure Pipelines and Power Platform deployment capabilities for ALM and code deployment.
- The environment consumes capacity under the [Power Platform capacity model](/power-platform/admin/unified-experience/finance-operations-apps-overview#transition-from-an-environment-slot-purchasing-model-to-a-capacity-based-model).
- The Lifecycle Services environment slot isn't returned or made available for another environment. Future environment provisioning is based on available Power Platform capacity instead of Lifecycle Services environment slots.
- The Lifecycle Services project remains available. The migrated environment is read-only in Lifecycle Services, but you can still use the project's [Asset library](asset-library.md). Environments that you haven't migrated continue to be managed in Lifecycle Services.
- Some Lifecycle Services scenarios aren't available for the migrated environment. To plan how to complete them in the Power Platform admin center, see [Lifecycle Services scenarios and Power Platform admin center alternatives](#lifecycle-services-scenarios-and-power-platform-admin-center-alternatives).

## Supported environments and limitations

| Environment or workload | Migration support |
| --- | --- |
| Self-service sandbox | Supported. Migrate and validate sandboxes before you plan a production migration. |
| Self-service production | The migration action might be available, but production migration isn't recommended during public preview. |
| Cloud-hosted developer environment | Not supported. Deploy a [Unified Developer Environment](/power-platform/developer/unified-experience/finance-operations-dev-overview) or use a [downloadable virtual hard disk (VHD)](../dev-tools/access-instances.md#vm-running-locally) for local development. |
| Environment that uses Dynamics 365 Commerce functionality | Not supported during public preview. The migration prerequisite check doesn't currently detect Commerce usage. Don't migrate an environment that uses Commerce functionality. |

## Lifecycle Services scenarios and Power Platform admin center alternatives

A migrated environment is read-only in Lifecycle Services, so you can't use Lifecycle Services to run operations on it. Some Lifecycle Services features also aren't implemented in the Power Platform admin center. Use the tables in this section to plan how to complete each scenario after migration, and update your operational runbooks and ALM processes before you migrate. For more information about the differences between the two admin centers, see [Overview of unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview) and [Administration for partners and systems implementers](/power-platform/admin/unified-experience/partners-systems-implementers).

### Environment operations

The following table lists Lifecycle Services environment scenarios and the alternative to use after you migrate the environment.

| Lifecycle Services scenario | Alternative in the Power Platform admin center |
| --- | --- |
| Deploy a new sandbox or production environment in an environment slot | Provision a new environment from an ERP-based template. Provisioning uses available Power Platform capacity instead of environment slots. For more information, see [Tutorial: Provision a new environment with an ERP-based template](/power-platform/admin/unified-experience/tutorial-deploy-new-environment-with-erp-template). |
| Deploy a cloud-hosted developer environment | Deploy a [Unified Developer Environment](/power-platform/developer/unified-experience/finance-operations-dev-overview). |
| Build deployable packages on a Lifecycle Services build environment | Build unified packages by using Microsoft-hosted agents in Azure DevOps. For more information, see [Continuous integration and deployment](/power-platform/developer/unified-experience/finance-operations-pipelines). |
| Upload a software deployable package to the Asset library, and then apply it to a sandbox | Create a unified package that contains your X++ modules and Dataverse solutions. Deploy the package to the environment by using Azure Pipelines or the [Power Platform CLI package commands](/power-platform/developer/cli/reference/package). |
| Promote an update from a sandbox to production | Deploy the same unified package directly to the production environment by using Azure Pipelines or the Power Platform CLI. You can automate production deployments by using service principal authentication. |
| Refresh a database from another environment | Copy the environment. A copy includes both the code and the data from the source environment. To reduce storage consumption in a sandbox, use a [transaction-less copy](/power-platform/admin/unified-experience/tutorial-perform-transactionless-copy). For more information, see [Copy an environment](/power-platform/admin/copy-environment). |
| Export a database to a `.bacpac` file in the Asset library | Create a backup of the environment. Backups are kept in the cloud, and you can't download them as `.bak` or `.bacpac` files. To work with data directly in SQL, use a Unified Developer Environment and [request just-in-time database credentials](/power-platform/developer/unified-experience/finance-operations-product-db-access) from Visual Studio. |
| Restore a database to a point in time | Restore the environment from a system backup or a manual backup. For more information, see [Back up and restore environments](/power-platform/admin/backup-restore-environments). |
| Turn maintenance mode on or off | Turn **Administration mode** on or off for the environment. Administration mode has the same effect as maintenance mode in Lifecycle Services. For more information, see [Maintenance mode](../sysadmin/maintenance-mode.md#turn-maintenance-mode-on-and-off-in-unified-developer-experience-for-finance-and-operations-apps-environments-through-the-power-platform-admin-center). |
| Monitor environment health by using [Lifecycle Services monitoring and diagnostics tools](monitoring-diagnostics.md) | Use Application Insights for near real-time application health and proactive monitoring. For more information, see [Get started with monitoring and telemetry](../monitoring-telemetry/monitoring-getting-started.md). |
| Submit a support request from the Lifecycle Services project | Create and view support requests in **Help + Support** for any environment in the tenant that you can manage. For more information, see [Get support in the Power Platform admin center](/power-platform/admin/get-help-support) and [Migration of the Lifecycle Services Support experience to Power Platform admin center](support-migration-to-ppac.md). |
| Manage the environment through Lifecycle Services project roles, such as Project owner | Assign the Power Platform administrator role in Microsoft Entra ID or an environment admin role. Admins can [add users to the environment](/power-platform/admin/add-users-to-environment) directly from the Power Platform admin center. Partners should use [granular delegated admin privileges (GDAP)](/partner-center/gdap-introduction) to manage customer environments. For more information, see [For partners: Delegated administrator role](/power-platform/admin/for-partners-delegated-administrator). |

### Project features

The Lifecycle Services project remains available after you migrate its environments. However, the following Lifecycle Services features aren't implemented in the Power Platform admin center. Use these alternatives as you move your processes to the Power Platform admin center.

| Lifecycle Services feature | Alternative |
| --- | --- |
| [Asset library](asset-library.md) | Store unified packages as build artifacts in Azure DevOps, in source control, or in local storage. Database backups aren't available for offline use. |
| [Methodologies](create-methodology.md) | Track phases and timelines in the [Dynamics 365 Implementation Portal](/dynamics365/guidance/implementation-portal/overview) or in Azure DevOps. |
| Project settings and project users | Use the [Dynamics 365 Implementation Portal](/dynamics365/guidance/implementation-portal/overview). |
| Organization users | Use the [Microsoft 365 admin center](/microsoft-365/admin/add-users/add-users). |
| [Business process modeler](bpm-overview.md) | Use the [business process catalog](/dynamics365/guidance/business-processes/about). |
| [Task recorder](../user-interface/task-recorder.md) recordings saved to Lifecycle Services | Save Task recorder files locally. |
| Translation service | Use the [Dynamics Translation Service connector](/connectors/dynamicstranslations/). |
| Solution management | Use Microsoft Marketplace. |
| Alert service | Create a support request in **Help + Support**. |

## Prerequisites

Before you migrate an environment, complete the following preparation steps:

1. Confirm that the environment doesn't use Commerce functionality.
1. Ensure that the environment is healthy and has a status of **Deployed** in Lifecycle Services.
1. Link the environment to a Power Platform environment. For more information, see [Enable the Power Platform integration](../power-platform/enable-power-platform-integration.md).
1. Resolve any [Power Platform storage capacity deficit](/power-platform/admin/finance-operations-storage-capacity). Available database capacity is validated before migration.
1. Ensure that the person who starts the migration is an administrator of the linked Power Platform environment.
1. If the environment is the last sandbox in the project that's managed in Lifecycle Services, and production is still managed in Lifecycle Services, review how migration affects production updates. For more information, see [Recommended migration sequence](#recommended-migration-sequence).
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
1. Migrate and validate the remaining sandbox environments. Before you migrate the last sandbox, review the following note about production updates.
1. Plan production last, after sandbox validation is complete and production migration is recommended for your release stage.

Coordinate the last sandbox migrations with your ALM cutover. After a sandbox is migrated, Lifecycle Services deployment and promotion workflows no longer manage that environment. Use the Power Platform and Azure Pipelines that you prepared before migration.

> [!IMPORTANT]
> In Lifecycle Services, you update a production environment by promoting an update from a sandbox in the same project. For more information, see [Promote an update to production environments](../deployment/updateenvironment-newinfrastructure.md#promote-an-update-to-production-environments). After you migrate the last sandbox in a project, no sandbox remains in Lifecycle Services to promote updates from. If production is still managed in Lifecycle Services, you can't promote updates, including custom code changes, to production until you migrate production to the Power Platform admin center. To avoid an unplanned code freeze, keep at least one sandbox in Lifecycle Services until you're ready to migrate production.

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

## Turn on unified admin user management after migration

[Unified admin user management](/power-platform/admin/unified-experience/unified-admin-user-management) (preview) lets you manage System Administrator users for finance and operations apps from the Power Platform admin center. A migrated environment might not have the required version of the Unified User Management solution. Until you install or update the solution, you can't turn on the **(Preview) Unified admin user management** feature in the migrated environment.

After you turn on the feature, the Power Platform admin center becomes the source of truth for admin roles, and admin roles that exist only in finance and operations apps are removed. Before you turn it on, review [how admin user management works after unification](/power-platform/admin/unified-experience/unified-admin-user-management#how-admin-user-management-works-after-unification).

To turn on unified admin user management in a migrated environment, follow these steps:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), and open the migrated environment.
1. In the command bar, expand **Resources**, and then select **Dynamics 365 apps**.
1. Search for **Unified User Management**, and then take one of the following actions:
   - If the status is **Update available**, select **Update**.
   - If the solution isn't listed, select **Install app**, select **Unified User Management**, and then follow the prompts to install it.
1. Wait until the installation or update is complete. Then confirm that the environment meets all the [prerequisites for unified admin user management](/power-platform/admin/unified-experience/unified-admin-user-management#prerequisites), including the minimum platform update and solution versions.
1. Sign in to finance and operations apps as a user who has the System Administrator role in both Dataverse and finance and operations apps.
1. Go to **System administration** > **Workspace** > **Feature management**, select **All**, and then turn on **(Preview) Unified admin user management**.
1. Verify that your Dataverse environment admins appear as users in finance and operations apps.

## Resolve prerequisite check failures

| Failed check | Resolution |
| --- | --- |
| **Environment is in Deployed status** | Wait for any lifecycle operation to finish, and resolve environment health issues until the status returns to **Deployed**. |
| **Power Platform environment is linked** | Complete [Power Platform integration](../power-platform/enable-power-platform-integration.md) for the environment. |
| **Database storage capacity is available** | Review [finance and operations storage capacity](/power-platform/admin/finance-operations-storage-capacity), and free or purchase enough capacity to clear the deficit. |
| **You are an administrator of the linked Power Platform environment** | Have an existing administrator assign you an appropriate environment admin role, and then refresh the Lifecycle Services page. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
