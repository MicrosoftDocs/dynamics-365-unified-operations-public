---
title: Commerce offline implementation considerations
description: This article provides an overview of Microsoft Dynamics 365 Commerce offline implementation considerations.
author: aneesmsft
ms.date: 07/05/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2021-08-31
ms.custom: 
  - bap-template
---

# Commerce offline implementation considerations

[!include[banner](../includes/banner.md)]

This article is intended for people who implement offline functionality related to the Microsoft Dynamics 365 Commerce Store Commerce application. This article describes features, functionality, and implementation tips that are related to the use of offline functionality.

Proper configuration and synchronization of data is crucial to a correct implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synchronized, the whole environment is effectively useless. Therefore, a top priority is to understand what's required to configure, generate, synchronize, and verify data across the full implementation. This full implementation extends from Commerce headquarters through the Commerce Scale Unit to the brick-and-mortar stores that use the Store Commerce app (with or without an offline database) and other in-store components. Commerce Data Exchange (CDX) is the Commerce functionality that replicates and synchronizes data across databases. However, CDX differs from typical data replication functionality because it also allows for filtering. CDX helps minimize data sets by generating only data that is specific to the channels specified for selection, filtering specific tables from offline databases, and filtering expired records for data that is no longer used, such as expired discounts.

Before reviewing this article, it's important that you understand the concepts of a channel (store), registers and devices, and the Store Commerce app offline database. We recommend that you review some of the resources listed at the end of this article, such as [Device management implementation guidance](../implementation-considerations-devices.md) and [Commerce architecture overview](../commerce-architecture.md).

## Important offline features

For details regarding features that enhance or alter the data synchronization of an offline database (based on CDX), see [Commerce Data Exchange best practices](CDX-Best-Practices.md). The following table highlights some important offline features. 

| Feature name | Description |
|--------------|-------------|
| Advanced offline | This feature consists of a series of settings in the offline profile. These settings make additional offline switching scenarios available, give users the ability to switch to offline mode before they sign in to the POS, and allow for enhanced Commerce headquarters availability testing so that you can easily switch to offline mode and return to online status. |
| Offline status dashboard | A new dashboard, provided as of the Commerce version 10.0.20 release, shows the latest offline status, error, and details of the database for each device. This dashboard can be found at **Retail and Commerce \> Channel setup \> POS setup \> Register offline status**. For this dashboard to function correctly the **Modern POS offline monitoring** feature must be turned on in the **Feature management** workspace, followed by the execution of the **1110** distribution schedule job. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). |
| Performance-based offline switching (POS seamless offline for performance degradation) | This feature, provided in release 10.0.20 and later, enables Store Commerce devices to switch to offline mode seamlessly when encountering outbound web request performance degradation. This feature requires the **Enable advanced offline switching** functionality to be enabled from the **Offline profile** page in Headquarters. The **POS seamless offline for performance degradations** feature must be turned on in the Feature management workspace. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). |

### Enable database index compression

In addition to the above features, use database index compression features to help reduce the database size. See [**Commerce database index compression**](index-compression.md) for details on these features.

### Advanced offline feature

The advanced offline feature can be configured in the offline profile. The following settings are related to this feature:

- **Allow manual switch to offline before sign in** – This setting lets Store Commerce app users switch to offline mode before they sign in to the POS. It's helpful in scenarios where timeouts might occur before sign-in is completed, or where atypical response codes from the Commerce Scale Unit (cloud or self-hosted) are occurring. When this setting is turned on, a Store Commerce app user who is using an offline database can access the **Settings** menu from the POS sign-in page. This menu includes a new option for switching to offline mode. When users select this option they can sign in directly against the offline database instead of first having to sign in via a call to the Commerce Scale Unit.
- **Enable advanced offline switching** – This setting enables the Store Commerce app to switch to offline mode more easily and more often. Typically, the Store Commerce app tries to maintain its online status and switches to offline mode only when such a switch is required to continue functionality. When this setting is turned on, the Store Commerce app can switch more often, especially in scenarios that involve sign-in and additional Commerce Scale Unit responses that might be considered a delay to POS operation. This setting is most valuable in scenarios where speed is a higher priority than maintaining availability of online-only features (for example, paying with a gift card, which requires connection to Headquarters).
- **System health check interval (mins)** – This setting works as a subfeature of the **Enable advanced offline switching** setting that was described previously. Usually, when that setting is turned off, and the Store Commerce app is in offline mode, the POS waits a specific amount of time, based on configuration in the **Offline profile**, and then tries to reconnect to the Commerce Scale Unit during the next operation call that occurs. This advanced offline health check provides a more frequent, operation-independent method of checking online availability and switching as soon as online functionality is available again.

## Implementation considerations

