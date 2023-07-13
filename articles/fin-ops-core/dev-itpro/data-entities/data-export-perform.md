---
title: Data entity export performance tips  
description: This article provides tips about improving performance when exporting.
author: gned  
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 7/13/2023
ms.custom:

---

# Data entity export performance tips  

[!include [banner](../includes/banner.md)]

This article provides tips about improving performance when exporting.


## Computed columns 

Computed columns shouldn't have joins. Add all the tables needed for the computation as data sources instead. Computed columns are computed values that SQL server needs to return as part of executing the data entity view. They have a number of possible uses such as returning default values, casing logic, formatting values etc. But they need to be written so SQL can computed the things quickly and not need large amounts of storage space. The main thing to avoid when writing a computed column formula is a join to some table or view. That forces SQL to compute the values row by row and keep them all in temporary storage. Instead, add the tables needed for the formula as data sources in the entity view. SQL can then join all the table data to all the rows in one operation instead of repeating it per row.

To test if a computation is causing slowness, connect to your sandbox database. Run sp_helptext command to get the view definition. Copy the output to another SQL management studio window. Remove the line breaks.
Remove CREATE VIEW [SOME NAME] AS from the start of the view definition command so that only the select command is present. Run the command and record the time needed to return all data. Comment out the computed 
column formula. Run the command again and record the time needed to return all data. If the time to return data is faster by more than one to two seconds without the computation, then the computation is causing 
slowness.

## Postload 

Don't implement postload as it forces export to go through staging. There are many methods on data entities that entity authors can implement to customize what happens when the entity is used. One method to avoid using is postLoad. PostLoad requires your export data to be copied into your staging table so that postload can then be called once for each row. After, copy from staging table to your destination database or file. Copying all the data a second time is inefficient. Over time, for full exports, the staging table sizes quickly grow. This makes insert update and select on the staging table slower. If there’s values you want to change prior to export, consider using a computed column formula to return the modified value. For values to be set just before importing to the entity, consider using postStaging instead. The entity’s insert and update methods could also be customized to modify values for specific columns. Any of these will let you skip staging for your export.

Don't set export to use staging unless you have a postload method or the entity has a virtual field or a bitmap that has to be exported. In the UI, when creating an export project, don’t set your export to use staging unless the entity has a postload method, a virtual filed, that is a value computed by x++ method, or needs to export bitmaps. Export through staging requires the data to be exported twice, once to the staging table, and again to your destination. Only use if there’s something to export that can only run in the staging process.

If your entity has any columns linked to configuration keys that are disabled, it will fail to export if you select any of its disabled columns unless you use staging for the export. If your entity only works 
when exporting through staging, check for fields with configuration keys. If yes, rather than export through staging, remove the mappings for all the disabled columns so you can skip staging. That will be 
faster than going through staging. The configuration key settings are often on the extended data type or enumeration object, rather than on the table or data entity view field, so check for config keys on your 
enumerations and extended data types, not just your fields.

### Number of data sources 

Limit the number of data sources in an entity or view. The fewer the joins, the faster the results can be returned. Many of the data entities in the system, were created with import in mind and expose every possible field on every related table just in case you need to set it. That may be alright for importing small numbers of records, but for export, if you don’t use it, don’t select it. Look through the list of data sources in your entity and more importantly in any other entities you reference. Compare with the requirements of the processes using the export data. If the process doesn’t use any values from a data source, remove that data source.

Try to keep the total number of joins for an export entity small. 
 - Zero to three works well
 - four to seven works a bit slower
 - 8 to 13 is slow
 - Don’t use more than 13

An example of what not to do, consider BIExchangeRateView. At first glance it looks simple, just one more view and a table. But when you look at ExchangeRateEffectiveView, it has a union over 16 other views. 
And those views have unions over other views too.

