---
# required metadata

title: View purge or archive jobs (AX 2012)
description: 
author: kfend
manager: AnnBe
ms date: 2017-04-04
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
ms.custom: 18771
ms.assetid: fd4f59b6-280e-4091-b563-44315a1bb893
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# View Intelligent Data Management Framework purge or archive jobs (AX 2012)



You can use the options on the Microsoft Dynamics AX IDMF **Status **menu to refresh the status of all currently running jobs and provide details for all currently running and completed jobs. On the toolbar, click **Status** to open the **Status** workspace.

## Navigation of the Status workspace
The following tables provide descriptions for the controls in the **Status** workspace.

### Panes

| Pane               | Description                                                                                                                                                                                                                                                                                                                                                                                 |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Job status**     | Provides a list of all currently running, canceled, failed, or completed tasks. Each currently running or completed task is referred to as a job. This workspace uses the terms job, task, and schedule interchangeably.Use the **Show status details** **for previous** option in the **Administer** &gt; **Framework options** window to configure the number of jobs shown in this pane. |
| **Status details** | Provides status details of the selected task.                                                                                                                                                                                                                                                                                                                                               |
| **Trace**          | Lists the multiple steps and queries for the selected task, if there are any.                                                                                                                                                                                                                                                                                                               |

### 

### Fields

#### Job status pane

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
<td>The name of the task.</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Type</span></strong></td>
<td>The type of the task.</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">Last run time</span></strong></td>
<td>The date and the time when this task was last run.</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Last run result</span></strong></td>
<td>The result can be <strong><span class="ui">Pass</span></strong>, <strong><span class="ui">Fail</span></strong>, <strong><span class="ui">Running</span></strong>, or <strong><span class="ui">Canceled</span></strong>. The Intelligent Data Management Framework and scheduler service log errors in their respective error log files. Use the following steps to restart a failed or canceled archive, revert, or restore an archive task:
<ol>
<li>Check the task details in the <strong>Status</strong> workspace.</li>
<li>Check the error log files to determine the conditions that caused the error, and fix the error condition.</li>
<li>To restart an archive or restore an archive, in the <strong>Status</strong> <strong>workspace</strong> &gt; <strong><span class="ui">Job status</span></strong> pane, right-click the task, and then select <strong><span class="ui">Restart task</span></strong>. For all other task, create a new task, and run it. <strong>Note:</strong> You can't restart a task that failed or was canceled before it started copying the data. If you can't restart a failed or canceled task, you must create a new task.</li>
<li>Monitor the task you started in the previous step to verify successful completion.</li>
</ol>
Use the following steps to revert a failed or canceled archive task:
<ol>
<li>Check the task details in the <strong>Status</strong> workspace.</li>
<li>Check the error log files to determine the conditions that caused the error, and fix the error condition.</li>
<li>To revert an archive task, in the <strong>Status</strong> <strong>workspace</strong> &gt; <strong><span class="ui">Job status</span></strong> pane, right-click the task, and then select <strong><span class="ui">Revert schedule</span></strong>. For all other tasks, create a new task, and run it. <strong>Note:</strong> If you revert a task that failed or was canceled before it started copying the data, IDMF displays a message indicating that there is nothing to revert.</li>
<li>Monitor the task you started in the previous step to verify successful completion.</li>
</ol></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">Next schedule</span></strong></td>
<td>The date and time for the next run of a recurring task.</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Description</span></strong></td>
<td>The task description. By default, IDMF provides a brief description for the task, such as purge data for the selected Purge Object. The description does not provide any information about the rules in the Archive Object or Purge Object. You can modify IDMF configuration file to provide the rules and their values in the description. Use the following steps to modify the configuration file:
<ol>
<li>Using an editing tool such as Notepad, open <strong>AXDataManagementTool.exe.Config</strong> from the installation folder of the Data Management Framework. The default path of the installation folder is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework.</li>
<li><p>Locate the configuration key <strong>IncludeRulesInDescription</strong>, and change the value to <strong>true</strong> as shown in the following code.</p>
<pre><code>&lt;add key=&quot;IncludeRulesInDescription&quot; value=&quot;true&quot; /&gt;</code></pre></li>
<li>Save the configuration file, and restart IDMF.</li>
</ol>
With the modified configuration file, when you create or update an archive or purge task, the description includes all the rules and their values for the selected Purge Object or Archive Object.</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">SSIS trace</span></strong></td>
<td>This field provides a hyperlink to view the Microsoft SQL Server Integration Services (SSIS) trace output for this task.The hyperlink is only available when you set the trace level to <span class="ui">Verbose</span>. Use the <span class="ui">Framework options</span> menu to set the SSIS trace level.</td>
</tr>
</tbody>
</table>

#### Status details pane

| Field                | Description                                                                                                                                                                                     |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Type**             | The type of task.                                                                                                                                                                               |
| **Status**           | The status can be **Pass**, **Fail**, **Running**, or **Canceled**. You must run a failed or canceled, task again. Determine the effect of the status on any currently running or future tasks. |
| **Start time**       | The start time of the task.                                                                                                                                                                     |
| **End time**         | The end time of the task.                                                                                                                                                                       |
| **Created datetime** | The date and time when the task was created.                                                                                                                                                    |

