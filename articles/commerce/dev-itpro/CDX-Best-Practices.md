---
# required metadata

title: Commerce Data Exchange best practices
description: This article describes data synchronization with Commerce Data Exchange (CDX) in a Microsoft Dynamics 365 Commerce environment.
author: aneesmsft
ms.date: 07/05/2024
ms.topic: how-to
ms.search.form: RetailTerminalTable, RetailDevice
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2020-08-31
ms.custom: 
  - bap-template
---

# Commerce Data Exchange best practices

[!include[banner](../includes/banner.md)]

This article is intended for people who implement functionality that is related to data synchronization, Commerce Data Exchange (CDX), in a Microsoft Dynamics 365 Commerce environment. It gives best practices advice for implementations.

Proper data configuration and data synchronization are crucial to correctly functioning implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synchronized, the whole environment is effectively useless. Therefore, a top priority is to understand what is required to configure, generate, synchronize, and verify data across the full implementation from Commerce headquarters through the Commerce Scale Unit to the brick-and-mortar stores that use the Store Commerce app with an offline database.

Before you go through this article, it's important that you understand the concepts of a channel (store), registers and devices, and the Store Commerce app offline database. Therefore, we recommend that you review some of the resources at the end of this article, such as the Device management implementation guide and the overview of the Commerce architecture.

The main content of this article is organized into tables, where the first column includes lists of tag-like "associated areas" to help you more quickly find best practices that are related to your areas of concern. For new implementations, you might find it useful to copy these tables to a location where you can check off the various best practices as they're completed. In this way, you can help ensure that the implementation is prepared as well as possible before you move forward to production.

## Recommended configurations (with up-to-date maturity information to denote confidence of functionality)

The following configurations are released but cause changes to logic that may not be useful for all usage scenarios. These features were tested but haven't been thoroughly validated in all scenarios. In the following table, maturity is included to provide insight into the confidence of functionality.

Features change from month to month, so it's valuable to check back regarding the maturity of a particular feature and whether any new features are added. To apply any of the following features, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the left pane menu, select **Configuration parameters**. On the **Set up the configuration parameters** page, enter the key value (shown in the **Key** column in following table) into the **Name** field and the default value (shown in the **Description** column in the following table) into the **Value** field.

