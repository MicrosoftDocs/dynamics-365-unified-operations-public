---
# required metadata

title: Maintainance in the Intelligent Data Management Framework (AX 2012)
description: 
author: kfend
manager: AnnBe
ms.date: 04/04/2017
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
ms.custom: 18471
ms.assetid: a8cab868-0e2f-406e-b486-4883876f1f09
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Maintainance in the Intelligent Data Management Framework (AX 2012)



Database
--------

This command lets you configure connection strings for the production replica, archive, and production databases. The production database is the Microsoft Dynamics AX database in the production environment. The production replica database is used to run the queries for the health check snapshot. Although it is technically possible to run the health check queries against the production database, doing so causes performance degradation. The archive database is used by the archive task to archive records based on the Archive Object used in the task. On the toolbar, click **Database** to work with the **Database connection settings** window. **Caution:** Although it is technically possible to configure the application health check queries to run in the production database, doing so causes performance downgrade and slower response time. We recommend that you run the health check queries in the production replica database and not select the **Same as production** field.

### Navigation of the Database connection settings window

The following tables provide descriptions for the controls in the **Database connection settings** window.

#### Tabs

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tab</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong><span class="ui">Production</span></strong></td>
<td>Configure the connection string for the production database.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The production database you select here must match the database in the Microsoft Dynamics AX server configuration.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
<tr class="even">
<td><strong><span class="ui">Production replica</span></strong></td>
<td>Configure the connection string for the production replica database.</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">Archive</span></strong></td>
<td>Configure the connection string for the archive database.</td>
</tr>
</tbody>
</table>

#### 

#### Buttons

| Button              | Description                                                               |
|---------------------|---------------------------------------------------------------------------|
| **Test connection** | Test the database connection using the connection strings you configured. |
| **Save**            | Save the database configuration.                                          |
| **Clear**           | Clear all the input fields.                                               |

#### 

#### Fields (across all tabs)

| Field                                               | Description                                                                                                                                                                                                                                      |
|-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SQL Server name**                                 | Select the name of the database server from the list.                                                                                                                                                                                            |
| **Use Windows integrated security**                 | The scheduler service connects to the database using Windows integrated security.                                                                                                                                                                |
| **Use specific username and password**              | The scheduler service connects to the database using the user name and password values that you enter in this window.                                                                                                                            |
| **Username**                                        | The user name that the scheduler service uses to connect to the database.                                                                                                                                                                        |
| **Password**                                        | The password that the scheduler service uses to connect to the database.                                                                                                                                                                         |
| **Name of the database on the server**              | The database that you are connecting to.                                                                                                                                                                                                         |
| **Connection timeout (seconds)**                    | The value of the connection time-out, in seconds.                                                                                                                                                                                                |
| **Maximum pool size**                               | The maximum value of the connection pool.                                                                                                                                                                                                        |
| **Minimum pool size**                               | The minimum value of the connection pool.                                                                                                                                                                                                        |
| **Same as production** (**Production replica** tab) | When you select this field, the connection string from the production database is copied to the production replica database. Therefore, the health check queries run against the production database instead of the production replica database. |

 

## Email
IDMF can send email alerts to configured recipients. This command is used to configure the email functionality. On the toolbar, click **Email** to work with the **Email parameters** window.

### Navigation of the Email parameters window

The following tables provide descriptions for the controls in the **Email parameters** window.

#### Buttons

| Button     | Description                                   |
|------------|-----------------------------------------------|
| **Save**   | Save changes made to the email configuration. |
| **Cancel** | Clear all the input fields.                   |

#### 

#### Fields

| Field                    | Description                                                                                                                                      |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| **Outbound SMTP server** | The IP address of a valid SMTP server.                                                                                                           |
| **SMTP port number**     | The port number that IDMF uses to send email.                                                                                                    |
| **From address**         | The email address that appears as the sender of email.                                                                                           |
| **Recipient list**       | The email address for the recipient. You can enter multiple email addresses separated by a semicolon.                                            |
| **Username**             | The user name that is used to access the SMTP server. This is an optional field. Enter this value if you want to receive email alerts from IDMF. |
| **Password**             | The password that is used to access the SMTP server. This is an optional field. Enter this value if you want to receive email alerts from IDMF.  |

 

## Thresholds
This command lets you determine the threshold values for index fragmentation growth, index-to-data growth ratio, and snapshot-to-snapshot growth ratio. When a table or a measure reaches the threshold value, an alert is generated. By default, the threshold parameter values are 0. Only a threshold parameter containing a non-zero value generates an alert. You can see the alerts in the **Analysis details** workspace. Click **Analysis menu** &gt; **Analysis details command**. You also receive an email message, together with an alert, if you have configured the email functionality. On the toolbar, click **Threshold** to work with the **Configure threshold parameters** window.

