---
# required metadata

title: Compressing tables in AX 2012 environments
description: An overview sentence that describes what this article is all about.
author: ttreen 
ms.date: 04/08/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Compressing tables in Microsoft Dynamics AX 2012 environments

[!include[banner](../includes/banner.md)]

# Background
Microsofy Dynamics AX 2012 environments with large databases may experience errors, similar to the one below, during the upgrade to D365 in Self-Service environments. 

_Managed Sync Table Worker encountered an exception, but is continuing because ContinueOnError is true. Table Sync Failed for Table: TaxTrans. Exception: System.InvalidOperationException: Database execution failed: The elastic pool has reached its storage limit. The storage usage for the elastic pool cannot exceed (4194304) MBs.
The statement has been terminated._

If you experience such an error, then one option is to reduce the size of the source database (AX 2022) through table\index compression the data prior to upgrading. 

Within D365 the tables and indexes maybe compressed with PAGE or ROW data compression. 

Out of the box, most customers didn't enable compression in AX 2012, but it can be enabled afterwards, and this will have the effect that the data when replicated to D365 will also be compressed. Therefore, this should free up enough space in the database to allow the upgrade to complete.

# Tech Details

**NOTE:** In order for the compression status on the tables to be replicated, you need to use a version of the Data Upgrade Toolkit that has a date from March 30th 2022 or later. Releases prior to this did not support the compression flags.

## Identify Tables For Compression

1. Open SQL Management Studio, and connect to the server which hosts the Dynamics AX 2012 database
2. In the Object Explorer, right click on the AX 2012 database you are using, and select: **Reports > Standard Reports > Disk Usage by Top Tables**
3. The report will run, and analyze the results:
4. Determine the tables that use the largest amount of storage, and will benefit from being compress to free up enough volume to assist with the upgrade.  

## AX 2012 Setup

1. From the Developer Workspace, find an open form **SysSqlSetup** (This form can take several mins to open)
2. In the **Table:** dropdown find one of the tables you want to compress, in this example we're going to use the **RetailTtransactionSalesTrans** tables.
3. Select **The selected table** and then check **Enable Compression** and select **Page** or **Row**, then **Save** as in the example below
4. Next select **All indexes for selected table**, and then check **Enable Compression** and select **Page** or **Row**, then **Save** as in the example below
5. Repeat the steps 2 to 4 above for all required tables.

Tip: You can use the following SQL query to see which tables you have setup the compression on:

```SQL
select t2.name as TABLENAME, t1.*
from sqlstorage t1
join sqldictionary t2 on t1.TABLEID = t2.TABLEID and t2.FIELDID = 0 
```

## Compressing the Tables

There are two options:

1. You can compress the tables from the **SysSqlAdmin** form
   - One limitation with this form is that the compression is processed for all tables you have compression set on. You cannot be selective which ones you want to process. However, the index compression is selective. As you may want to control this process, especially on a live database, the SQL script in option 2 may be a better choice.
2. You can run a SQL script 
   - This is more controllable and granular.

### Option 1 - SysSqlAdmin 

- In the AOT, find the SysSqlAdmin form and open it.
- Choose menu **Table actions** > **Apply compression**
- Next find the table(s) you enabled in the steps above, and select(highlight) each table and then select menu **Index actions** > **Reindex**
- Check the compression was enabled using the following SQL Script

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


### Option 2 - SQL Script
Run the following SQL script against the AX 2012 database. Edit the list of tables, as commented in the script, to the tables you require to compress.
By default, the script will also compress the indexes on the tables as well, but as commented, you can disable that. 

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


