---
# required metadata

title: Overview of Feature management
description: This topic describes the Feature management feature and how you can use it.
author: mikefalkner
manager: AnnBe
ms.date: 03/01/2019
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

# Overview of Feature management

[!include[banner](../../includes/banner.md)]

Features are added and updated in every release of Dynamics 365 for Finance and Operations. The **Feature management** experience provides you with a workspace where you can view a list of features that have been delivered in each release. New features are disabled by default and you can use the workspace to enable those features and view the documenation for them.

## Using the Feature management workspace

The **Feature management** workspace is found in the Workspaces menu area or in the **Common** area page. Click on the workspace icon and you will see a page with a list of features for all releases that have been supported by the Feature management experience. We will be enhancing the Feature management experience over time to include additional functionality to help you manage feature.

The list of features includes the following information:
1) The **Feature name** describes the feature that was added
2) The **Enabled** check box indicates that a feature has been enabled. The feature is enabled for all legal entities. Note that the feature may be enabled but it is still controlled by security. The feature will only be available to users that have access to the feature based on their security role. It will also only be available for legal entities to which the user has access. 
3) The **Enable date** is the date on which the feature was enabled or will be enabled. If the feature must be enabled after an update, you will see "Auto-enabled" in this column.
4) The **Feature added** date is the date that the feature was added to your environment. The date is added automatically when you update your environment during the monthly release cycles. 
5) The **Module** column describes which module is affected by the new feature.

The features are shown in release order with the newest features at the top of the list. Features will remain on the list indefinitely so that you can still access features at a later date. We plan to add tabs to organize the features by age.

When you select a feature, additional information is presented in a pane to the right of the feature list. At the top of the pane, you will see the feature name, the date that the feature was added, the module that is affected by the feature, and a link to the documentation. The link is labelled **Learn more**. Click on the link to view the documenation for the feature. You will be routed to a temporary page if the documentation is not available. You can also add your own comments in the **Comments** box on that pane. 

## Enable a feature
You can enable features using the **Enable** button on that pane.
1) If the feature is not enabled, an **Enable** button appears on the form. Click on **Enable**.
2) A dialog appears when you can specify the date on which you want to enable the feature. The date is defaulted to today's date.
3) Click on **Enable** to enable the feature.
4) Some features cannot be disabled once you have enabled them. You will receive a warning that the feature cannot be disabled and you will be able to cancel your request. However, once you enable that feature, you will not be able to disable it.
5) A message will appear in the pane below the "Learn more" link that describes that the feature was enabled or when the feature will be enabled. It will appear every time you select the feature in the grid. 

## Disable a feature
You can disable features using the **Disable** button that appears for features that have already been enabled. The button will not be available if the feature cannot be disabled. 
1) If the feature is enabled, a **Disable** button appears on the form unless the feature has been identified as a feature that can't be disabled once it is enabled. Click on **Disable**.
2) A dialog appears and the date on which you want to enable the feature is erased. 
3) A message will appear in the pane below the "Learn more" link that describes that the feature is not yet enabled. It will appear every time you select the feature in the grid. 

## Features that must be enabled
In a rare circumstance, we may deliver a critical feature that must be enabled automatically when you do an update. A message will appear in the pane below the "Learn more" link that describes that the feature was enabled automatically. It will appear every time you select the feature in the grid.  

## Assigning roles

The **Feature management** workspace can be opened by System administrators and by users that are assigned to the **Feature manager** or **Feature viewer** roles that were created to support the Feature management experience. The **Feature manager** can enable and disable any feature and update the comments section for the feature. The **Feature viewer** can view the **Feature management** workspace. 

The **Feature manager** and **Feature viewer** roles do not override the existing security that the user has. The role only controls access to enabling and disabling the features. It does not provide access to the features. 
