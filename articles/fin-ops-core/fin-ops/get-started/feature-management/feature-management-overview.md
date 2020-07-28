---
# required metadata
title: Feature management overview
description: This topic describes the Feature management feature and how you can use it.
author: ChrisGarty
manager: AnnBe
ms.date: 06/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  FeatureManagementWorkspace
audience: IT Pro, Application user
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: cgarty
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: 10.0.2
---

# Feature management overview

[!include [banner](../../includes/banner.md)]

Features are added and updated in every release. The Feature management experience provides a workspace where you can view a list of features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them.

## The Feature management workspace

You can open the **Feature management** workspace by selecting the appropriate tile on the dashboard. You will see a page that shows a list of features for all releases that are supported by the Feature management experience. Over time, Microsoft will enhance the Feature management experience so that it includes additional functionality to help you manage features.

The feature list includes the following information:

- **Feature name** – A description of the feature that was added.
- **Enabled status** – A symbol indicates whether a feature has been turned on (check mark), hasn't been turned on (blank), is scheduled to be turned on (clock), is mandatorily turned on (lock), requires attention before you turn it on (warning), or can't be enabled (X). The setting that is shown is used for all legal entities. Note that even when a feature has been turned on, it's still controlled by security. Therefore, the feature will be available only to users who have access to it, based on their security role. It will also be available only in legal entities that the user has access to.
- **Enable date** – The date when the feature was turned on or is scheduled to be turned on.
- **Feature added** – The date when the feature was added to your environment. This date is automatically entered when you update your environment during the monthly release cycles.
- **Module** – The module that is affected by the new feature.

When you select a feature, additional information appears in the details pane to the right of the feature list. At the top of the pane, you will see the feature name, the date when the feature was added, the module that is affected by the feature, and a **Learn more** link. Select this link to view the documentation for the feature. If documentation isn't available, you're taken to a temporary page. The details pane also includes a **Comments** field where you can add your own comments about the feature.

The **Feature management** workspace also has several tabs, each of which shows a list of features.

- **New** – This tab shows all features that have been added since the last monthly update. If you've skipped any monthly updates, the tab shows all the new features that have been added since the last time that you updated. The newest features appear at the top of the list. The total number of new features is also shown on a tile at the top of the page.
- **Not enabled** – This tab shows all features that haven't been turned on. The newest features appear at the top of the list. The total number of new features that haven't been turned on is also shown on a tile at the top of the page.
- **Scheduled** – This tab shows all features that have been scheduled to be turned on in the future. The features that have the earliest scheduled date appear at the top of the list. The total number of schedule new features is also shown on a tile at the top of the page.
- **All** – This tab shows all features. The newest features appear at the top of the list.

## Turn on a feature

If a feature hasn't been turned on, an **Enable Now** button appears in the details pane. You can use this button to turn on the feature.

- Select the feature to turn on, and then, in the details pane, select **Enable Now**. The feature is turned on.

Some features can't be turned off after you turn them on. If the feature that you're trying to turn on can't be turned off, you receive a warning. At that point, you can select **Cancel** to cancel the operation and leave the feature turned off. However, if you select **Enable** to turn on the feature, you won't be able to turn it off later.

Some features will display a message that provides additional information before you turn them on. These features are indicated by a yellow warning symbol. You should read the additional information carefully to better understand what will happen when the feature is enabled. However, you can still select **Enable** to turn on the feature.

Some features will display a message that the feature can't be enabled until an action is taken. These features are indicated by a red X symbol. You must take the actions described in the description before the feature is enabled. For example, if you can't use a feature until a configuration key is disabled, then you must disable the configuration key first and then return to Feature management to enable the feature.

After a feature is turned on, a message appears below the **Learn more** link in the details pane. This message either states that the feature was turned on or indicates the future date when the feature is scheduled to be turned on. It appears every time that you select the feature in the feature list.

Features that are scheduled to be turned on in the future appear on the **Scheduled** tab. A batch process will turn them on at midnight on the specified date, based on the time zone that is represented by the system date.

## Reschedule a feature

If a feature has been scheduled to be turned on in the future, a **Schedule** button appears in the details pane. You can use this button to change the **Enable date** value to a different date.

1. Select the scheduled feature to reschedule, and then, in the details pane, select **Schedule**.
2. In the dialog box that appears, in the **Enable date** field, specify the new date when the feature should be turned on.
3. Select **Enable** to reschedule the feature or **Disable** to cancel the schedule.

## Turn off a feature

If a feature has already been turned on, a **Disable** button appears in the details pane. You can use this button to turn off the feature. The **Disable** button isn't available if the feature can't be turned off after it's turned on.

- Select the feature to turn off, and then, in the details pane, select **Disable**. The feature is turned off, and the **Enable date** field is cleared.

After a feature is turned off, a message appears below the **Learn more** link in the details pane. This message states that the feature hasn't yet been turned on. It appears every time that you select the feature in the feature list. Features that haven't been turned on appear on the **Not enabled** tab.

## Features that must be turned on

Sometimes, a critical feature is delivered that must be turned on automatically when you do an update. These features will be turned on automatically on the date that is specified in the **Enable date** field. For these features, a message appears below the **Learn more** link in the details pane. This message either states that the feature was turned on or indicates the future date when the feature will be turned on. It appears every time that you select the feature in the feature list.

## Enable all features

By default, all features that are added to your environment are turned off. You can enable all features by selecting the **Enable all** button. 

When you select **Enable all**, an option will appear where you need provide the following information:
- A list of all features that require confirmation before they can be enabled. If you want to enable the features in the list, select **Yes** for the **Enable features requiring confirmation** button.
- A list of all features that can't be enabled will be shown. Those features will not be enabled.

