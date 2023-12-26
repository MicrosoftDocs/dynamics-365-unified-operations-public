---
title: Tile and list caching for workspaces
description: This article discusses framework support for caching data that is used for tiles and lists, so that workspaces perform well and are responsive.
author: jasongre
ms.date: 01/05/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: c84d7929-4662-4abb-b345-ccc539d809d0
---

# Tile and list caching for workspaces

[!include [banner](../includes/banner.md)]

It's important that workspaces perform well, and that they be responsive (that is, the data that appears in a workspace is refreshed as expected and kept up to date). This article discusses framework support for caching data that is used for tiles and lists.

## Introduction

Workspaces are intended to be the hub of activity for most users. They display a wealth of information that is collected from various sources. Therefore, you must make sure that workspaces perform well and are responsive (that is, the data shown in the workspace is refreshed as expected and/or kept up to date). Caching can help guarantee great workspace performance when data comes from poorly performing queries, and is especially useful when multiple users require access to the same set of data at the same time. For example, if a grid on a form uses a complex (that is, low-performing) query, you can cache the results so that they are available for subsequent loads of the form. This article discusses framework support for caching data that is used for tiles and lists. In terms of a responsive workspace, when users navigate to a workspace (or return to it), they expect that the data in the workspace will be relatively up to date. For example, if a user takes an action that changes the data for a list or tile in a workspace, the workspace should reflect that change immediately after the action is performed (if the action was taken directly from the workspace) or when the user returns to the workspace form (if the action was taken on a different form). This article describes techniques for making sure that this type of data refresh occurs (both metadata and code) for both tiles and lists.

## Count tiles
### Automatic data caching

The framework automatically sets up data caching behind any defined count tile. Therefore, no extra code is required in this case. A **Refresh Frequency** metadata property on Tiles determines how often the count on the tile is automatically updated. The following table describes the options and guidance for this property.

| Value                              | When to use                                                                                                                |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| As Fast As Permissible (5 seconds) | Query execution time is 25 ms or less, and there is demand to see the updated value all the time.                          |
| 10 Minutes                         | Query execution time is less than 250 ms, and updated data must be seen periodically                                       |
| 24 Hours                           | Query execution time is less than 2000 ms, and/or the count isn't expected to change often or up-to-date counts are vital. |

### Refresh management

Count tiles that show values that represent pending work should be fairly responsive. Ideally, the fastest possible refresh frequency should be defined for these tiles, so that the count that appears on a workspace tile is always within five seconds of being up to date. Because this quick refresh rate should be set only on performant queries (queries that have an execution time of less than 25 ms), the first recommendation is that you work on query performance for count tiles, to try to get query execution under the 25-ms threshold. In general, achieving this execution speed requires two things:

-   A selective WHERE condition on the query Preferably, the conditions on the query should reduce the result set to fewer than ~500 records, and ideally to fewer than ~100 rows.
-   An index structure that can act on the selective WHERE condition

See the "Common mistakes and tips for query optimization" section for details about how to evaluate and improve query performance to achieve these execution speeds. For tiles that have backing queries and can't meet the 25-ms execution speed threshold, the refresh frequency on the tile should be set to one of the lower values (for example, 10 minutes or 24 hours). If the values must be updated more frequently for tiles that have less-efficient queries (which should be rare), you can add the following code to manually refresh the cache when an action is taken that will affect the cached set.

```xpp
TileDataService::forceRefresh(tilestr(<tileName>), formRun)
```

An example of a data set that might not change often is products that have no configuration. A tile that shows this count might have a refresh frequency of 10 minutes. However, the tile count might still appear responsive if the products form is instrumented to force-refresh the data cache when a configuration is defined for a product that previously had no configuration.

## Workspace lists
Although the framework automatically sets up data caches for count tiles, manual setup is required for lists that must use data caching. Here are the high-level steps for introducing cached data for a list:

1.  Create a query that references all the columns that you want in the cached data set.
2.  Create a table that contains all the fields that you want to cache.
3.  Create a class that defines a mapping between the cache query and cache table.
4.  Add/reference the cached table as a data source on your form.

