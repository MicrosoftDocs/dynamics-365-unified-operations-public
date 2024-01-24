---
title: Complete and deploy a Globalization feature
description: This article provides information about the lifecycle of Globalization features.
author: ilikond
ms.date: 01/29/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ikondratenko
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Complete and deploy a Globalization feature

[!include [banner](../../includes/banner.md)]

## Electronic invoicing feature versions

Electronic invoicing features are versioned. When a new version is created, the version number is automatically incremented.

Electronic invoicing feature versions follow a lifecycle that has up to three statuses:

- **Draft** – When a feature version has this status, you can edit its configuration attributes and its artifacts (for example, file format configurations).
- **Completed** – This status indicates that you've finished editing the feature version and don't intend to make any more updates to it. When a feature version has this status, you can no longer edit it or any of its components.

You can specify an **Effective from** date for a new version of an electronic invoicing feature. In this way, you can define a default version that can be used, or that can be overwritten when the feature is deployed to the service environment.

To change the status of an electronic invoicing feature version, follow these steps.

1. In the **Globalization studio** workspace, select the **Electronic invoicing** tile.
2. On the left side of the **Electronic invoicing features** page, select the electronic invoicing feature.
3. On the **Versions** tab on the right side of the page, select the version.
4. Select **Change status**, and then select **Complete**.
5. In the message box, select **Yes** to confirm the request.

You can track the status in the **Feature version status** column on the **Versions** tab.

## Deploy feature versions

You use the **Deploy** command to deploy an electronic invoicing feature version to the Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment.

1. On the left side of the **Electronic invoicing features** page, select the electronic invoicing feature.
2. On the **Versions** tab on the right side of the page, select the electronic invoicing feature version that you want to deploy. The selected version must have a status of **Completed**.
3. Select **Deploy**, and then select the date when the feature version will be effective from.

## Remove feature versions

You can select **Cancel deployment** command to remove a specific electronic invoicing feature version from the service, if it was deployed there. You can see in the **Deployed to the service** column if a specific feature version is deployed to the service or not.

## Rebase electronic invoicing features

When one electronic invoicing feature is derived from another, you can select **Rebase** to update the derived feature with the changes that have been made in the original (parent) feature.

To rebase a derived version of a feature that you created, follow these steps.

1. Get the latest version of the feature by importing it from the Global repository. For more information, see [Import features from the repository](GS-e-invoicing-import-feature-global-repository.md).
2. In the list of features, select the feature to rebase.
3. On the **Versions** tab, select **New** to create a draft version.
4. Select **Rebase**.
5. In the **Rebase** dialog box, select the version of the feature to rebase to.
6. Select **OK**.
7. Review the feature components, and make any changes that are required.
8. Select **Change status** to complete the rebased feature. When the rebase is completed, you can perform additional actions.

## Get a specific version of electronic invoicing features

When you create a new version of an electronic invoicing feature, the system creates a copy of the latest feature version. To use an earlier version of the feature as the base for a new version, select the version, and then select **Get this version** command. A new draft version of the feature is created that is a copy of the selected version.

