---
# required metadata
title: Feature management overview
description: This topic describes the Feature management feature and how you can use it.
author: ChrisGarty
ms.date: 10/05/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  FeatureManagementWorkspace
audience: IT Pro, Application user
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: cgarty
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: 10.0.2
---

# Feature management overview

[!include [banner](../../includes/banner.md)]

Features are added and updated in every release. The Feature management experience provides a workspace where you can view a list of features that have been delivered in each release. you can use the workspace to view the documentation and conditonally enabled or disable them .

## The Feature management workspace

You can open the **Feature management** workspace by selecting the appropriate tile on the dashboard. You will see a page that shows a list of features for all releases that are supported by the Feature management experience. 

The feature list includes the following information:

- **Feature name** – A description of the feature that was added.
- **Status** – A symbol indicates whether a feature has been enabled(check mark), hasn't been enabled (blank), is scheduled to be enabled (clock), is mandatorily enabled (lock), requires attention before you enable (warning), or can't be enabled (X). The setting that is shown is used for all legal entities. Note that even when a feature has been enabled on, it's still controlled by security. Therefore, the feature will be available only to users who have access to it, based on their security role. It will also be available only in legal entities that the user has access to.
- **Enable date** – The date when the feature was enabled or is scheduled to be enabled.
- **Feature added** – The date when the feature was added to your environment. This date is automatically entered when you update your environment during the monthly release cycles.
- **Feature state** – The current life cyle state of the feature: Preview, (blank), On by default and Mandatory. The states are covered in more details below. 
- **Module** – The module that is affected by the new feature.

> [!NOTE]
> **Feature state** is included starting in the release of the platform update for version 10.0.21.

When you select a feature, more information appears in the details pane to the right of the feature list. At the top of the pane, you will see the feature name, the date when the feature was added, the module that is affected by the feature, and a **Learn more** link. Select this link to view the documentation for the feature. If documentation isn't available, you're taken to a temporary page. The details pane also includes a **Comments** field where you can add your own comments about the feature.

The **Feature management** workspace also has several tabs, each of which shows a list of features.

- **New** – This tab shows all features that have been added since the last monthly update. If you've skipped any monthly updates, the tab shows all the new features that have been added since the last time that you updated. The newest features appear at the top of the list. The total number of new features is also shown on a tile at the top of the page.
- **Not enabled** – This tab shows all features that haven't been enabled. The newest features appear at the top of the list. The total number of new features that haven't been enabled is also shown on a tile at the top of the page.
- **Scheduled** – This tab shows all features that have been scheduled to be enabled in the future. The features that have the earliest scheduled date appear at the top of the list. The total number of schedule new features is also shown on a tile at the top of the page.
- **All** – This tab shows all features. The newest features appear at the top of the list.

## Preview features (Optional)

Product teams can decide to initially start a new feature as a preview feature. Preview features are not enabled by default and are optional. The owning product team will update features to released once they have completed a succesful preview period.  

> [!NOTE]
> Preview features are subject to specific preview terms and conditions: https://go.microsoft.com/fwlink/?linkid=2105274. 

## Released features (Optional)

These features have **(blank)** as value for Feature state. Features initially added as released are not enabled by default and are optional to enable. Features updated from preview will keep their enablement status.  

## On by default features (Optional)

Features that are updated to **On by default** are enabled by default, but can still be disabled. Released features that can be disabled are expected to move to this state in the major release that follows after the features have been in the released state for at least 6 months. Features that moved to **On by default** will be communicate in What's new (need link). The update is initiated by the owning product team.   

> [!NOTE]
> Since these features will be enabled automatically, it is important to determine if your organization is ready to uptake these features or if more time is required. For the latter it will be required to at least temporarily disable applicable features.

## Released features (Mandatory)

This is the final state of for features and it means that they are enabled and cannot be disabled without contacting Microsoft. Optional feature are expected to become mandatory after two major releases. Critical features can by exception be introduced as mandatory. 

## Example of expected feature lifecycles

Feature that can be disabled and were added as released and optional before or as part of the April release, are expected to move to **On by default** in the October release and to become **Mandatory** in April the following year.

