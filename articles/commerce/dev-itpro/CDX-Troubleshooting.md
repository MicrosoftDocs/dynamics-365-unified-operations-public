---
# required metadata

title: Commerce Data Exchange troubleshooting
description: This article provides information that will help you troubleshoot CDX in implementations.
author: jashanno
ms.date: 01/30/2023
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

# Commerce Data Exchange troubleshooting

[!include[banner](../includes/banner.md)]

This article is intended for IT personas that are implementing functionality that is related to data synchronization (Commerce Data Exchange \[CDX\]) in a Microsoft Dynamics 365 Commerce environment. It provides information that will help you troubleshoot CDX in implementations.

Data configuration and synchronization are crucial to correct implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synced, the whole environment is effectively useless. Therefore, it's crucial that you understand the process of troubleshooting any issue that is related to data synchronization, from Commerce headquarters, through the Commerce Scale Unit, to the brick-and-mortar stores that use the Store Commerce app (either with or without an offline database) and other in-store components. This article provides some general guidance about how to mitigate or fix some issues. It also provides information about the best time to create a support request and the most important data to provide if you want to speed up a support request.

Before you go through this article, it's important that you understand the concepts of a channel (store), registers and devices, and the Store Commerce app offline database. Therefore, we recommend that you review some of the resources at the end of this article, such as the CDX implementation guide and the overview of the Commerce architecture.

## Scenario-based usage troubleshooting

In the following known scenarios, some configurations in Commerce headquarters might cause out-of-box CDX functionality not to achieve expected, successful results. This list will be updated as additional scenarios become known.

- When the [Extensible Data Security (XDS) policies](../../fin-ops-core/dev-itpro/sysadmin/extensible-data-security-policies.md) feature is enabled, CDX might not work correctly. Specifically, users might not be able to see all the Commerce channels in Commerce headquarters. In this scenario, if a user runs a CDX job, it will generate only partial data (the data that this user is able to see). Therefore, the channel database data will be incomplete, and an error will likely occur.
- The **RetailServiceAccount** user is altered, or XDS policies are assigned to it. The **RetailServiceAccount** is an important, pre-generated account that is used for a variety of reasons and purposes. We highly recommend that you not alter this account in any way. If you're using XDS policies, don't assign any to this account that will reduce the data that the account can see or access.
- CDX jobs fail with timeout errors when upload packages are generated. This issue most often occurs when custom-created transactional tables are missing an index on the **ReplicationCounterFromOrigin** column in these generated tables.

## Error-based troubleshooting

If an error that occurs doesn't appear in the following table, create a support request, as required, so that Microsoft Support can help you fix the issue. This article is focused on issues that you can work on directly, without the help of Microsoft Support, and issues that you can directly see but can't fix without the help of Microsoft Support.


