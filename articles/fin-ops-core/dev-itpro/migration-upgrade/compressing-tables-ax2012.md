---
# required metadata

title: Compress tables in Dynamics AX 2012 environments
description: This topic describes how to compress tables in Microsoft Dynamics AX 2012 environments.
author: ttreen 
ms.date: 04/22/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Compress tables in Microsoft Dynamics AX 2012 environments

[!include[banner](../includes/banner.md)]

This topic describes how to compress tables in Microsoft Dynamics AX 2012 environments.

## Background

When upgrading to Dynamics 365 in self-service environments, Dynamics AX 2012 environments with large databases may generate errors similar to the following: 

`_Managed Sync Table Worker encountered an exception, but is continuing because ContinueOnError is true. Table Sync Failed for Table: TaxTrans. Exception: System.InvalidOperationException: Database execution failed: The elastic pool has reached its storage limit. The storage usage for the elastic pool cannot exceed (4194304) MBs.
The statement has been terminated._`

One option to avoid such an error is to reduce the size of the Dynamics AX 2012 source database by compressing table and index data prior to upgrading. 

Within Dynamics 365, tables and indexes may be compressed using page or row data compression. 

Most Dynamics AX 2012 customers don't enable compression out of the box, but compression can be enabled afterwards. With compression enabled, data replicated to Dynamics 365 will also be compressed, which should free up enough space in the database to allow the upgrade to complete.

## Prerequisites

You must fulfill the following prerequisites before compressing the tables.

> [!NOTE]
> For the compression status on the tables to be replicated, you must use a version of the AX 2012 Database Upgrade Toolkit for Dynamics 365 dated March 30, 2022 or later. Prior releases don't support compression flags.

### Identify tables for compression

To identify tables for compression, follow these steps.

1. Open SQL Management Studio and connect to the server that hosts the Dynamics AX 2012 database.
1. In the Object Explorer, right-click the AX 2012 database that you are using, and then select **Reports \> Standard Reports \> Disk Usage by Top Tables**. This will run the **Disk Usage by Top Tables** report.
1. From the report results, determine which tables use the largest amount of storage. Compressing these tables should free up enough volume to assist with the upgrade.  
### Configure AX 2012 for the upgrade

To configure AX 2012 for the upgrade, follow these steps.

1. From the Dynamics AX 2012 Development Workspace, find and open the **SysSqlSetup** form. This form can take several minutes to open.
1. In the **Table** drop-down list, find and select one of the tables that you want to compress (for example, **RetailTtransactionSalesTrans**).
1. Select the **Enable Compression** checkbox, select **Page** or **Row**, then select **Save**.
1. Select **All indexes for selected table**, select the **Enable Compression** checkbox, select **Page** or **Row**, and then select **Save**.
1. Repeat steps 2 to 4 above for all the tables you want to compress.

> [!TIP]
> You can use the following SQL query to determine which tables you have set up the compression on.

```SQL
select t2.name as TABLENAME, t1.*
from sqlstorage t1
join sqldictionary t2 on t1.TABLEID = t2.TABLEID and t2.FIELDID = 0 
```

## Compress the tables

There are two options to compress the tables:

