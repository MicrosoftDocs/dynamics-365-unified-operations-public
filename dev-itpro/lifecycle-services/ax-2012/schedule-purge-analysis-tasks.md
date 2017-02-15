---
# required metadata

title: Troubleshoot your Dynamics AX 2012 R3 deployment on Azure
description: This topic describes the options on the Microsoft Dynamics AX Intelligent Data Management Framework(IDMF) Schedule menu, and how to use them.
author: annbe
manager: AnnBe
ms.date: 2015-12-05 17 - 58 - 43
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18631
ms.assetid: c5438f25-3030-49c7-a233-1bdde1facffd
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: 
ms.dyn365.version: 2012

---

# Troubleshoot your Dynamics AX 2012 R3 deployment on Azure

This topic describes the options on the Microsoft Dynamics AX Intelligent Data Management Framework(IDMF) Schedule menu, and how to use them.

Overview of scheduling
----------------------

Use the **Schedule** menu to schedule tasks. IDMF lets you create different types of tasks from different areas of the application, as shown in the following table.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Task type</th>
<th>Description</th>
<th>Available from</th>
<th>Frequency defaults to</th>
<th>Frequency can be changed</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Defragment index</td>
<td>Defragments selected indexes. Follow these steps to defragment indexes:
<ol>
<li>Click <strong><span class="ui">Analysis</span> menu</strong> &gt; <strong><span class="ui">Manage indexes</span></strong>.</li>
<li>On the <strong><span class="ui">Fragmented indexes</span></strong> tab, select the indexes to defragment, and then click <strong><span class="ui">Schedule</span></strong>.</li>
</ol>
–or–
<ol>
<li>Click <strong><span class="ui">Analysis</span> menu</strong> &gt; <strong><span class="ui">Analysis details</span></strong> &gt; <span class="ui"><strong>Index details</strong> pane</span> &gt; <strong><span class="ui">Fragmentation</span></strong> tab.</li>
<li>Select the indexes to defragment.</li>
<li>Click <strong><span class="ui">Defragment index</span></strong>.</li>
</ol></td>
<td><strong><span class="ui">Analysis</span></strong> menu</td>
<td>One time only</td>
<td>No</td>
</tr>
<tr class="even">
<td>Analysis snapshot</td>
<td>Creates a snapshot of the database, including the data size, index size, and index fragmentation. This task is available for the production and archive databases.</td>
<td><strong><span class="ui">Schedule</span></strong> menu</td>
<td></td>
<td>Yes</td>
</tr>
<tr class="odd">
<td>Ledger periods</td>
<td>Creates ledger periods that are used for the application health check queries. This task uses the production replica database.</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Health check</td>
<td>Creates an application snapshot of selected measures from key modules. This task uses the production replica database.</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Metadata synchronization</td>
<td>Copies all database objects, but not data, from the production database to the archive database, based on the Microsoft Dynamics AX metadata.</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Master data synchronization</td>
<td>Copies data from the production database to the archive database for selected tables.</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Purge</td>
<td>Deletes records from the production database, using a Purge Object and based on verification of rules in the Purge Object.</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Archive</td>
<td>Moves or archives records from the production database to the archive database, using an Archive Object and rules in the Archive Object.</td>
<td></td>
<td></td>
<td>No</td>
</tr>
<tr class="odd">
<td>Restore archive</td>
<td>Restores data from the archive database to the production database.</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Restart</td>
<td>Restarts the following failed or ended tasks:
<ul>
<li>Archive</li>
<li>Restore archive</li>
<li>Revert task</li>
</ul></td>
<td><strong><span class="ui">Status</span></strong> &gt; <strong><span class="ui">Job Status</span></strong> window</td>
<td></td>
<td>No</td>
</tr>
<tr class="odd">
<td>Revert</td>
<td>Reverts a failed or canceled archive task, and brings the production database to the state it was in before the archive task started.</td>
<td><strong><span class="ui">Status</span></strong> &gt; <strong><span class="ui">Job Status</span></strong> window</td>
<td></td>
<td>No</td>
</tr>
</tbody>
</table>

## Navigation of the Scheduled tasks window
The following tables provide descriptions for the controls in the Scheduled tasks window. All tasks use this window.

### Panes