| Error | Description |
|-------|-------------|
| You receive the following error message: "System.ArgumentNullException: Value cannot be null.Parameter name: connectionString at Microsoft.Dynamics.Retail.CommerceDataExchange.SqlTargetRequestHandler." | An error has occurred because of batch job statuses. (You can see the error in a failed download job on the **Download sessions** page.) Go to **System administration \> Inquiries \> Batch jobs**, find the data writing batch that is associated with the Commerce Scale Unit that the download job was supposed to be applied to, and change the batch job's status to **Withhold**. In environments that are earlier than version 10.0.12, we recommend that you also create a channel database group that is named **Legacy**, associate the **Default** channel database with this new group, and then exclude the new database group from all distribution schedules. CDX jobs should no longer be generated for the **Default** channel database in the **Legacy** group. |
| You can't perform the **Run now** command from the **Distribution schedule** page unless batch processing is used. | This change was intentionally made in version 10.0.11 because of performance issues that occurred if jobs were run during times when environments were most heavily used. In another change that was made as part of this feature enhancement, recurrence can't be used when the **Full data sync** command (full job synchronization) is run from the **Channel database** page in Commerce headquarters. Only a single occurrence can be run. We don't recommend that you change this behavior. However, if you're in a development environment, you can change it by going to **Commerce shared parameters \> Configuration parameters** and setting a new name, **CDX\_DISABLE\_FORCESCHEDULEINBATCH**, that has a value of **1**. |
| You receive the following error message: "Microsoft.Dynamics.Retail.CommerceDataExchange.SqlWriteRequestRunException: Failed to run SqlWriteRequestRunner for table AX.\<TABLE NAME\>." | An error has occurred because the length of one or more **DBO** tables has been extended, so that truncation of data was required. Therefore, a truncation failure has occurred. Generate a support request. For best practices, see [Enable custom Commerce Data Exchange synchronization via extension](cdx-extensibility.md). These best practices include removing the extended data type (EDT) extension on the table field that is being edited and using the CDX extension table to store the long (full) value that is required. |
| The download session is failing. The error message states, "...tried too many times." | Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce scheduler parameters**, and set the **Try count** field to **3**. If the value of this field is too high, download sessions might fail during high-usage times. After you complete this step, the job will set its status to **Canceled** and stop retrying itself. We recommend that you to read [Commerce Data Exchange best practices](CDX-Best-Practices.md). |
| You can't cancel a running CDX job. | If this issue occurs in a production environment, sign in to Microsoft Dynamics Lifecycle Services (LCS), and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| You use LCS to copy a Commerce headquarters database between environments, but the target environment also uses Commerce Scale Unit (Cloud) (previously known as Retail Cloud Scale Unit). | Create a support request, and specify whether it's acceptable to delete and reprovision the Commerce Scale Unit (Cloud), or whether the Commerce Scale Unit must be maintained as it currently exists. In both cases, downtime will be required. |
| CDX or environment issues occur after you change the value of the **Days transactions exist** field in the functionality profile. | If the **Days transactions exist** value is reduced by a large amount, one or more tables might become locked while purging occurs. Before you reduce the value by a large amount, we recommend that you generate a support request. Microsoft Support can remove the data before the value is changed. In this way, the database impact of the change will be minimized. |
| After you add multiple POS terminals, download sessions take a very long time, or there is overall Commerce headquarters slowness. | When you create a new Store Commerce app offline database and add it to the relevant channel database group, it inherits all existing download sessions since the last full database synchronization occurred. Even at the best of times, the exceptional data generation that might occur can be too large and therefore affect performance. At the worst (that is, busiest) of times, it can severely impair the environment's performance. We highly recommend that you have either a "dummy" channel database group (that is, a group that isn't associated with any distribution schedule job) that you assign to the newly generated terminals or a special offline profile where the **Pause offline synchronization** option is set to **Yes**. In this way, data generation can occur when it's required and when the system is most available to do it. (However, the system might pause multiple times as required.) If it's too late to use this approach, create a support request. |
| Normal, incremental (delta) synchronization takes much too long, even though the number of affected rows is small. | This issue can occur when a new channel (store) is created, because all the data must be re-created for the new store. We highly recommend that you have a "dummy" channel database that is associated with a "dummy" channel database group, and assign it to the newly generated channel (store). In this way, data generation can occur when it's required and when the system is most available to do it. If it's too late to use this approach, create a support request. |
| The P-job fails to create an upload session, and you receive the following error message: "System.Data.SqlClient.SqlException (0x80131904): Violation of PRIMARY KEY constraint 'PK\_UPLOADSESSION'. Cannot insert duplicate key in object 'crt.UPLOADSESSION'." | If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| When you try to download an upload session package from the **Upload sessions** page in Commerce headquarters, you receive the following error message: "Record for Id - \<Number\> not found." | Create a support request. |
| CDX download sessions fail to be applied, and you receive the following error message: "Failed to get download session package URI." | If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| No download sessions are applied, and no upload sessions are created. | If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| Upload sessions fail, and you receive the following error message: "Infolog for task Default:P-0001 (...) Error when bulk inserting data. Target table: RetailListingStatusLog." | An error has occurred because the upload session package contains multiple records in the **RetailListingStatusLog** table. These records have the same **StatusDateTime** value between two or more. If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |
| When a cashier tries to switch to offline mode or is forced offline, the switch fails. | There are many possible causes. First, verify basic information: Does the computer have available hard drive space? If you're using SQL Server Express, is the size of the offline database at the 10 gigabyte (GB) limit? Are there pending download sessions for the register? (Pending download sessions indicate that the register is no longer up to date. Therefore, offline switching might temporarily be prevented.) Additionally, we recommend that you contact Microsoft Support. If this issue occurs in a production environment, sign in to LCS, and create a request for immediate support. If the issue occurs in a non-production environment, create a support request. |

## Resources

- [Commerce Data Exchange best practices](CDX-Best-Practices.md)
- [Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)
- [Commerce offline implementation and troubleshooting](implementation-considerations-offline.md)
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md)
- [Select an in-store topology](retail-in-store-topology.md)
- [Device management implementation guidance](../implementation-considerations-devices.md)
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)
- [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
