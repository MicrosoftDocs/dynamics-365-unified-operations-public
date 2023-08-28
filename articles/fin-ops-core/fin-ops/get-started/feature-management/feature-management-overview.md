---
# required metadata
title: Feature management overview
description: This article describes Feature management and how you can use it.
author: Peakerbl
ms.date: 04/25/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  FeatureManagementWorkspace
audience: IT Pro, Application user
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 

ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: peakerbl
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: 10.0.2
---

# Feature management overview

[!include [banner](../../includes/banner.md)]


[!INCLUDE [PEAP](../../../../includes/peap-3.md)]

Features are added and updated in every release. The Feature management experience provides a workspace where you can view a list of features that have been delivered in each release. You can then use the workspace to view feature documentation, and to enable or disable features.

## The Feature management workspace

You can open the **Feature management** workspace by selecting the appropriate tile on the dashboard. You will see a page that shows a list of features for all releases that are supported by the Feature management experience. 

The feature list includes the following information:

- **Feature name** – A description of the feature that was added.
- **Status** – A symbol indicates whether a feature is turned on (check mark), is turned off (blank), is scheduled to be turned on (clock), is mandatory (lock), requires attention before you turn it on (warning symbol), or can't be turned on (X). The setting that is shown is used for all legal entities. Note that even when a feature has been turned on, it's still controlled by security. Therefore, the feature will be available only to users who have access to it based on their security role. It will also be available only in legal entities that the user has access to.
- **Enable date** – The date when the feature was turned on or is scheduled to be turned on.
- **Feature added** – The date when the feature was added to your environment. This date is automatically entered when you update your environment during the monthly release cycles.
- **Feature state** – The current lifecycle state of the feature: **Preview**, **Released** (shown as blank), **On by default**, and **Mandatory**. The states are covered in more details later in this article. 
- **Module** – The module that is affected by the new feature.

> [!NOTE]
> The **Feature state** column is included as of version 10.0.21.

When you select a feature, more information appears in the details pane to the right of the feature list. At the top of the pane, you will see the feature name, the date when the feature was added, the module that is affected by the feature, and a **Learn more** link. Select this link to view the documentation for the feature. If documentation isn't available, you're taken to a temporary page. The details pane also includes a **Comments** field where you can add your own comments about the feature.

The **Feature management** workspace also has several tabs, each of which shows a list of features.

- **New** – This tab shows all features that have been added since the last monthly update. If you've skipped any monthly updates, the tab shows all the new features that have been added since the last time that you updated. The newest features appear at the top of the list. The total number of new features is also shown on a tile at the top of the page.
- **Not enabled** – This tab shows all features that aren't turned on. The newest features appear at the top of the list. In addition, a tile at the top of the page shows the total number of new features that are currently off.
- **Scheduled** – This tab shows all features that have been scheduled to be turned on in the future. The features that have the earliest scheduled date appear at the top of the list. In addition, a tile at the top of the page shows the total number of scheduled features.
- **All** – This tab shows all features. The newest features appear at the top of the list.

## Feature recommendation notifications

Starting in version 10.0.35, users may start to see notifications informing them about recommended features. Users can review a recommended feature and request that it be enabled by an administrator. The request triggers a notification to be sent to administrators, which they can use to assess the suggested feature and decide whether it should be enabled for their organization.


## Feature states
Features can transition between several states, from being introduced in Feature management to eventually becoming mandatory in the product. This section describes the valid feature states.

### Preview features (optional)

Product teams can decide to initially start a new feature as a preview feature. Preview features aren't enabled by default, and they're optional. The owning product team will update features to released after they have completed a successful preview period.

> [!NOTE]
> Preview features are subject to specific preview [terms and conditions](https://go.microsoft.com/fwlink/?linkid=2105274). 

### Released features (optional)

The **Feature state** column for these features is blank. Features that are initially added as released aren't turned on by default, and enabling them is optional. Features that are updated from preview will keep their enablement status.

### On by default features (optional)

Features that are updated to **On by default** are turned on by default, but they can be disabled. After features that can be disabled have been in the **Released** state for at least six months, they're expected to move to this state in the next major release. Features that transition to **On by default** are expected to be communicated in the [What's new](../whats-new-changed.md) article for the release. The update is initiated by the owning product team.

> [!NOTE]
> Because these features will be enabled automatically, it's important that you determine whether your organization is ready to uptake these features, or whether more time is required. If more time is required, it might be necessary to temporarily disable these features. Note that the transition of a feature to **On by default** is typically done in the major release before the feature is targeted to become **Mandatory**. At that point, you won't have the option to disable the feature. 

### Mandatory

**Mandatory** is the expected final state for features. It indicates that the features are turned on, and that you can't disable them without contacting Microsoft. Optional features are expected to become mandatory after two major releases. Critical features can, by exception, be introduced as mandatory.

## Example of expected feature lifecycle

Features that can be disabled, and that were added as released and optional before or as part of the April release, are expected to transition to **On by default** in the following October release. They're then expected to become **Mandatory** in April of the following year.

Feature that can't be disabled, and that were added as released and optional before or as part of the April release, are expected to transition to **Mandatory** in April of the following year.

## Enable a feature

If a feature hasn't been turned on, an **Enable now** button appears in the details pane. You can use this button to enable the feature.