### Navigation of the Configure threshold parameters window

The following tables provide descriptions for the controls in the **Configure threshold parameters** window.

#### Tabs

| Tab                       | Description                                                 |
|---------------------------|-------------------------------------------------------------|
| **Tables**                | A list of tables and their threshold values.                |
| **Health check measures** | A list of health check measures and their threshold values. |
| **Purge**                 | A list of tables and their threshold values.                |

#### 

#### Buttons

| Button        | Description                                               |
|---------------|-----------------------------------------------------------|
| **Configure** | Add the entered or modified threshold values to the list. |
| **Save**      | Save the changes to the database.                         |

#### 

#### Fields (across all tabs)

| Field                               | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Filter criteria**                 | This list consists of types and categories of tables.You can select a value based on types of tables, such as top 50 tables, top 100 tables, or all tables. You can also select a value based on the category of the table, such as log tables or parameters tables.The data grid is filtered based on the value you select in this list.By default, the **Filter criteria** field is set to **Top 10 tables**. |
| **Table name**                      | The name of the table.                                                                                                                                                                                                                                                                                                                                                                                          |
| **Index fragmentation growth (%)**  | A threshold value for the index fragmentation growth percentage between snapshots for the selected table. For example, a threshold value of 10 generates an alert if the index fragmentation percentages grow by 10 between now and the next snapshot.This value is only available for tables.                                                                                                                  |
| **Index to data ratio growth (%)**  | A threshold value for the index-to-data ratio growth percentage between two snapshots for the selected table.This value is only available for tables.                                                                                                                                                                                                                                                           |
| **Snapshot-to-snapshot growth (%)** | A threshold value for the snapshot-to-snapshot growth ratio as a percentage for the selected table.You can enter this value for tables or measures.                                                                                                                                                                                                                                                             |
| **Measure name**                    | The name of the measure.                                                                                                                                                                                                                                                                                                                                                                                        |
| **Data size (MB)**                  | A threshold value for the purge tables. When a purge table reaches the specified size, an alert is generated.                                                                                                                                                                                                                                                                                                   |

 

## Alerts
This command is used to configure the alerts functionality in IDMF. To receive an email alert, you must configure email parameters from the **Administer** &gt; **Email command**. On the toolbar, click **Alerts** to open the **Configure alerts** window. Select an alert event to generate an alert. The following table describes the alert events you can select.

| Alert event    | Description                                                                                                                                                                                             |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Job start**  | Send an alert when a task starts. This option is selected by default.                                                                                                                                   |
| **Job end**    | Send an alert when a task ends. The alert is sent, regardless of the completion status of the task. The completion status can be **Pass**, **Fail**, or **Cancel**. This option is selected by default. |
| **Thresholds** | Send an alert when a specific threshold value is reached.                                                                                                                                               |

To view generated alerts, click **Analysis** &gt; **Analysis details**, and then click **Alerts** in the **Related information** pane. If you have configured email functionality, the generated alerts are sent via email to the configured recipients.

## Related information
This command lets you work with related information. Related information provides a contextual description for various application entities, such as tables, measures, and tasks, in the **Related information** pane throughout the application. These application entities are called related information parameters. These parameters are categorized in a grouping called the related information type, as described in the following table.

| Related information type | Description                                                                                                                                                                                                    |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Analysis**             | Provides a contextual description for a table in the **Detailed analysis** view.                                                                                                                               |
| **Measure**              | Provides information for a measure, such as the measure description, the archival relevance, and the formula used to calculate the measure. This information is used in the application health check analysis. |
| **OfflineObject**        | Provides a contextual description for a table in an Archive Object.                                                                                                                                            |
| **RecyleObject**         | Provides a contextual description for a table in a Purge Object.                                                                                                                                               |
| **UnusedIndex**          | Evaluate this unused index to determine whether the index is required or can be deleted.                                                                                                                       |
| **FragmentedIndex**      | Provides instructions to create a task to defragment fragmented indexes.                                                                                                                                       |

| **Note**                                                                                                                                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IDMF provides related information for a limited set of related information parameters. You can add your own related information parameters or modify existing related information parameters to suit your requirements. |

On the toolbar, click **Related information** to open the **Related information** window.
### Navigation of the Related information window

The following tables provide descriptions for the controls in the **Related information** window.
#### Panes

| Pane                            | Description                                                        |
|---------------------------------|--------------------------------------------------------------------|
| **Related information list**    | A list of related information parameters.                          |
| **Related information details** | Fields that let you add or modify a related information parameter. |

#### 

#### Buttons

| Button          | Description                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **New**         | Add a new related information parameter.                                                                                                |
| **Update/Save** | The label changes, depending on your selection. The label is **Update for an existing description** and **Save for a new description**. |

