---
# required metadata

title: Feature management overview
description: This topic describes the Feature management feature and how you can use it.
author: mikefalkner
manager: AnnBe
ms.date: 03/21/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro, Application user
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mfalkner
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: 10.0.2
---

# Feature management overview

[!include[banner](../../includes/banner.md)]

Features are added and updated in every release of Microsoft Dynamics 365 for Finance and Operations. The Feature management experience provides a workspace where you can view a list of features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them.

## The Feature management workspace

You can open the **Feature management** workspace from either the **Workspaces** menu area or the **Common** area page. When you select the workspace icon, you will see a page that includes a list of features for all releases that are supported by the Feature management experience. Over time, Microsoft will enhance the Feature management experience so that it includes additional functionality to help you manage features.

The **Feature management** workspace contains a list of features and a details pane. The feature list includes the following information:

- **Feature name** – A description of the feature that was added.
- **Enabled** – A symbol indicates whether a feature has been turned on (check mark), has been scheduled (clock), or is turned off (blank). The setting that is shown here is used for all legal entities. Note that even when a feature has been turned on, it's still controlled by security. Therefore, the feature will be available only to users who have access to it, based on their security role. It will also be available only for legal entities that the user has access to.
- **Enable date** – The date when the feature was turned on or will be turned on.
- **Feature added** – The date when the feature was added to your environment. This date is automatically entered when you update your environment during the monthly release cycles.
- **Module** – The module that is affected by the new feature.

The newest features appear at the top of the list. Features will remain on the list indefinitely. Therefore, you will still be able to access features later. Microsoft plans to add tabs to better organize the features by age.

When you select a feature, additional information appears in the details pane to the right of the feature list. At the top of the pane, you will see the feature name, the date when the feature was added, the module that is affected by the feature, and a **Learn more** link. Select this link to view the documentation for the feature. If documentation isn't available, you will be taken to a temporary page. The details pane also includes a **Comments** field where you can add your own comments about the feature.

## Turn a feature on

If a feature hasn't been turned on, an **Enable** button appears in the details pane. You can use this button to turn the feature on.

1. Select the feature that you want to turn on, and then, in the details pane, select **Enable**.
2. A dialog box appears, where you can specify the date when the feature should be turned on. By default, this date is set to the current date.
3. Select **Enable** to turn the feature on.

    Some features can't be turned off after you turn them on. If the feature that you're turning on can't be turned off, you receive a warning. At this point, you can cancel the operation and leave the feature turned off. However, if you decide to turn the feature on, you won't be able to turn it off later.

After the feature is turned on, a message appears below the **Learn more** link in the details pane. This message either states that the feature was turned on or indicates when the feature will be turned on. This message will appear every time that you select the feature in the feature list.

## Turn a feature off

If a feature has already been turned on, a **Disable** button appears in the details pane. You can use this button to turn the feature off. The **Disable** button isn't available if the feature can't be turned off after it's turned on.

- Select the feature that you want to turn off, and then, in the details pane, select **Disable**.

    A dialog box appears, and the date when the feature was set to be turned on is deleted.

After the feature is turned off, a message appears below the **Learn more** link in the details pane. This message states that the feature hasn't yet been turned on. It will appear every time that you select the feature in the feature list.

## Features that must be enabled

In a rare circumstance, we might deliver a critical feature that must be turned on automatically when you do an update. In this case, a message will appear below the **Learn more** link in the details pane. This message will state that the feature was turned on automatically. It will appear every time that you select the feature in the feature list.

## Assigning roles

The **Feature management** workspace can be opened by system admins, and by users who are assigned to the **Feature manager** or **Feature viewer** roles that were created to support the Feature management experience. Users in the **Feature manager** role can turn any feature on and off. They can also update the comments section for the feature. Users in the **Feature viewer** role can only view the **Feature management** workspace. They can't turn features on and off.

The **Feature manager** and **Feature viewer** roles don't override the existing security that a user has. The role just controls access to turning features on and off. It doesn't provide access to the features themselves.