Analyze the indices that exist on any custom tables you join. Is there an index for the table that includes the columns that you filter on and the columns you join on?
Sql server needs to create a query plan for queries using your data entity in which it does the filters and joins from your data entity definition. Look at the joins and compare with the table indices, 
especially when the join is custom or the table is custom. Is there already an index on the table that includes the columns you filter by or join on? If not, test adding an index to see if SQL can return data 
faster. If the index doesn’t improve the execution time for the view, then remove it. If you find an indices that help, add them into the table metadata for your table.

### Data source 

Avoid using other data entities or views as a data source. To make an entity faster, the number of joins needs to be limited, the number of computations it does and the number of columns it returns. Even if there is another data entity that has some of the values you want, it may include joins you don’t need or computation formulas you don’t use. Instead, add the same tables to your entity as the other entity and join them the way the other entity does. But leave out the 
data sources for any tables your export doesn’t need.

### Minimize the number of columns

The fewer columns included in the select from the data entity, the faster the data can be transferred to the destination. The default mapping for an export project will include all the columns. If exporting a 
standard entity, check what columns it has. There are likely columns for which you don’t use the data. Remove them from the mapping so you don’t transfer unnecessary data. If it’s your entity, remove unneeded
columns from the entity itself. Try to keep total columns selected by your entity less than 200.

### Implement defaultCTQuery to specify which tables to track for changes to limit the amount of change data that has to be processed.

Incremental export queries for change data on the tables in the data entity and will export only rows related to those changed records. But lots of entities have large number of joins or joins to tables that 
aren’t important the processes using the entity data. You can limit what change records are processed by implementing a method named defaultCTQuery for your data entity. Return a query that joins the tables for 
which you require change data. Leave out any tables where the values don’t matter to your process. This can speed up incremental export by skipping over change data for less important entity tables.

>[!IMPORTANT]
>Never track DimensionAttributeValueCombination, DimensionAttributeValueSet or InventDim for changes.

These three tables are all very large cross company tables that do not allow record update and have large numbers of inserts daily. Tracking them can result in extremely slow exports. There is never a need to
track changes for these tables. The processes that change financial or inventory dimension data for a record, will create a new record if there isn’t already one for that combination of dimension values, and 
update the related record to point to the dimension record. The table that stores the references to the dimension values will always be updated if the value changes. It’s sufficient to track the related table as any rows in the entity related to new dimension records will also be related to changed records in the tables that store the reference to the dimension value.

### Schedule staging data clean up job

Over time the amount of data in staging tables for the entities that are exported through staging or imported can build up to a point it slows the imports and exports. If a staging table row count gets
over 20 million, its data needs to be reduced. From the data management workspace, you can schedule a batch process to look for staging data related to old imports or exports and remove it. When scheduling the 
data cleanup job, use a larger number for number of hours it is allowed to run and run it daily. The default of two hours per day is often not enough. Six or eight hours allowed works better. It will stop if it 
runs out of data to remove.

### Don't add any custom or customized entity in production until after you tested it in sandbox with your data.

Sometimes performance problems don’t show up on development environments because the smount of the data, but they may show up if you test with actual data on your sandbox. Always test how slow any new entity is to export on sandbox. If it’s slow, improve it before deploying that entity to production.

### Don't schedule processes that read from your destination tables at the same times you export to those tables

Export to database needs to make changes to the data for the destination tables. It runs commands to remove the data for the company it is exporting before running a full export, and removes older versions of 
records that were exported for incremental export. These commands can be significantly slowed if there is some process using the entity data at the times they run. Try to schedule exports for times when you are 
not running reports against the same entity tables in your destination database.

It’s not always obvious if there’s another process using the same tables as your export, but if you have a slow export to database, query for blocking on your destination database and you might find it. Check in the Azure portal to see if your database is hitting DTU limits.

### Index type setting for database export

When setting up your database export connection, consider which type of index you want created. The default is to create a clustered column store index. This index type makes select queries fast which can help
with reports on the destination table, but it makes insert and delete slow. You can turn off use CCI index. With CCI index off, the tables you publish will have an index based on your staging table key. It’s 
usually much faster to insert or delete by the staging table index than by the clustered column store index. If you already published using CCI index, you can still add an index for the staging table key columns
yourself.