#### 

#### Fields

| Field                        | Description                                                                                                                                                                                                                                                       |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Related information type** | The related information type.                                                                                                                                                                                                                                     |
| **Language ID**              | The language ID of the related information parameter. By default, the language ID is **en-US** (English, United States) for the default related information parameters. You can select a language from the list when you add a new related information parameter. |
| **Parameter**                | The name of the related information parameter. This is the name of the application entity, such as a table name, a measure name, or a task type.                                                                                                                  |
| **Description**              | A contextual description for the related information parameter. For example, the description provides the measure description, the archive relevance, and the formula for a measure.                                                                              |

## Discovery
This command lets you work with the exception list. The exception list consists of exception parameters. The exception list restricts you from adding tables, relations, or rules to a Purge Object or an Archive Object. The type of restriction depends on the type of exception you apply to an exception parameter. The following table describes the exception parameters. For a detailed explanation of configuration keys and table groups, see the Microsoft Dynamics AX documentation.

| Exception parameter type | Description                                                                                                                                                                                                                                                               |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Table name**           | Tables that are added explicitly by table name to the exception list. For example, the **BOMCalcTrans** table is configured to be an exception for the driver table. Therefore, you cannot use **BOMCalcTrans** as a driver table in a Purge Object or an Archive Object. |
| **Configuration key**    | A list of configuration keys in the exception list. All the tables that use these configuration keys are implicitly included in the exception list, based on their relationships with the configuration keys.                                                             |
| **Table group**          | A list of table groups in the exception list. All the tables that are part of the table groups in the exception list are implicitly included in the exception list, based on their relationship with the table group.                                                     |

| **Caution**                                                                                                                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Be careful when including or excluding tables from the exception list, because this can lead to incorrect discovery and, therefore, an incorrect Purge Object or Archive Object. |

| **Note**                                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------|
| Use the **Properties** pane in the Purge Object to see the table group and the configuration key for the selected table. |

Click **Administer** &gt; **Discovery** to work with the **Exception parameters** window.
### Navigation of the Exception parameters window

The following tables provide descriptions for the controls in the **Exception parameters** window for discovery.
#### Panes

| Pane                                    | Description                                                                                                                                                                                                    |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Exception parameters**                | Select the exception parameter type to filter the data grid based on your selection.You cannot delete or modify the default exceptions in IDMF. You can add, modify, and delete your own exception parameters. |
| **Save or update exception parameters** | Create or modify your custom exception parameters.                                                                                                                                                             |
| **Search**                              | Search for a specific exception parameter.                                                                                                                                                                     |

#### 

#### Buttons

| Button                | Description                                                                                                                             |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **Add new parameter** | Add a new exception parameter.                                                                                                          |
| **Add**               | Add the new parameter to the **Exception parameters** list.                                                                             |
| **Save/Update**       | Modify the data grid to reflect additions, deletions, and changes to the exception parameter, and save the information to the database. |
| **Search**            | Use the search value to filter the **Exception parameters** list.                                                                       |
| **Clear**             | Clear the search text in the **Parameter name** field.                                                                                  |
| **Delete**            | Delete selected exception parameters.                                                                                                   |

#### 

#### Fields (Exception parameters pane)

| Field                 | Description                                                                                                                                                                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Parameter name**    | The name of the exception parameter, which can be a table name, a configuration key name, or a table group name.                                                                                                                                                                                                                                                           |
| **Parameter type**    | The exception parameter type: **Table name**, **Configuration key**, or **Table group**.                                                                                                                                                                                                                                                                                   |
| **Rules**             | When this field is selected, you cannot use this parameter to create a rule in a Purge Object or an Archive Object.                                                                                                                                                                                                                                                        |
| **Relations**         | When this field is selected, you cannot use this parameter to create a relation in a Purge Object or an Archive Object.                                                                                                                                                                                                                                                    |
| **Purge discovery**   | When this field is selected, you cannot include any table from this parameter as a related, or child, table in a new Purge Object. The discovery process ignores all tables that are part of the exception parameter when generating the hierarchical relationship tree.Existing Purge Objects that use this parameter as a child table continue to function normally.     |
| **Driver table**      | When this field is selected, you cannot use any tables from this parameter as a driver table in a Purge Object or Archive Object.                                                                                                                                                                                                                                          |
| **Archive discovery** | When this field is selected, you cannot include any table from this parameter as a related, or child, table in a new Archive Object. The discovery process ignores all tables that are part of the exception parameter when generating the hierarchical relationship tree.Existing Archive Objects that use this parameter as a child table continue to function normally. |

#### 

#### Fields (Search pane)

