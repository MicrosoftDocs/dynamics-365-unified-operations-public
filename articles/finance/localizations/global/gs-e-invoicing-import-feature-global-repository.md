---
title: Import features from the repository
description: Learn how to import Globalization features from the Dataverse repository, including a step-by-step process for importing features.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 11/04/2024
ms.custom: 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.search.form: 
ms.dyn365.ops.version: 10.0.39
---

# Import features from the repository

[!INCLUDE[banner](../../includes/banner.md)]

The Dataverse repository contains Electronic invoicing features that are shared with your configuration provider. All Electronic invoicing features that Microsoft provides are shared with all companies. You automatically have access to all the Electronic invoicing features that Microsoft releases and publishes to the Dataverse repository.

To start to work with Electronic invoicing features that are shared with your configuration provider, import them into your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment from the Dataverse repository. Then review the feature details, such as the Electronic reporting (ER) configurations and processing pipelines.

## Set up integration with Dataverse

To use this functionality, you should have a Dataverse environment that's connected to your Dynamics 365 Finance environment. For more information, see the following articles:

- [Enable Power Platform Integration](../../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md)
- [Connect finance and operations apps with a new Microsoft Dataverse instance](../../../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv.md)
- [Connect finance and operations apps with an existing Microsoft Dataverse instance](../../../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv.md)

You should also add a security role to access tables in Dataverse by following these steps:

1. Create a new security role as described in [Create or edit a security role](/power-platform/admin/create-edit-security-role).
2. In that security role add **Create, Read, Write, Delete, Append, Append to, Assign, Share** permissions for **Organization** to the following tables: **Electronic Reporting Configuration File, Electronic Reporting Configurations Index File, Globalization Feature File, and Globalization Features Index File**. 
3. Assign the created security role to users as described in [Assign security roles](/power-platform/admin/assign-security-roles).

## Import a feature from the Dataverse repository

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
1. Select **Import** to open the **Import feature from Dataverse repository** lookup.
1. To browse the Electronic invoicing features that are available for a specific configuration provider in the Dataverse repository, select **Synchronize** to sync your organization's Finance or Supply Chain Management environment. After synchronization is completed, the list of available Electronic invoicing features is updated from the Dataverse repository. This update might take a few minutes.
1. Select the feature to import, and then select **Import**.

To view the imported Electronic invoicing feature, make sure that the correct configuration provider is selected. By default, features that the active configuration provider created are filtered out. You can adjust the filter to view features that were created by other configuration providers, such as Microsoft.

> [!NOTE]
> It may take up to two weeks for a new Electronic invoicing feature released by Microsoft or a new version of a feature released by Microsoft to appear in the Dataverse repository. You may also need to manually trigger the update of the Globalization solution package in your Power Platform admin center (PPAC) portal. See [Manage Dynamics 365 apps](/power-platform/admin/manage-apps.md#environment-level-view-of-apps) for more details on how to update solutions in PPAC.

You can now work with the imported feature. You can review its details and create a new feature by using the imported feature as a template.

> [!NOTE]
> You can modify a feature only if it was created by the configuration provider that's currently active. You can create a new feature by using the original feature as a base. You can then make the required changes or set up the parameters.