### 

### Trace pane

All tasks contain the following fields. Archive and restore archive tasks do not include **Start time** and **End time** fields, but provide a **Duration** field instead.

| Field          | Description                                                                                                                                                                                                                                                                                                                         |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Start time** | The start time of the subtask. This field is available for all tasks except for ledger periods, archive, and restore tasks.                                                                                                                                                                                                         |
| **End time**   | The end time of the task. This field is available for all tasks except for the ledger periods, archive, and restore tasks.                                                                                                                                                                                                          |
| **Status**     | The completion status for all tasks is either **Pass** or **Fail**. The archive and purge tasks also show the status as Running when a task is active. For a failed task, check to see which subtask has failed before you run the task again. Determine the effect of the failed task or running the task again on any other task. |

#### 

#### Trace pane for analysis snapshot tasks for production and archive databases

| Field        | Description                                                                                                                                                                  |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Subtasks** | A subtask is a step in a task, such as **Index analysis snapshot** or **Table analysis snapshot**. The **Trace** pane lists all subtasks for a given task, where applicable. |

#### 

#### Trace pane for master data synchronization tasks

| Field             | Description                                                                                               |
|-------------------|-----------------------------------------------------------------------------------------------------------|
| **Table name**    | The table name in the Purge Object.                                                                       |
| **Rows inserted** | The number of rows inserted into this master table, from the production database to the archive database. |
| **Rows updated**  | The number of rows updated in this master table, from the production database to the archive database.    |

#### 

#### Trace pane for metadata synchronization tasks

| Field                   | Description                                                                                                                                                                                                                                                  |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Subtasks**            | The name of the subtask that the metadata synchronization task performs. Each subtask corresponds to a database object, such as a function, index, primary key, stored procedure, table, or view.                                                            |
| **Production DB count** | The number of objects found in the production database.                                                                                                                                                                                                      |
| **Archive DB count**    | The number of database objects copied to the archive database. The values of Production db count and Archive db count must match for Table, Index, and Primary key subtasks. In case of a mismatch in these counts, the metadata synchronization task fails. |

#### 

#### Trace pane for system health check tasks

| Field       | Description                                                       |
|-------------|-------------------------------------------------------------------|
| **Period**  | The period is a four-digit calendar year based on ledger periods. |
| **Measure** | A description of the measure.                                     |

#### 

#### Trace pane for purge tasks

| Field                                     | Description                                                                                                                                                                                                                                           |
|-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Table name**                            | The name of the table in the Purge Object.                                                                                                                                                                                                            |
| **Records recycled**                      | The total number of records recycled from this table by the purge task.                                                                                                                                                                               |
| **Records inserted into the purge table** | The total number of records inserted into the purge table. The purge table contains all records that are recycled from the production database, until you remove them from the purge table. This value is the same as the number of records recycled. |

#### 

#### Trace pane for archive tasks

| Field                                          | Description                                                                                                                                                                                                                                       |
|------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Table name**                                 | The name of the table in the Archive Object or Related Archive Object.                                                                                                                                                                            |
| **Records inserted into the temporary tables** | The total number of records inserted into the temporary table that was used as the source for this archival activity.                                                                                                                             |
| **Records inserted into the archive database** | The total number of records inserted into the tables in the archive database from the corresponding tables in the production database. This number must match the number of records in the source database.                                       |
| **Records offlined**                           | The total number of records archived, or in other words, the total number of records that were copied from the production database to the archive database, and then deleted from the production database.                                        |
| **Summation count**                            | The total number of adjustment records inserted into the production database. You may have to make adjusting entries to balance the affected accounts.                                                                                            |
| **Duration**                                   | The time required to complete this archival step. Various stages of the data archival process run at different times for each table in an Archive Object. As a result, the data grid provides a duration instead of a start time and an end time. |
| **Status**                                     | The status of the subtask, such as **Pass** or **Fail**.                                                                                                                                                                                          |

#### 

#### Trace pane for restore archive tasks

| Field                                     | Description                                                                                                                                                                                                                                   |
|-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Table name**                            | The name of the table in the Archive Object or Related Archive Object that is being restored.                                                                                                                                                 |
| **Archive date**                          | The archive date and time.                                                                                                                                                                                                                    |
| **Records qualified for restoration**     | The total number of records that were selected based on the company and period you selected for a calendar year.                                                                                                                              |
| **Records restored**                      | The total number of records restored from the archival database to the production database for this table.                                                                                                                                    |
| **Summation count**                       | The total number of adjustment records deleted from the production database.                                                                                                                                                                  |
| **Records deleted from archive database** | The total number of records deleted from the archive database for this table.                                                                                                                                                                 |
| **Duration**                              | The time required to complete this archival step. Various stages of data archival process run at different times for each table in an Archive Object. As a result, the data grid provides a duration instead of a start time and an end time. |
| **Status**                                | The status of the subtask, such as **Pass** or **Fail**.                                                                                                                                                                                      |

## Refresh
To update the **Status** workspace, click **Refresh** on the toolbar.

## Export to Excel
This command lets you export selected rows from the data grid, from all workplaces where this command is available.

