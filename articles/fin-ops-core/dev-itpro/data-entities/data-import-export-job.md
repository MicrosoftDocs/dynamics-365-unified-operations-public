---
# required metadata

title: Data import and export jobs overview
description: Use the Data management workspace to create and manage data import and export jobs.
author: Sunil-Garg
manager: AnnBe
ms.date: 04/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data import and export jobs overview

[!include [banner](../includes/banner.md)]

To create and manage data import and export jobs, you use the **Data management** workspace. By default, the data import and export process creates a staging table for each entity in the target database. Staging tables let you verify, clean up, or convert data before you move it.

> [!NOTE]
> This topic assumes that you are familiar with [data entities](data-entities.md).

## Data import/export process
Here are the steps to import or export data.

1. Create an import or export job where you complete the following tasks:

    - Define the project category.
    - Identify the entities to import or export.
    - Set the data format for the job.
    - Sequence the entities, so that they are processed in logical groups and in an order that makes sense.
    - Determine whether to use staging tables.

2. Validate that the source data and target data are mapped correctly.
3. Verify the security for your import or export job.
4. Run the import or export job.
5. Validate that the job ran as expected by reviewing the job history.
6. Clean up the staging tables.

The remaining sections of this topic provide more details about each step of the process.

> [!NOTE]
> In order to refresh the Data import/export form to see the latest progress, use the form refresh icon. Browser level refresh is not recommended because it will interrupt any import/export jobs that are not run in batch.

## Create an import or export job
A data import or export job can be run one time or many times.

### Define the project category
We recommend that you take the time to select an appropriate project category for your import or export job. Project categories can help you manage related jobs.

### Identify the entities to import or export
You can add specific entities to an import or export job or select a template to apply. Templates fill a job with a list of entities. The **Apply template** option is available after you give the job a name and save the job.

### Set the data format for the job
When you select an entity, you must select the format of the data that will be exported or imported. You define formats by using the **Data sources setup** tile. A source data format is a combination of **Type**, **File format**, **Row delimiter** and **Column delimiter**. There are also other attributes, but these are the key ones to understand. The following table lists the valid combinations.

| File Format            | Row/Column delimiter                       | XML Style                 |
|------------------------|--------------------------------------------|---------------------------|
| Excel                  | Excel                                      | \-NA-                     |
| XML                    | \-NA-                                      | XML-Element XML-Attribute |
| Delimited, fixed width | Comma, semicolon, tab, vertical bar, colon | \-NA-                     |

### Sequence the entities
Entities can be sequenced in a data template, or in import and export jobs. When you run a job that contains more than one data entity, you must make sure that the data entities are correctly sequenced. You sequence entities primarily so that you can address any functional dependencies among entities. If entities don’t have any functional dependencies, they can be scheduled for parallel import or export.

#### Execution units, levels, and sequences
The execution unit, level in the execution unit, and sequence of an entity help control the order that the data is exported or imported in.

- Entities in different execution units are processed in parallel.
- In each execution unit, entities are processed in parallel if they have the same level.
- In each level, entities are processed according to their sequence number in that level.
- After one level has been processed, the next level is processed.

#### Resequencing
You might want to resequence your entities in the following situations:

- If only one data job is used for all your changes, you can use resequencing options to optimize the execution time for the full job. In these cases, you can use the execution unit to represent the module, the level to represent the feature area in the module, and the sequence to represent the entity. By using this approach, you can work across modules in parallel, but you can still work in sequence in a module. To help guarantee that parallel operations succeed, you must consider all dependencies.
- If multiple data jobs are used (for example, one job for each module), you can use sequencing to affect the level and sequence of entities for optimal execution.
- If there are no dependencies at all, you can sequence entities at different execution units for maximum optimization.

The **Resequencing** menu is available when multiple entities are selected. You can resequence based on execution unit, level, or sequence options. You can set an increment to resequence the entities that have been selected. The unit, level, and/or sequence number that is selected for each entity is updated by the specified increment.

#### Sorting
Use can use the **Sort by** option to view the entity list in sequential order.

### Truncating
For import projects, you can choose to truncate records in the entities prior to import. This is useful if your records must be imported into a clean set of tables. This setting is off by default.

## Validate that the source data and target data are mapped correctly
Mapping is a function that applies to both import and export jobs.