| Field              | Description                                                                                                                                  |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| **Parameter type** | This field is used to filter the data grid. The data grid is automatically filtered based on the value you select. The default value is All. |
| **Parameter name** | Enter the search value.                                                                                                                      |

#### 

#### Fields (Save or update exception parameters pane)

| Field                 | Description                                                                                                                                                                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Parameter type**    | When adding a new parameter, select the parameter type from this list.                                                                                                                                                              |
| **Parameter name**    | When adding a new parameter, select the parameter name from this list.                                                                                                                                                              |
| **Rules**             | You cannot use tables that belong to this parameter to create rules in an Archive Object or a Purge Object. For more information, see the field description for the **Exception parameters** pane in the previous section.          |
| **Relations**         | You cannot use tables that belong to this parameter to create relations in an Archive Object or a Purge Object. For more information, see the field description for the **Exception parameters** pane in the previous section.      |
| **Purge discovery**   | You cannot use tables that belong to this parameter in the discovery process of a Purge Object. For more information, see the field description for the **Exception parameters** pane in the previous section.                      |
| **Driver table**      | You cannot use tables that belong to this parameter as a driver table to create an Archive Object or a Purge Object. For more information, see the field description for the **Exception parameters** pane in the previous section. |
| **Archive discovery** | You cannot use tables that belong to this parameter in the discovery process of an Archive Object. For more information, see the field description for the **Exception parameters** pane in the previous section.                   |

## Framework options
This command lets you configure options for IDMF, such as the minimum and maximum database analysis snapshots used in the trend analysis. On the toolbar, click **Administer** &gt; **Framework options** to work with the configuration options for IDMF.
### Navigation of the Framework options workspace

The following tables provide descriptions for the controls in the **Framework options** workspace.
#### Panes

| Pane                    | Description                                                            |
|-------------------------|------------------------------------------------------------------------|
| **Framework options**   | Provides configuration options for IDMF.                               |
| **Related information** | Provides additional information for the selected configuration option. |

#### 

#### Fields (Framework options pane, Database analysis options group)

| Field                                                     | Description                                                                                                                                                                      |
|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Number of snapshots required for index analysis**       | The minimum number of snapshots required for meaningful analysis of index statistics. The default value is 5.                                                                    |
| **Minimum number of snapshots required for trend charts** | The minimum number of snapshots required for trend analysis. The default is 2, and you cannot decrease this value.                                                               |
| **Maximum number of snapshots allowed for trend charts**  | The maximum number of snapshots required for trend analysis. The default is 10. Enter a number between 2 and 10 to configure the maximum number of snapshots for trend analysis. |

#### 

#### Fields (Framework options pane, Other configuration options group)

| Field                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Number of Related Archive Objects per row** | The number of Related Archive Objects that are displayed per row in the **Configure** workspace. The default value is 6.                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **Table row count**                           | The threshold value for the row count. The default value is 500,000. An Archive Object highlights each table with a row count that is less than the configured threshold value with an "x" in the upper-right corner. You can configure the highlighted table to be a master data table, and then remove it from the relationship tree. A master data table is copied and not archived.                                                                                                                                                                                                    |
| **Table size**                                | The threshold value for the table size. The default value is 512,000 (MB). An Archive Object highlights each table with a size that is less than the threshold value with an "x" in the upper-right corner. You can configure the highlighted table to be a master data table, and then remove it from the relationship tree. A master data table is copied and not archived. Enter the size, a non-zero value, in this field, and then select a value from the adjoining list to specify the size in megabytes, kilobytes, or gigabytes. The default value in the list is megabytes (MB). |

#### 

#### Fields (Framework options pane, Status display)

| Field                                | Description                                                                                                                                                                                                                                                             |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Show status details for previous** | This field lets you select the period for which the status details are displayed in the **Status** workspace. The default value is 1 week. To change this value, enter a non-zero number in this field, and then select days, weeks, or months from the adjoining list. |

#### 

#### Fields (Framework options pane, Logging group)

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
<td><strong><span class="ui">Trace level</span></strong></td>
<td>Select a trace level from the list. Select <strong><span class="ui">Minimal</span></strong> to log only critical errors. Select <strong><span class="ui">Verbose</span></strong> to log all events, including informational events. Select <strong><span class="ui">None</span></strong> to stop logging of events.If you select <strong><span class="ui">Verbose</span></strong>, the master data synchronization and analysis snapshot tasks provide a hyperlink in the <span class="ui">SSIS trace</span> field in the <strong><span class="ui">Job status</span></strong> pane. Use the <strong><span class="ui">Status</span></strong> menu, and locate the task in the <strong><span class="ui">Job status</span></strong> pane. Click the hyperlink in the <strong><span class="ui">SSIS trace</span></strong> field to view the trace output.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The <strong><span class="ui">SSIS trace</span></strong> field becomes available in the <strong>Status</strong> workspace only when you select a trace level of <strong><span class="ui">Verbose</span></strong>.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
<tr class="even">
<td><strong><span class="ui">SQL Server Integration Services (SSIS) trace log refresh frequency</span></strong></td>
<td>The frequency, in milliseconds, at which the Microsoft SQL Server Integration Services (SSIS) trace output is refreshed. The default value is <span class="ui">1000</span>.</td>
</tr>
</tbody>
</table>