Each of these steps is described in detail in the following sections and is paired with an example from the Fleet workspace (Reservation Management).

### Cache query

First, you must create a query that will be used to populate the cache table. This query should have the following characteristics:

-   It should be against the tables that you want to get your cache data from.
-   It should limit the results to the results that you’re actually interested in.
-   It should select only the fields that you want to cache. **Note:** Each data source should have **DynamicFields**=**No** to avoid extraneous fields.

### Cache table

Next, you must define a table that contains a set of fields that match the fields from the cache query. In addition to those fields, you must also add a field that is named **SysDataCacheContextId** (Int64). This field is used to map the cache row to the base cache tables. You'll define a mapping on the table, between the SysDataSetCacheTableMap table’s **Id** and **SysDataCacheContextId** fields and the cache table’s **RecId** and **SysDataCacheContextId** fields, respectively. You can also define relations between this table and others, in addition to data methods that use the cached fields.

### Cache class

The third step is to create a class that defines the relationship between the cache query and the cache table. This class requires that a few attributes be defined, and it must also extend and implement the appropriate framework data caching classes. The following code shows the corresponding class from the Reservation Management workspace.

```xpp
[SysDataSetExtension(classStr(FMPickupAndReturn)), // The name of this class
SysDataSetCacheTableExtension(tableStr(FMPickupAndReturnTable))] // The name of the cache table
class FMPickupAndReturn extends SysDataSetQuery implements SysIDataSet
{
    public SysDataCacheRefreshFrequency parmRefreshFrequency()
    {
        return 600; // Cache refresh frequency, in seconds.
    }
    public SysQueryableIdentifier parmQueryableIdentifier()
    {
        return queryStr(FMPickupAndReturnQuery); // The name of the query.
    }
    public SysDataCacheTypeId parmCacheTypeId()
    {
        return tableNum(FMPickupAndReturnTable); // The name of the table.
    }
    public static FMPickupAndReturn construct()
    {
        return new FMPickupAndReturn();
    }
}
```

In some circumstances, you might also have to implement the **parmQueryableToCacheMapping()** method. This method is required when at least one column name in your cache table doesn't match the name of the corresponding column in the backing table (for example, if you must add two fields that have the same name but are from different tables). In this case, you can implement this method to define the column mapping between the cache table and the backing tables. The syntax is the same as the syntax for the **Query::Insert\_RecordSet()** method (<https://msdn.microsoft.com/library/query.insert_recordset.aspx>).

```xpp
public Map parmQueryableToCacheMapping()
{
    Map sourceToTargetMap = super();
    return sourceToTargetMap;
}
```

### Form implementation

After you've built your cache query, table, and class, you’re ready to use the cache on your form. Add the cache table to your form as a data source, and reference it just as you would reference any other data source. In order for the form to correctly take advantage of caching, some code is required.

1.  In a **registerDatasourceOnQueryingEvent()** method, add an event handler to the data source’s **OnQueryExecuting** event that calls **prepareDataSet**,. This requires that the form class implement **SysIDataSetConsumerForm**.
2.  If you want the form to use filtering, as provided by a workspace-wide filter, in a **registerDatasourceOnQueryingEvent()** method, register **applyFilter** on the **OnQueryExecuting** event. This requires that the form class implement **SysIFilterConsumerForm**.
3.  If the form must react when a parent form’s filters change (for example, a workspace-wide filter), implement **SysIFilterEventHandler** on the form class, and include an **onFilterChanged()** method that calls **executeQuery()** on the cache data source.

The following code is an example from the **FMPickingUpTodayPart** form, which is one of the tabbed lists on the Reservation Management workspace.