| Feature | Key | Description | Maturity |
|------------------|---------------------|------------------------------|-----------------------------------|
| Delayed download session creation | CDX_ENABLE_DELAYED_OFFLINE_DOWNLOAD_SESSION_CREATION | This parameter delays the download sessions from being created until after the Store Commerce app device is activated. This delay prevents creating unnecessary download sessions that may not be used for an extended period of time. The default value is **0**, which means disabled. To enable the feature, set the value to **1**.| High<br><br>(Feature was released in version 10.0.15.) |
| Package order enforcement | CDX_ENABLE_DOWNLOAD_SESSION_DEPENDENCY_ENFORCEMENT | This parameter enforces download session application to apply in order. If a download session application fails (which occurs after the number of attempts defined in the **Try count times** property, with a default value of three), the session is marked as **Suspended** and session applications won't proceed until the suspended session is retried or canceled. Using this key, you can't rerun previously applied sessions (sessions that aren't in the **Available** or **Suspended** state).<br><br>This feature will prevent download sessions failures due to unique key exceptions that could occur after applying download sessions out of order. The default value is **0**, which means disabled. | Moderate<br><br>(Feature was released in version 10.0.18.) |
| Roll back on failure | CDX_ENABLE_ROLLBACK_ON_FAILURE | Due to a known issue with this key, it isn't recommended for use. When you synchronize transactions from an offline database to the channel database (based on the P-job distribution schedule), the system normally merges records. During this process, records with duplicate transaction IDs are overwritten. With this feature, the offline synchronization instead inserts records. This insertion prevents the overwrite and throws an error so the issue can be investigated. Currently, the purge of offline transactions post synchronization could fail, triggering the insert error and stopping the offline sync. Due to this issue, it's currently recommended that this feature should be disabled. The default value is **1**, meaning that it's enabled by default. It's highly recommended to change this value to **0**. | Low, due to known issue.<br><br>(Feature was released in version 10.0.13.) |

## Update configurations

You must initialize the base configuration data for Commerce scheduler after you perform the following steps:

1. Apply a service update.
2. Enable a Commerce feature that impacts a configuration key.

To initialize the base configuration data, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Initialize commerce scheduler**, where you're prompted as to whether you want like to proceed with initializing the base configuration data for Commerce scheduler. Performing this action after every update is key to maintaining functionality as it correctly sets the configuration data for new tables or columns. 
2. There's a parameter to **Delete existing configuration**. Unless you're explicitly instructed to do delete an existing configuration, or you're working on a nonproduction environment where losing the configuration doesn't create an impact, leave this parameter set to **No**.

> [!NOTE]
> As of the Commerce version 10.0.24 release, the Commerce scheduler can be set to run automatically after updates to Commerce headquarters. To enable this capability in Commerce headquarters, go to **Workspaces \> Feature management**, and enable the **Run "Initialize commerce scheduler" after Headquarters is updated** feature. 

## Valuable configurations

| Associated areas | Best practice |
|------------------|---------------|
| <ul><li>Parameters</li><li>Commerce scheduler</li><li>Retry</li></ul> | Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce scheduler parameters**, and set **Try count** to **3**. If this value is set is too high, download sessions might fail during periods of high usage. Also, verify that the **Full dataset generation interval in days** is set to **0**. This setting means that full dataset generation doesn't occur unless required by something other than time. Setting these values allows CDX to function as expected while reducing possible error or performance issues. |
| <ul><li>Functionality profile</li><li>Data retention</li><li>Return policy</li> | Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profile**, and then, in the **Functions** section, set **Days transactions exist** to a value that is the same as, or close to the value that is defined for the return policy. For example, if the return policy states an item can be returned within 30 days, set this field to **30** or **31**. If special exceptions are allowed beyond the usual policy, set the field to **60**, which allows for faster returns even beyond the usual policy limits). |
| <ul><li>Channel database group</li><li>Distribution schedule</li><li>Offline profile</li><li>Pause</li><li>Data</li><li>Download</li></ul> | Microsoft highly recommends that you have either a "dummy" channel database group (in other words, a group that isn't associated with any distribution schedule job) that you assign to the newly generated terminals, or a special offline profile where the **Pause offline synchronization** option is set to **Yes**. In this way, data generation occurs when required and when the system is most available to do it. (However, the system might pause multiple times as needed.) |

## Enable database index compression

Use database index compression features to help reduce the database size. For details on these features, see [Commerce database index compression](index-compression.md).

## Practices that affect performance

| Associated areas | Best practice |
|------------------|---------------|
| <ul><li>Channel database group</li><li>Offline profile</li><li>Pause</li><li>Data</li><li>Download</li></ul> | <p>Don't generate data for offline databases until that data is required so that an offline database can be used. The following scenario shows why this best practice is important.</p><p>A new Store Commerce app offline database that added to the relevant channel database group inherits all existing download sessions since the last full database synchronization occurred. 100 new Store Commerce app instances that have offline terminals are created, and a full synchronization hasn't occurred in two months. Only five scheduler jobs have actual changes every 20 minutes. (For example, these changes might involve prices and discounts, or customers, which can be updated often.) In this scenario, up to 2,000,000 download sessions are immediately generated and must be applied, regardless of whether the newly created terminals are activated and capable of applying this data.</p><p>Even at the best times, this type of exceptional data generation is large and affects performance. At the worst (that is, busiest) times, it severely impairs the environment's performance. Therefore, we highly recommend that you either have a "dummy" channel database group (that is, a group that isn't associated with any distribution schedule job) that you assign to the newly generated terminals, or set the **Pause offline synchronization** option for the offline profile to **Yes**. By setting the **Pause offline synchronization** option to **Yes**, you stop data generation for anything that uses the offline profile. Therefore, data generation can occur only when required (instead of constantly), and only when the system is most available to do it. (However, the system might pause multiple times as needed.) |
| <ul><li>Distribution schedule</li><li>Scheduler jobs</li><li>Upload</li></ul> | No more than one P-job (upload batch job) should occur at any time. If multiple P-job upload batch jobs are created that might occur in parallel, table locks and delays (performance degradation) can occur while data of the uploaded transactions is applied. The job doesn't have to occur multiple times at the same time, but can just occur frequently. |
| <ul><li>Parameters</li><li>Commerce scheduler</li><li>Post database sync</li></ul> | Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce scheduler parameters**. Under the **Post database sync** subheading, there are two fields that can impact performance for different reasons.<br><br>**Clean up irrelevant master data after sync** performs the store procedure **Strip Master Data** after each CDX download session is executed. This step deletes unnecessary records included in package generation, but not necessary for the offline functionality for that specific device as a member of a specific store (channel). This feature helps minimize data stored in the offline database. A smaller database can assist performance and minimize size issues if using an Express version of SQL. It's recommended to test this feature in Sandbox first as some custom SQL views could introduce dependencies between tables that this functionality isn't aware of, resulting in errors in functionality.<br><br> **Optimize database statistics automatically** runs an update on the table statistics for each table in the CDX download session applied to the channel database. Outdated table statistics cause more performance issues than fragmented indexes. When enabled, it's also recommended to add a specific flag into the configuration parameters. To add the flag, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**, navigate to the **Configuration parameters** listing, and enter the new flag **CDX_ENABLE_UPDATE_STATISTICS_FOR_REQUIRED_TABLE** with the value **1**. This configuration parameter will be automatically added to all environments in a future release, but it's valuable to verify that it exists. |

## Additional resources

- [Commerce Data Exchange troubleshooting](CDX-Troubleshooting.md)
- [Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)
- [Commerce offline implementation](implementation-considerations-offline.md)
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md)
- [Select an in-store topology](retail-in-store-topology.md)
- [Device management implementation guidance](../implementation-considerations-devices.md)
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)
- [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
