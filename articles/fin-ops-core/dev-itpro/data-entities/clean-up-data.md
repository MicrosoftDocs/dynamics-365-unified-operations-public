---
title: Clean up data management job history
description: Learn how to clean up data management job history, including how to troubleshoot an execution history cleanup batch error.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 01/27/2025
ms.custom:
ms.reviewer: twheeloc
---

# Clean up data management job history

[!include [banner](../includes/banner.md)]

## Clean up data

1. Go to **Data management** \> **Job history cleanup**.
2. In the **Job history** pane, set the **Number of days to retain history**, **Number of hours to execute the job**, and **Batch job recurrence** fields.
3. To schedule the job to run regularly in the background, select the **Batch processing** field.
4. To define a recurrence, select **Recurrence**, and then, in **Recurrence definition**, select **No end date**.

> [!NOTE]
> To clean large staging tables, we recommend that you set an execution time of six hours and a batch recurrence of at least once per day.

### Execution history cleanup batch error

If a **Job history cleanup** batch job has already been scheduled, it must be deleted before a new recurrence can be rescheduled. If you try to schedule a batch recurrence when one has already been scheduled, an error occurs. To address the error, follow these steps.

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
2. Search for the description **Job history cleanup**.
3. Delete batch jobs that are in a **Waiting** state.
4. If a batch job is in an **Executing** state, you can either cancel it or select **Remove recurrence**. The **Remove recurrence** function removes the batch job schedule after the current cleanup execution is completed.
5. After the job is either deleted or in an **Ended** state, create a new batch job recurrence.

### Cleanup job history in cloud environments 

Past job history cleanup activity is tracked in the DMFStagingHistoryCleanupTable table. It can be viewed by clicking **Cleanup job history** on the **Job history cleanup** page. 

There are two types of cleanup job are recorded on this page:
 - Records with positive values in the **Hours to execute the job** and **Retain job history** columns correspond to runs of the Job history cleanup batch job. This is the cleanup job that is configured using the **Job history cleanup** page. To improve cleanup performance, this job has been updated to target only parent DMF execution records. Staging table data and other data related to the execution aren't deleted by this job. Only execution records older than the configured **Retain job history value** are deleted.
 - Records with **-1** in the **Retain job history** column correspond to an automatic background cleanup job. This job runs automatically and removes all child records from staging tables and other DMF-related tables where the parent execution record has been deleted by the Job history cleanup batch job (1). 

These two jobs work in tandem: 
 - **Job history cleanup batch** job removes execution records which have gone out of the configured retention period.
 - **Automatic background cleanup** job removes all staging data and ancillary job data associated with those executions.
 
 


