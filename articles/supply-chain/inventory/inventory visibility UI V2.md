## Overview of Dynamics 365 SCM Inventory Visibility User Interface Version 2
Inventory Visibility power app offers a new model-driven user experience as user interface version 2 (referred to as UI version 2 in this article)

Inventory Visibility user now have the option to use only the legacy UI (also refferred to as UI version 1 in this article) or with UI version 2. 

This document talks about the difference between two versions, new operations supported under UI version 2, and how to migrate to UI version 2. 

### Supported features and configurations in different versions

Below settings and features are only accessible in the UI version 1 configuration page: 
- Clean up of preloaded onhand results. Note the majority of preloaded onhand feature settings and viewing the preloaded onhand result is supported by both versions, only the clean up of existing preloaded onhand result needs to be done in verion 1 UI
- Inventory Allocation relevant operations

Below settings and features are only accessible in UI version 2 pages: 
- Support for 180 days available-to-promise (ATP) calculation
- Inventory adjustment via UI

Below settings are accessible in both Version 1 and Version 2 pages, and the change in one version would be synchronized to the other version: 
- Index hierarchy setup

For other features and settings, they can be accessed in the both versions while the changes will not synchronize to corresponding pages in the other version. 

## Configuring Inventory Visibility in UI version 2

For users first time installing IV after `${specificVersion}`, the default user interface version is version 2. For earlier users whose first installation is before `${specificVersion}`, the default configuration is version 1. 

### Switching user interface versions

User can go to `UI Version Control` - `Configuration entity version` to set the version value. You can select the row and update the version number from 1 to 2. 
After the value is updated, configuration update API calls read configuration value from data verse entities corresponding to the version 2 user interface. 

Users are still able to access legacy UI (UI version 1) pages on the lower left of the Inventory Visibility power app menu and make adjustments on these pages even if the UI version 2 is enabled. 

However, when updating configurations, Inventory will only read from the pages under current UI version. 

### Migrating configuration from Version 1 to Version 2

For users already using version 1 and wish to switch to version 2 without manually re-create the entries, go to `Settings (Preview)` - `Admin settings` - `Migrate entities to V2` and click `Manage` button. This triggers a job to copy existing settings in version 1 interface to its equivalence in version 2. 

User can migrate entities multiple times. For the difference between migrations, only newly created records will be included in the latter migrations. The updated and deleted records will not be migrated. 

There is no reverse process to migrate configuration from version 2 to version 1. However, user can switch the user interface to version 1 at any time by going to `UI Version Control` - `Configuration entity version` to set the version value as 1. 

## Detailed setups for different features and configurations in Version 2

This section illustrates the usage of different features in Version 2. All changes under the UI pages requires a configuration update operation to activate. 

### Feature related setups

From start up page or left navigation bar, user can go to feature management to configure the use of different feature, including enable/disable feature and related settings. Under version 2, user can select "manage" button beside the corresponding feature descriptions, whereas for version 1, all these buttons will redirect to the legacy configuration page. Detailed coverages are as follows: 

#### Data Source settings

In this page user is presented with a list of data source names. In the detail form of each name, contains the below configuration for a data source: 
- `Data Source Name`: The name of data source to be used in Inventory Visibility Add-in. 
- `Dimension mappings`: The mapping of custom dimension name to base dimension name. User needs to specify data source name, customer dimension and base dimension correspondingly. 
- `Physical measures`: Unlike version 1, user no longer needs to specify the data source for a physical measure, it's by default the current data source. 
- `Calculated measures`: Unlike version 1, user specifies the measure in two steps: (1) Calculated measre metadata to specify the name and data source for a calculated measure; and (2) Calculated measure detail, each record consists of an addition / subtraction operator of an existing physical measure to a calculated measure with specified metadata. 

#### Available-to-Promise (ATP)

Below settings are for users configurating ATP. For user using ATP for a time period longer than 7 days, using version 2 of user interface is required. 

- `Enable feature` controls on-off of the feature
- `Schedule for 180 days`: When enabled, the longest period for ATP calculation is 180 days; when disabled, the longest support is 7 days. 

The below fields and reference tables are only valid for configurations when `Schedule for 180 days` option enabled: 
- `Schedule common configurations`: Controls the schedule period as maximum number of days, whose value cannot exceed the max schedule period; and the bucket size controlling the group size of storage. ATP calculation under same group is generally faster than that of different groups.
- `Schedule measures`: Configures the calculated measure to calculate in ATP, and their maximum schedule period correspondingly. 
- `Schedule index configuration`: The ATP calculation is required to be queried with a dimension combination as a subset of a defined dimension set in schedule configuration. 

#### Inventory Allocation

- `Enable feature` controls on-off of the feature
- `Allocation group` contains the group name for allocations. This is not in the same table of version 1, so change in one version is not reflected to the allocation configuration group in the other version. 

#### Advanced Warehouse Inventory 

- `Enable feature` controls on-off of the feature
- `Use truncated dimensions`: When enabled, Warehouse items would support queries excluding certain dimensions for faster query and fewer storage. This would be enabled by default during configuration updates, unless at least one of below dimensions is included in index hierarchy: Batch ID, Serial ID, License Plate ID, WMS Location Id."

#### Soft Reservation

For soft reservation feature, when feature is enabled, the option `filter unconfigured dimensions` would control the behavior when user reserves with dimensions not specified in `Reservation dimensions`

- `Enable feature` controls on-off of the feature
- `Filter unconfigured dimensions`: When enabled, soft reserve request that are not in reserve dimensions will be automatically purged; when disabled, system will only accept requests will all dimensions in reservation dimensions. Users making reservations from Dynamics 365 Supply Chain Management's Sales Orders is required to enable this option. 
- `Reservation mappings`: Defines a mapping of a physical measure to its corresponding `available to reserve` calculated measures. User needs to specify reserving against a physical measure configured in soft reservation. 
- `Reservation Dimensions`: Defines the set of dimensions that are expected to appear in reservation requests. 

#### Other features

For the features below, see their corresponding feature pages for detailed usage. 

- Inventory Log History
- Inventory Summary
- Preloaded On hand (Clearing preloaded on-hand is required to operate on legacy configuration page)

### System Configurations

User finds below operations in `Admin settings` section as below: 

- Set of accessed tokens
- Show / update service configurations
- Migrate entities to V2. This is only needed for users using UI version 1 and wish to try out version 2. 
- Delete all configuration / Clear user data. 

## Sending API requests with Version 2

Version 2 also provides the capability of users to send API directly. It supports the use of below APIs: 

1. On hand query
2. Inventory Adjustment (on hand change)
3. Soft Reserve

Each API page consists of 3 sections: 
1. Product related settings: User can specify the Product ID, organization ID and dimension values.
2. API specific settings: Include the API specific attributes to specify. E.g., whether to query ATP or negative quantities for on hand query; the fields and values to add / subtract for an on hand change; and the reservation measure as well as whether to enforce an available to reserve calculation when doing soft reserve. 
3. Request body. Upon updating the mentioned 2 sections, this field updates with latest request JSON body, where user can copy and save for later references. 

When the required fields are set, the Query or Update button will be enabled for user to execute the API with info on the page. 