#### 

#### Fields (Framework options pane, Threading options group)

| Field                                    | Description                                                                                                                                                                                                                                                                  |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Enable threading for scheduled tasks** | Select **Yes** to enable the use of multiple threads when processing tasks.Threading in IDMF is not fully parallel because of dependencies. For example, if a table is listed twice in a level, each instance is processed in serial to avoid conflicts and race conditions. |
| **Maximum number of threads**            | Set a maximum number of threads no greater than the number of processors on the computer running IDMF.                                                                                                                                                                       |
| **Disable lock escalation**              | To speed processing, if you are running during a maintenance window, we recommend that you disable lock escalation when you are archiving in production environments, and set a small number for the archive batch size (4000 or less).                                      |
| **Batch size for purge**                 | Number of rows to include in a batch.                                                                                                                                                                                                                                        |
| **Batch size for archive**               | Number of rows to include in a batch.                                                                                                                                                                                                                                        |

#### 

#### Fields (Related information pane)

| Field          | Description                                                                      |
|----------------|----------------------------------------------------------------------------------|
| **(Untitled)** | This pane displays related information for the selected field in this workspace. |

## Application health check
This command lets you work with the queries that are used to capture the application health information from selected modules. You can view and modify existing queries or create new queries. On the toolbar, click **Administer** &gt; **Application health check** to work with the **Application health check queries** workspace.
### Navigation of the Application health check queries workspace

The following tables provide descriptions for the controls in the **Application health check queries** workspace.
#### Panes

| Pane                                    | Description                                                                                                                                                     |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Application health check queries**    | Lists all the health check queries and their data sources in a tree view.                                                                                       |
| **Additional health check information** | Provides additional information for the selected query. For example, this pane lists the SQL statement when you generate a query.                               |
| **Message**                             | Provides an error message, such as the error message from the Generate SQL query or Save query command.                                                         |
| **Table dictionary**                    | Provides a tree view listing tables and their fields from the Microsoft Dynamics AX production database.                                                        |
| **Properties**                          | View or change the properties of the query. You can change some properties, such as the query name. You can only view other properties, such as the field name. |

#### 

#### Buttons (Application health check queries pane)

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Button</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong><span class="ui">Validate queries</span></strong></td>
<td>The <strong><span class="ui">Validate queries</span></strong> button is available only when you start the application for the first time. An invalid query is caused either by a metadata mismatch or by incorrect security keys. When you expand the <strong><span class="ui">Queries</span></strong> node, queries that are not valid appear in red. You must validate the queries before you create an application health check task, because all queries that are not valid are ignored by the task. To validate queries, click <strong><span class="ui">Validate queries</span></strong>, and wait for the validation to be completed. Scroll through the <strong><span class="ui">Queries</span></strong> node, and verify that all the queries are displayed in black.</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Search</span></strong></td>
<td>Open the <strong>Health check query search</strong> window.In the <strong>Health check query search</strong> window, follow these steps:
<ol>
<li>From the <strong><span class="ui">Search</span></strong> list, select <strong><span class="ui">Query name</span></strong> or <strong><span class="ui">Table name</span></strong>.</li>
<li>In the <strong><span class="ui">Containing</span></strong> text box, enter the search text. You can use an asterisk (*) as a wildcard character before and after the text. For example, you can search for <span class="ui">*sales</span>, <span class="ui">sales*</span>, or <span class="ui">*sales*</span>.</li>
<li>Click <strong><span class="ui">Find now</span></strong> to begin the search. Depending on your selection in step 1, IDMF searches for matching values in table names or query names. The <strong><span class="ui">Query name</span> data grid</strong> displays matching results.</li>
<li>Double-click the query of interest from the result set. The <strong>Health check query search</strong> window closes and takes you to the query node that matches your selection.</li>
</ol></td>
</tr>
</tbody>
</table>

#### 

