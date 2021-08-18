---
# required metadata

title: Commerce offline database implementation considerations
description: This topic is intended for people who implement offline functionality related to the Dynamics 365 Commerce Modern POS or Store Commerce applications. It gives an overview, implementation tips, and overall guidance and troubleshooting that should be considered.
author: jashanno
ms.date: 08/18/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: global
ms.author: jashanno
ms.search.validFrom: 2021-08-31
---

# Commerce offline database implementation considerations

[!include[banner](../includes/banner.md)]

This topic is intended for people who implement offline functionality related to the Dynamics 365 Commerce Modern POS or Store Commerce applications. It gives an overview, implementation tips, and overall guidance that should be considered.

## Overview

Proper configuration and synchronization of data is crucial to a correct implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synchronized, the whole environment is effectively useless. Therefore, a top priority is to understand what is required to configure, generate, synchronize, and verify data across the full implementation. This goes from Commerce headquarters through the Commerce Scale Unit to the brick-and-mortar stores that use Modern POS (With or without an offline database) and other in-store components. Commerce Data Exchange (CDX) is the Commerce functionality that replicates and synchronizes data across databases. However, CDX differs from typical data replication functionality because it also allows for filtering. Therefore, CDX helps minimize data sets by generating only data that is specific to the channels that were specified for selection, filtering specific tables from offline databases, and filtering expired records for data that is no longer used, such as expired discounts.

Before you go through this topic, it's important that you understand the concepts of a channel (store), registers and devices, and the Modern POS offline database. Therefore, we recommend that you review some of the resources at the end of this topic, such as the [Device management implementation guidance](../implementation-considerations-devices.md) and [Dynamics 365 Commerce architecture overview](../commerce-architecture.md).


### Important offline features

For details regarding features that enhance or alter the usage of an offline database, review the offline features detailed in [Commerce Data Exchange best practices](CDX-Best-Practices.md).

## Implementation considerations

This section describes configurations that you should consider when you begin to plan your implementation. The features that are described here are related to data management and data configuration. 

- **Create a Scheduler job calendar** – How ofll ejob).
- **Pause offline synchronization** – As a ret used.
- **Advanced offline** – The previously descr.

### SQL Server versions and licenses 
SQL Server comes in a variety of versions (such as SQL Server 2017 and SQL Server 2019) and a variety of editions (such as SQL Standard and SQL Express). For more in-depth information about these versions, see [Editions and supported features of SQL Server 2019 (15.x)](/sql/sql-server/editions-and-components-of-sql-server-version-15?view=sql-server-ver15#Cross-BoxScaleLimits).

For SQL Server versions, the only recommendation is to use a version that is currently still within the mainstream support date. Support dates can be searched for, by product, in [Search Product and Services Lifecycle Information](/lifecycle/products/).

#### Which SQL Server edition to use
While not an exhaustive list, here are the most used SQL Server editions for Dynamics 365 Commerce. The use cases for each edition are also described.

| Edition | Use cases |
|--------------|-------------|
| Express | SQL Server Express has some major limitations (such as CPU core count or RAM usage), but the most major limiting factor is the 10 GB database size limit.  As a result, Express is often used for a Modern POS offline database, not for a CSU (self-hosted) channel database. If the Express edition is used for a CSU (self-hosted), be aware that there could be data synchronization issues if the database ever reaches the 10 GB maximum size limit, which could cause issues such as loss of data. When using the Express edition, it is crucial to use compression and the Dynamics 365 Commerce features to exclude data from offline databases. For more information about SQL compression, see [Commerce Data Exchange best practices](CDX-Best-Practices.md#enable-table-and-index-compression). We recommended that you maintain a database at 8 GB in size, or less. |
| Standard | SQL Server Standard is often used for CSU (self-hosted) channel databases.  This provides enough size and system utilization to typically handle a CSU (self-hosted) channel database for one to several retail store locations. |
| Enterprise | SQL Server Enterprise is rarely necessary, but there are scenarios where it could be valuable. For example, if hosting a CSU (self-hosted) in a datacenter VM for use across a large area of many devices, removing the limitations could be valuable to maximize performance capabilities. |

## Additional resources

- [Commerce Data Exchange troubleshooting](CDX-Troubleshooting.md)
- [Commerce Data Exchange best practices](CDX-Best-Practices.md)
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md)
- [Select an in-store topology](retail-in-store-topology.md)
- [Device management implementation guidance](../implementation-considerations-devices.md)
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)
- [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
