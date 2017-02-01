---
# required metadata

title: Analysis in the Intelligent Data Management Framework (AX 2012) | Microsoft Docs
description: This topic describes the functionality available from the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF) Analysis menu.
author: kfend
manager: AnnBe
ms.date: 2015-12-04 20:04:53
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 51
ms.suite: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 17672
ms.assetid: 6b7eb698-b9e8-4ef0-b46c-85f6e2677c84
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Analysis in the Intelligent Data Management Framework (AX 2012)

This topic describes the functionality available from the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF) Analysis menu.

The **Analysis** menu lets you analyze the production and archive databases, and application health statistics, from the production replica database. IDMF automatically starts in the **Analysis dashboard** view for the production database.

## Analysis dashboard (Production database group)
The **Analysis dashboard** command shows a graphical view of the database that resembles the following screen shot. At least two database analysis schedules must be completed before the database growth trend chart is displayed. The controls and commands available for the analysis dashboard are similar for the production database and the archive database. The command you click becomes unavailable, to visually distinguish the database that is being used. For example, when you click **Analysis dashboard** from the **Production database** group, the command becomes unavailable, as shown in the following screen shot. ![IDMF Analysis Dashboard](./media/idmfanalysisdashboard.png)

### Navigation of the Analysis dashboard workspace

The following table describes the panes in the Analysis dashboard workspace.

| Pane                            | Description                                                                                                                                                                                                                                                                                                                                |
|---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Top 10 tables by row count**  | Provides a graphical view of the top 10 tables by row count. The pie chart shows the name of the table and the number of rows when you point to an area. The percentage shown for each table is calculated from the number of rows in the table versus the total rows in the top 10 tables.                                                |
| **Top 10 tables by data size**  | Provides a graphical view of the top 10 tables by data size. The pie chart shows the name and size of the table when you point to an area. The percentage shown for each table is calculated from the size of the table versus the total size of the top 10 tables.                                                                        |
| **Top 10 tables by index size** | Provides a graphical view of the top 10 tables by index size. The pie chart shows the name of the table and the size of the index when you point to an area. The percentage shown for each table is calculated from the index size of the table versus the total index size of the top 10 tables.                                          |
| **Table and index space**       | Provides two pie charts. One chart provides a graphical view of the table space used by the top 10 tables versus other tables. The other chart provides a graphical view of the index space used by the top 10 tables versus other tables.                                                                                                 |
| **Database growth trend**       | Provides a trend analysis of your production or archive database over multiple snapshots. You must have a minimum of two snapshots to see the trend analysis. The trend analysis processes the 10 most recent snapshots. Snapshots that are older than the 10 most recent snapshots are ignored by the trend analysis feature.             |
| **Row count trend**             | Provides the row count trend analysis of your production or archive database over multiple snapshots. You must have a minimum of two snapshots to see the trend analysis. The trend analysis processes the 10 most recent snapshots. Snapshots that are older than the 10 most recent snapshots are ignored by the trend analysis feature. |

## Analysis details (Production database group)
The **Analysis details** command provides detailed database analysis information that resembles the following screen shot. At least two database analysis schedules must be completed before the table growth trend chart and the **Growth trend** button are displayed. Use the Analysis details workspace to work with database and index analysis for the production or archive database, to work with the performance dashboard for the selected database, or to manage indexes for the production database. The controls and commands available for the analysis details are similar for the production database and the archive database. The command you click becomes unavailable, to visually distinguish the database that is being used. For example, when you click **Analysis details** from the **Production database** group, the command becomes unavailable, as shown in the following screen shot. ![IDMF Analysis Details](./media/idmfanalysisdetails.png)
### Navigation of the Analysis details workspace

