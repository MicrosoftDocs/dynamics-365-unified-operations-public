---
title: Complete and deploy a Globalization feature
description: Learn about the lifecycle of Globalization features, including overviews on electronic invoicing feature versions and deploying and remove feature versions.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 01/29/2024
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.search.form: 
ms.dyn365.ops.version: 10.0.39 
---

# Complete and deploy a Globalization feature

[!INCLUDE[banner](../../includes/banner.md)]

## Electronic invoicing feature versions

Electronic invoicing features are versioned. When a new version is created, the version number is automatically incremented.

Electronic invoicing feature versions follow a lifecycle that has up to three statuses:

- **Draft** – When a feature version has this status, you can edit its configuration attributes and its artifacts (for example, file format configurations).
- **Completed** – This status indicates that you finished editing the feature version and don't intend to make any more updates to it. When a feature version has this status, you can no longer edit it or any of its components.

You can specify an **Effective from** date for any new version of an Electronic invoicing feature. In this way, you can define a default version that can be used, or a version that can be overwritten, when the feature is deployed to the service environment.

To change the status of an Electronic invoicing feature version, follow these steps.

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
1. On the left side of the **Electronic invoicing features** page, select the Electronic invoicing feature.
1. On the **Versions** tab on the right side of the page, select the version.
1. Select **Change status**, and then select **Complete**.
1. In the message box, select **Yes** to confirm the request.

You can track the status in the **Feature version status** column on the **Versions** tab.

## Deploy feature versions

You use the **Deploy** command to deploy a version of an Electronic invoicing feature to the Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment.

1. On the left side of the **Electronic invoicing features** page, select the Electronic invoicing feature.
1. On the **Versions** tab on the right side of the page, select the version to deploy. The selected version must have a status of **Completed**.
1. Select **Deploy**, and then select the date when the feature version becomes effective.

## Remove feature versions

You can select **Cancel deployment** to remove a specific version of an Electronic invoicing feature from the service, if it was deployed there. The **Deployed to the service** column indicates whether a version is deployed to the service.

## Rebase Electronic invoicing features

When one Electronic invoicing feature is derived from another, you can select **Rebase** to update the derived feature with the changes that have been made in the original (parent) feature.

To rebase a derived version of a feature that you created, follow these steps.

1. Get the latest version of the feature by importing it from the Global repository. For more information, see [Import features from the repository](gs-e-invoicing-import-feature-global-repository.md).
1. In the list of features, select the feature to rebase.
1. On the **Versions** tab, select **New** to create a draft version.
1. Select **Rebase**.
1. In the **Rebase** dialog box, select the version of the feature to rebase to.
1. Select **OK**.
1. Review the feature components, and make any changes that are required.
1. Select **Change status** to complete the rebased feature. When the rebase is completed, you can perform additional actions.

## Get a specific version of Electronic invoicing features

When you create a new version of an Electronic invoicing feature, the system creates a copy of the latest feature version. To use an earlier version of the feature as the base for a new version, select the version, and then select **Get this version**. A new draft version of the feature is created that's a copy of the selected version.
