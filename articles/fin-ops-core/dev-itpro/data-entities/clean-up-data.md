---
title: Clean up data management job history
description: This article describes how to clean up data management job history.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 9/28/2023
ms.custom:

---

# Clean up data management job history

[!include [banner](../includes/banner.md)]

As of September 2023, Data Management job history entries and related staging table data that are older than 90 days are automatically deleted. To configure a job history retention period of less than 90 days, customers can use the **Job history cleanup** batch job.

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
