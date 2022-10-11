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

The following table shows the data that can be transferred between instances and the actions that can be used to transfer it.

| Migration method | Project types | Capabilities |
|------------------|---------------|--------------|
| Automated | <ul><li>Cloud implementation project</li><li>On-premises implementation project</li><li>Partner project</li></ul> | <ul><li>Business process modeler</li><li>Methodologies</li><li>Project onboarding</li><li>Project settings</li><lip>Support</li><li>Work items</li></ul> |
| Manual migration | <ul><li>Cloud implementation project</li><li>On-premises project</li><li>Partner project</li></ul> | <ul><li>Asset library</li><li>Commerce</li><li>Self-service environments (support ticket)</li><li>Cloud-hosted environments (CHE)</li></ul> |
| Not supported | All | <ul><li>Configuration and Data Manager (CDM)</li><li>SharePoint Online integration</li><li>System diagnostics</li><li>Upgrade analysis</li><li>Globalization</li><li>Code upgrade</li><li>Translation service</li><li>Non-project features</li></ul> |

You're responsible for migrating data that requires manual migration. However, you aren't required to migrate any or all of this data. You might choose to migrate only your most recent assets from the Asset library. Alternatively, you might choose to re-create developer cloud-hosted environments, for example, in the target project.

## Start your project migration

1. On the navigation menu, select **Project migration manager**.

    > [!NOTE]
    > You must be a project owner to migrate a project.

2. Select **New** to start a new migration request.
3. In the **Schedule Migration** dialog box, select a target geography that meets your specifications.
4. Select a migration start time in the future. This step will begin the migration of your project, and several aspects of the project will become read-only.
5. Select the checkbox to agree to the terms and continue.

After the migration is scheduled, you can cancel it by selecting it on the Project migration manager list page and then selecting **Delete**.

### Validations

The Project migration manager utility performs several validations:

- All migrations must be scheduled in the future.
- Migration can be done for only some project types. For information about the supported project types, see the "Automated" row of the table earlier in this article.
- A migration can be deleted or canceled only if it hasn't yet started.

### During migration

While the migration is in progress, a banner is shown across the source and target projects to indicate that they are participating in a migration. The projects are locked for changes until either the migration is successfully completed, or it fails and is rolled back.

## Frequently asked questions (FAQ)

This section provides answers to some common questions.

### My sandbox and production environments are already in my desired geography (for example, Europe). Why is there downtime when I move my Lifecycle Services project to EU?

Finance and operations apps store metadata that includes the connection to the Lifecycle Services project that the apps were created from. When you migrate your project to a new geography, such as Lifecycle Services Europe, the connection information must be updated in those environments. This update requires an environment restart, which can take up to an hour.

### Which geographies are available for me to choose from?

For more information about the different geographies that are available, see [Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies](/dynamics365/fin-ops-core/dev-itpro/deployment/deployment-options-geo).

### What happens to the source project after migration is completed?

The source project remains available for up to one year, in read-only mode. Although you can download assets, you can't make any other changes. You also can't manage the environments from the source project. After one year, the source project and its data are deleted. You can delete the project sooner if you've moved all your required data to the target project and no longer want data to reside in the source geography.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
