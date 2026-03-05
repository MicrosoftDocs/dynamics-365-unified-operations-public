---
title: Project migration manager
description: Learn about how to use the Project migration manager to move your project from one Microsoft Dynamics Lifecycle Services geography to another.
author: LaneSwenka
ms.author: laswenka
ms.topic: how-to
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-09-30
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
---

# Project migration manager

The Microsoft Dynamics Lifecycle Services Project migration manager helps you move your project data from one geography to another geography that Lifecycle Services supports. This article describes the terminology and supported scenarios for this functionality, and provides answers to frequently asked questions.

## Move projects to new geographies

By using the Project migration manager, you can move your Lifecycle Services project from one geography to another geography that meets your requirements. However, it's important that you understand why you might want to move your project in this way.

Originally, Lifecycle Services supported only one instance (<https://lcs.dynamics.com/>), which served as the global endpoint for all customers. However, because of recent regulatory trends across the industry, customers and software vendors are now required to keep data within a geographic boundary. Therefore, Lifecycle Services started to deploy geography-specific instances, so that customers can have all their project data in the desired location. For more information about the different geographies that are available, see [Available geographies for Dynamics 365 finance and operations apps](../deployment/deployment-options-geo.md).

## Considerations

Before you migrate Lifecycle Services projects from one geography to another, consider the following aspects:

- Migration can take up to two hours when Lifecycle Services projects and environments are unavailable.
- As part of the migration, the process creates a new Lifecycle Services project. The new project has a different project URL and Lifecycle Services project ID. 
- Dynamics 365 Commerce isn't available in all target geographies. If you have Commerce components enabled, the migration manager doesn't schedule your migration if you're migrating to one of the target geographies where Commerce isn't available. Be sure to review the [availability of features in the selected target geography](../deployment/deployment-options-geo.md#feature-availability-across-geographies) before you decide which geography to deploy in.
- All project environments (sandbox and production) must be on supported versions before migration is scheduled.
- Only Lifecycle Services project owners can access the Project migration manager feature.
- You can use the Project migration manager to transfer data only within cloud implementation projects and partner projects for finance and operations apps. Other types of projects aren't yet supported.
- This functionality has some limitations in terms of the data that's automatically transferred. These limitations are described in the following table.

### Data that you can transfer between instances

The following table shows the data that you can transfer between instances and the actions that you can use to transfer it.

| Migration method | Feature | Details |
|------------------|---------|---------|
| Automated | Business process modeler | |
| Automated | Methodologies | The state of the methodology isn't migrated. You can manually complete stages as required in the target project. |
| Automated | Commerce | Metadata is moved for the Commerce Scale Unit (CSU) and other Commerce functionality. This metadata doesn't migrate the CSU, but rather ensures it's available for use in the target project. |
| Automated | Self-service environments | Metadata is moved for the Sandbox and Production environments. This metadata doesn't migrate the actual environment to a new geography, but rather ensures it's available for use in the target project for applying updates, database movement, and other admin activities. |
| Automated | Subscription estimator | |
| Automated | Project onboarding | |
| Automated | Project settings | Azure connectors aren't migrated. Update schedules are migrated, but paused updates aren't. You can manually configure these aspects in the target project. |
| Automated | Support | |
| Automated | Work items | |
| Automated | Organization users | Only users who were in the source project are created as organization users in the target Lifecycle Services geography. |
| Automated | Project users | Only project owners from the tenant that owns the source project are migrated to the target Lifecycle Services project. | 
| Automated | Asset library | Only the last application or merged software deployable package asset that you applied to your sandbox or production environments is automatically migrated. |
| Manual | Asset library | You can download and manually upload assets in the target project. You don't have to move all assets. You can move only assets that you require. |
| Manual | Shared asset library | The shared asset library is different in each geo. For a package to be globally available, it must be uploaded to each geo's shared asset library. |
| Manual | Self-service environments | Sandbox and production environments remain in their current deployed region and aren't affected by the Project migration manager. They'll have the same environment IDs but are in a new project. If you must move your environment to a different region, follow the [Geo-to-geo migrations](/dynamics365/fin-ops-core/dev-itpro/deployment/geo-to-geo-migrations) article.|
| Manual | Cloud-hosted environments | Azure connectors can be manually reconfigured, and new environments can be deployed in the target after migration. After migration, the source project is locked but you're still allowed to delete cloud-hosted environments from the source to clean up the older project. |
| Manual | Project users | Remaining users must be added manually by project owners. |
| Not supported | System diagnostics | You can't export system diagnostics data. However, new diagnostics are generated from your environments in the target project after migration. |
| Not supported | Upgrade analysis | This feature is deprecated. You can't export upgrade analysis data. |
| Not supported | Globalization | You can't transfer regulatory alerts between projects. |
| Not supported | Code upgrade | You can't export code upgrade data. This feature is only supported in US-based public cloud instance of Lifecycle Services. |
| Not supported | Translation service | You can't export translation service data. However, you can start a new translation request in the target project after migration. |
| Not supported | Environment history | You can't transfer history for environments. It starts new in the target project. However, you can access and download the history from the source project by using the **Export to excel** button from each history page. |

You're responsible for migrating data that requires manual migration. However, you aren't required to migrate any or all of this data. You might choose to migrate only your most recent assets from the Asset library. Alternatively, you might choose to re-create developer cloud-hosted environments, for example, in the target project.

## Start your project migration

1. On the navigation menu, select **Project migration manager**.

>[!NOTE]
>You must be a project owner to migrate a project. In addition, your account must be in the tenant that owns the project.

1. Select **New** to start a new migration request.
1. In **Schedule Migration**, select a target geography that meets your specifications.

:::image type="content" source="media/projectmigrationmanager.png" alt-text="Screenshot of the Schedule Migration dialog with inputs to populate.":::

1. Select a migration start time in the future. This step starts the migration of your project, and several aspects of the project become read-only.
1. Select the checkbox to agree to the terms and continue.

After you schedule the migration, you can cancel it by selecting it on the **Project migration manager** list page and then selecting **Delete**.

### Validations

The **Project migration manager** performs several validations:

- All project environments (sandbox and production) must be on supported versions before you schedule a migration.
- When a migration begins, all environments must be in a **Deployed** state. Any other state cancels the migration.
- You must schedule all migrations in the future.
- You can schedule only one migration at a time.
- You can migrate cloud implementation projects and partner projects. 
- You can delete or cancel a migration only if it hasn't yet begun.
- Commerce isn't available in all target geographies. If you have Commerce components enabled, your migration isn't scheduled if you're migrating to one of the target geographies where Commerce isn't available.
- Migration isn't possible if you have e-commerce deployed in a geography that is different from the target. To address this limitation, you can re-create e-commerce in the target geography and move the content. Alternatively, if your business requires e-commerce to remain in a geography different from the target, you can back up and temporarily remove e-commerce. After the project migration, you can restore e-commerce in the same geography as before. 

### Before the migration begins

The system sends emails to all project owners to notify them that you scheduled a migration. These emails include the date when the migration begins. 

The system shows banners across the source project to indicate that you scheduled an upcoming migration.

You can cancel the migration at any time before it begins.

### During the migration

The system creates a new Lifecycle Services project in the target geography. This project provides you with a new Lifecycle Services Project ID and URL. The migration can take up to two hours depending on the size of the data that the system automatically transfers.

While the migration is in progress, the system shows a banner across the source and target projects to indicate that they're participating in a migration. The system locks the projects for changes until either the migration is successfully completed, or it fails and is rolled back.

If you schedule any customization, service, or quality updates during your migration, the system automatically cancels them.

You must update the Lifecycle Services project and other information in the Sandbox and Production environments. This update restarts the environment and can take up to one hour on each environment.

### After the migration

After the migration is completed, you receive an email stating the success of the migration, or the reason for the failure. Upon successful migration, you should manually transfer any other assets and settings that the system didn't automatically transfer from the old project to the new project. Make sure to update the release pipeline to newly created Lifecycle Services project. In addition, you have to reconfigure the update calendar for automatic updates and resubmit any pause requests that you previously entered.

You should attend to any project data that the system didn't automatically transfer and that you require in the new project.  

The system locks the source project after successful migration, and data is in read-only mode. If you still have cloud-hosted environments deployed on the source project, you're still allowed to deallocate and delete them despite the source project being locked. This access is to allow for cleaning up any resources as required on the source project.

Microsoft stores the source project for up to one year until it automatically deletes it. You can delete the source project sooner to remove the data from the source geography.

## Frequently asked questions (FAQ)

This section provides answers to some common questions.

### My sandbox and production environments are already in my desired geography (for example, Europe). Why is there downtime when I move my Lifecycle Services project to EU?

Finance and operations apps store metadata that includes the connection to the Lifecycle Services project that the apps were created from. When you migrate your project to a new geography, such as Lifecycle Services Europe, the apps need to update this connection information. This update requires an environment restart, which can take up to an hour.

### What happens to the source project after migration is completed?

The source project remains available for up to one year in read-only mode. Although you can download assets, you can't make any other changes. You also can't manage the environments from the source project. After one year, the source project and its data are deleted. You can delete the project sooner if you moved all your required data to the target project and no longer want data to reside in the source geography.

### What if I want to go back to my source geography after migration is successfully completed?

The software doesn't support this option. You must open a support ticket so that the product engineering group can help you.

### What happens if my migration is canceled or rolled back?

Your source project is unlocked, and you receive an email notification that the migration wasn't successful. Open a support ticket, and we'll help you.

### I'm currently a preview customer. Am I still a preview customer after migration?

Preview is a program that only exists in the US-based public cloud instance of Lifecycle Services. It's not available in the other geographies at this time. If you were previously part of the preview program and are migrating to another geography, you won't be in the preview program after migration.

### Does Lifecycle Services Project migration affect finance and operations apps add-ins?

Because there aren't changes to finance and operations apps environments or the Power Platform environments, Lifecycle Services Project migration doesn't affect finance and operations apps add-ins.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