```xpp
[Form]public class FMPickingUpTodayPart extends FormRun
implements SysIFilterConsumerForm, SysIDataSetConsumerForm, SysIFilterEventHandler
{
    public void registerDatasourceOnQueryingEvent()
    {    
        FMPickupAndReturnTable_DS.OnQueryExecuting += eventhandler(this.parmDataSetFormQueryEventHandler().prepareDataSet);    
        FMPickupAndReturnTable_DS.OnQueryExecuting +=eventhandler(this.parmFilterFormQueryEventHandler().applyFilter);    
    }
    public void onFilterChanged()
    {    
        FMPickupAndReturnTable_DS.executeQuery();    
    }    
}
```

### Additional examples

In addition to the previous examples, you can refer to **SysFoundationTestOpenHeaderDataset**, which is used on **SysFoundationTestOpenHeadersFormPart** (which is itself referenced in **SysFoundationTestWorkspace**). This form uses the same method that is described earlier, but also includes some caching of a query aggregate count.

### Refresh management

Lists of data in workspaces should also be responsive to user actions, especially if those actions cause records to no longer meet the criteria for appearing in the list. For example, you have a list of car rentals that are scheduled to start today. Every time that an employee initiates a rental record from that list with a customer, that record should no longer appear in the workspace list. Two mechanisms are available for keeping this list up to date:

-   If the user takes an action that removes the record from the list, code can be added to guarantee that the list is immediately updated by refreshing the data source. If the data source is a cache data source, and the refresh frequency is slow, you might want to delete the corresponding records from the cache data source before you call **refresh**, to avoid having to force-refresh the cache.
-   If the first option doesn't meet your requirements, you can asynchronously refresh form parts at a time interval. This option can be set up by using the **AutoRefreshInterval** property on the FormPart control.
    -   For workspaces that have user interaction, the cache refresh frequency should be set based on query performance. In this case, the current recommendation is to not set the **AutoRefreshInterval**. Instead, rely on the user to manually refresh the workspace to bring in more data. Alternatively, you consider using an infrequent auto-refresh. However, in this case, the user’s current selection will not be retained if the list is updated while the user is interacting with it.
    -   A small percentage of workspaces are intended for viewing purposes only (no user interaction). These workspaces should use set the **AutoRefreshInterval** property programmatically to match the current refresh frequency of the backing cache. (Use **SysIDataCacheConfiguration.parmRefreshFrequency()** to retrieve the current refresh frequency of a cache, because it can be modified by the system administrator at run time.)
    -   FormParts that have Charts should set the **AutoRefreshInterval** property to periodically show updated chart data.

## Common mistakes and tips for query optimization
Here a few general guidelines to consider when you optimize queries. This isn't an extensive guide to query optimization but provides just a few simple guiding principles.

-   **Trace the statement by using SQL Profiler.** Attach the Microsoft SQL Server Profiler to the database, and capture the SQL statement that you want to optimize. You can use the tuning template that is provided in a default installation. Don’t forget to disable tracing after you've obtained the statement that you're interested in. For more information, see <https://msdn.microsoft.com/library/ms175047.aspx>.
-   **Always look at the query plan.** In Microsoft SQL Server Management Studio, make sure that you've enabled **Include actual Execution Plan**. Look at the query plan, and watch out for any warnings. The thickness of the arrows indicate how many rows have been fetched and brought to the next step.
-   **Compare CPU milliseconds and logical I/O.** One good way to determine whether a change to a given SQL statement improved the statement is to look at the logical I/O and CPU milliseconds. To obtain these numbers, use the following statements in the query editor:
    -   set statistics time on
    -   set statistics io on
-   **Always clear caches when you measure a statement.** To make sure that Microsoft SQL Server isn't using a cached execution plan, it's advisable that you flush the cache when you rerun a statement. To flush the cache, run the following two commands:
    -   dbcc dropCleanBuffers
    -   dbcc freeProcCache
-   **Here are some common patterns to watch out for:**
    -   **Missing index:** Analyze your WHERE conditions, and make sure that a selective index exists.
    -   **Processing the same table/row many times:** Especially when you do joins, try not to repeat yourself. Minimize the number of times that the same table/row must be processed. If you have tables that must be part of the result set but aren't used to narrow down the result set, move them as far out as possible (especially in union queries).
-   **Test on volume data.** To identify issues in your query, always run it on volume data.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
