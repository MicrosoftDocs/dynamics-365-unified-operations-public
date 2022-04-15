---
# required metadata

title: Complete, publish, and deploy a Globalization feature
description: This topic provides information about the lifecycle of Globalization features.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Complete, publish, and deploy a Globalization feature

[!include [banner](../includes/banner.md)]

## Electronic invoicing feature versions

Electronic invoicing features are versioned. When a new version is created, the version number is automatically incremented.

Electronic invoicing feature versions follow a lifecycle that has up to three statuses:

- **Draft** – When a feature version has this status, you can edit its configuration attributes and its artifacts (for example, file format configurations).
- **Complete** – This status indicates that you've finished editing the feature version and don't intend to make any more updates to it. When a feature version has this status, you can no longer edit it or any of its components.
- **Published** – This status indicates that the feature version has been published to the Global repository that is associated with your organization. When a feature version has this status, you can no longer edit it or any of its components.

You can specify an **Effective from** date for a new version of an electronic invoicing feature. In this way, you can define a default version that can be used, or that can be overwritten when the feature is deployed to the service environment.

To change the status of an electronic invoicing feature version, follow these steps.

1. Sign in to your Regulatory Configuration Service (RCS) account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
3. On the left side of the **Electronic invoicing features** page, select the electronic invoicing feature.
4. On the **Versions** tab on the right side of the page, select the version.
5. Select **Change status**, and then select **Complete** (if the current status is **Draft**) or **Published** (if the current status is **Complete**).
6. In the message box, select **Yes** to confirm the request.

The manual change from **Complete** status to **Published** status is optional. Electronic invoicing feature versions are automatically updated to **Published** status when they are deployed to the service environment.

You can track the status in the **Feature version status** column on the **Versions** tab.

## Deploy feature versions

In RCS, you use the **Deploy** command to publish an electronic invoicing feature version to the target service environment or connected application.

1. On the left side of the **Electronic invoicing features** page, select the electronic invoicing feature.
2. On the **Versions** tab on the right side of the page, select the electronic invoicing feature version that you want to deploy to the service environment or connected application. The selected version must have a status of **Complete** or **Published**.
3. Select **Deploy**, and then select one or both of the following options to define the target of the deployment:

    - **Connected application** – The configuration that is provided by the application setup is written in the instance of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management that was previously associated with it.
    - **Service environment** – The electronic invoicing feature version is deployed to the service environment. Electronic invoicing is then ready to receive and process electronic documents that Finance or Supply Chain Management sends.

> [!NOTE]
> Usually, you will change the parameters of the Electronic reporting (ER) feature that must be deployed to the service environment. Changes to the connected application will be rare. You should deploy new versions to the connected application only when you change the corresponding parameters of your application.

To determine whether a specific version of an electronic invoicing feature is deployed to a specific environment, review the information on the **Environments** tab.

## Remove feature versions

In RCS, you can select **Cancel** to remove a specific electronic invoicing feature version from a service environment, if it was deployed there.

> [!IMPORTANT]
> The **Cancel** button works only for service environments. It doesn't remove anything from the connected application for the current electronic invoicing feature.

## Rebase electronic invoicing features

When one electronic invoicing feature is derived from another, you can select **Rebase** to update the derived feature with the changes that have been made in the original (parent) feature.

To rebase a derived version of a feature that you created, follow these steps.

1. Get the latest version of the feature by importing it from the Global repository. For more information, see [Import feature from Global repository](e-invoicing-import-feature-global-repository.md).
2. In the list of features, select the feature to rebase.
3. On the **Versions** tab, select **New** to create a draft version.
4. Select **Rebase**.
5. In the **Rebase** dialog box, select the version of the feature to rebase to.
6. Select **OK**.
7. Review the feature components, and make any changes that are required.
8. Select **Change status** to complete the rebased feature. When the rebase is completed, you can perform additional actions.

## Get a specific version of electronic invoicing features

When you create a new version of an electronic invoicing feature, the system creates a copy of the latest feature version. To use an earlier version of the feature as the base for a new version, select the version, and then select **Get this version command**. A new draft version of the feature is created that is a copy of the selected version.
