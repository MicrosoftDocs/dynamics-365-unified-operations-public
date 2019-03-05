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

Features are added and updated in every release of Dynamics 365 for Finance and Operations. The **Feature management** experience provides you with a workspace where you can view a list of features that have been delivered in each release. New features are disabled by default (see exception discussed below) and you can use the workspace to enable those features and view the documenation for them.

## Using the Feature management workspace

The **Feature management** workspace is found in the Workspaces menu area or in the **Common** area page. Click on the workspace icon and you will see a page with a list of features for all releases that have been supported by the Feature management experience. We will be enhancing the Feature management experience over time to include additional functionality to help you manage feature.

The list of features includes the following information:
1) The **Feature name** describes the feature that was added
2) The **Feature added** date is the date that the feature was added to your environment. It is added automatically when you update your environment during the monthly release cycles. 
3) The **Release** information is the version in which the feature was added. If you have skipped a monthly release cycle, you may see new features from more than one version. 
4) The **Enable** check box allows you to enable a feature by clicking on the box. You can disable the feature by clicking on the box to remove the check mark. The feature is enabled for all legal entities. Note that the feature may be enabled but it is still controlled by security. It will only show up for users that have access to the feature based on their security role. It will also only show up for legal entities to which the user has access. 
5) The **Enable date** field is the date on which the feature will be enabled. Once you enable a feature, the date will default to today's date. You can change the date to a future date to delay access to the feature but you can't select a date earlier than today.
6) The **Mandatory** field indicates that a feature must be enabled. You will not be able to control the release of a feature set to Mandatory. The field will be used for critical features that must be implemented. It will also be used for feature deprecations where we have provided notice that a feature will be deprecated at a future date and that date has been reached. 
7) The **Documenatation** icon will point to a URL where you can view the documentation. You will be routed to a temporary page if the documentation is not available

Each feature also comes with nnotes in the **Notes** box provided by the author of the feature. These notes are shown in the pane at the right of the workspace. You can also add your own comments in the **Comments** box on that pane. 

The features are shown in release order with the newest features at the top of the list in a tab labelled **All**. Features will remain on the list indefinitely so that you can still access features at a later date. We will be adding additional tabs to organize the features by age.

## Default action for enabling features

By default, all features are disabled. However, your implementation team may decide to enable all features automatically when they become available in a new version. You can enable this process change by modifying the value shown in the **Default action** drop down. Select **Enable new features** to automatically enable all features as of the date that the feature was added to the environment. You can still disable a feature at any time as long as it is not mandatory.

## Assigning roles

The **Feature management** workspace can be opened by System administrators and by users that are assigned to the **Feature manager** role that was created to support the Feature management experience. The **Feature manager** can enable and disable any feature and update the comments section for the feature. However, the **Feature manager** role does not override the existing security that the user has. The role only controls access to enabling and disabling the features. It does not provide access to the features. 
