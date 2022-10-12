---
# required metadata

title: Project migration manager
description: This article explains how to use the Project migration manager to move your project from one Microsoft Dynamics Lifecycle Services geography to another.
author: LaneSwenka
ms.date: 10/05/2022
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form:
# ROBOTS:
audience: IT Pro, Developer
# ms.devlang:
ms.reviewer: sericks
# ms.tgt_pltfrm:
ms.custom: 257614
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
ms.search.region: Global
# ms.search.industry:
ms.author: laswenka
ms.search.validFrom: 2016-09-30
ms.dyn365.ops.version: AX 7.0.0

---

# Project migration manager

[!include [banner](../includes/banner.md)]

The Microsoft Dynamics Lifecycle Services Project migration manager utility lets you move your project data from one geography (or geo) to another geography that Lifecycle Services supports. This article describes the terminology, the supported scenarios, and frequently asked questions for this functionality.

## Move projects to new geographies

The Project migration utility lets you move your Lifecycle Services project from one geography to another geography that meets your requirements. However, it's important that you understand why you might want to move your project in this way.

Originally, Lifecycle Services supported only one instance (<https://lcs.dynamics.com/>), which served as the global endpoint for all customers. However, because of recent regulatory trends across the industry, customers and software vendors are now required to keep data within a geographic boundary. Therefore, Lifecycle Services has started to deploy geography-specific instances, so that customers can have all their project data in the desired location. For more information about the different geographies that are available, see [Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies](/dynamics365/fin-ops-core/dev-itpro/deployment/deployment-options-geo).

There are some limitations to this functionality in terms of all the data that is automatically transferred. These limitations will be described later in this article.

## Data that can be transferred between instances

Data can be transferred using the Project migration manager within cloud implementation projects, and partner projects.  Other types of projects are not yet supported.

The following table shows the data that can be transferred between instances of and the actions that can be used to transfer it.

| Migration method | Feature | Details |
|------------------|---------|---------|
| Automated | Business process modeler | ** |
| Automated | Methodologies | *The state of the methodology is not migrated.  You can manually complete as needed. |
| Automated | Commerce |  |
| Automated | Subscription estimator | |
| Automated | Project onboarding | |
| Automated | Project settings | *Update schedules including paused updates, as well as Azure connectors are not migrated |
| Automated | Support | |
| Automated | Work items | |
| Automated | Organization users | *Only users who were in the source project will be created as organization users in the target LCS geo |
| Automated | Project users | *Only Project Owners from the tenant who owns the source project are migrated to the target LCS project | 
| Automated | Asset library | *Only the last asset applied to your sandbox / production environments are migrated automatically |
| Manual | Asset library | You will be able to download and manually upload in the target project.  You do not need to move all assets, only those you require. |
| Manual | Self-service environments | Sandbox and Production environments will remain in their current deployed region and are not touched by the Project migration manager.  They will have the same Environment IDs but will live in a new Project.  If you need to move your enviornment to a different region, please open a support ticket separately. |
| Manual | Cloud-hosted environments | Azure connectors can be manually re-configured, and new environments can be deployed thereafter in the target. |
| Not supported | System diagnostics | This cannot be exported, but new diagnostics will be generated from your environments in the target project after migration |
| Not supported | Upgrade analysis | This cannot be exported, but you can start a new upgrade analysis in the target project after migration |
| Not supported | Globalization | Regulatory alerts ** |
| Not supported | Code upgrade | This cannot be exported, but you can start a new Code upgrade in the target project after migration |
| Not supported | Translation service | This cannot be exported, but you can start a new translation request in the target project after migration |

You're responsible for migrating data that requires manual migration. However, you aren't required to migrate any or all of this data. You might choose to migrate only your most recent assets from the Asset library. Alternatively, you might choose to re-create developer cloud-hosted environments, for example, in the target project.

## Start your project migration

1. On the navigation menu, select **Project migration manager**.

    > [!NOTE]
    > You must be a project owner to migrate a project.  In addition, your account must be in the same tenant that owns the project.

2. Select **New** to start a new migration request.
3. In the **Schedule Migration** dialog box, select a target geography that meets your specifications.
4. Select a migration start time in the future. This step will begin the migration of your project, and several aspects of the project will become read-only.
5. Select the checkbox to agree to the terms and continue.

After the migration is scheduled, you can cancel it by selecting it on the Project migration manager list page and then selecting **Delete**.

### Validations

The Project migration manager utility performs several validations:

- Project environments (Sandbox and Production) must all be on supported versions prior to scheduling migration.
- At the time migration begins, all environments must be in a Deployed state.  Any other state will cancel the migration.
- All migrations must be scheduled in the future.
- Only one migration can be scheduled at a time.
- Migration can be done for only some project types. For information about the supported project types, see the "Automated" row of the table earlier in this article.
- A migration can be deleted or canceled only if it hasn't yet started.
- Commerce is not available in all target geos.  If you have Commerce components enabled, your migration will not be scheduled if you're migrating to one of these target geos.  (Need list from Commerce team).

### Before the migration starts

Emails will be sent out to all Project Owners, indicating that a migration has been scheduled.  This will include the date when the migration will start.  During preview, emails may not be sent.

Banners will also be shown across the source project that indicates an upcoming migration has been scheduled.  

You may cancel the migration at any time up until it starts.

### During migration

While the migration is in progress, a banner is shown across the source and target projects to indicate that they are participating in a migration. The projects are locked for changes until either the migration is successfully completed, or it fails and is rolled back.

If there are any customization, service or quality updates scheduled during your migration, those updates will be automatically cancelled.

### Post migration

What do I do in source vs target?

## Frequently asked questions (FAQ)

This section provides answers to some common questions.

### My sandbox and production environments are already in my desired geography (for example, Europe). Why is there downtime when I move my Lifecycle Services project to EU?

Finance and operations apps store metadata that includes the connection to the Lifecycle Services project that the apps were created from. When you migrate your project to a new geography, such as Lifecycle Services Europe, the connection information must be updated in those environments. This update requires an environment restart, which can take up to an hour.

### Which geographies are available for me to choose from?

For the initial preview, the first target region supported is EU.  Over time we will add support for all LCS geographies.  For more information about the different geographies that are available, see [Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies](/dynamics365/fin-ops-core/dev-itpro/deployment/deployment-options-geo).

### What happens to the source project after migration is completed?

The source project remains available for up to one year, in read-only mode. Although you can download assets, you can't make any other changes. You also can't manage the environments from the source project. After one year, the source project and its data are deleted. You can delete the project sooner if you've moved all your required data to the target project and no longer want data to reside in the source geography.

### What happens if I want to go back to my source geo after migration completes successfully?

This is not supported via the software.  You will need to open a support ticket for the product engineering group to help you.

### What happens if my migration is cancelled or is rolled back?

Your source project will be unlocked, and you will receive an email notification that the migration has not completed successfully.  Please open a support ticket and we will help you.

### I am a First Release customer today, will I still be First Release after migration?

TBD

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

