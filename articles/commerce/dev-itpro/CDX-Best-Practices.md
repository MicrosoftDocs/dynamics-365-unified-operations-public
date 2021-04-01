---
# required metadata

title: Commerce Data Exchange best practices
description: This topic describes data synchronization with Commerce Data Exchange (CDX) in a Microsoft Dynamics 365 Commerce environment.
author: jashanno
ms.date: 03/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailTerminalTable, RetailDevice
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2020-08-31
ms.dyn365.ops.version: 10.0.12
---

# Commerce Data Exchange best practices

[!include[banner](../includes/banner.md)]

This topic is intended for people who implement functionality that is related to data synchronization, Commerce Data Exchange (CDX), in a Microsoft Dynamics 365 Commerce environment. It gives best practices advice for implementations.

## Overview

Proper data configuration and data synchronization are crucial to correctly functioning implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synchronized, the whole environment is effectively useless. Therefore, a top priority is to understand what is required to configure, generate, synchronize, and verify data across the full implementation from Commerce headquarters through the Commerce Scale Unit to the brick-and-mortar stores that use Modern POS with an offline database.

Before you go through this topic, it's important that you understand the concepts of a channel (store), registers and devices, and the Modern POS offline database. Therefore, we recommend that you review some of the resources at the end of this topic, such as the Device management implementation guide and the overview of the Commerce architecture.

The main content of this topic is organized into tables, where the first column includes lists of tag-like "associated areas" to help you more quickly find best practices that are related to your areas of concern. For new implementations, you might find it useful to copy these tables to a location where you can check off the various best practices as they are completed. In this way, you can help ensure that the implementation is prepared as well as possible before you move forward to production.

## Recommended configurations (with up-to-date maturity information to denote confidence of functionality)

The following configurations have been released but cause changes to logic that may not be useful for all usage scenarios. These features have been tested but have not been thoroughly validated in all scenarios. In the following table, maturity has been listed to provide insight in regard to confidence of functionality.

The features will change from month to month, so it is valuable to check back regarding the maturity of a particular feature and whether any new features have been added. To apply any of the following features, go to **Retail and Commerce > Headquarters setup > Parameters > Commerce parameters**.  On the leftmost menu, select **Configuration parameters**.  In the page that appears, enter the key (shown in the table below) into the **Name** field and the default value (listed in the **Description** column in the table below) into the **Value** field.

| Feature | Key | Description |  Maturity |
|------------------|---------------------|------------------------------|-----------------------------------|
| Delayed download session creation | CDX_ENABLE_DELAYED_OFFLINE_DOWNLOAD_SESSION_CREATION | This parameter delays the download sessions from being created until after the Modern POS device is activated.  This delay prevents creating unnecessary download sessions that may not be used for an extended period of time. The default value is **0**, which means disabled. To enable the feature, set the value to **1**.| High<br><br>(Feature was released in version 10.0.15.) |
| Package order enforcement | CDX_ENABLE_DOWNLOAD_SESSION_DEPENDENCY_ENFORCEMENT | This parameter enforces download session application to apply in order. If a download session application fails (which would occur after a number of attempts that are defined in the **Try count times** value that is by default a value of three), the session will be marked as **Suspended** and session applications will not proceed until the suspended session is retried or canceled. Using this key, you cannot rerun previously applied sessions (sessions that are not in the **Available** or **Suspended** state).<br><br>This feature will prevent download sessions failures due to unique key exceptions that could occur after applying download sessions out of order. The default value is **0**, which means disabled. | Moderate<br><br>(Feature was released in version 10.0.18.) |
| Roll back on failure | CDX_ENABLE_ROLLBACK_ON_FAILURE | **Due to a known issue with this key, it is not recommended for use.**  When synchronizing transactions from an offline database to the channel database (based on the P-job distribution schedule), the system normally merges records. This means that records with duplicate transaction IDs will be overwritten. With this feature, the offline synchronization will instead insert records. This insert prevents the overwrite and throws an error so the issue can be investigated. At this time, the purge of offline transactions post synchronization could fail, triggering the insert error and stopping the offline sync. Due to this, it is currently recommended that this feature should be disabled. The default value is **1**, meaning that it's enabled by default.  It is highly recommended to change this value to **0**. | Low, due to known issue.<br><br>(Feature was released in version 10.0.13.) |

## Updating configurations

The following should be performed after every update to the Dynamics 365 environment.

| Associated areas | Best practice |
|------------------|---------------|
| <ul><li>Parameters</li><li>Commerce scheduler</li><li>Initialization</li></ul> | Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Initialize commerce scheduler**. You will be asked if you would like to proceed with initializing the base configuration data for Commerce scheduler. Performing this action after every update is key to maintaining functionality as it correctly sets the configuration data for new tables or columns. There is also a parameter to **Delete existing configuration**.  Unless explicitly told to do so or working on a non-production environment where losing configuration will not create an impact, leave this set to **No**. |

