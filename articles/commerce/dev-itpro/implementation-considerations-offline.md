---
# required metadata

title: Commerce offline implementation considerations and troubleshooting
description: This topic provides an overview of Commerce
author: jashanno
ms.date: 05/11/2021
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

# Commerce offline implementation considerations and troubleshooting

[!include[banner](../includes/banner.md)]

This topic is intended for people who implement offline functionality related to the Dynamics 365 Commerce Modern POS or Store Commerce applications. This article shall detail the features and functionality, implementation tips, and troubleshooting methods related to the usage of offline functionality.

## Overview

Proper configuration and synchronization of data is crucial to a correct implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synchronized, the whole environment is effectively useless. Therefore, a top priority is to understand what is required to configure, generate, synchronize, and verify data across the full implementation. This goes from Commerce headquarters through the Commerce Scale Unit to the brick-and-mortar stores that use Modern POS (With or without an offline database) and other in-store components. CDX is the Commerce functionality that replicates and synchronizes data across databases. However, CDX differs from typical data replication functionality because it also allows for filtering. Therefore, CDX helps minimize data sets by generating only data that is specific to the channels that were specified for selection, filtering specific tables from offline databases, and filtering expired records for data that is no longer used, such as expired discounts.

Before you go through this topic, it's important that you understand the concepts of a channel (store), registers and devices, and the Modern POS offline database. Therefore, we recommend that you review some of the resources at the end of this topic, such as the Device management implementation guide and the overview of the Commerce architecture.


## Important offline features

For details regarding features that enhance or alter the data synchronization of an offline database (Based on Commerce Data Exchange (CDX)), review the CDX features detailed in the [Commerce Data Exchange best practices](CDX-Best-Practices.md)

| Feature name | Description |
|--------------|-------------|
| Advanced offline | This feature consists of a series of settings in the offline profile. These settings make additional offline switching scenarios available, give users the ability to switch to offline mode before they sign in to the POS, and allow for enhanced Commerce headquarters availability testing, so that you can switch to offline mode more often and more easily return to online status. |
| Offline status dashboard | A new dashboard showing the latest offline status, error, and details of the database for each device. |
| Performance based offline switching | In. |

- **Pause offline synchronization** – As a retail organization expands, it should take advantage of this offline profile feature as fully as possible. Growth is good, but data generation should be managed to help minimize the performance impact on the currently operating business. This feature enables the creation of channels, registers, and databases, but without requiring a massive, performance-affecting amount of data generation long before the registers are ever used.
- **Advanced offline** – The previously described advanced offline features can be helpful, but they should be used only if they suit the priorities and values of the retail organization. Although the advanced offline health check interval can help maximize online time, it will also be more forceful about pushing a register to offline mode if Commerce headquarters or the Commerce Scale Unit becomes unresponsive or unavailable for any reason. It can be valuable to maximize the performance of registers by quickly switching to offline mode instead of waiting for time-outs or repeated retry responses. However, this approach must be understood and managed against the standard seamless offline model that tries to stay online as long as possible, to allow for operations such as loyalty operations, additional payment methods, and customer orders.

### Advanced offline

This feature can be configured in the offline profile. Three settings are related to it:

- **Allow manual switch to offline before sign in** – This setting lets Modern POS users switch to offline mode before they sign in to the POS. It's helpful in scenarios where time-outs might occur before sign-in is completed, or where atypical response codes from the Commerce Scale Unit (Cloud or Self-hosted) are occurring. When this setting is turned on, a Modern POS user who is using an offline database can access the **Settings** menu from the POS sign-in page. This menu includes a new option for switching to offline mode. By selecting this option, the user can sign in directly against the offline database instead of first having to sign in via a call to the Commerce Scale Unit.
- **Enable advanced offline switching** – This setting enables Modern POS to switch to offline mode more easily and more often. Typically, Modern POS tries to maintain its online status and switches to offline mode only when such a switch is required to continue functionality. When this setting is turned on, Modern POS can switch more often, especially in scenarios that involve sign-in and additional Commerce Scale Unit responses that might be considered a delay to POS operation. This setting is most valuable in scenarios where speed is a higher priority than maintaining availability of online-only features (for example, paying with a gift card, which requires connection to Headquarters).
- **System health check interval (mins)** – This setting works as a subfeature of the **Enable advanced offline switching** setting that was just described. Usually, when that setting is turned off, and Modern POS is in offline mode, the POS waits a specific amount of time, based on configuration in the **Offline profile**, and then tries to reconnect to the Commerce Scale Unit during the next operation call that occurs. This advanced offline health check provides a more frequent, operation-independent method of checking online availability and switching more quickly as soon as online functionality is available again.


## Implementation considerations

This section describes configurations that should be considered when you begin to plan your POS usage scenarios while functioning offline. The features that are described here are related to data management and data configuration. Before you read the guidance that is provided here, we highly recommend that you understand these concepts. To gain additional information, it is recommended to read the [Commerce Data Exchange best practices](CDX-Best-Practices.md) document.