The following tables provide descriptions for the controls in this workspace. For a detailed explanation of Microsoft SQL Server terms, see the [SQL Server documentation](http://go.microsoft.com/fwlink/?LinkId=227464).
#### Panes

| Pane                                            | Description                                                                                                                                                                                                                               |
|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Upper-left pane (by default, **Top 50 tables**) | Displays sizing statistics for each table. By default, IDMF displays the top 50 tables. You can select **Top 100 tables** or **All tables** by using the filter on the title bar of the pane.                                             |
| **Index details**                               | Displays index statistics for the selected table and lets you defragment selected fragmented indexes.                                                                                                                                     |
| **Related information**                         | Provides additional information about some tables. If the selected table has any additional information, it appears in this pane. Read the related information carefully, because it provides critical insights about the selected table. |
| **Graphical view**                              | Appears below the Related information pane, and displays the Table information view by default. Change the graphical view by clicking a button that appears below the Graphical view pane.                                                |

#### 

#### Tabs (Index details pane)

| Tab               | Description                                                                                                                                                                                                                                       |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Index details** | Provides information about the data size and index size, and index information for indexes of the selected table.                                                                                                                                 |
| **Index stats**   | Provides information about the index statistics, such as the index reads, index writes, and system fragmentation percentage.                                                                                                                      |
| **Fragmentation** | Provides information about index fragmentation. Select one or more rows in the grid, and then click **Defragment index** to create a schedule to defragment the selected indexes. Creating and managing schedules is covered later in this topic. |

#### 

#### Buttons

| Button                                       | Description                                                                                                                                                                   |
|----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Defragment index** (**Fragmentation tab**) | Create a schedule to defragment selected indexes.                                                                                                                             |
| **Growth trend**                             | Display a graphical view of the growth trend of the selected table. This button appears only after successful completion of two or more database analysis snapshot schedules. |
| **Table information**                        | Display a graphical view of the record count by company for the selected table.                                                                                               |
| **Top 10 tables**                            | Display a graphical view of the top 10 tables by data size, in megabytes.                                                                                                     |
| **Top 10 unused indexes**                    | Display a graphical view of the top 10 unused indexes by index size.                                                                                                          |
| **Top 10 fragmented indexes**                | Display a graphical view of the top 10 fragmented indexes.                                                                                                                    |
| **By table group**                           | Display a graphical view of data size by table group.                                                                                                                         |
| **By configuration key**                     | Display a graphical view of data size by configuration key.                                                                                                                   |
| **Alerts**                                   | Display a list of alerts. Additional details for the selected alert, if there are any, appear in the Related information pane.                                                |

#### 

#### Fields (upper-left pane)

| Field                       | Description                                                            |
|-----------------------------|------------------------------------------------------------------------|
| **Table name**              | The name of the table.                                                 |
| **Rows**                    | The number of rows in the table.                                       |
| **Reserved (MB)**           | The size that is reserved for the table in the database, in megabytes. |
| **Data size (MB)**          | The total data size of the table, in megabytes.                        |
| **Index size (MB)**         | The total index size for the table, in megabytes.                      |
| **Unused (MB)**             | The unused database space in this table, in megabytes.                 |
| **Index to data ratio (%)** | The index-to-data ratio for this table, expressed as a percentage.     |

#### 

#### Fields (Index details pane, Index details tab)

| Field                 | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **Index name**        | The name of the index.                                                      |
| **Index size (MB)**   | The index size.                                                             |
| **Index keys**        | The columns that are used to create the index.                              |
| **Index description** | Index properties, such as clustered, non-clustered, unique, or primary key. |

#### 

#### Fields (Index details pane, Index stats tab)

By default, the data grid displays an average of all snapshots which is indicated by the value **All** in the **Stats time** column. Expand each index to see the statistics for each snapshot.
| Field                   | Description                                                                                                                      |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| **Index name**          | The name of the index. Expand this node to see statistics for each snapshot.                                                     |
| **Stats time**          | The timestamp for each snapshot, or an average of all snapshots (shown as **All**). By default, the data grid is set to **All**. |
| **Index reads**         | The number of index reads.                                                                                                       |
| **Index writes**        | The number of index writes.                                                                                                      |
| **Avg fragmentation %** | The index fragmentation percentage.                                                                                              |
| **Index description**   | Index properties, such as clustered, non-clustered, unique, or primary key.                                                      |
| **Index keys**          | The fields that are used to create the index.                                                                                    |
| **User seeks**          | The number of user seeks.                                                                                                        |
| **User scans**          | The number of user scans.                                                                                                        |
| **User lookups**        | The number of user lookups.                                                                                                      |
| **System seeks**        | The number of system seeks.                                                                                                      |
| **System scans**        | The number of system scans.                                                                                                      |
| **System lookups**      | The number of system lookups.                                                                                                    |
| **Index size (MB)**     | The index size, in megabytes.                                                                                                    |

#### 

#### Fields (Index details pane, Fragmentation tab)

| Field                         | Description                                                                                                                                                                                                |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Index name**                | The name of the index.                                                                                                                                                                                     |
| **Average fragmentation (%)** | The average fragmentation percentage for the index across all database snapshots. Select one or more indexes, and then click **Defragment index** to create a schedule to defragment the selected indexes. |

## Manage indexes
This command lets you create a schedule to defragment fragmented indexes. Follow these steps to create a schedule to defragment fragmented indexes:
1.  Click **Analysis** &gt; **Manage indexes** to open the **Manage indexes** window. This window contains the **Unused indexes** and **Fragmented indexes** tabs. Both tabs provide a data grid that contains **Table name** and **Index name** fields. The **Fragmented indexes** tab also provides fragmentation percentages for indexes. Use this window to create a schedule to defragment fragmented indexes.
2.  In the **Manage indexes** window, click the **Fragmented indexes** tab. This tab provides a list of all the tables and their fragmented indexes. Use the **Advanced** filter control to search by table name or fragmentation percentage. Click the column headings in the data grid to sort the column in ascending or descending sequence.
3.  Select the table or index of interest. You can select multiple indexes from multiple tables. You must select at least one index to create a schedule. Click **Schedule**.
4.  In the **Task details** pane, enter the required information, and then click **Save**.
5.  Confirm that the schedule appears in the **Scheduled tasks** pane.

| **Note**                                                                                                                                            |
|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Some indexes retain a non-zero fragmentation percentage even after the defragmentation schedule is completed successfully. This is normal behavior. |

## Analysis dashboard (Archive database group)
This command provides similar information for the archive database as the **Analysis dashboard** command in the **Production database** group provides for the production database. For detailed information, see the section "[Analysis dashboard (Production database group)](#AnalysisProduction)."
Analysis details (Archive database group)
-----------------------------------------

This command provides similar information for the archive database as the Analysis details command in the Production database group provides for the production database. For detailed information, see [Analysis functionality in the Microsoft Dynamics AX Intelligent Data Management Framework workspace (IDMF)](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/lifecycle-services/ax-2012/analysis-functionality-in-the-microsoft-dynamics-ax-intelligent-data-management-framework-workspace-idmf).
Show system health
------------------

This command provides graphical views and details for key measures from the Microsoft Dynamics AX application, based on predetermined queries. You can also create your own queries by using the **Administer** &gt; **Application health check** command. A measure captures aggregated statistics for key business processes for each company in the Microsoft Dynamics AX application. This information is captured across calendar years, based on the ledger periods you set up in the application. For example, the measure **Number of inactive Sales Quotations** is calculated as "the total number of sales quotations which are canceled, confirmed, or lost." The total is grouped by company and by year. The application health check provides key measures for the **Inventory**, **Accounts receivable**, **Accounts payable**, **General ledger**, and **Administration** modules, as shown in the following screen shot. ![Show IDMF system health](./media/idmfshowsystemhealth.png) **Figure 3. Show system health**
### Navigation of the Application health check workspace

The following tables provide descriptions for the controls in this workspace.
#### Panes

| Pane                                                 | Description                                                                                                                                                                                                                                                                                 |
|------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Application health check**                         | Provides aggregates of measures by company and by year for selected modules from the Microsoft Dynamics AX application. The default view is the aggregate of all companies by year. Expand the measure to select the measure statistics for individual companies.                           |
| **Additional health check information**              | Provides additional information for the selected measure, including a brief description, the archival relevance, and the formula that was used to calculate the measure.                                                                                                                    |
| **Measure by year for company &lt;company name&gt;** | Shows a graphical view of the selected measure for the first company in the data grid. If there are multiple companies, expand the measure and select another company to change the graphical view. When you point to an area, the chart shows the year and value for the selected measure. |
| **Measure by year**                                  | Shows a graphical view of the aggregate value for all companies for the selected measure, by year. The chart shows the year and value for the selected measure when you point to an area.                                                                                                   |
| **Measures growth trend**                            | Shows the aggregate trend analysis from different snapshots. You must complete at least two health check analysis schedules to see a graphical view in this pane. The trend analysis captures the 10 most recent snapshots and ignores older snapshots, if there are any.                   |

#### 

#### Tabs (Application health check pane)

| Tab                     | Description                                                          |
|-------------------------|----------------------------------------------------------------------|
| **Inventory**           | Provides selected measures from the **Inventory management** module. |
| **Accounts receivable** | Provides selected measures from the **Accounts receivable** module.  |
| **Accounts payable**    | Provides selected measures from the **Accounts payable** module.     |
| **General ledger**      | Provides selected measures from the **General ledger** module.       |
| **Administration**      | Provides selected measures from the **Administration** module.       |

#### 

#### Fields (Application health check pane)

| Field            | Description                                                                                                                                                                |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure name** | The name of the measure.                                                                                                                                                   |
| **Company**      | Company accounts in Microsoft Dynamics AX represent the organizational structure of a company. An aggregate of the measure for all the companies by year is listed as All. |
| **Year**         | The aggregate of the measure is put in a column for each year, based on the ledger period configuration.                                                                   |

## Performance dashboard
This command provides information about SQL Server configuration options, database options, and statistics for tables and indexes for the production and archive databases. This command displays the database configuration details for all databases used by IDMF, and table statistics and query statistics for the production and archive databases.
### Navigation of the Performance dashboard workspace

The following tables provide descriptions for the controls in this workspace.
#### Tabs (Index details pane)

| Tab                        | Description                                                                                                                                                                                                                                                                                                                                                                        |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Database configuration** | Provides information about the database properties and configuration options for the selected database, such as information about the data and log files, database options, and other database properties. This information is available for the selected database.                                                                                                                |
| **Table stats**            | This tab is only available when you select the production or archive database from the list on the **Database configuration** tab. Provides information about table statistics for the selected database, such as tables without clustered indexes, tables with missing indexes, tables with locks, and tables that can be enabled for caching in Application Object Server (AOS). |
| **Query stats**            | This tab is only available when you select the production or archive database from the list on the **Database configuration** tab. Provides information about the query statistics, such as the cached query plans, query statement, and query plan for the selected cached query plan.                                                                                            |

#### 

#### Panes (Database configuration)

| Pane                                          | Description                                                                                                                                                                                                                            |
|-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Database properties**                       | Provides database properties for the selected database, such as the database name, database owner, and number of active users, information about database and log files, and the currently configured values for the database options. |
| **Advanced SQL Server configuration options** | Provides the minimum, maximum, configured, and currently used (run) values of advanced configuration options for SQL Server.                                                                                                           |

#### 

#### Panes (Table stats)

| Pane                               | Description                                                                                                                                                                                                                                                                                                                                                |
|------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Cacheable tables**               | You can enable these tables so that Application Object Server (AOS) caches the whole table. To enable a table for caching, change the **CacheLookup** property of the table to **EntireTable**. For more information, see the Microsoft Dynamics AX developer documentation in the [MSDN Library](https://msdn.microsoft.com/en-us/library/cc678142.aspx). |
| **Tables without clustered index** | Provides a list of tables without a clustered index.                                                                                                                                                                                                                                                                                                       |
| **Missing indexes**                | Provides a list of tables that do not have any index.                                                                                                                                                                                                                                                                                                      |
| **Tables with locks**              | Provides a list of locked tables together with relevant details, such as the row or page lock count, and the row or page lock wait time.                                                                                                                                                                                                                   |

#### 

#### Panes (Query stats)

| Pane                      | Description                                                                                                                                                  |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Query plan statistics** | Provides statistics for the cached query plans, such as the usage count, and logical and physical reads and writes.                                          |
| **Query text**            | Provides the Transact-SQL query statement that was used to create the cached query plan. Click **Export** to export the query text as an SQL text file.      |
| **Query plan**            | Provides the query plan for the query text that was used to create the selected cached query plan. Click **Export** to export the query plan as an XML file. |

#### 

#### Fields (Database configuration tab)

| Field                                                         | Description                                                                                                                                                                                                                                                                                                                                                       |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Select database**                                           | Select a database from the list. The performance dashboard displays relevant information for the selected database.                                                                                                                                                                                                                                               |
| **Property name**                                             | The name of the database property, such as database name, owner, status, creation date, collation, last backup date, or number of users.                                                                                                                                                                                                                          |
| **Value**                                                     | The value of the database property. For example, the owner property value displays the current owner of the database.                                                                                                                                                                                                                                             |
| **Name (Files list)**                                         | The name of the data or log file.                                                                                                                                                                                                                                                                                                                                 |
| **File name**                                                 | The file name of the data or log file.                                                                                                                                                                                                                                                                                                                            |
| **File group**                                                | The name of the file group that is used for the data file.                                                                                                                                                                                                                                                                                                        |
| **Size**                                                      | The size of the data or log file, in kilobytes (KB).                                                                                                                                                                                                                                                                                                              |
| **Growth**                                                    | The growth size for the data or log file, in kilobytes (KB) or as a percentage.                                                                                                                                                                                                                                                                                   |
| **Usage**                                                     | Whether the file is used for the data or transaction log.                                                                                                                                                                                                                                                                                                         |
| **Property name** (**Options** list)                          | The name of the database option, such as database name, compatibility level, recovery model, or auto close.                                                                                                                                                                                                                                                       |
| **Value**                                                     | The value of the database option.                                                                                                                                                                                                                                                                                                                                 |
| **Name** (**Advanced SQL Server configuration options** pane) | The name of the SQL Server configuration option.                                                                                                                                                                                                                                                                                                                  |
| **Minimum**                                                   | The minimum value of the configuration option.                                                                                                                                                                                                                                                                                                                    |
| **Maximum**                                                   | The maximum value of the configuration option.                                                                                                                                                                                                                                                                                                                    |
| **Configuration value**                                       | The value to which the configuration option was set by using sp\_configure (the value in sys.configurations.value). For more information about these options, see [Setting Server Configuration Options](https://msdn.microsoft.com/en-us/library/ms189631.aspx) and [sys.configurations (Transact-SQL)](https://msdn.microsoft.com/en-us/library/ms188345.aspx). |
| **Run value**                                                 | The currently running value of the configuration option (the value in sys.configurations.value\_in\_use).For more information, see [sys.configurations (Transact-SQL)](https://msdn.microsoft.com/en-us/library/ms188345.aspx).                                                                                                                                   |

#### 

#### Fields (Table stats tab, Cacheable tables list)

| Field            | Description                      |
|------------------|----------------------------------|
| **Table name**   | The table name.                  |
| **Row count**    | The number of rows in the table. |
| **User seeks**   | The number of user seeks.        |
| **User scans**   | The number of user scans.        |
| **User lookups** | The number of user lookups.      |
| **User updates** | The number of user updates.      |

#### 

#### Fields (Table stats tab, Tables without clustered index list)

| Field                 | Description                                                  |
|-----------------------|--------------------------------------------------------------|
| **Table index**       | The index name.                                              |
| **Row count**         | The number of rows in the table.                             |
| **Total index reads** | The number of times this index was used for read operations. |

#### 

#### Fields (Table stats tab, Missing indexes list)

| Field                   | Description                                                                                                                                                                                                                                            |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Table name**          | The name of the table.                                                                                                                                                                                                                                 |
| **Equality columns**    | A comma-separated list of columns that contribute to equality predicates, in the form table.column = constant\_value.                                                                                                                                  |
| **Inequality columns**  | A comma-separated list of columns that contribute to inequality predicates, such predicates in the form table.column &gt; constant\_value.                                                                                                             |
| **Included columns**    | A comma-separated list of columns required as covering columns for the query.                                                                                                                                                                          |
| **Avg total user cost** | The average cost of the user queries that may be able to be reduced by the index in the group.                                                                                                                                                         |
| **Avg user impact**     | The average benefit, as a percentage, that user queries may be able to experience if this missing index group is implemented. The value means that the query cost may, on average, drop by this percentage if this missing index group is implemented. |
| **Last user seek**      | The date and time of the last seek caused by user queries that the recommended index in the group could have been used for.                                                                                                                            |
| **Unique compiles**     | The number of compilations and recompilations that may benefit from this missing index group. Compilations and recompilations of many different queries can contribute to this column value.                                                           |

#### 

#### Fields (Tables with locks list)

| Field                              | Description                                                                              |
|------------------------------------|------------------------------------------------------------------------------------------|
| **Table name**                     | The name of the table.                                                                   |
| **Index name**                     | The name of the index.                                                                   |
| **Index description**              | Index properties, such as clustered, non-clustered, unique, primary key, or heap.        |
| **Row lock waits (milliseconds)**  | The total number of milliseconds the database engine waited on a row lock.               |
| **Page lock waits (milliseconds)** | The total number of milliseconds the database engine waited on a page lock.              |
| **Row lock wait count**            | The cumulative number of times (milliseconds) the database engine waited on a row lock.  |
| **Row lock count**                 | The cumulative number of row locks requested.                                            |
| **Page lock count**                | The cumulative number of page locks requested.                                           |
| **Page lock wait count**           | The cumulative number of times (milliseconds) the database engine waited on a page lock. |
| **Index lock promotion count**     | The cumulative number of times the database engine escalated locks.                      |

#### 

#### Fields (Query stats tab, all panes)

The **Select a snapshot** **time** list lets you select query plan statistics, query text, and a query plan for a specific analysis snapshot. By default, the list displays the most recent time. The data grid filters the information based on your selection. The following table describes the fields in the data grid.
| Field                    | Description                                                                                                        |
|--------------------------|--------------------------------------------------------------------------------------------------------------------|
| **Usage count**          | The number of time the plan has been run since it was last compiled.                                               |
| **Total elapsed time**   | The total elapsed time, in microseconds, for completed processing of this plan.                                    |
| **Total worker time**    | The total amount of CPU time, in microseconds, that was consumed by processing of this plan since it was compiled. |
| **Avg elapsed time**     | The average amount of CPU time, in microseconds, based on the **Usage count** and **Total worker time** values.    |
| **Avg physical reads**   | The average number of physical reads performed by processing of this plan since it was compiled.                   |
| **Avg logical reads**    | The average number of logical reads performed by processing of this plan since it was compiled.                    |
| **Last elapsed time**    | The elapsed time, in microseconds, for the most recently completed processing of this plan**.**                    |
| **Min elapsed time**     | The minimum elapsed time, in microseconds, for any completed processing of this plan.                              |
| **Max elapsed time**     | The maximum elapsed time, in microseconds, for any completed processing of this plan.                              |
| **Total physical reads** | The total number of physical reads performed by processing of this plan since it was compiled.                     |
| **Last physical reads**  | The number of physical reads performed the last time the plan was processed.                                       |
| **Min physical reads**   | The minimum number of physical reads that this plan has ever performed during a single processing.                 |
| **Max physical reads**   | The maximum number of physical reads that this plan has ever performed during a single processing.                 |
| **Total logical reads**  | The total number of logical reads performed by processing of this plan since it was compiled.                      |
| **Last logical reads**   | The number of logical reads performed the last time the plan was processed.                                        |
| **Min logical reads**    | The minimum number of logical reads that this plan has ever performed during a single processing.                  |
| **Max logical reads**    | The maximum number of logical reads that this plan has ever performed during a single processing.                  |
| **Total logical writes** | The total number of logical writes performed by processing of this plan since it was compiled.                     |
| **Last logical writes**  | The number of logical writes performed the last time the plan was processed.                                       |
| **Min logical writes**   | The minimum number of logical writes that this plan has ever performed during a single processing.                 |
| **Max logical writes**   | The maximum number of logical writes that this plan has ever performed during a single processing.                 |
| **Last worker time**     | The CPU time, in microseconds, that was consumed the last time the plan was processed.                             |
| **Min worker time**      | The minimum CPU time, in microseconds, that this plan has ever consumed during a single processing.                |
| **Max worker time**      | The maximum CPU time, in microseconds, that this plan has ever consumed during a single processing.                |

## Export to Excel
This command lets you export selected rows from the data grid in all workspaces where this command is available.