This section describes various aspects and configurations of the advanced offline feature that should be considered when you begin to plan your POS usage scenarios while functioning offline. The features that are described here are related to data management, offline usage, and data configuration. Before you read the guidance that is provided, we highly recommend that you understand these concepts. To gain additional information, we recommended that you read [Commerce Data Exchange best practices](CDX-Best-Practices.md).

### SQL Server versions and licenses 
SQL Server comes in various versions (such as SQL Server 2022 and SQL Server 2019) and various editions (such as SQL Standard and SQL Express). For more in-depth information about these versions, see [Editions and supported features of SQL Server 2022](/sql/sql-server/editions-and-components-of-sql-server-2022#scale-limits). Also see the [Additional resources](implementation-considerations-offline.md#additional-resources) listed at the bottom of this article.

Customers must use a SQL Server version that is currently under mainstream support. SQL Server versions that aren't under mainstream support aren't supported for use with Microsoft Dynamics 365 Commerce. Mainstream support dates for SQL Server versions (and other products) can be found here: [Search Product and Services Lifecycle Information](/lifecycle/products/).

Customers must also periodically ensure that the version of SQL Server they're using continues to remain under mainstream support. If the version of SQL Server they're using is approaching the end of mainstream support, they should upgrade to the latest SQL Server version to avoid potential disruptions. 

#### Which SQL Server edition to use
While not an exhaustive list, here are the most used SQL Server editions for Dynamics 365 Commerce. Various details and use case scenarios are listed for each edition.

| Edition | Use cases |
|--------------|-------------|
| Express | When using SQL Server Express as a SQL Server version for the offline database, it's important to understand that there are some limitations, such as CPU core count or RAM usage. The largest limiting factor is the 10 GB database size limit. Given the ability to use this version freely, Express is often used for a Store Commerce app offline database and not for a Commerce Scale Unit (CSU) self-hosted channel database. If the Express edition is used for a CSU (self-hosted), there could be data synchronization issues if the database ever reaches the 10 GB maximum size limit, which could cause issues such as loss of data. When using the Express edition, it's crucial to use index compression and the Dynamics 365 Commerce features to exclude data from offline databases. For more information on database compression, see [Commerce database index compression](index-compression.md). We recommended that you maintain a database at 8 GB in size, or less. |
| Standard | SQL Server Standard is often used for CSU (self-hosted) channel databases becuase it provides enough size and system utilization to typically handle a CSU (self-hosted) channel database for one to several retail store locations. While not common, the Standard version is sometimes used for offline databases to cut away any limitations and maximize offline performance. Further, a more hybrid method can be used where only a set number of Store Commerce app registers use a full Standard version while other registers use the Express version (or potentially no offline database, possibly using Store Commerce for web instead of the Store Commerce app). |
| Enterprise | SQL Server Enterprise is rarely necessary, but there are scenarios where it could be valuable. For example, if hosting a CSU (self-hosted) in a datacenter VM for use across a large area of many devices, removing the limitations could be valuable to maximize performance capabilities. |

### Offline testing

When you perform updates, it's crucial that you thoroughly test the Store Commerce app and offline functionality. Here's a nonexhaustive list of functions that you should test while you're offline, to verify correct functionality:

- Test cashier and manager sign-in.
- Test shift opening and closing.
- Test product browsing by using categories.
- Test product search by using the search bar.
- Test a cash and carry transaction.
- Test blind returns.
- Test discounts.
- Test unit of measure changes.
- Test payment functionality. All the following payment types should work and be available while you're offline:

    - Cash
    - Currency
    - Check
    - Loyalty
    - Card
    - Gift card

- Test **Show journal**.
- Start a transaction while you're in online mode. Then force the switch to offline mode (in other words, disconnect the system from the internet instead of manually switching to offline mode), and continue to check out.
- Perform the previous test when the offline database doesn't have the latest data for the customer (missing) or a product (missing) in cart, for example. In this case, the expectation is that the cashier receives a warning or error message, but is still able to continue to use the Store Commerce app in offline mode to perform new cash and carry transactions.
- Perform one or more transactions while you're offline. Then switch back to online mode, and verify that the transactions are uploaded.

## Troubleshooting

For more information about troubleshooting, see [Commerce offline implementation troubleshooting](implementation-offline-troubleshooting.md).

## Additional resources

[Commerce offline implementation troubleshooting](implementation-offline-troubleshooting.md)

[Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)

[Commerce Data Exchange troubleshooting](CDX-Troubleshooting.md)

[Commerce Data Exchange best practices](CDX-Best-Practices.md)

[Online and offline point of sale (POS) operations](../pos-operations.md)

[Dynamics 365 Commerce architecture overview](../commerce-architecture.md)

[Select an in-store topology](retail-in-store-topology.md)

[Device management implementation guidance](../implementation-considerations-devices.md)

[Configure, install, and activate the Store Commerce app](../retail-modern-pos-device-activation.md)

[Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