### SQL Server versions and licenses 
SQL Server comes in a variety of versions (such as SQL Server 2017 and SQL Server 2019) and a variety of editions (such as SQL Standard and SQL Express). For more in-depth information about these versions, see [Editions and supported features of SQL Server 2019 (15.x)](/sql/sql-server/editions-and-components-of-sql-server-version-15?view=sql-server-ver15#Cross-BoxScaleLimits). Also see the "Additional resources" later in this topic regarding additional versions.

For SQL Server versions, the only recommendation is to use a version that is currently still within the mainstream support date. Support dates can be searched for, by product, in [Search Product and Services Lifecycle Information](/lifecycle/products/).

#### Which SQL Server edition to use
While not an exhaustive list, here are the most used SQL Server editions for Dynamics 365 Commerce. Various details and use case scenarios are listed for each edition.

| Edition | Use cases |
|--------------|-------------|
| Express | When using SQL Server Express as SQL version for the offline database, it is crucial to understand that there are some limitations (such as CPU core count or RAM usage). The largest limiting factor is the 10 GB database size limit. Given the ability to use this version freely, Express is often used for a Modern POS offline database and not for a CSU (self-hosted) channel database. If the Express edition is used for a CSU (self-hosted), be aware that there could be data synchronization issues if the database ever reaches the 10 GB maximum size limit, which could cause issues such as loss of data. When using the Express edition, it is crucial to use compression and the Dynamics 365 Commerce features to exclude data from offline databases. For more information about SQL compression, see [Commerce Data Exchange best practices](CDX-Best-Practices.md#enable-table-and-index-compression). We recommended that you maintain a database at 8 GB in size, or less. |
| Standard | SQL Server Standard is often used for CSU (self-hosted) channel databases.  This provides enough size and system utilization to typically handle a CSU (self-hosted) channel database for one to several retail store locations. While not common, the Standard version is sometimes used for offline databases to cut away any limitations and maximize offline performance. Further, a more hybrid method may be used where only a set number of Modern POS registers utilize a full Standard version while other registers utilize the Express version (Or potentially no offline database, possibly using Cloud POS instead of Modern POS). |
| Enterprise | SQL Server Enterprise is rarely necessary, but there are scenarios where it could be valuable. For example, if hosting a CSU (self-hosted) in a datacenter VM for use across a large area of many devices, removing the limitations could be valuable to maximize performance capabilities. |

### Which features to use



## Troubleshooting

If an error that occurs doesn't appear in the following table, create a support request, as required, so that Microsoft Support can help you fix the issue. This section will be updated over time with additional errors so it is valuable to review this document prior to implementing or updating Modern POS registers that utilize offline databases.

| Error | Description |
|----------------------------------------------------------------------|-----------------------------------------------------------------------|
| Microsoft_Dynamics_Commerce_Runtime_AuthenticationMethodDisabled Microsoft_Dynamics_Commerce_Runtime_ChannelConfigurationNotFound Microsoft_Dynamics_Commerce_Runtime_ChannelNotPublished Microsoft_Dynamics_Commerce_Runtime_InvalidChannelConfiguration |  Unable to switch to offline mode. The channel information is either not available or not configured correctly. To resolve this issue, run the Channel configuration scheduler job (by default, this is the 1070 scheduler job). Please contact your system administrator. |
| Microsoft_Dynamics_Commerce_Runtime_CredentialsNotConfigured Microsoft_Dynamics_Commerce_Runtime_CredentialsNotFound Microsoft_Dynamics_Commerce_Runtime_InvalidAuthenticationCredentials Microsoft_Dynamics_Commerce_Runtime_LocalLogonFailed Microsoft_Dynamics_Commerce_Runtime_UserBlockedDueToTooManyFailedLogonAttempts | Unable to switch to offline mode. The user information is either not available or not configured correctly. To resolve this issue, run the Staff scheduler job (by default, this is the 1060 scheduler job). Please contact your system administrator. |
| Microsoft_Dynamics_Commerce_Runtime_CriticalStorageError  | To check the status offline db permissions, size, disk space (could use offline dashboard) |
| Microsoft_Dynamics_Commerce_Runtime_ElevatedUserSameAsLoggedOnUser | CHECKING |
| Microsoft_Dynamics_Commerce_Runtime_RealtimeServiceNotSupported Microsoft_Dynamics_Commerce_Runtime_TransientStorageError | Unable to switch to offline mode. The offline database is either not correctly installed or not configured correctly. Verify that everything has been setup successfully. Please contact your system administrator. |
| Microsoft_Dynamics_Commerce_Runtime_TerminalNotFound | To resolve this issue, run the Channel configuration scheduler job (by default, this is the 1070 scheduler job). Please contact your system administrator. |
| Microsoft_Dynamics_Internal_Server_Error | Create a support ticket |



## Additional resources

- [Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)
- [Commerce Data Exchange troubleshooting](CDX-Troubleshooting.md)
- [Commerce Data Exchange best practices](CDX-Best-Practices.md)
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md)
- [Select an in-store topology](retail-in-store-topology.md)
- [Device management implementation guidance](../implementation-considerations-devices.md)
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)
- [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