| Pane                    | Description                                                                                                                                                                                                                                             |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Scheduled tasks**     | Provides a list of tasks that you have created. To delete inactive current or future tasks, select the tasks. Right-click the selected tasks, and then select **Delete schedule(s)**. In the **Delete schedule** dialog box, click **Yes** to continue. |
| **Task details**        | Provides an area to enter the necessary information to create a scheduled task.                                                                                                                                                                         |
| **Related information** | Provides a list of the steps required to create a scheduled task.                                                                                                                                                                                       |

### 

### Tabs

| Tab                             | Description                                                                                                                                  |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| **General**                     | Allows you to enter or modify the name and description of the task.                                                                          |
| **Configure rules for purge**   | Allows you to enter values for the rules that are created in the Purge Object. This tab is available only when you create a purge task.      |
| **Configure rules for archive** | Allows you to enter values for the rules that are created in the Archive Object. This tab is available only when you create an archive task. |
| **Configure archive restore**   | Allows you to select the archive task that is used to restore data. This tab is available only when you create a restore archive task.       |
| **Schedule**                    | Allows you to enter or select the frequency, start date, and start time of the task.                                                         |

### Buttons

| Button          | Description                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Save/Update** | Save the new or modified task. A saved task appears in the list in the **Scheduled tasks** pane. The label changes to **Update** when you select an existing task, and to **Save** when you are adding a new task. |
| **Cancel**      | Cancel an add or edit action.                                                                                                                                                                                      |

### 

### Fields (Scheduled tasks pane)

| Field             | Description                                                                                                                                    |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| **Schedule name** | The name of the task.                                                                                                                          |
| **Type**          | The type of the task.                                                                                                                          |
| **Occurs**        | The frequency, start date, and start time of the task.                                                                                         |
| **Created by**    | The user ID that created the task. By default, this value is the logon ID of the user that created the task, and you cannot change this value. |
| **Description**   | A description of the task.                                                                                                                     |

### 

### Fields (Task details pane)

#### General tab

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong><span class="ui">Name</span></strong></td>
<td>Enter the name of the task in this field.</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Description</span></strong></td>
<td>Enter the description of the task in this field.</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">Author name</span></strong></td>
<td>By default, this value is the currently logged on user, and you cannot change this value.</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Index physical statistics</span></strong></td>
<td>When this field is selected, the analysis snapshot task captures physical statistics for indexes, such as the defragmentation percentage. This field is selected by default when you run the analysis snapshot for the first time. This capture is resource intensive and affects the performance of your production system. Therefore, the field is not automatically selected for snapshots after the first snapshot. You must manually select the field to recalculate index statistics. Schedule the snapshot at times that least affect your users.</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">Statistics by company</span></strong></td>
<td>When this field is selected, the index and data statistics are grouped by each company in your Microsoft Dynamics AX system. This field is selected by default when you run the analysis snapshot for the first time. The grouping of data and index statistics by company is resource intensive and affects the performance of your production system. Therefore, the field is not automatically selected for snapshots after the first snapshot. You must manually select the field to group statistics by company. Schedule the snapshot at times that least affect your users.</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Select archive type</span></strong></td>
<td>Select a value from the list to indicate whether the archival transactions are row-based or set-based. Select <strong><span class="ui">Row-by-row</span></strong> to create a row-based transactional unit for the archival function. A row-based transactional unit archives a single row from the Archive Object at a time. Similarly, a set-based transactional unit archives all matching records from the Archive Object as a record set.The default value for this list is <strong><span class="ui">Set-based</span></strong>. We recommend that you use a set-based archive type for improved performance.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>This field is available only for an archive task.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">Number of threads</span></strong></td>
<td>Select the number of threads that are used for master data synchronization, ranging from 1 to 8. When you select a number that is larger than 1, each thread processes a certain number of tables.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>This field is available only for a master data synchronization task.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
</tbody>
</table>

#### 

#### Schedule tab

| Field                    | Description                                                                                                                                                             |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Frequency**            | Select a frequency from the list.                                                                                                                                       |
| **Start date**           | Select or enter the start date in the date control.                                                                                                                     |
| **Start time**           | Select or enter the time by using the hour, minute, and AM/PM lists.                                                                                                    |
| **Every day**            | Select a daily schedule. This field is available only for the daily frequency.                                                                                          |
| **Every &lt;n&gt; days** | Select the number of days between recurrences of a task. For example, select 10 to repeat the task every 10 days. This field is available only for the daily frequency. |
| **Select days**          | Select the days of recurrence in a weekly task. This field is available only for the weekly frequency.                                                                  |
| **Select months**        | Select the months of recurrence in a monthly task. This field is available only for the monthly frequency.                                                              |
| **Day**                  | Select the date of recurrence in a monthly task. This field is available only for the monthly frequency.                                                                |