#### Fields

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
<td><strong><span class="ui">Queries</span></strong></td>
<td>Expand the <strong><span class="ui">Queries</span></strong> node to work with the data source of the query. Right-click the query to work with the following commands:
<ul>
<li><strong><span class="ui">Generate SQL query</span></strong> – Generates the query and shows it in the <span class="ui"><strong>Additional health check</strong> information</span> pane. You must generate a query before you can save it.</li>
<li><strong><span class="ui">Save query</span></strong> – Saves the query to the database. The status of the save operation and errors are displayed in the <strong><span class="ui">Message</span></strong> pane.</li>
<li><strong><span class="ui">Disable query</span></strong> – This command is available when you select an already-saved query that is enabled. It disables the selected query and shows it in red. A disabled query is ignored by the application health check task and does not appear in the application health check analysis.</li>
<li><strong><span class="ui">Delete query</span></strong> – This command is available for a new query that is not yet saved. Right-click the newly created query, and then select <strong><span class="ui">Delete query</span></strong> to delete the query.</li>
<li><strong><span class="ui">Enable query</span></strong> – This command is available when you select a disabled query. It enables the query and shows it in black. Enabled queries are run by the health check task and appear in the health check analysis.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong><span class="ui">Table dictionary</span></strong></td>
<td>Expand the <span class="ui">T<strong>able dictionary</strong></span> node to see tables in the production database.</td>
</tr>
<tr class="odd">
<td><strong>Fields in the properties pane</strong></td>
<td>The fields in the <strong><span class="ui">Properties</span></strong> pane change, depending on your selection in the <strong><span class="ui">Queries</span></strong> node.</td>
</tr>
</tbody>
</table>

### 

### Walkthrough: Create a new query

Follow these steps to create a new query:
1.  Click **Administer** &gt; **Application health check** to open the **Application health check queries** workspace.
2.  In the **Application health check queries** pane, right-click the **Queries** node, and then click **New query**.
3.  The query name is **Query\_nnn**, where nnn is a number. For example, the query name may be Query\_70.
4.  Click the newly created query. In the **Properties** pane, click the **Name** field, and enter an appropriate name for the query. For the purpose of this walkthrough, type **SalesTable query** in the **Name** field. After you type the name, click outside the **Name** field, and verify that the name has changed to **SalesTable query** in the **Queries** node.
5.  Expand **SalesTable query**, right-click **Data sources**, and then click **New data source**.
6.  By default, the new data source is the first table in the **Table dictionary** pane. The data source name is **Address(Address)**, where **Address** is the name of the data source, and **(Address)** is the name of the database table that is being used as the data source.
7.  In the **Queries** &gt; **SalesTable query** &gt; **Data sources** node, click the data source **Address(Address)**.
8.  In the **Properties** pane, click the **Name** field, and enter an appropriate name for the data source. For this walkthrough, type **SalesTable DS** in the **Name** field.
9.  Click the **Tables** list. Enter **SalesTable**, or navigate to and select **SalesTable** from the list.
10. In the **Application health check queries** pane, click **Queries** &gt; **SalesTable query** &gt; **Data sources**, and verify that the data source is now **SalesTable DS(SalesTable)**.
11. Right-click **SalesTable query**, and then click **Generate SQL query**. Review the SQL statement in the **Additional health check** information pane.
12. Right-click **SalesTable query**, and then click **Save query**.
13. In the **Select modul**e dialog box, select **AR** from the list, and then click **OK**.
14. Click **OK** to continue.

## Export to Excel
This command lets you export selected information, such as master data tables, to Microsoft Excel. To export, select information in an active window that allows the export functionality, and then click **Export to Excel** on the toolbar.

## Master data tables
This command lets you classify selected tables as the master data tables. The master data synchronization task copies the master data tables from the production database to the archive database.

| **Caution**                                                                                                                                     |
|-------------------------------------------------------------------------------------------------------------------------------------------------|
| When a master data table becomes part of an Archive Object, IDMF disables the master data table and does not replicate it, but does archive it. |

On the toolbar, click **Administer** &gt; **Master data tables** to work with the **Master data tables** workspace.
### Navigation of the Master Data tables workspace

The following tables provide descriptions for the controls in the **Master data tables** workspace.
#### Tabs

| Tab                               | Description                                                                                                                                                                                                                                                                                                         |
|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Master tables**                 | A list of tables with a **TableGroup** value of **Group**, **Main**, **Reference**, or **Parameter**.                                                                                                                                                                                                               |
| **Recommended tables**            | A list of tables with a **TableGroup** value of **Miscellaneous**, **Transaction**, **TransactionLine**, **TransactionHeader**, **Worksheet**, **WorksheetHeader**, or **WorksheetLine**. Top 100 tables, based on data size or row count, are not included in this list, regardless of their **TableGroup** value. |
| **System and custom user tables** | A list of tables that are not visible in the Application Object Tree (AOT).                                                                                                                                                                                                                                         |

#### 

#### Buttons

| Button     | Description                                       |
|------------|---------------------------------------------------|
| **Save**   | Save the changes in the list and in the database. |
| **Clear**  | Clear the search criteria.                        |
| **Search** | Perform the search in the data grid.              |

