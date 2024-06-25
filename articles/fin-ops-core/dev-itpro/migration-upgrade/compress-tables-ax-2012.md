---
title: Compress tables in Dynamics AX 2012 environments
description: Learn about how to compress tables in Microsoft Dynamics AX 2012 environments, including background information and prerequisites
author: ttreen
ms.author: ttreen
ms.date: 05/23/2022
ms.topic: article
ms.reviewer: johnmichalakffin
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
---

# Compress tables in Microsoft Dynamics AX 2012 environments

[!include[banner](../includes/banner.md)]

This article describes how to compress tables in Microsoft Dynamics AX 2012 environments.

## Background

When you upgrade to Dynamics 365 in self-service environments, Dynamics AX 2012 environments that have large databases might generate errors that resemble the following example:

> Managed Sync Table Worker encountered an exception, but is continuing because ContinueOnError is true. Table Sync Failed for Table: TaxTrans. Exception: System.InvalidOperationException: Database execution failed: The elastic pool has reached its storage limit. The storage usage for the elastic pool cannot exceed (4194304) MBs.  
The statement has been terminated.

One way to help avoid errors of this type is to reduce the size of the Dynamics AX 2012 source database by compressing table and index data before you upgrade.

In Dynamics 365, you can compress tables and indexes by using page or row data compression.

Although most Dynamics AX 2012 customers don't enable compression out of the box, it can be enabled afterward. When compression is enabled, data that is replicated to Dynamics 365 will also be compressed. This compression should free up enough space in the database to enable the upgrade to be completed.

## Prerequisites

The following prerequisites must be in place before you compress the tables.

> [!NOTE]
> For the compression status of the tables to be replicated, you must use a version of the AX 2012 Database Upgrade Toolkit for Dynamics 365 that is dated March 30, 2022, or later. Earlier releases don't support compression flags.

### Identify tables for compression

To identify tables for compression, follow these steps.

1. Open SQL Management Studio, and connect to the server that hosts the Dynamics AX 2012 database.
1. In Object Explorer, select and hold (or right-click) the Dynamics AX 2012 database that you're using, and then select **Reports \> Standard Reports \> Disk Usage by Top Tables** to run the **Disk Usage by Top Tables** report.
1. Review the report results to determine which tables use the largest amount of storage. By compressing those tables, you should free up enough volume to help the upgrade.

### Configure Dynamics AX 2012 for the upgrade

To configure Dynamics AX 2012 for the upgrade, follow these steps.

1. From the Dynamics AX 2012 Development Workspace, find and open the **SysSqlSetup** form. This form can take several minutes to be opened.
1. In the **Table** drop-down list, find and select one of the tables that you want to compress (for example, **RetailTtransactionSalesTrans**).
1. Select the **Enable Compression** checkbox, select **Page** or **Row**, and then select **Save**.
1. Select **All indexes for selected table**, select the **Enable Compression** checkbox, select **Page** or **Row**, and then select **Save**.
1. Repeat steps 2 through 4 for each additional table that you want to compress.

> [!TIP]
> You can use the following SQL query to determine which tables you've set up compression on.
>
> ```SQL
> select t2.name as TABLENAME, t1.*
> from sqlstorage t1
> join sqldictionary t2 on t1.TABLEID = t2.TABLEID and t2.FIELDID = 0 
> ```

## Compress the tables

You have two options for compressing the tables:

- **[Option 1: Compress the tables from the SysSqlAdmin form](#option-1-compress-the-tables-from-the-syssqladmin-form)** – One limitation of the **SysSqlAdmin** form is that the table compression isn't selective. In other words, you can't select which tables you want to process. The compression is always processed for all the tables that you've set up compression on. However, the index compression *is* selective. Because you might want to control this process, especially for a live database, option 2 might be a better choice.
- **[Option 2: Run a SQL script](#option-2-run-a-sql-script)** – This option is more granular, and you have more control over it.

### Option 1: Compress the tables from the SysSqlAdmin form

To compress the tables from the **SysSqlAdmin** form, follow these steps.

1. In the Dynamics AX Application Object Tree (AOT), find the **SysSqlAdmin** form, and open it.
1. On the drop-down menu, select **Table actions \> Apply compression**.
1. Find and select each table that you previously enabled, and then, on the drop-down men, select **Index actions \> Reindex**.
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

### Option 2: Run a SQL script

For this option, you must run the following SQL script against the Dynamics AX 2012 database. First edit the list of tables (as commented in the script) so that it includes the tables that you want to compress. By default, the script will also compress the indexes on the tables. However, you can disable that functionality (as commented in the script).

```SQL
--
-- This source code or script is freeware and is provided on an "as is" basis without warranties of any kind, 
-- whether express or implied, including without limitation warranties that the code is free of defect, 
-- fit for a particular purpose or non-infringing. The entire risk as to the quality and performance of 
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
                    AND T2.schema_id = (select schema_id from sys.schemas where name = 'DBO')
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
