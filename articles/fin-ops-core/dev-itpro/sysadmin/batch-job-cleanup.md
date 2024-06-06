---
title: Clean up the batch job table
description: Learn about how to clean up the batch job table, including a step-by-step process that details the run batch job cleanup process.
author: snagamalla
ms.author: snagamalla
ms.topic: how-to
ms.date: 05/02/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2024-03-15
ms.search.form: 
ms.dyn365.ops.version: Platform update 63
---

# Clean up the batch job table

[!include [banner](../includes/banner.md)]

Over time, new batch jobs are created for specific user actions, one-time jobs are run, and batch jobs are re-created. As a result, many abandoned or unused batch jobs accumulate in the system. Accumulated batch jobs can eventually lead to the growth of the batch job table and related tables. This growth can negatively affect the performance of other jobs.

In version 10.0.39 (Platform update 63), the **System administration** module includes a **Batch job clean-up** page that simplifies the process of cleaning up the batch job table. To open this page, go to **System administration** \> **Periodic tasks** \> **Batch job clean-up**.

## Run batch job cleanup

To quickly clean up the records in the batch job table, follow these steps.

1. Go to **System administration** \> **Periodic tasks** \> **Batch job clean-up**.
1. In the **Retain jobs (days)** field, specify the number of days to keep the records of batch jobs.
1. In the **Records to delete in a transaction** field, input a value ranging from **1** to **200** to indicate the number of records to be deleted within a single database transaction. The associated job iterates through and removes data in batches of this size until all records are deleted. When the batch job processes a large volume of data, particularly within the parameters and information log fields of related jobs and tasks, it's advisable to enter a smaller number. This approach facilitates deletion in smaller segments and prevents the obstruction of other jobs.
1. In the **Caption** field, specify the title of the batch job to be deleted. The matching process is case-insensitive and requires an exact match.
1. In the **Class** field, specify the class name of a batch task for the batch job to delete.
1. Enable the **Delete by end date time** field if the cleanup should consider the end date/time of the last execution to determine which batch jobs to delete. By default, the cleanup considers the creation date/time.
1. In the **Created by** field, specify the user ID of the person who created the job.
1. In the **Withhold**, **Error**, **Finished**, and **Canceled** terminal status fields, select at least one option to delete the batch jobs.
1. Select **OK**.

## Best Practice

- We recommend that you regularly clean up the batch job table, and that you do this cleanup outside business hours.
- It's advisable to avoid running multiple **Batch job clean-up** Jobs simultaneously. This precaution is necessary because simultaneous runs might lead to database deadlocks, especially considering the typically high volume of data involved.
- If you need to run multiple tasks within the **Batch job clean-up**, each with different criteria, it's best to run them one after another in sequence. Running these tasks concurrently could result in deadlocks, as the cleanup processes might overlap, particularly when deleting large amounts of data from Batch tables.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
