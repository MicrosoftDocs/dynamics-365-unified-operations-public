---
title: Export a database
description: Learn how to export a database for finance and operations, including processes for self-service exporting of databases and known issues.
author: LaneSwenka
ms.author: laswenka
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-01-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.3
---

# Export a database

[!include [banner](../includes/banner.md)]

Use Microsoft Dynamics Lifecycle Services to export a database from a sandbox user acceptance testing (UAT) environment to the Asset library.

> [!NOTE]
> If you apply the customer managed key (CMK) to the environment, the exported file is stored without the CMK in the Lifecycle Services asset library. CMK support for the Lifecycle Services asset library will be available soon. After that, the exported files are stored with the CMK policy applied to the Lifecycle Services asset library.

## Self-service export database

[!include [dbmovement-export](../includes/dbmovement-export.md)]

### Long running operations

The export operation can take several hours and, in extreme cases, days to complete. This amount of time is due to the schema complexity of finance and operations apps, and limitations of Azure SQL provided tools to convert a cloud database to a flat file for use by traditional SQL Server. When the export operation takes too long and you want to stop the process, select **Cancel** from the environment details page.

### Maximum limit 50-GB on exported bacpacs

To maintain the system that performs database export from Lifecycle Services, a limit on the maximum bacpac size is imposed. This limit is set at 50 GB for each bacpac exported. The reasons for this limit include:

- A centralized system performs the exports for multiple customers in the same geographic region, and this system has constraints on disk space.  

- If you need to reduce the size of the database, follow the [cleanup routines](../sysadmin/cleanuproutines.md).

- If the preceding cleanup routines don't bring the bacpac file to under 50 GB in size, try running the following SQL script against your sandbox database to identify the top 15 tables by size in megabytes. You can truncate any tables for data entity staging (they have "staging" at the end of the table name). For any tables that store binary or blob data (JSON, XML, or binary), either truncate the table or delete the contents of that field to free up space. Binary data can't be compressed, so storing large volumes of data in the database itself causes you to quickly reach the 50-GB limit.

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

Most often, export operations fail because the process in Lifecycle Services times out while it's waiting for a response from Microsoft Azure SQL Database. If the operation times out, it *rolls back* automatically and restores your sandbox environment to the state it was before the export began.

The failed export operation automatically **rolls back**.

### Data elements that aren't exported

When you export a database backup from an environment, the backup file doesn't include some elements of the database. Here are some examples:

- Email addresses in the **LogisticsElectronicAddress** table.
- Batch job history in the **BatchJobHistory**, **BatchHistory**, and **BatchConstraintsHistory** tables.
- SMTP Relay server in the **SysEmailParameters** table.
- Print Management settings in the **PrintMgmtSettings** and **PrintMgmtDocInstance** tables.
- Environment-specific records in the **SysServerConfig**, **SysServerSessions**, **SysCorpNetPrinters**, **SysClientSessions**, **BatchServerConfig**, and **BatchServerGroup** tables.
- Document attachments in the **DocuValue** table. These attachments include any Microsoft Office templates that were overwritten in the source environment.
- Database log history in the **DatabaseLog** table.
- All users except the admin are set to **Disabled** status.
- All batch jobs are set to **Withhold** status.
- All users have their partition value reset to the "initial" partition record ID.
- All Microsoft-encrypted fields are cleared, because they can't be decrypted on a different database server. An example is the **Password** field in the **SysEmailSMTPPassword** table.
- [Maintenance mode](../sysadmin/maintenance-mode.md) settings are disabled even if they were enabled in source.
- Dual-write configuration.  To set up a new link on the target environment after this operation is successful, see [Enable Power Platform Integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).

### Commerce-related data elements that aren't exported

- The following tables aren't exported:
  - RetailCDXDownloadSession
  - RetailCDXDownloadSessionDataStore
  - RetailCDXDownloadSummaryCache
  - RetailCDXUploadSession
  - RetailCDXUploadPathHistory
  - RetailCDXUploadSummaryCache
  - RetailCDXDataSyncRowVersion
- All references to a Commerce Scale Unit are removed from the **RetailConnDatabaseProfile** table.
- All references to a Commerce Scale Unit are removed from the **RetailScaleUnit** table.
- All references to a Commerce Scale Unit are removed from the **RetailChannelProfile** table and all children of this table.
- All environment-specific values are removed from the **RetailSharedParamaters** table.
- All environment-specific values are removed from the **RetailHardwareProfile** table.
- All environment-specific values are removed from the **CreditCardAccountSetup** table.
- All environment-specific values are removed from the **RetailSelfServicePackageInfo** table and all children of this table.

### Known issues

#### Export runs for some time and then reaches a "Preparation failed" state

The export process can time out on Azure SQL Database when large databases are involved. In some cases, you can recover the export process by using the **Resume** action from Lifecycle Services. The Lifecycle Services team is working to identify known error codes, so they can add these errors to the logs for the export database operation to help guide users toward a resolution. These known error codes will be added in a future release of Lifecycle Services.

#### Export doesn't show any progress in Lifecycle Services

The export process differs from other database movement operations, and the general package deployment doesn't use a runbook. Therefore, the progress indicator in Lifecycle Services doesn't show any output, even though it typically shows output in other scenarios. The Lifecycle Services team is working to identify known error codes so that they can add these codes to the logs for the export database operation to help guide users toward a resolution. These known error codes will be added in a future release of Lifecycle Services.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
