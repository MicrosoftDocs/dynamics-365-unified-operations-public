---
# required metadata

title: Export a database
description: This article explains how to export a database for finance and operations.
author: LaneSwenka
ms.date: 06/01/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: 8.1.3

---

# Export a database

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services to export a database from a sandbox user acceptance testing (UAT) environment to the Asset library.

> [!NOTE]
> If the customer managed key (CMK) is applied to the environment, the exported file is stored without the CMK in the Lifecycle Services asset library. CMK support for the Lifecycle Services asset library will be available soon, after that the exported files will be stored with the CMK policy applied to the Lifecycle Services asset library.

## Self-service export database

[!include [dbmovement-export](../includes/dbmovement-export.md)]

### Maximum limit 50 GB on exported bacpacs 
To maintain the system that performs database export from Lifecycle Services, a limit on the maximum bacpac size is being imposed. This limit is set at 50 GB for each bacpac exported. The reasons for this limit include: 

- A centralized system is performing the exports for multiple customers in the same geographic region, and this system has constraints on disk space.  

If you need to reduce the size of the database, follow the [cleanup routines](../sysadmin/cleanuproutines.md).

If the above cleanup routines don't bring the bacpac file to under 50 GB in size, try running the following SQL script against your sandbox database to identify the top 15 tables by size in megabytes. Any tables for data entity staging (they have "staging" at the end of the table name) can be truncated. Any tables that store binary or blob data (JSON/XML/binary) should either be truncated or the contents of that field should be deleted to free up space. Binary data can't be compressed, so storing large volumes of data in the database itself causes you to quickly reach the 50 GB limit.

```sql
USE [YourDBName] -- replace your dbname
GO
SELECT top 15
s.Name AS SchemaName,
t.Name AS TableName,
p.rows AS RowCounts,
CAST(ROUND((SUM(a.used_pages) / 128.00), 2) AS NUMERIC(36, 2)) AS Used_MB,
CAST(ROUND((SUM(a.total_pages) - SUM(a.used_pages)) / 128.00, 2) AS NUMERIC(36, 2)) AS Unused_MB,
CAST(ROUND((SUM(a.total_pages) / 128.00), 2) AS NUMERIC(36, 2)) AS Total_MB
FROM sys.tables t
INNER JOIN sys.indexes i ON t.OBJECT_ID = i.object_id
INNER JOIN sys.partitions p ON i.object_id = p.OBJECT_ID AND i.index_id = p.index_id
INNER JOIN sys.allocation_units a ON p.partition_id = a.container_id
INNER JOIN sys.schemas s ON t.schema_id = s.schema_id
GROUP BY t.Name, s.Name, p.Rows
ORDER BY Total_MB DESC
GO
```

### Export operation failure

Most often, export operations fail because the process in Lifecycle Services times out while it's waiting for a response from Microsoft Azure SQL Database. You can use the **Resume** button to reconnect Lifecycle Services to the ongoing export process and see it through to completion. If more than 24 hours have passed since you began the export, the pending asset in the Lifecycle Services Project asset library is expired. In this case, you must roll back the export operation and restart it.

To cancel an export operation that has failed, you can use the **Rollback** button.

### Data elements that aren't exported

When you export a database backup from an environment, some elements of the database aren't exported in the backup file. Here are some examples:

* Email addresses in the **LogisticsElectronicAddress** table.
* Batch job history in the **BatchJobHistory**, **BatchHistory**, and **BatchConstraintsHistory** tables.
* SMTP Relay server in the **SysEmailParameters** table.
* Print Management settings in the **PrintMgmtSettings** and **PrintMgmtDocInstance** tables.
* Environment-specific records in the **SysServerConfig**, **SysServerSessions**, **SysCorpNetPrinters**, **SysClientSessions**, **BatchServerConfig**, and **BatchServerGroup** tables.
* Document attachments in the **DocuValue** table. These attachments include any Microsoft Office templates that were overwritten in the source environment.
* Database log history in the **DatabaseLog** table.
* All users except the admin will be set to **Disabled** status.
* All batch jobs are set to **Withhold** status.
* All users will have their partition value reset to the "initial" partition record ID.
* All Microsoft-encrypted fields are cleared, because they can't be decrypted on a different database server. An example is the **Password** field in the **SysEmailSMTPPassword** table.
* [Maintenance mode](../sysadmin/maintenance-mode.md) settings are disabled even if it was enabled in source.
* Dual-write configuration.  To set up a new link on the target environment after this operation is successful, see [Dual-write environment linking](../data-entities/dual-write/link-your-environment.md).

### Commerce-related data elements that aren't exported

* The following tables aren't exported:
  * RetailCDXDownloadSession
  * RetailCDXDownloadSessionDataStore
  * RetailCDXDownloadSummaryCache
  * RetailCDXUploadSession
  * RetailCDXUploadPathHistory
  * RetailCDXUploadSummaryCache
  * RetailCDXDataSyncRowVersion
* All references to a Commerce Scale Unit are removed from the **RetailConnDatabaseProfile** table.
* All references to a Commerce Scale Unit are removed from the **RetailScaleUnit** table.
* All references to a Commerce Scale Unit are removed from the **RetailChannelProfile** table and all children of this table.
* All environment specific values are removed from the **RetailSharedParamaters** table.
* All environment specific values are removed from the **RetailHardwareProfile** table.
* All environment specific values are removed from the **CreditCardAccountSetup** table.
* All environment specific values are removed from the **RetailSelfServicePackageInfo** table and all children of this table.

### Known issues

#### Export ran for some time and then reached a "Preparation failed" state

The export process can time out on Azure SQL Database when large databases are involved. In some cases, the export process can be recovered by using the **Resume** action from Lifecycle Services. The Lifecycle Services team is working to identify known error codes, so these errors can be added to the logs for the export database operation to help guide users toward a resolution. These known error codes will be added in a future release of Lifecycle Services. 

#### Export doesn't show any progress in Lifecycle Services

The export process differs from other database movement operations, and the general package deployment doesn't use a runbook. Therefore, the progress indicator in Lifecycle Services doesn't show any output, even though it typically shows output in other scenarios. The Lifecycle Services team is working to identify known error codes so that they can be added to the logs for the export database operation to help guide users toward a resolution. These known error codes will be added in a future release of Lifecycle Services.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

