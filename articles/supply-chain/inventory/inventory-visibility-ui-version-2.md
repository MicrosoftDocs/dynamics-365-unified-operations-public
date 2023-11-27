---
title: Inventory Visibility app user interface version 2
description: This article describes the difference between version 1 and version 2 of the Inventory Visibility app user interface. It describes the new operations supported in version 2 and how to migrate to it from version 1.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/27/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Inventory Visibility app user interface version 2

The Inventory Visibility app runs in Microsoft Power Apps. The current version of the app supports two user interface versions. You can choose which version you prefer to use. The following versions are available:

- User interface version 2, which is referred to as *UI version 2* in this article
- User interface version 1, which is referred to as *UI version 1* in this article

This article describes the differences between the two versions, the new operations supported in UI version 2, and how to migrate from UI version 1 to UI version 2.

## Features and configurations supported by each version

The following settings and features are only accessible from the UI version 1 configuration page:

- Clean up of preloaded on-hand results
- Inventory Allocation relevant operations

> [!NOTE]
> The majority of the features for setting up and viewing preloaded on-hand results are supported by both UI versions. Only the clean up of existing preloaded on-hand result requires UI version 1.

The following settings and features are only accessible from UI version 2 pages:

- Support for 180 days available-to-promise (ATP) calculations
- Inventory adjustments via the user interface

The following settings are accessible both in UI version 1 and UI version 2 pages. Changes are synchronized between versions:

- Index hierarchy setup

All other features and settings can be accessed in the both UI versions, but changes aren't synchronized between versions.

## Switch between UI versions

If the first version of Inventory Visibility that you installed was `${specificVersion}` or later, the default user interface is UI version 2. If you first installed an older version of Inventory Visibility, the default user interface is UI version 1. <!-- KFM: Did you mean to specify a number here (instead of `${specificVersion}`)?-->

### Switch between UI versions 1 and UI version 2

Follow these steps to switch between UI versions:

1. Open the **Inventory Visibility** app in Power Apps.
1. On the navigation pane, select **UI Version Control**.
1. Select **Configuration entity version**.
1. Set **Entity version** to *2* or *1*, depending on which version of the UI (and Dataverse configuration entities) you want to use.
1. If you're moving to UI version 2, you'll probably want to migrate your UI version 1 settings, as described in the next section.

### Migrate configuration settings from UI version 1 to UI version 2

When you change from UI version 1 to UI version 2, Inventory Visibility updates to only use configuration values from the Dataverse entities that correspond to UI version 2. You'll still be able to read and update the legacy Dataverse entities using the pages from UI version 1, but changes to these settings won't have any effect unless you switch the entire app back to UI version 1. While UI version 2 is active, only the settings made on the UI version 2 pages are used. To view and edit the legacy settings from UI version 1, open the Inventory Visibility menu at the bottom of the navigation pane and then select **Legacy UI**. <!-- KFM: Please confirm this edit. -->

After you change to UI version 2, you can migrate your previous UI version 1 settings to the new Dataverse entities used by UI version 2. You can switch back to UI version 1 at any time, but you can't migrate settings from UI version 2 to UI version 1. If you later return to UI version 2 after working in UI version 1 for a while, you can remigrate your UI version 1 settings, but only newly created records will be migrated; updated and deleted records aren't replicated, so all of your previous UI version 2 settings will be kept.

To migrate your settings from UI version 1 to UI version 2, follow these steps:

1. Open the **Inventory Visibility** app in Power Apps.
1. On the navigation pane, select **Admin settings**.
1. On the **Migrate entities to V2** tile, select **Manage**.
1. A dialog opens where you must enter the credentials you used when installing the Inventory Visibility service. Enter the credentials and then select **Login**.
1. The system copies your existing settings from UI version 1 to UI version 2.

## Set up features and configurations in UI version 2

This section illustrates the usage of different features in version 2.

From start up page or left navigation bar, user can go to feature management to configure the use of different feature, including enable/disable feature and related settings. Under version 2, user can select "manage" button beside the corresponding feature descriptions, whereas for version 1, all these buttons will redirect to the legacy configuration page. Detailed coverages are as follows:

### Data Source settings