Feature that cannot be disabled and were added as released and optional before or as part of the April release. are expected to become **Mandatory** in April the following year.

## Enable a feature

If a feature hasn't been turned on, an **Enable Now** button appears in the details pane. You can use this button to enable the feature.

- Select the feature to enable, and then, in the details pane, select **Enable Now**.

Some features can't be disabled after you enable them. If the feature that you're trying to enable on can't be enabled, you receive a warning. At that point, you can select **Cancel** to cancel the operation and leave the feature disabled. However, if you select **Enable** to enable the feature, you won't be able to disable it later.

Some features will display a message that provides additional information before you enable them. These features are indicated by a yellow warning symbol. You should read the additional information carefully to better understand what will happen when the feature is enabled. However, you can still select **Enable** to enable the feature.

Some features will display a message that the feature can't be enabled until an action is taken. These features are indicated by a red X symbol. You must take the actions described in the description before the feature is enabled. For example, if you can't use a feature until a configuration key is disabled, then you must disable the configuration key first and then return to Feature management to enable the feature.

After a feature is enabled, a message appears below the **Learn more** link in the details pane. This message either states that the feature was enabled or it indicates that the future date when the feature is scheduled to be enabled. It appears every time that you select the feature in the feature list.

Features that are scheduled to be enabled in the future appear on the **Scheduled** tab. A batch process will enable them at midnight on the specified date, based on the time zone that is represented by the system date.

## Reschedule a feature

If a feature has been scheduled to be enabled in the future, a **Schedule** button appears in the details pane. You can use this button to change the **Enable date** value to a different date.

1. Select the scheduled feature to reschedule, and then, in the details pane, select **Schedule**.
2. In the dialog box that appears, in the **Enable date** field, specify the new date when the feature should be enabled.
3. Select **Enable** to reschedule the feature or **Disable** to cancel the schedule.

## Disable a feature

If a feature has already been enabled, a **Disable** button appears in the details pane. You can use this button to disable the feature. The **Disable** button isn't available if the feature can't be disabled.

- Select the feature to disbale and then, in the details pane, select **Disable**. The feature is disabled, and the **Enable date** field is cleared.

After a feature is disabled, a message appears below the **Learn more** link in the details pane. This message states that the feature hasn't yet been enabled. It appears every time that you select the feature in the feature list. Features that haven't been enabled appear on the **Not enabled** tab.

## Features that must be enabled

Sometimes, a critical feature is delivered that must be enabled automatically when you do an update. These features will be enabled automatically on the date that is specified in the **Enable date** field. For these features, a message appears below the **Learn more** link in the details pane. This message either states that the feature was enabled or indicates the future date when the feature will be enabled. It appears every time that you select the feature in the feature list.

## Enable all features

You can enable all features by selecting the **Enable all** button. 

When you select **Enable all**, an option will appear where you need provide the following information:
- A list of all features that require confirmation before they can be enabled. If you want to enable the features in the list, select **Yes** for the **Enable features requiring confirmation** button.
- A list of all features that can't be enabled will be shown. Those features will not be enabled.

All features that can be enabled will be enabled. If a feature is already scheduled to be enabled in the future, the schedule will not change. 

## Enable all features automatically

If you want to automatically enable all new features, you can use the drop-down list under the workspace title to change what occurs when new features are added.

- Select `Enable new features automatically` to automatically enable all new features when they are added to your environment.
- Select `Do not enable new features automatically` to default all applicable new features to off when they are added to your environment.

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

- If you change the value of the **Enabled** field to **Yes**, the feature is enabled, and the **Enable date** field is set to the current date.
- If you change the value of the **Enabled** field to **No** or leave the **EnableDate** field blank, the feature is disabled, and the **Enable date** field is cleared. You can't disable a mandatory feature or a feature that can't be disabled after it's enabled.
- If you change the value of the **EnableDate** field to a future date, the feature is scheduled for that date.
- If you change the value of the **Enabled** field to **Yes** and change the value of the **EnableDate** field to a future date, the feature is scheduled for that date. 
- If you change the value of the **Enabled** field to **No**, but you also change the value of the **EnableDate** field to a future date, the feature is scheduled for that date.
- If a feature is enabled, and you add an **EnableDate** field that is set to a future date, the feature remains enabled. To reschedule the feature, you must change the **Enabled** field to **No**.