## Valuable configurations

| Associated areas | Best practice |
|------------------|---------------|
| <ul><li>Parameters</li><li>Commerce scheduler</li><li>Retry</li></ul> | Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce scheduler parameters**, and set **Try count** to **3**. If the value of this field is too high, download sessions might fail during high-usage times.  Additionally, verify (or set) **Full dataset generation interval in days** to **0**. This means full dataset generation will not occur unless required by something other than time. Setting these values allows CDX to function in a more expected manner while reducing possible error or performance issues. |
| <ul><li>Functionality profile</li><li>Data retention</li><li>Return policy</li> | Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profile**, and then, in the **Functions** section, set **Days transactions exist** to a value that is the same as, or close to the value that is defined for the return policy. For example, if the return policy states an item can be returned within 30 days, set this field to **30**, **31**, or **60** if special exceptions are allowed beyond the usual policy (this would be twice the usual policy, allowing for faster returns even beyond the usual policy limits). |
| <ul><li>Channel database group</li><li>Distribution schedule</li><li>Offline profile</li><li>Pause</li><li>Data</li><li>Download</li></ul> | We highly recommend that you have either a "dummy" channel database group (that is, a group that isn't associated with any distribution schedule job) that you assign to the newly generated terminals, or a special offline profile where the **Pause offline synchronization** option is set to **Yes**. In this way, data generation can occur when it's required and when the system is most available to do it. (However, the system might pause multiple times as required.) |

## Practices that affect performance

| Associated areas | Best practice |
|------------------|---------------|
| <ul><li>Channel database group</li><li>Offline profile</li><li>Pause</li><li>Data</li><li>Download</li></ul> | <p>Don't generate data for offline databases until that data is required so that an offline database can be used. The following scenario shows why this best practice is important.</p><p>A new Modern POS offline database that has been added to the relevant channel database group inherits all existing download sessions since the last full database synchronization occurred. One hundred new Modern POS instances that have offline terminals are created, and a full synchronization hasn't occurred in two months. Only five scheduler jobs have actual changes every 20 minutes. (For example, these changes might involve prices and discounts, or customers, which can be updated often.) In this scenario, up to 2,000,000 download sessions are immediately generated and must be applied, regardless of whether the newly created terminals are activated and capable of applying this data.</p><p>Even at the best times, this type of exceptional data generation is large and affects performance. At the worst (that is, busiest) times, it severely impairs the environment's performance. Therefore, we highly recommend that you either have a "dummy" channel database group (that is, a group that isn't associated with any distribution schedule job) that you assign to the newly generated terminals, or set the **Pause offline synchronization** option for the offline profile to **Yes**. By setting the **Pause offline synchronization** option to **Yes**, you stop data generation for anything that uses the offline profile. Therefore, data generation can occur only when it's required, instead of constantly, and only when the system is most available to do it. (However, the system might pause multiple times as required.) |
| <ul><li>Distribution schedule</li><li>Scheduler jobs</li><li>Upload</li></ul> | No more than one P-job (upload batch job) should occur at any time. If multiple P-job upload batch jobs are created that might occur in parallel, table locking and delays (performance degradation) could occur while data of the uploaded transactions is being applied. The job doesn't have to occur multiple times at the same time. It can just occur frequently. |
| <ul><li>Parameters</li><li>Commerce scheduler</li><li>Post database sync</li></ul> | Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce scheduler parameters**. Under the **Post database sync** sub-heading, there are two fields that can impact performance for different reasons.<br><br>**Clean up irrelevant master data after sync** performs the store procedure **Strip Master Data** after each CDX download session is executed.  This step deletes unnecessary records that were included in package generation, but not necessary for the offline functionality for that specific device as a member of a specific store (channel). This feature assists in minimizing the data stored in the offline database.  A smaller database can assist performance and minimize size issues if using an Express version of SQL. It is recommended to test this feature in Sandbox first as some custom SQL views could introduce dependencies between tables that this functionality is not aware of, resulting in errors in functionality.<br><br> **Optimize database statistics automatically** runs an update on the table statistics for each table in the CDX download session applied to the channel database. Outdated table statistics cause more performance issues than fragmented indexes. When enabled, it is also recommended to add a specific flag into the configuration parameters.  If using this, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**, navigate to the **Configuration parameters** listing, and enter the new flag **CDX_ENABLE_UPDATE_STATISTICS_FOR_REQUIRED_TABLE** with the value **1**.  Note that in a future release this configuration parameter will be automatically added to all environments, but it is valuable to verify that it exists. |

## Additional resources

- [Commerce Data Exchange troubleshooting](CDX-Troubleshooting.md)
- [Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md)
- [Select an in-store topology](retail-in-store-topology.md)
- [Device management implementation guidance](../implementation-considerations-devices.md)
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)
- [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
