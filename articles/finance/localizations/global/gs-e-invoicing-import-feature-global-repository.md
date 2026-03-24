---
title: Import features from the repository
description: Learn how to import Globalization features from the Dataverse repository, including a step-by-step process for importing features.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.custom: 
  - bap-template
---

# Import features from the repository

[!INCLUDE[banner](../../includes/banner.md)]

The Dataverse repository contains electronic invoicing features that you can share with your configuration provider. Microsoft shares all electronic invoicing features with all companies. You automatically get access to all the electronic invoicing features that Microsoft releases and publishes to the Dataverse repository.

To start working with electronic invoicing features that you can share with your configuration provider, import them into your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment from the Dataverse repository. Then, review the feature details, such as the Electronic reporting (ER) configurations and processing pipelines.

## Set up integration with Dataverse

To use this functionality, you need a Dataverse environment that's connected to your Dynamics 365 Finance environment. For more information, see the following articles:

- [Enable Power Platform Integration](../../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md)
- [Connect finance and operations apps with a new Microsoft Dataverse instance](../../../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv.md)
- [Connect finance and operations apps with an existing Microsoft Dataverse instance](../../../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv.md)

Also, add a security role to access tables in Dataverse by following these steps:

1. Create a new security role as described in [Create or edit a security role](/power-platform/admin/create-edit-security-role).
1. In that security role, add **Create, Read, Write, Delete, Append, Append to, Assign, Share** permissions for **Organization** to the following tables: **Electronic Reporting Configuration File, Electronic Reporting Configurations Index File, Globalization Feature File, and Globalization Features Index File**. 
1. Assign the created security role to users as described in [Assign security roles](/power-platform/admin/assign-security-roles).

## Import a feature from the Dataverse repository

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
1. Select **Import** to open the **Import feature from Dataverse repository** lookup.
1. Select **Synchronize** to sync your organization's Finance or Supply Chain Management environment and browse the Electronic invoicing features that are available for a specific configuration provider in the Dataverse repository. After synchronization is completed, the list of available Electronic invoicing features is updated from the Dataverse repository. This update might take a few minutes.
1. Select the feature to import, and then select **Import**.

To view the imported Electronic invoicing feature, make sure that the correct configuration provider is selected. By default, the portal filters out features that the active configuration provider created. You can adjust the filter to view features that other configuration providers created, such as Microsoft.

> [!NOTE]
> It can take up to two weeks for a new Electronic invoicing feature released by Microsoft or a new version of a feature released by Microsoft to appear in the Dataverse repository. If you expect a feature update but it doesn't appear in the Dataverse repository, or if auto-updates are disabled in your environment, you can also manually trigger the update of the Globalization solution package in your Power Platform admin center portal. To learn more about how to update solutions in Power Platform admin center, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps#environment-level-view-of-apps).

You can now work with the imported feature. You can review its details and create a new feature by using the imported feature as a template.

> [!NOTE]
> You can modify a feature only if the active configuration provider created it. You can create a new feature by using the original feature as a base. You can then make the required changes or set up the parameters.

## Additional information

[Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