- In the context of an import job, mapping describes which columns in the source file become the columns in the staging table. Therefore, the system can determine which column data in the source file must be copied into which column of the staging table.
- In the context of an export job, mapping describes which columns of the staging table (that is, the source) become the columns in the target file.

If the column names in the staging table and the file match, the system automatically establishes the mapping, based on the names. However, if the names differ, columns aren’t mapped automatically. In these cases, you must complete the mapping by selecting the **View map** option on the entity in the data job.

There are two mapping views: **Mapping visualization**, which is the default view, and **Mapping details**. A red asterisk (\*) identifies any required fields in the entity. These fields must be mapped before you can work with the entity. You can unmap other fields as you require when you work with the entity. To unmap a field, select the field in either the **Entity** column or the **Source** column, and then select **Delete selection**. Select **Save** to save your changes, and then close the page to return to the project. You can use the same process to edit the field mapping from source to staging after you import.

You can generate a mapping on the page by selecting **Generate source mapping**. A generated mapping behaves like an automatic mapping. Therefore, you must manually map any unmapped fields.

![Data mapping](./media/dixf-map.png)

## Verify the security for your import or export job
Access to the **Data management** workspace can be restricted, so that non-administrator users can access only specific data jobs. Access to a data job implies full access to the execution history of that job and access to the staging tables. Therefore, you must make sure that appropriate access controls are in place when you create a data job.

### Secure a job by roles and users
Use the **Applicable roles** menu to restrict the job to one or more security roles. Only users in those roles will have access to the job.

You can also restrict a job to specific users. When you secure a job by users instead of roles, there is more control if multiple users are assigned to a role.

### Secure a job by legal entity
Data jobs are global in nature. Therefore, if a data job was created and used in a legal entity, the job will be visible in other legal entities in the system. This default behavior might be preferred in some application scenarios. For example, an organization that imports invoices by using data entities might provide a centralized invoice processing team that is responsible for managing invoice errors for all divisions in the organization. In this scenario, it’s useful for the centralized invoice processing team to have access to invoice import jobs from all legal entities. Therefore, the default behavior meets the requirement from a legal entity perspective.

However, an organization might want to have invoice processing teams per legal entity. In this case, a team in a legal entity should have access only to the invoice import job in its own legal entity. To meet this requirement, you can configure legal entity–based access control on the data jobs by using the **Applicable legal entities** menu inside the data job. After the configuration is done, users can see only jobs that are available in the legal entity that they are currently signed in to. To see jobs from another legal entity, users must switch to that legal entity.

A job can be secured by roles, users, and legal entity at the same time.

## Run the import or export job
You can run a job one time by selecting the **Import** or **Export** button after you define the job. To set up a recurring job, select **Create recurring data job**.

> [!NOTE]
> An import or an export job can be run asynchronously by selecting the **Import** or **Export** button. Running in async uses the async framework, which is different than batch framework. However, like batch framework, async framework can also undergo throttling and as a result, the job may not execute immediately. The jobs can also be run synchronously by selecting **Import now** or **Export now**. This starts the job immediately and is useful if async or a batch does not start due to throttling. The jobs can also be executed in a batch by choosing the **Run in batch** option. Batch resources are subject to throttling, so the batch job might not start immediately. The async option is useful when users interact directly with the user interface and are not power users to understand batch scheduling. Using a batch is an alternate option if large volumes need to be imported or exported. Batch jobs can be scheduled to run on a specific batch group, which allows more control from a load balancing perspective. If async and batch are both undergoing throttling due to high resource utilization on the system, then as an immediate workaround, the synchronous version of import/export can be used. The synchronous option will start immediately and will block the user interface because its executing synchronously. The browser window must remain open when the synchronous operation is in progress.

## Validate that the job ran as expected
The job history is available for troubleshooting and investigation on both import and export jobs. Historical job runs are organized by time ranges.

![Job history ranges](./media/dixf-job-history.md.png)

Each job run provides the following details:

- Execution details
- Execution log

Execution details show the state of each data entity that the job processed. Therefore, you can quickly find the following information:

- Which entities were processed.
- For an entity, how many records were successfully processed, and how many failed.
- The staging records for each entity.

You can download the staging data in a file for export jobs, or you can download it as a package for import and export jobs.

From the execution details, you can also open the execution log.