#### 

#### Fields

| Field                                | Description                                                                                                                                                     |
|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Table name**                       | The name of the table.                                                                                                                                          |
| **Index name**                       | The name of the index.                                                                                                                                          |
| **Index fields**                     | The fields that are used to create the index.                                                                                                                   |
| **Table group**                      | The **TableGroup** property of the table.                                                                                                                       |
| **Rows**                             | The number of rows in the table.                                                                                                                                |
| **Modified by**                      | The last user to select or deselect this table.                                                                                                                 |
| **Search list (untitled)**           | Select a field from the list that you want to use to search the data grid. The default value is **All**.                                                        |
| **Search condition list (untitled)** | Select a search condition from the list. The default value is **=**. The values you can select depend on the field you selected from the search list.           |
| **Search value (untitled)**          | Enter the value that you are searching for in this box. You can use the wildcard character, \*. For example, you can search for \*sales, sales\*, or \*sales\*. |

### 

### Working with master tables

The **Master tables** tab lists all the tables with a **TableGroup** value of **Group**, **Main**, **Reference**, or **Parameter**. By default, all tables in the master data tables list are selected. At run time, the master data synchronization task synchronizes all selected tables in this list, using the production database as the source database and the archive database as the target database. Clear the check box for a table to deselect the table. A deselected table is not considered a master data table and is not synchronized when the master data table synchronization task runs. Tables that have indexes defined on the **RecId** column are shown in red. Evaluate these tables to determine whether selecting another index may improve synchronization performance. To select a different index:
1.  Double-click the **Index name** column for the table in the grid.
2.  Select another index from the list, if there are other indexes.
3.  Click **Save**.

To search for a particular table, use the search utility at the top of the window. Select the field, select the search criteria, provide the search value, and then click **Search**. The search utility filters the data grid to display matching records. You can use the wildcard character, \*, in your search value. Click **Clear** to clear the search criteria. Select **All** from the **Search** list, and then click **Search** to display all tables.

### Working with the recommended tables

Recommended tables typically belong to the **TableGroup** types **Miscellaneous**, **Transaction**, **TransactionLine**, **TransactionHeader**, **Worksheet**, **WorkSheetHeader**, and **WorksheetLine**. The recommended tables list excludes top 100 tables in the database, based on size or row count. By default, no tables in the recommended tables list are selected. Review the recommended tables list, and select the tables that have to be treated as master data tables. To select a table, select the check box next to the table. The synchronization task treats all selected tables from the **Recommended tables** tab the same as the master tables, and copies data from the production database to the archive database. The data grid shows tables with an index based on the **RECID** field in red. If the table has multiple indexes, you can select another index, one with a unique key based on a field other than **RECID**. To change the index, double-click the Index name column, and select another index from the list, if there is one. The search and filter functionality works the same as on the **Master tables** tab. For more information, see the previous section.

### Working with system tables and custom user tables

The Microsoft Dynamics AX application uses certain tables for initialization of Application Object Server (AOS) and to maintain metadata. These tables are part of the Microsoft Dynamics AX database but do not appear in the Application Object Tree (AOT). IDMF considers these tables system tables. However, you may have created some custom tables in the Microsoft Dynamics AX database for integration purposes. These tables may not appear in the AOT. IDMF does not differentiate between the system tables and custom user tables. IDMF lists all system tables and custom user tables on the **System and custom user tables** tab. Review the tables, and make sure that all system tables are selected for data synchronization. You can deselect any custom user tables that are not required in the archive database. This list also includes top 100 tables, based on number of rows, with a **TableGroup** property of **Worksheet**, **WorkSheetHeader**, **WorkSheetLine**, **Transaction**, **TransactionLine**, **TransactionHeader**, or **Miscellaneous**. However, these tables are not selected by default. Determine whether you have to synchronize these tables with the archive database.

| **Caution**                                                                                                                                                                                                                                                                                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| You must configure Application Object Server (AOS) to connect with the archive database to view archived transactions. If the system tables are not replicated properly, AOS cannot connect with the archive database. Be sure that users have only read access to the archive database. Modifying archived transactions causes data inconsistency. |