All features that can be enabled will be enabled. If a feature is already scheduled to be enabled in the future, the schedule will not change. 

## Turn on all features automatically

By default, all features that are added to your environment are turned off, unless they are mandatory features. However, if you want to automatically turn on all new features, you can use the drop-down list under the workspace title to change what occurs when new features are added.

- Select **Enable new features automatically** to automatically turn on all new features when they are added to your environment.
- Select **Do not enable new features automatically** to default all new features to off when they are added to your environment.


When you enable all feature automatically, it will enable all of the features that would be enabled when you click the **Enable all** button. It will not enable the features that require confirmation or the features that can't be enabled until an action is taken.

## Check for updates

Features are added to your environment after each update. However, you can manually check for updates by clicking on the **Check for updates** button. Any feature that was added to the system after the update will be added to the list of features. For example, if a flighted feature is enabled after a release, then you can check for updates and the feature will be added to your list.

## Assigning roles

The **Feature management** workspace can be opened by system admins, and also by users who are assigned to the Feature manager role or the Feature viewer role. These two roles were created to support the Feature management experience. Users in the Feature manager role can turn any feature on or off. They can also update the **Comments** field for the feature. Users in the Feature viewer role can only view the **Feature management** workspace. They can't turn features on or off.

The Feature manager role and Feature viewer role don't override the existing security that a user has. They just control whether the user can turn features on and off. They don't provide access to the features themselves.

## Features that use configuration keys

If a feature uses a configuration key, but the configuration key isn't turned on, the **Feature management** workspace doesn't show the feature in the list of available features. After you turn on the configuration key, you must update the feature list by using the **Check for update** menu item. The feature then appears in the feature list.

If you turn off the configuration key, the feature isn't removed from the feature list.

## Data entities

A data entity that is named **Feature management** lets you export the Feature management settings from one environment and then import them into another environment. This entity updates only existing features. The business logic in the entity also helps guarantee that the same rules that are used on the **Feature management** workspace will be applied when the import is done. For example, you can't override a mandatory feature setting by removing the date during import.

The following examples describe what occurs when you use the **Feature management** entity to import data.

- If you change the value of the **Enabled** field to **Yes**, the feature is turned on, and the **Enable date** field is set to the current date.
- If you change the value of the **Enabled** field to **No** or leave the **EnableDate** field blank, the feature is turned off, and the **Enable date** field is cleared. You can't turn off a mandatory feature or a feature that can't be turned off after it's turned on.
- If you change the value of the **EnableDate** field to a future date, the feature is scheduled for that date.
- If you change the value of the **Enabled** field to **Yes** and change the value of the **EnableDate** field to a future date, the feature is scheduled for that date. 
- If you change the value of the **Enabled** field to **No**, but you also change the value of the **EnableDate** field to a future date, the feature is scheduled for that date.
- If a feature is turned on, and you add an **EnableDate** field that is set to a future date, the feature remains turned on. To reschedule the feature, you must change the **Enabled** field to **No**.

## Feature management and flighting

Feature management lets you to control the features that are delivered in each release. Flighting lets Microsoft teams release features to a limited number of customers, so that those features can be tested and validated without affecting all customers. Feature management doesn't control the flighting of any features.

## New features are optional for 12 months

When a new non-critical feature is installed, it will be optional for a 12-month period. This allows you and your organization time to plan ahead for when to uptake a feature and have it tested against your daily operations. For more information, see [One Version service updates FAQ](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/one-version#what-about-new-features).

## Using Feature management to turn on ISV features or custom features

Feature management is currently unavailable for features from independent software vendors (ISVs) and custom features. However, Microsoft is adding more functionality to enhance Feature management. After those enhancements are completed, Microsoft will make Feature management available to all features and provide instructions for updating your features to use it.

## Frequently asked questions (FAQ)

### When are features added, removed, or changed? 
Features are added, removed, and changed through code changes. Environments need to be updated to receive those changes.

### Does a feature become mandatory automatically? 
No, a feature becoming mandatory is not an automatic action. The product teams need to make a code change.

### When do features become mandatory? 
The policy is that all new features will be opt-in for a 12-month period and will not require any change management until you enable the feature. The product teams can choose whether to make a feature mandatory after that period has ended. 

### Why isn't there a specific 'mandatory enabled date'? 
Update release timing is variable, environment update timing is variable, and customers can opt to skip some updates. As a result, specific dates are difficult to determine. 

### Where's the documentation for features that are being made mandatory? 
This documentation comes from the application teams. Often, these will be mentioned in [Removed or deprecated features](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features). 

### Is there an in-product notification or signal that a feature is going to be mandatory enabled? 
A notification mechanism related to making a feature mandatory does not exist today.

### Do features ever get enabled without the customer knowing about it? 
Yes, if features don't have a functional impact then they can be enabled by default.

### What is feature flighting and how does it relate to feature management? 
Feature flights are real-time on/off switches that Microsoft controls. They are separate from the customer control provided by Feature Management. 
- Private Preview features will not be listed in Feature Management until they are flighted on. In production, the customer needs to agree to be part of a special program for that to occur.
- Public Preview and Released (generally available) features will be listed in Feature Management unless they are flighted off. Flighting a feature off is considered a last resort option for product teams if a critical issue is found and would usually be a per-customer operation.

### Do features ever get flighted off without the customer knowing about it? 
Yes, if a feature is impacting the functioning of an environment that doesn't have a functional impact then they can be enabled by default.