## Parallel imports
To speed up the import of data, parallel processing of importing a file can be enabled if the entity supports parallel imports. To configure the parallel import for an entity, the following steps must be followed.

1. Go to **System administration \> Workspaces \> Data management**.
2. In the **Import / Export** section, select the **Framework parameters** tile to open the **Data import/export framework parameters** page.
3. On the **Entity settings** tab, select **Configure entity execution parameters** to open the **Entity import execution parameters** page.
4. Set the following fields to configure parallel import for an entity:

    - In the **Entity** field, select the entity.
    - In the **Import threshold record count** field, enter the threshold record count for import. This determines the record count to be processed by a thread. If a file has 10K records, a record count of 2500 with a task count of 4 will mean, each thread will process 2500 records.
    - In the **Import task count** field, enter the count of import tasks. This must not exceed the max batch threads allocated for batch processing in **System administration \>Server configuration**.

## Clean up the staging tables
Starting in Platform update 29, this functionality has been deprecated. This is replaced by a new version of job history clean-up functionality explained below.

You can clean up staging tables by using the **Staging clean up** feature in the **Data management** workspace. You can use the following options to select which records should be deleted from which staging table:

- **Entity** – If only an entity is provided, all records from that entity’s staging table are deleted. Select this option to clean up all the data for the entity across all data projects and all jobs.
- **Job ID** – If only a job ID is provided, all records for all entities in the selected job are deleted from the appropriate staging tables.
- **Data projects** – If only a data project is selected, all records for all entities and across all jobs for the selected data project are deleted.

You can also combine the options to further restrict the record set that is deleted.

## Job history clean up (available in Platform update 29 and later)

The job history clean-up functionality in data management must be used to schedule a periodic cleanup of the execution history. This functionality replaces the previous staging table clean-up functionality, which is now deprecated. The following tables will be cleaned up by the clean-up process.

-   All staging tables

-   DMFSTAGINGVALIDATIONLOG

-   DMFSTAGINGEXECUTIONERRORS

-   DMFSTAGINGLOGDETAIL

-   DMFSTAGINGLOG

-   DMFDEFINITIONGROUPEXECUTIONHISTORY

-   DMFEXECUTION

-   DMFDEFINITIONGROUPEXECUTION

The functionality must be enabled in feature management and then can be accessed from **Data management \> Job history cleanup**.

### Scheduling parameters

When scheduling the clean-up process, the following parameters must be specified to define the clean-up criteria.

-   **Number of days to retain history** – This setting is used to control the amount of execution history to be preserved. This is specified in number of days. When the clean-up job is scheduled as a recurring batch job, this setting will act like a continuously
moving window thereby, always leaving the history for the specified number of days intact while deleting the rest. The default is 7 days.

-   **Number of hours to execute the job** – Depending on the amount of history to be cleaned up, the total execution time for the clean-up job can vary from a few minutes to a few hours. This parameter must be set to the number of hours that the job will execute. After the clean-up job has executed for the specified number of hours, the job will exit and will resume the clean up the next time it is run based on the recurrence schedule.

    A maximum execution time can be specified by setting a max limit on the number of hours the job must run using this setting. The clean-up logic goes through one job execution ID at a time in a chronologically arranged sequence, with oldest being first for the cleanup of related execution history. It will stop picking up new execution ID’s for cleanup when the remaining execution duration is within the last 10% of the specified duration. In some cases, it will be expected that the clean-up job will continue beyond the specified max time. This will largely depend on the number of records to be deleted for the current execution ID that was started before the 10% threshold was reached. The cleanup that was started must be completed to ensure data integrity, which means that cleanup will continue despite exceeding the specified limit. When this is complete, new execution ID’s are not picked up and the clean-up job completes. The remaining execution history that was not cleaned up due to lack of enough execution time, will be picked up the next time the clean-up job is scheduled. The default and minimum value for this setting is set to 2 hours.

-   **Recurring batch** – The clean-up job can be run as a one-time, manual execution, or it can be also scheduled for recurring execution in batch. The batch can be scheduled using the **Run in background** settings, which is the standard batch set up.

> [!NOTE]
> If records in the staging tables are not cleaned up completely, ensure that the cleanup job is scheduled to run in recurrence. As explained above, in any clean up execution the job will only clean up as many execution ID's as is possible within the provided maximum hours. In order to continue cleanup of any remaining staging records, the job must be scheduled to run periodically.