#### 

#### Configure rules for purge tab (only appears when you create a purge task)

| Field            | Description                                                               |
|------------------|---------------------------------------------------------------------------|
| **Purge Object** | Select the Purge Object that you want to use in the purge task.           |
| **Table**        | The name of the table that is used in the rule.                           |
| **Field**        | The name of the field that is used in the rule.                           |
| **Operator**     | The condition that is used in the rule.                                   |
| **Value**        | Select or update values for the rules. Verify rules with existing values. |

#### 

#### Configure rules for archive tab (only appears when you create an archive task)

| Field              | Description                                                               |
|--------------------|---------------------------------------------------------------------------|
| **Archive Object** | Select the Archive Object that you want to use in the archive task.       |
| **Table**          | The name of the table that is used in the rule.                           |
| **Field**          | The name of the field that is used in the rule.                           |
| **Operator**       | The condition that is used in the rule.                                   |
| **Value**          | Select or update values for the rules. Verify rules with existing values. |

#### 

#### Configure archive restore tab (only appears when you create a restore archive task)

| Field              | Description                                                                                                                                                                                                                                                                                                                                                                                                      |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Restore type**   | Select the filter that is applied to the task that you are restoring. When you select **Other schedules**, the data grid displays the names of all successfully archived tasks.                                                                                                                                                                                                                                  |
| **Schedule**       | The name of the archive task. Select the task that you want to restore. You can select multiple tasks. If you select a prior task, all the more recent tasks are selected automatically. For example, if you select 2014 for restoration, 2013 and 2012 are automatically selected for restoration. The Microsoft Dynamics AX application requires data for the more recent periods for transactional integrity. |
| **Archive date**   | The date when the archive task was run.                                                                                                                                                                                                                                                                                                                                                                          |
| **Archive Object** | The name of the Archive Object.                                                                                                                                                                                                                                                                                                                                                                                  |

## Production database
This command lets you create a new database analysis snapshot task for the production database. The database snapshot task runs queries against the production database to capture database statistics such as the data size, index size, table size, and data and index usage. You must have at least one database analysis snapshot to work with IDMF. You can schedule recurring database snapshots to create the trend analysis of your production database. The trend analysis requires a minimum of two database analysis snapshots and processes up to the latest 10 snapshots, ignoring earlier ones, if you have any. On the toolbar, click **Production database** to create a scheduled task for the database analysis. Enter the required information in the **Scheduled tasks** window, and then click **Save**. This information is used in the analysis dashboard, analysis details, and performance dashboard for the production database on the **Analysis** menu.

## Archive database
This command lets you create a new database analysis snapshot task for the archive database. The database snapshot task runs queries against the archive database to capture database statistics such as the data size, index size, table size, and data and index usage. This is an optional step. This information is used in the analysis dashboard, analysis details, and performance dashboard for the archive database on the **Analysis** menu. You must have at least one database analysis snapshot to work with the analysis dashboard and analysis details for the archive database. The trend analysis requires a minimum of two database analysis snapshots and processes up to the 10 most recent snapshots. IDMF works with the 10 most recent snapshots and ignores earlier ones, if you have any. On the toolbar, click **Archive database** to create a scheduled task for the database analysis. Enter the required information in the **Scheduled tasks** window, and then click **Save**.

## Ledger periods
This command les you create a new task for the ledger periods that are required by the health check queries to capture and aggregate transactional information by company and year. You must successfully complete this task before running a health check task. On the toolbar, click **Ledger periods** to create a scheduled task for the ledger periods. Enter the required information in the **Scheduled tasks** window, and then click **Save**. This command works with the production replica database.

## System health check
This command creates a snapshot of key measures from the **Inventory management**, **Accounts receivable**, **Accounts payable**, **General ledger**, and **Administration** modules in the Microsoft Dynamics AX application. These queries capture an aggregate for each measure by company and by year. The number of years this information is captured for depends on the information in your ledger periods table. A measure provides information about a specific business process. For example, the **Inventory management** module provides a measure called **Cancelled Inventory Settlement**. You must have at least one application health check analysis snapshot to work with the application health check measures. You can schedule recurring application health check snapshots to create the trend analysis of your application health. The trend analysis requires a minimum of two analysis snapshots and processes up to the latest 10 snapshots, ignoring earlier ones, if you have any. These application health check queries are extensive and adversely affect the response time for online users. Therefore, by default, these queries are run in a database called the production replica database. The accuracy of the application health check queries depends on the relevance of the application data in the production replica database. Develop a synchronization strategy to keep your production replica database as close to the production database as possible. On the toolbar, click **System health check** to create a scheduled task for the application health check snapshot. Enter the required information in the **Scheduled tasks** window, and then click **Save**. This information is used to provide the application health check measures in the **Analysis** &gt; **Show system health** command.
| **Caution**                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| It is possible for you to configure the application to run the application health check queries against the production database. We recommend that you not run the application health check queries against the production database, because these queries adversely affect the response time of the Microsoft Dynamics AX application. |