In this page user is presented with a list of data source names. In the detail form of each name, contains the below configuration for a data source:

- `Data Source Name`: The name of data source to be used in Inventory Visibility Add-in.
- `Dimension mappings`: The mapping of custom dimension name to base dimension name. User needs to specify data source name, customer dimension and base dimension correspondingly.
- `Physical measures`: Unlike version 1, user no longer needs to specify the data source for a physical measure, it's by default the current data source.
- `Calculated measures`: Unlike version 1, user specifies the measure in two steps: (1) Calculated measre metadata to specify the name and data source for a calculated measure; and (2) Calculated measure detail, each record consists of an addition / subtraction operator of an existing physical measure to a calculated measure with specified metadata.

### Available-to-Promise (ATP)

Below settings are for users configurating ATP. For user using ATP for a time period longer than 7 days, using version 2 of user interface is required.

- `Enable feature` controls on-off of the feature
- `Schedule for 180 days`: When enabled, the longest period for ATP calculation is 180 days; when disabled, the longest support is 7 days.

The below fields and reference tables are only valid for configurations when `Schedule for 180 days` option enabled:

- `Schedule common configurations`: Controls the schedule period as maximum number of days, whose value cannot exceed the max schedule period; and the bucket size controlling the group size of storage. ATP calculation under same group is generally faster than that of different groups.
- `Schedule measures`: Configures the calculated measure to calculate in ATP, and their maximum schedule period correspondingly.
- `Schedule index configuration`: The ATP calculation is required to be queried with a dimension combination as a subset of a defined dimension set in schedule configuration.

### Inventory Allocation

- `Enable feature` controls on-off of the feature
- `Allocation group` contains the group name for allocations. This is not in the same table of version 1, so change in one version is not reflected to the allocation configuration group in the other version.

### Advanced Warehouse Inventory

- `Enable feature` controls on-off of the feature
- `Use truncated dimensions`: When enabled, Warehouse items would support queries excluding certain dimensions for faster query and fewer storage. This would be enabled by default during configuration updates, unless at least one of below dimensions is included in index hierarchy: Batch ID, Serial ID, License Plate ID, WMS Location Id."

### Soft Reservation

For soft reservation feature, when feature is enabled, the option `filter unconfigured dimensions` would control the behavior when user reserves with dimensions not specified in `Reservation dimensions`

- `Enable feature` controls on-off of the feature
- `Filter unconfigured dimensions`: When enabled, soft reserve request that are not in reserve dimensions will be automatically purged; when disabled, system will only accept requests will all dimensions in reservation dimensions. Users making reservations from Dynamics 365 Supply Chain Management's Sales Orders is required to enable this option.
- `Reservation mappings`: Defines a mapping of a physical measure to its corresponding `available to reserve` calculated measures. User needs to specify reserving against a physical measure configured in soft reservation.
- `Reservation Dimensions`: Defines the set of dimensions that are expected to appear in reservation requests.

### Other features

For the features below, see their corresponding feature pages for detailed usage.

- Inventory Log History
- Inventory Summary
- Preloaded On hand (Clearing preloaded on-hand is required to operate on legacy configuration page)

## Configure the system in UI version 2

All changes under the UI pages requires a configuration update operation to activate.

User finds below operations in `Admin settings` section as below:

- Set of accessed tokens
- Show / update service configurations
- Migrate entities to V2. This is only needed for users using UI version 1 and wish to try out version 2.
- Delete all configuration / Clear user data.

## Sending API requests with version 2

Version 2 also provides the capability of users to send API directly. It supports the use of below APIs:

1. On hand query
2. Inventory Adjustment (on hand change)
3. Soft Reserve

Each API page consists of 3 sections:

1. Product related settings: User can specify the Product ID, organization ID and dimension values.
2. API specific settings: Include the API specific attributes to specify. E.g., whether to query ATP or negative quantities for on hand query; the fields and values to add / subtract for an on hand change; and the reservation measure as well as whether to enforce an available to reserve calculation when doing soft reserve.
3. Request body. Upon updating the mentioned 2 sections, this field updates with latest request JSON body, where user can copy and save for later references.

When the required fields are set, the Query or Update button will be enabled for user to execute the API with info on the page.