Some features can't be disabled after you enable them. If the feature that you're trying to turn on can't be enabled, you will receive a warning. At that point, you can select **Cancel** to cancel the operation and leave the feature disabled. However, if you select **Enable** to enable the feature, you won't be able to disable it later.

Some features will display a message that provides additional information before you enable them. These features are indicated by a yellow warning symbol. You should read the additional information carefully, to ensure that you understand what will happen when the feature is enabled. However, you can still select **Enable** to enable the feature.

Some features will display a message that the feature can't be enabled until an action is taken. These features are indicated by a red X symbol. You must take the actions described in the description before the feature is enabled. For example, if you can't use a feature until a configuration key is disabled, then you must disable the configuration key first and then return to Feature management to enable the feature.

After a feature is enabled, a message appears below the **Learn more** link in the details pane. This message either states that the feature was enabled or indicates the future date when the feature is scheduled to be enabled. It appears every time that you select the feature in the feature list.

Features that are scheduled to be enabled in the future appear on the **Scheduled** tab. A batch process will enable them at midnight on the specified date, based on the time zone that is represented by the system date.

## Reschedule a feature

If a feature has been scheduled to be enabled in the future, a **Schedule** button appears in the details pane. You can use this button to change the **Enable date** value to a different date.

1. Select the scheduled feature to reschedule, and then, in the details pane, select **Schedule**.
2. In the dialog box that appears, in the **Enable date** field, specify the new date when the feature should be enabled.
3. Select **Enable** to reschedule the feature or **Disable** to cancel the schedule.

## Disable a feature

If a feature has been enabled, a **Disable** button appears in the details pane. You can use this button to disable the feature. The **Disable** button isn't available if the feature can't be disabled. 

After a feature is disabled, a message appears below the **Learn more** link in the details pane. This message states that the feature hasn't been enabled. It appears every time that you select the feature in the feature list. Features that haven't been enabled appear on the **Not enabled** tab.

## Features that must be enabled

Sometimes, a critical feature is delivered that must be enabled automatically when you do an update. These features will be enabled automatically on the date that is specified in the **Enable date** field. For these features, a message appears below the **Learn more** link in the details pane. This message either states that the feature was enabled or indicates the future date when the feature will be enabled. It appears every time that you select the feature in the feature list.

## Enable all features

You can enable all features by selecting the **Enable all** button. 

When you select **Enable all**, an option appears where you must provide the following information:

- A list of all features that require confirmation before they can be enabled. If you want to enable the features in the list, select **Yes** for the **Enable features requiring confirmation** button.
- A list of all features that can't be enabled will be shown. Those features will not be enabled.

All features that can be enabled will be enabled. If a feature is already scheduled to be enabled in the future, the schedule will not change. 

## Enable all features automatically

If you want to automatically enable all new features, you can use the drop-down list under the workspace title to change what occurs when new features are added.

- Select **Enable new features automatically** to automatically enable all new features when they're added to your environment.
- Select **Do not enable new features automatically** if all applicable new features should be off by default when they're added to your environment.

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
- If a feature is enabled, and you add an **EnableDate** field that is set to a future date, the feature remains enabled. To reschedule the feature, you must change the value of the **Enabled** field to **No**.

## Feature management and flighting

Feature management lets you control the features that are delivered in each release. Flighting lets Microsoft teams release features to a limited number of customers, so that those features can be tested and validated without affecting all customers. Feature management doesn't control the flighting of any features.

## Using Feature management to turn on ISV features or custom features

Feature management is currently unavailable for features from independent software vendors (ISVs) and custom features. However, Microsoft is adding more functionality to enhance Feature management. After those enhancements are completed, Microsoft will make Feature management available to all features and provide instructions for updating your features to use it.

## Frequently asked questions (FAQ)

### When are features added, removed, or changed? 
Features are added, removed, and changed through code changes by the owning product teams. Environments must be updated to receive those changes.

### Does a feature become mandatory automatically? 
No, a feature doesn't become mandatory automatically. The owning product team must make a code change.

### Why isn't there a specific 'mandatory-enabled date'? 
Update release timing is variable, environment update timing is variable, and customers can opt to skip some updates. As a result, specific dates are difficult to determine. 

### Where's the documentation for features that are mandatory? 
This documentation comes from each Dynamics 365 application team. Often, these features will be mentioned in [Updates to client feature states](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/updates-client-feature-states) or [Removed or deprecated features](../../../dev-itpro/migration-upgrade/deprecated-features.md). 

### Is there an in-product notification or signal that a feature is going to be mandatory-enabled? 
A notification mechanism related to making a feature mandatory does not exist today.

### Do features ever get enabled without the customer knowing about it? 
Yes, features can be enabled without the customer's knowledge in the following situations:
- A feature is moved to **On by default**. In this state, the feature can still be disabled. 
- A feature is updated to **Mandatory**. This change will only occur in combination with a major release. Critical features might, by exception, be moved to **Mandatory** at any update.

### What is feature flighting and how does it relate to feature management? 
Feature flights are real-time on/off switches that Microsoft controls. They're separate from the customer control provided by Feature Management. 
- Private Preview features will not be listed in Feature Management until they're flighted on. In production, the customer needs to agree to be part of a special program for that to occur.
- Public Preview and Released (generally available) features will be listed in Feature Management unless they're flighted off. Flighting a feature off is considered a last resort option for product teams if a critical issue is found and would usually be a per-customer operation.

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