## Metadata
This command synchronizes the metadata from the production database with the archive database. The metadata synchronization task copies database objects, but not data, from the production database to the archive database. You must complete this task successfully before running the master data synchronization process. Run the metadata synchronization task during your system maintenance period or at a time when the least amount of activity is occurring on the Microsoft Dynamics AX application. The metadata synchronization task can fail while copying objects such as views, functions, and stored procedures. This failure may be caused by invalid code in these objects that prevents creation, or by cyclic dependencies. A successful task is completed with a **Pass** status. If the task fails to copy database objects such as tables, indexes, and primary keys, the job shows a **Fail** status. Click the **Status** menu, and check the **Subtasks** list in the **Trace** pane to determine the exact step that caused the error. IDMF creates trace files for these subtasks in the installation location. Each trace file maps to a specific subtask, such as **CreateColumn.txt**, **CreateIndex.txt**, and **DropTables.txt**. Review the trace file corresponding to the failed subtask to determine the cause of the error. You must troubleshoot and manually resolve the issues that cause the jobs to fail. You must complete the metadata synchronization task successfully to use the archive feature. Upon successful completion of the first metadata synchronization task, you must maintain the metadata synchronization between the production database and the archive database. After the first metadata synchronization task, if there are changes in the production database schema, you must run the metadata synchronization task to keep both the databases synchronized. On the toolbar, click **Metadata** to create a scheduled task for the metadata synchronization. Enter the required information in the **Scheduled tasks** window, and then click **Save**.

## Master data
This command synchronizes the master data tables from the production database with the archive database. The metadata synchronization task copies all the tables that you configure as master tables on the **Administer** menu. You must successfully complete the metadata synchronization task at least one time before you can run the master data synchronization task. Whenever the metadata changes in the production database, you must successfully complete the metadata synchronization task before you run the master data synchronization task. The master data synchronization task follows these steps to copy master tables:
1.  Delete all the existing records from each target table.
2.  Copy the whole source table from the production database to the target database.

On the toolbar, click **Master data** to create a scheduled task for the master data synchronization. Enter the required information in the **Scheduled tasks** window, and then click **Save**.

## Purge
This command lets you create a new purge task. You must have a Purge Object before you create a purge task. At run time, a purge task uses the rules in the Purge Object to filter records. The scheduled Purge Object task deletes matching records from all the tables in the relationship tree of the Purge Object. On the toolbar, click **Schedule** &gt; **Purge** to open the **Scheduled tasks** window. When you create a purge task, you work with an additional tab in the **Scheduled tasks** window. On the **Configure rules for purge** tab, select the Purge Object, and validate or modify values for the rules, in addition to working with the **General** and **Schedule** tabs.

## Archive
This command lets you create a new archive task. You must have an Archive Object before you create an archive task. At run time, an archive task uses the rules in the Archive Object to filter records. The scheduled Archive Object task archives matching records from all the tables in the relationship tree of the Archive Object. On the toolbar, click **Schedule** &gt; **Archive** to open the **Scheduled tasks** window. When you create an archive task, you work with an additional tab in the **Scheduled tasks** window. On the **Configure rules for archive** tab, select the Archive Object, and validate or modify values for the rules in the Archive Object, in addition to working with the **General** and **Schedule** tabs.
### Restart the failed or canceled archive task

IDMF considers an unexpected error condition a failure and cancels the task if the scheduler service is not available. Both cases are logged in the error log files. An archive task moves selected records from the production database to the archive database. IDMF archives each table as a single transaction. IDMF also tracks the completion of the archive process for each table. For example, you are processing a table called **CustTable**. If an archive task fails while archiving **CustTable**, it rolls back the transaction that was archiving **CustTable**. IDMF marks the tables being processed and is aware that the failure occurred during the processing of CustTable. When you restart the failed archive task, IDMF starts archiving **CustTable** from the beginning and continues with the remaining tables in the Archive Object. If an archive task fails or is canceled in the first phase, before it starts to copy data, you cannot restart the task. In that case, you must create and run a new task to archive data.

