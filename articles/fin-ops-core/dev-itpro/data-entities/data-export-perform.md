---
title: Data entity export performance tips
description: This article provides tips that can help improve performance during export.
author: gned
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 7/13/2023
ms.custom:

---

# Data entity export performance tips

[!include [banner](../includes/banner.md)]

This article provides tips that can help improve performance during export.

## Don't use computed columns that have joins

Computed columns should not have joins. Instead, add all the tables that are required for the computation as data sources.

Computed columns are computed values that SQL Server must return as part of the process of running the data entity view. They have many possible uses, such as returning default values, casing logic, and formatting values. Computed column formula must be written so that SQL Server can quickly compute values and doesn't need large amounts of storage space.

When you write a computed column formula, the main thing to avoid is a join to some table or view. Such a join forces SQL Server to compute the values row by row and keep them all in temporary storage. Instead, add the tables that are needed for the formula as data sources in the entity view. SQL Server can then join all the table data to all the rows in one operation instead of repeating the process for each row.

To test whether a computation is causing slowness, follow these steps.

1. Connect to your sandbox database, and run the `sp_helptext` command to get the view definition.
1. Copy the output to another SQL Server Management Studio window, and make the following changes:

    - Remove the line breaks.
    - Remove `CREATE VIEW [SOME NAME] AS` from the start of the view definition command, so that only the `select` command is present.

1. Run the command, and record the time that's required to return all data.
1. Comment out the computed column formula, run the command again, and record the time that's required to return all data. If the required time is more than one to two seconds faster without the computation, the computation is causing slowness.

## Don't implement postLoad

Don't implement `postLoad`, because it forces the export to go through staging.

Entity authors can implement many methods on data entities to customize what happens when those entities are used. One method that you should avoid using is `postLoad`. This method requires that your export data is copied into your staging table, so that the method can be called once for each row. Afterward, you must copy the data from the staging table to your destination database or file. It's inefficient to copy all the data a second time. In addition, for full exports, the size of the staging table quickly grows over time. As a result, `insert`, `update`, and `select` operations on the staging table become slower.

If there are values that you want to change before export, consider using a computed column formula to return the modified value. If values must be set just before import into the entity, consider using `postStaging`. In addition, the entity's `insert` and `update` methods can be customized to modify values for specific columns. Any of these alternative approaches let you skip staging for your export.

When you create an export project in the user interface (UI), don't set up your export to use staging unless the entity has a `postLoad` method or a virtual field (that is, a value that's computed by an X++ method), or unless it must export bitmaps. Export through staging requires that the data is exported two times: once to the staging table and once to your destination. Therefore, use this approach only if you must export something that can only run in the staging process.

If any columns in your entity are linked to configuration keys that are disabled, and you select any of the disabled columns, export fails unless you use staging for it. If your entity only works if you export through staging, check for fields that have configuration keys. In addition, because the configuration key settings are often on the enumeration (enum) object or extended data type (EDT) instead of the table or data entity view field, check for configuration keys on enums and EDTs too. If any fields, enums, and EDTs have configuration keys, don't export through staging. Instead, remove the mappings for all the disabled columns, so that you can skip staging. This approach is faster than going through staging. 

## Limit the number of data sources

Limit the number of data sources in an entity or view. The fewer the joins, the more quickly the results can be returned. Many data entities were created with import in mind and expose every possible field in every related table, in case you have to set it. This behavior might be acceptable when you import small numbers of records. However, for export, you should select only what you use. Look through the list of data sources in your entity and, more importantly, in any other entities that you reference. Compare those data sources with the requirements of the processes that use the export data. If those processes don't use any values from a data source, remove that data source.

Try to keep the total number of joins for an export entity small.

- **0–3** – This number of joins works well.
- **4–7** – Performance is a bit slower.
- **8–13** – Performance is slow.
- **14 or more** – Don't use this many joins.

For an example of what **not** to do, consider the `BIExchangeRateView` view. At first glance, it looks simple: it has just one other view and a table. However, if you look closely at the `ExchangeRateEffectiveView` view, it has a union over 16 other views, and those views have unions to other views in turn.

