---
# required metadata

title: Commerce offline database implementation considerations and troubleshooting
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

# Commerce offline database implementation considerations and troubleshooting

[!include[banner](../includes/banner.md)]

This topic is intended for people who implement offline functionality related to the Dynamics 365 Commerce Modern POS or Store Commerce applications. This article shall detail the features and functionality, implementation tips, and troubleshooting methods related to the usage of offline functionality.

## Overview

Proper configuration and synchronization of data is crucial to a correct implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synchronized, the whole environment is effectively useless. Therefore, a top priority is to understand what is required to configure, generate, synchronize, and verify data across the full implementation. This goes from Commerce headquarters through the Commerce Scale Unit to the brick-and-mortar stores that use Modern POS (With or without an offline database) and other in-store components. CDX is the Commerce functionality that replicates and synchronizes data across databases. However, CDX differs from typical data replication functionality because it also allows for filtering. Therefore, CDX helps minimize data sets by generating only data that is specific to the channels that were specified for selection, filtering specific tables from offline databases, and filtering expired records for data that is no longer used, such as expired discounts.

Before you go through this topic, it's important that you understand the concepts of a channel (store), registers and devices, and the Modern POS offline database. Therefore, we recommend that you review some of the resources at the end of this topic, such as the Device management implementation guide and the overview of the Commerce architecture.


## Important offline features

For details regarding features that enhance or alter the data synchronization of an offline database (Based on Commerce Data Exchange (CDX)), review the CDX features detailed in the [Commerce Data Exchange best practices](CDX-Best-Practices.md)

- **Pause offline synchronization** – As a retail organization expands, it should take advantage of this offline profile feature as fully as possible. Growth is good, but data generation should be managed to help minimize the performance impact on the currently operating business. This feature enables the creation of channels, registers, and databases, but without requiring a massive, performance-affecting amount of data generation long before the registers are ever used.
- **Advanced offline** – The previously described advanced offline features can be helpful, but they should be used only if they suit the priorities and values of the retail organization. Although the advanced offline health check interval can help maximize online time, it will also be more forceful about pushing a register to offline mode if Commerce headquarters or the Commerce Scale Unit becomes unresponsive or unavailable for any reason. It can be valuable to maximize the performance of registers by quickly switching to offline mode instead of waiting for time-outs or repeated retry responses. However, this approach must be understood and managed against the standard seamless offline model that tries to stay online as long as possible, to allow for operations such as loyalty operations, additional payment methods, and customer orders. For offline specific features, recommendations, and troubleshooting, review the [Commerce offline database implementation considerations and troubleshooting](implementation-considerations-offline.md) document.



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

## Troubleshooting

If an error that occurs doesn't appear in the following table, create a support request, as required, so that Microsoft Support can help you fix the issue. This section will be updated over time with additional errors so it is valuable to review this document prior to implementing or updating Modern POS registers that utilize offline databases.