### Revert the failed or canceled archive task

You can roll back a failed or canceled archive task. Rolling back the task restores the data that is partially archived. As detailed in the previous section, in case of a failure, IDMF rolls back the current table that is being processed. However, by default, the previously archived tables are not rolled back. For example, an archive task has successfully completed archiving the table **WMSOrder**. The task fails during archiving of the **WMSOrderTans** table and rolls back the archiving of the **WMSOrderTans** table. The database is now in a state where records from **WMSOrder** have been archived, but the corresponding records from **WMSOrderTans** and other related tables in the nested relationship tree have not been archived. In order to maintain the integrity of the database, you must revert or restart the failed archive task. When you revert the failed task, it tries to restore the data it archived from the **WMSOrder** table. A successful revert brings the database to the state it was in before the archive task started. If your archive task failed or was canceled before it started to copy data, there is nothing to revert. If you attempt to revert such failed tasks, IDMF displays a message that there is nothing to revert for such tasks. If a revert task fails or is canceled, you can restart the failed revert task. Monitor the revert task to verify successful completion.

## Restore archive
This command lets you restore archived records from a successful archive task. On the toolbar, click **Restore archive** to create a scheduled task for restoring the archived data. Enter the required information in the **Scheduled tasks** window, and then click **Save**. A successful archive task is completed with the **Pass** status. Click the **Status** menu to work with the **Status** workspace. In the **Job status** pane, select an archive task with the **Pass** status. The **Trace** pane in the **Status** workspace lists the number of records archived in each table of the Archive Object.
### Walkthrough: Create a restore archive task for the Archive Object

This section provides a walkthrough to create a restore archive task. Follow these steps to restore the archived records to the production database:
1.  Click **Schedule** &gt; **Restore archive** to create a restore archive task. For this walkthrough, you work in the **Task details** pane.
2.  On the **General** tab, enter the task name and description.
3.  On the **Configure archive restore** tab, select **Other schedules** from the list to filter the data grid based on your selection. Selecting **Other schedules** filters the data grid to show successfully completed tasks for all other Archive Objects, such as **SalesTable** and **BankDeposit**.
4.  Review the archive tasks shown in the **Schedule** column. You can select multiple tasks. When restoring, you can restore the most recent archive without having to restore an older archive for the same object.
5.  On the **Schedule** tab, enter values for the start date and start time.
6.  Click **Save**.
7.  Carefully read the warning that may appear, indicating that you have performed a valuation model change or a standard cost revaluation. Restoring the Archive Object after a validation model change or standard cost evaluation may lead to data inconsistencies. In the production environment, do not run the restore archive task if you have performed either of these actions. For the purpose of this walkthrough, continue the walkthrough in the test environment. Click **OK** to close the message.
8.  On the **Schedule** tab, click **OK** to continue.
9.  Using the **Status** menu, monitor the progress of the restore task, and verify that it has completed successfully with a **Pass** status. Compare the information in the **Trace** pane from the restore task with the information from the archive task. Verify that the number of records restored matches the number of records archived for all tables in the archive and restore tasks.
10. Test the restored tables in the test environment to verify data and application integrity.

| **Caution**                                                                                                                                                                                                                                                                                                                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Improper use of an Archive Object or a restoration of the archived records can cause unexpected results, database corruption, and application downtime requiring full database and application recovery. You must exercise extreme caution and thoroughly test your archival strategy in a test environment before working in the production environment. |

### Restart the failed or canceled restore archive task

IDMF considers an unexpected error condition a failure and cancels a task when the scheduler service is unavailable. Both cases are logged in the error log files. A restore archive task restores records from the archive database to the production database, as detailed in the previous section. IDMF restores each table as a single transaction. IDMF also tracks the completion of the restore process for each table. For example, you are restoring a table called **CustTable**. If a restore archive task fails while restoring **CustTable**, it rolls back the transaction that was restoring **CustTable**. IDMF marks the tables being processed and is aware that the failure occurred during the restoration of **CustTable**. When you restart the failed restore archive task, IDMF starts restoring **CustTable** from the beginning and continues with the remaining tables in the Archive Object. If a restore archive task fails or is canceled in the first phase, before it starts to restore data, you cannot restart the task. In that case, you must create and run a new task to archive data.

## Export to Excel
This command exports the selected task to Microsoft Excel.