## Database maintenance
You must maintain the management, archive, production, and production replica databases in accordance with your database maintenance, backup, and restore practices. Consider the following points for the configuration of the databases that are used by IDMF or when you schedule jobs:
-   Determine the location and initial size of data files and log files for each database. Be sure that the initial size of the database and log files is sufficient for optimal performance and future growth. For more information about database configuration, see [Planning database configuration for Microsoft Dynamics AX](http://www.microsoft.com/downloads/details.aspx?FamilyID=ab4cd401-b366-4c1c-9a73-88c945ae8191) and the Microsoft Dynamics AX Performance team's [blog](http://blogs.msdn.com/axperf/).
-   Schedule the set-based archive and purge operations during the regular maintenance window to maintain an optimal user experience. You can schedule row-by-row operations during regular user activities, but know that these operations can cause a slower response time for users.
-   Run only a single archive task at any time. Be sure to delay the start time of any future tasks if the current task seems to be taking longer than expected. Use the **Schedule** menu to work with your archive tasks.
-   The purge and archive tasks generate disk, processor, and memory intensive operations.

### Restore recycled records

This section describes how to restore recycled records after a successful purge task. A successful purge task is completed with the **Pass** status. The **Trace** pane in the **Status** workspace lists the number of records recycled in each table of the Purge Object. To restore the recycled records to the production database, follow these steps:
1.  Back up the product and management databases.
2.  The stored procedure in step 4 runs a distributed query in the production database. You must create a linked server from the production database to the management database. For instructions, see [SQL Server 2008 Books Online](http://msdn.microsoft.com/en-us/library/ms190479.aspx).
3.  In SQL Server Management Studio, click **New Query**. Connect to the production database by selecting the production database from the SQL Editor toolbar. Open and run the query **Cleanup\_restore\_purge.sql** from the installation path. The default installation path is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework. This query creates the two stored procedures that are required for restoring and deleting the recycled records.
4.  In SQL Server Management Studio, click **New Query**. Connect to the management database by selecting the management database from the SQL Editor toolbar. Run the following query to find the traceid from the **AXScheduleTrace** table. Replace 'Purge\_task\_name' in the query with the name of your purge task from the **Status** window. Copy the traceid from the **Results** pane to the clipboard or Notepad.

        SELECT B.TRACEID AS JOBIDENTIFIER , B.CREATEDDATETIME AS RUNTIME
        FROM AXSCHEDULES A, AXSCHEDULETRACE B 
        WHERE A.SCHID=B.SCHID AND A.SCHEDULENAME = 'Purge_task_name' ORDER BY B.CREATEDDATETIME

5.  In SQL Server Management Studio, click **New Query**. Connect to the production database. Replace the parameter values in the query with appropriate values from your environment and the traceid from the previous step. Run the stored procedure.

        EXEC IMPORT_PURGERECORDS @PRODDB = ‘Production database name’,
        @MANAGEMENTSERVER = ‘Management db Server Name’,@MANAGEMENTDB = ‘Management database name’,@JOBIDENTIFIER = ‘Selected TRACEID from Step 3’,
        @AXVERSION = ‘Version‘

6.  In the query, replace 'Version' with 5.0 for version 2009, and 6.0 for version 2012 of Microsoft Dynamics AX.
7.  Test the tables in the Purge Object to verify that the restoration is successful.

**Caution:** Improper use of a Purge Object or the restoration of purged records can cause unexpected results, database corruption, and application downtime requiring full database and application recovery. You must exercise extreme caution and thoroughly test your recycling strategy in a test environment before working in the production environment.
Delete recycled records

This section describes how to permanently delete recycled records after a successful purge task. A successful purge task is completed with the **Pass** status. The **Trace** pane in the **Status** workspace lists the number of records recycled in each table of the Purge Object. To permanently delete records from the recycled tables on the production database, follow these steps:
1.  Back up the production and management databases.
2.  Run steps 2 and 3 from the previous section to create the stored procedures and obtain the traceid.
3.  In SQL Server Management Studio, click **New Query**. Connect to the production database by selecting the production database from the SQL Editor toolbar. Replace the parameter values in the query with appropriate values from your environment and the traceid from the previous step. Run the stored procedure.

        EXEC  DELETE_PURGERECORDS 
        @MANAGEMENTSERVER = `Server Name’,
        @MANAGEMENTDB= `Management DB’,
        @JOBIDENTIFIER = ‘Selected TRACEID from Step 1’

4.  A purge task deletes records from the tables in the relationship tree of the Purge Object, and inserts them into purge tables in the production database. The naming convention of purge tables is purge\_nnnn, where nnnn is the ID of the table in the production database. For example, **table purge\_343** contains records that are deleted from the **PurchParm** table. Look at the **Properties** pane in the **Configure** &gt; **Purge templates/Purge Object** workspace to get the table ID for a table in the Purge Object. Start SQL Server Management Studio, and navigate to the **Tables** node for the production database in the left pane. Verify that records for the traceid you used in step 1 do not exist in the purge tables that correspond to the tables in the **Trace** pane of the **Status** workspace.

Perform this activity during a scheduled maintenance window. **Caution:** These records are permanently deleted from the database. You must exercise extreme caution and thoroughly test your recycling strategy in a test environment before working in the production environment.

