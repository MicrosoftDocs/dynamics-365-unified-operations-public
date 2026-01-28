---
title: Clean up data management job history
description: Learn how to clean up data management job history, including how to troubleshoot an execution history cleanup batch error.
author: pnghub
ms.author: twheeloc
ms.topic: how-to
ms.date: 01/14/2026
ms.custom:
ms.reviewer: twheeloc
---

# Clean up data management job history

[!include [banner](../includes/banner.md)]

## Clean up data

1. Go to **Data management** > **Job history cleanup**.
1. In the **Job history** pane, set the **Number of days to retain history**, **Number of hours to execute the job**, and **Batch job recurrence** fields.
1. To schedule the job to run regularly in the background, select the **Batch processing** field.
1. To define a recurrence, select **Recurrence**, and then, in **Recurrence definition**, select **No end date**.

> [!NOTE]
> To clean large staging tables, set an execution time of six hours and a batch recurrence of at least once per day.

### Execution history cleanup batch error

If you already scheduled a **Job history cleanup** batch job, you must delete it before you can reschedule a new recurrence. If you try to schedule a batch recurrence when one already exists, an error occurs. To fix the error, follow these steps:

1. Go to **System administration** > **Inquiries** > **Batch jobs**.
1. Search for the description **Job history cleanup**.
1. Delete batch jobs that are in a **Waiting** state.
1. If a batch job is in an **Executing** state, you can either cancel it or select **Remove recurrence**. The **Remove recurrence** function removes the batch job schedule after the current cleanup execution is completed.
1. After the job is either deleted or in an **Ended** state, create a new batch job recurrence.

### Cleanup job history in cloud environments

The system tracks past job history cleanup activity in the `DMFStagingHistoryCleanupTable` table. You can view this history by selecting **Cleanup job history** on the **Job history cleanup** page.

The page shows two types of cleanup jobs:

- Records with positive values in the **Hours to execute the job** and **Retain job history** columns correspond to runs of the Job history cleanup batch job. This cleanup job is the one you configure by using the **Job history cleanup** page. To improve cleanup performance, this job now targets only parent DMF execution records. It doesn't delete staging table data or other data related to the execution. It only deletes execution records that are older than the configured **Retain job history** value.
- Records with **-1** in the **Retain job history** column correspond to an automatic background cleanup job. This job runs automatically and removes all child records from staging tables and other DMF-related tables when the parent execution record is deleted by the Job history cleanup batch job.

These two jobs work together:

- The **Job history cleanup batch** job removes execution records that are older than the configured retention period.
- The **Automatic background cleanup** job removes all staging data and ancillary job data associated with those executions.