| Error | Description |
|------------|------------------------|
| You receive the following error message: "System.ArgumentNullException: Value cannot be null.Parameter name: connectionString at Microsoft.Dynamics.Retail.CommerceDataExchange.SqlTargetRequestHandler." | An error has occurred because of batch job statuses. (You can see the error in a failed download job on the **Download sessions** page.) Go to **System administration \> Inquiries \> Batch jobs**, find the data writing batch that is associated with the Commerce Scale Unit that the download job was supposed to be applied to, and change the batch job's status to **Withhold**. In environments that are earlier than version 10.0.12, we recommend that you also create a channel database group that is named **Legacy**, associate the **Default** channel database with this new group, and then exclude the new database group from all distribution schedules. CDX jobs should no longer be generated for the **Default** channel database in the **Legacy** group. |
| You can't perform the **Run now** command from the **Distribution schedule** page unless batch processing is used. | This change was intentionally made in version 10.0.11 because of performance issues that occurred if jobs were run during times when environments were most heavily used. In another change that was made as part of this feature enhancement, recurrence can't be used when the **Full data sync** command (full job synchronization) is run from the **Channel database** page in Commerce headquarters. Only a single occurrence can be run. We don't recommend that you change this behavior. However, if you're in a development environment, you can change it by going to **Commerce shared parameters \> Configuration parameters** and setting a new name, **CDX\_DISABLE\_FORCESCHEDULEINBATCH**, that has a value of **1**. |
| You receive the following error message: "Microsoft.Dynamics.Retail.CommerceDataExchange.SqlWriteRequestRunException: Failed to run SqlWriteRequestRunner for table AX.\<TABLE NAME\>." | An error has occurred because the length of one or more **DBO** tables has been extended, so that truncation of data was required. Therefore, a truncation failure has occurred. Generate a support request. For best practices, see [Enable custom Commerce Data Exchange synchronization via extension](cdx-extensibility.md). These best practices include removing the extended data type (EDT) extension on the table field that is being edited and using the CDX extension table to store the long (full) value that is required. |
| The download session is failing. The error message states, "...tried too many times." | Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce scheduler parameters**, and set the **Try count** field to **3**. If the value of this field is too high, download sessions might fail during high-usage times. After you complete this step, the job will set its status to **Canceled** and stop retrying itself. We recommend that you to read [Commerce Data Exchange best practices](CDX-Best-Practices.md). |
| You can't cancel a running CDX job. | If this issue occurs in a production environment, sign in to Microsoft Dynamics Lifecycle Services (LCS), and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| You use LCS to copy a Commerce headquarters database between environments, but the target environment also uses Commerce Scale Unit (Cloud) (previously known as Retail Cloud Scale Unit). | Create a support request, and specify whether it's acceptable to delete and reprovision the Commerce Scale Unit (Cloud), or whether the Commerce Scale Unit must be maintained as it currently exists. In both cases, downtime will be required. |
| CDX or environment issues occur after you change the value of the **Days transactions exist** field in the functionality profile. | If the **Days transactions exist** value is reduced by a large amount, one or more tables might become locked while purging occurs. Before you reduce the value by a large amount, we recommend that you generate a support request. Microsoft Support can remove the data before the value is changed. In this way, the database impact of the change will be minimized. |
| After you add multiple POS terminals, download sessions take a very long time, or there is overall Commerce headquarters slowness. | When you create a new Modern POS offline database and add it to the relevant channel database group, it inherits all existing download sessions since the last full database synchronization occurred. Even at the best of times, the exceptional data generation that might occur can be too large and therefore affect performance. At the worst (that is, busiest) of times, it can severely impair the environment's performance. We highly recommend that you have either a "dummy" channel database group (that is, a group that isn't associated with any distribution schedule job) that you assign to the newly generated terminals or a special offline profile where the **Pause offline synchronization** option is set to **Yes**. In this way, data generation can occur when it's required and when the system is most available to do it. (However, the system might pause multiple times as required.) If it's too late to use this approach, create a support request. |
| Normal, incremental (delta) synchronization takes much too long, even though the number of affected rows is small. | This issue can occur when a new channel (store) is created, because all the data must be re-created for the new store. We highly recommend that you have a "dummy" channel database that is associated with a "dummy" channel database group, and assign it to the newly generated channel (store). In this way, data generation can occur when it's required and when the system is most available to do it. If it's too late to use this approach, create a support request. |
| The P-job fails to create an upload session, and you receive the following error message: "System.Data.SqlClient.SqlException (0x80131904): Violation of PRIMARY KEY constraint 'PK\_UPLOADSESSION'. Cannot insert duplicate key in object 'crt.UPLOADSESSION'." | If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| When you try to download an upload session package from the **Upload sessions** page in Commerce headquarters, you receive the following error message: "Record for Id - \<Number\> not found." | Create a support request. |
| CDX download sessions fail to be applied, and you receive the following error message: "Failed to get download session package URI." | If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| No download sessions are applied, and no upload sessions are created. | If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| Upload sessions fail, and you receive the following error message: "Infolog for task Default:P-0001 (...) Error when bulk inserting data. Target table: RetailListingStatusLog." | An error has occurred because the upload session package contains multiple records in the **RetailListingStatusLog** table. These records have the same **StatusDateTime** value between two or more. If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| When a cashier tries to switch to offline mode or is forced offline, the switch fails. | There are many possible causes. First, verify basic information: Does the computer have available hard drive space? If you're using SQL Server Express, is the size of the offline database at the 10 gigabyte (GB) limit? Are there pending download sessions for the register? (Pending download sessions indicate that the register is no longer up to date. Therefore, offline switching might temporarily be prevented.) Additionally, we recommend that you contact Microsoft Support. If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |

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