Analyze the indexes that exist on any custom tables that you join. Is there an index for the table that includes the columns that you filter by or join on? SQL Server must create a query plan for queries that use your data entity. In this query plan, SQL Server does the filters and joins from your data entity definition. Look at the joins, and compare them with the table indexes if either the join or the table is custom. If there isn't already an index on the table that includes the columns that you filter by or join on, add one to test whether SQL Server can return data more quickly. If the index doesn't improve the execution time for the view, remove it. If you find an index that helps, add it to the table metadata for your table.

## Don't use data entities or views as data sources

Avoid using other data entities or views as data sources. To make an entity faster, you must limit the number of joins, the number of computations that it does, and the number of columns that it returns.

Even if another data entity has some of the values that you want, it might include joins that you don't need or computation formulas that you don't use. Instead of using that other entity, add the same tables that it has to your entity, and join them in the way the other entity joins them. Leave out the data sources for any tables that your export doesn't need.

## Minimize the number of columns

The fewer columns are included in the `select` operation from the data entity, the faster the data can be transferred to the destination.

The default mapping for an export project includes all the columns. If you're exporting a standard entity, check what columns it has. There are probably columns that you don't use the data for. In this case, remove those columns from the mapping, so that you don't transfer unnecessary data. If you're exporting your own entity, remove unneeded columns from the entity itself. Try to keep the total number of columns that your entity selects less than 200.

## Implement defaultCTQuery to specify which tables changes are tracked for and to limit the amount of change data that must be processed

Incremental export queries for change data on the tables in the data entity and exports only rows that are related to changed records. However, lots of entities have a large number of joins or joins to tables that aren't important for the processes that use the entity data. By implementing the `defaultCTQuery` method for your data entity, you can limit the change records that are processed. Return a query that joins the tables that you require change data for. Leave out any tables where the values aren't important for your process. This approach can speed up incremental export by skipping change data for less important entity tables.

> [!IMPORTANT]
> Never track the `DimensionAttributeValueCombination`, `DimensionAttributeValueSet`, or `InventDim` table for changes. These three large, cross-company tables don't allow for record update, and they all have a large number of inserts every day. There's no need to track changes for these tables, and doing so can lead to slow exports.
>
> The processes that change financial or inventory dimension data for a record create a new record if there isn't already one for that combination of dimension values. They also update the related record so that it points to the dimension record. The table that stores the references to the dimension values is always updated if the value changes. Because any rows in the entity that's related to new dimension records are also related to changed records in the tables that store the reference to the dimension value, it's enough to track the related table.

## Schedule the staging data cleanup job

Over time, the amount of data in staging tables that are used to export entities through staging, or to import them, can build up. The result is slower imports and exports.

If the row count in a staging table is over 20 million, the table's data must be reduced. From the **Data management** workspace, you can schedule a batch data cleanup job that looks for and removes staging data that's related to old imports or exports. When you schedule this job, increase the number of hours that it's allowed to run, and run it daily. The default value of two hours per day often isn't enough. Six or eight hours work better. The job stops when it runs out of data to remove.

## Don't add custom or customized entities in production until you test them with your data in your sandbox

Sometimes, performance issue don't show up in development environments because of the amount of data. However, they do show up when you test with actual data in your sandbox environment. Therefore, always test the export of new entities in your sandbox. If the export process is slow, improve it before you deploy the entities to production.

## Don't schedule processes that read from your destination tables for the same times that you export to those tables

Export to database must make changes to the data for the destination tables. Before it runs a full export, it runs commands to remove the data for the company that it's exporting and to remove older versions of records that were exported for incremental export. These commands can be slowed down if another process is using the entity data at the same time. Therefore, try to schedule exports for times when reports aren't running against the same entity tables in your destination database.

It isn't always obvious whether another process is using the same tables as your export. If you have a slow export to database, query for blocking on your destination database. In the Azure portal, check whether your database is hitting database transaction unit (DTU) limits.

## Review the index type setting for database export

When you set up your database export connection, consider which type of index you want to be created. By default, a clustered column store index is created. This type of index makes `select` queries fast and can therefore help with reports on the destination table. However, it makes `insert` and `delete` operations slow.

You can turn off the use of the clustered column store index. In this case, the index of the tables that you publish will be based on your staging table key. It's faster to insert or delete by using the staging table index than the clustered column store index. If you've already published by using the clustered column store index, you can still add an index for the staging table key columns yourself.