- [Option 1 - Compress the tables from the SysSqlAdmin form](#pption-1-compress-the-tables-from-the-syssqladmin-form) - One limitation with this form is that the compression is processed for all tables you have compression set on. You cannot be selective which ones you want to process. However, the index compression is selective. As you may want to control this process, especially on a live database, the SQL script in option 2 may be a better choice.
- [Option 2 - Run a SQL script](#option-2-run-a-sql-script) - This option is more controllable and granular.

### Option 1 - Compress the tables from the SysSqlAdmin form

To compress the tables from the **SysSqlAdmin** form, follow these steps.

1. In the Dynamics AX Application Object Tree (AOT), find the **SysSqlAdmin** form and open it.
1. Select **Table actions \> Apply compression** from the drop-down menu.
1. Find the table(s) you enabled previously, and select (highlight) each table, and then select **Index actions \> Reindex** from the drop-down menu.
1. Confirm that the compression was enabled by running the following SQL script.

```SQL
-- Tables with Compression
SELECT T2.name AS TableName, 
	T1.partition_number AS Partition,
    T1.data_compression_desc AS CompressionType
FROM sys.partitions AS T1
INNER JOIN sys.tables AS T2 ON T2.object_id = T1.object_id
WHERE T1.index_id in (0,1)
AND T1.data_compression_desc != 'NONE'
ORDER BY T2.name

-- Indexes with Compression
SELECT T2.name AS TableName, 
	T3.name AS IndexName,  
    T1.partition_number AS Partition,
    T1.data_compression_desc AS Compression
FROM sys.partitions AS T1
INNER JOIN sys.tables AS T2 ON T2.object_id = T1.object_id
INNER JOIN sys.indexes AS T3 ON T3.object_id = T1.object_id AND T3.index_id = T1.index_id
WHERE T1.index_id > 1
AND T1.data_compression_desc != 'NONE'
ORDER BY T2.name, T3.name 
```

### Option 2 - Run a SQL script

For option 2, you must run the following SQL script against the Dynamics AX 2012 database. First edit the list of tables (as commented in the script) to include the tables you want to compress. By default the script will also compress the indexes on the tables, but you can disable that (as commented in the script). 

```SQL
--
-- This source code or script is freeware and is provided on an "as is" basis without warranties of any kind, 
-- whether express or implied, including without limitation warranties that the code is free of defect, 
-- fit for a particular purpose or non-infringing.  The entire risk as to the quality and performance of 
-- the code is with the end user.
--

-- This script uses PAGE compression, if you wish to use ROW compression you will need to edit the script

-- Edit the list below to include the tables you want to compress
DECLARE @tablestocompress NVARCHAR(MAX) = 'TABLE1, TABLE2, TABLE3, TABLE4, TABLE4, TABLE6'  

-- If you want to disable the index compression, set the following to 0 
DECLARE @compressIndexes BIT = 1;


-- Script Code Block - Start
DECLARE @tablename NVARCHAR(256), @indexName NVARCHAR(256)
DECLARE @dataCompression TINYINT;
DECLARE @sql NVARCHAR(MAX);
DECLARE @xml XML
DECLARE @errors BIT

set @tablestocompress = REPLACE(@tablestocompress,' ', '')
set @xml = (SELECT CAST('<cr>'+REPLACE(@tablestocompress, ',', '</cr><cr>')+'</cr>' AS XML) AS STRING) 
set @errors = 0

-- Check tables in list exist
DECLARE tableCursor CURSOR FOR 
	select t.value('.','varchar(max)') as TABLESTOCOMPRESS from @xml.nodes('//cr') as a(t);
OPEN tableCursor;
FETCH NEXT FROM tableCursor INTO @tablename;
WHILE @@FETCH_STATUS = 0
	BEGIN
		IF NOT EXISTS (SELECT name from sys.tables where name = @tablename and schema_id = (select schema_id from sys.schemas where name = 'DBO')) 
		BEGIN
			IF (@errors) = 0
			BEGIN
				PRINT 'Some tables entered do not exist, please check the list you edited and the tables below...';
			END
			SET @errors = 1;
			PRINT @tablename + ' table does not exist';
		END
		FETCH NEXT FROM tableCursor INTO @tablename;
	END
CLOSE tableCursor;
DEALLOCATE tableCursor;

IF (@errors) = 0
BEGIN
	-- All Tables In List were Present
	-- Start Compression
	DECLARE tableCursor CURSOR FOR 
		select t.value('.','varchar(max)') as TABLESTOCOMPRESS from @xml.nodes('//cr') as a(t);
	OPEN tableCursor;
	FETCH NEXT FROM tableCursor INTO @tablename;
	WHILE @@FETCH_STATUS = 0
		BEGIN
			IF EXISTS (SELECT T1.data_compression_desc FROM sys.partitions AS T1 
				INNER JOIN sys.tables AS T2 ON T2.object_id = T1.object_id
				WHERE T1.index_id in (0,1) --0 HEAP, 1 CLUSTERED
				AND T2.object_id = OBJECT_ID(@tablename)
				AND T1.data_compression != 2) --PAGE
			BEGIN
				-- Table is not is not compressed
				PRINT 'Compressing table ' + @tablename + ' with DATA_COMPRESSION = PAGE'
				set @SQL = 'ALTER TABLE DBO.' + @tablename + ' REBUILD PARTITION = ALL WITH (DATA_COMPRESSION = PAGE);'
				EXEC (@SQL);
			END
			ELSE
			BEGIN
				-- Table is already compressed
				PRINT 'PAGE compression already set on table ' + @tablename + ', skipping...'
			END

			IF (@compressIndexes) = 1
			BEGIN
				-- Compress Indexes if not already compressed
				DECLARE indexCursor CURSOR FOR 
					SELECT T3.name, T1.data_compression 
					FROM sys.partitions AS T1
					INNER JOIN sys.tables AS T2 ON T2.object_id = T1.object_id
					INNER JOIN sys.indexes AS T3 ON T3.object_id = T1.object_id AND T3.index_id = T1.index_id
					WHERE T1.index_id > 1
					AND T2.name = @tablename;
				OPEN indexCursor;
				FETCH NEXT FROM indexCursor INTO @indexName, @dataCompression;
				WHILE @@FETCH_STATUS = 0
				BEGIN
					IF (@dataCompression) != 2
					BEGIN
						PRINT 'Compressing table index ' + @tableName + '.' + @indexName + ' with DATA_COMPRESSION = PAGE'
						set @SQL = 'ALTER INDEX ' + @indexName + ' ON DBO.' + @tablename + ' REBUILD PARTITION = ALL WITH (DATA_COMPRESSION = PAGE);'
						EXEC (@SQL);
					END
					ELSE
					BEGIN
						PRINT 'PAGE compression already set on table index ' + @tableName + '.' + @indexName;	
					END
					FETCH NEXT FROM indexCursor INTO @indexName, @dataCompression;	
				END
				CLOSE indexCursor;
				DEALLOCATE indexCursor;
			END

			FETCH NEXT FROM tableCursor INTO @tablename;
		END
	CLOSE tableCursor;
	DEALLOCATE tableCursor;
END
-- Script Code Block - End
```