## Feature management and flighting

Feature management lets you control the features that are delivered in each release. Flighting lets Microsoft teams release features to a limited number of customers, so that those features can be tested and validated without affecting all customers. Feature management doesn't control the flighting of any features.

## Using Feature management to turn on ISV features or custom features

Feature management is currently unavailable for features from independent software vendors (ISVs) and custom features. However, Microsoft is adding more functionality to enhance Feature management. After those enhancements are completed, Microsoft will make Feature management available to all features and provide instructions for updating your features to use it.

## Frequently asked questions (FAQ)

### When are features added, removed, or changed? 
Features are added, removed, and changed through code changes by the owning product teams. Environments need to be updated to receive those changes.

### Does a feature become mandatory automatically? 
No, a feature becoming mandatory is not an automatic action. The owning product team needs to make a code change.

### Why isn't there a specific 'mandatory-enabled date'? 
Update release timing is variable, environment update timing is variable, and customers can opt to skip some updates. As a result, specific dates are difficult to determine. 

### Where's the documentation for features that are mandatory? 
This documentation comes from each Dynamics 365 application team. Often, these features will be mentioned in [Updates to client feature states](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/updates-client-feature-states) or [Removed or deprecated features](../../../dev-itpro/migration-upgrade/deprecated-features.md). 

### Is there an in-product notification or signal that a feature is going to be mandatory-enabled? 
A notification mechanism related to making a feature mandatory does not exist today.

### Do features ever get enabled without the customer knowing about it? 
Yes, there are two common scenarios where this happens. One is when a feature is moved to **On by default**, in this state it is still possible to disable the feature. Another when a feature is updated to **Mandatory**. These changes will only occur in combination with a major release. Critical features might by exception be moved to **Mandatory** at any update.  

### What is feature flighting and how does it relate to feature management? 
Feature flights are real-time on/off switches that Microsoft controls. They are separate from the customer control provided by Feature Management. 
- Private Preview features will not be listed in Feature Management until they are flighted on. In production, the customer needs to agree to be part of a special program for that to occur.
- Public Preview and Released (generally available) features will be listed in Feature Management unless they are flighted off. Flighting a feature off is considered a last resort option for product teams if a critical issue is found and would usually be a per-customer operation.

### Do features ever get flighted off without the customer knowing about it? 
Yes, if a feature is impacting the functioning of an environment that doesn't have a functional impact then they can be enabled by default.

### How can feature enablement be checked in code?
Use the **isFeatureEnabled** method on the **FeatureStateProvider** class, passing it an instance of the feature class. Example:

```xpp
if (FeatureStateProvider::isFeatureEnabled(BatchContentionPreventionFeature::instance()))
```

### How can feature enablement be checked in metadata?
The **FeatureClass** property can be used to indicate that some metadata is associated with a feature. The class name used for the feature should be used, such as **BatchContentionPreventionFeature**. This metadata is visible only in that feature. The **FeatureClass** property is available on menus, menu items, enum values, and table/view fields.

### What is a feature class?
Features in Feature Management are defined as *feature classes*. A feature class **implements IFeatureMetadata** and uses the feature class attribute to identify itself to the Feature Management workspace. There are numerous examples of feature classes available that can be checked for enablement in code using the **FeatureStateProvider** API and in metadata using the **FeatureClass** property. Example:

```xpp
[ExportAttribute(identifierStr(Microsoft.Dynamics.ApplicationPlatform.FeatureExposure.IFeatureMetadata))]
internal final class BankCurrencyRevalGlobalEnableFeature implements IFeatureMetadata
```

### What is the IFeatureLifecycle implemented by some feature classes?
IFeatureLifecycle is a Microsoft-internal mechanism for indicating the feature lifecycle stage. 
Features can be:
- `PrivatePreview` - Needs a flight to be visible.
- `PublicPreview` - Shown by default but with a warning that the feature is in preview.
- `Released` - Fully released.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
