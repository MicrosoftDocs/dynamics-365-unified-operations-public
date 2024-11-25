---
title: Clean up the batch job history 
description: Learn about how to clean up the batch job history, including an overview on batch job history clean-up and a step-by-step process.
author: snagamalla
ms.author: snagamalla
ms.topic: article
ms.date: 05/02/2024
ms.reviewer: johnmichalak 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-03-08
ms.search.form:
ms.dyn365.ops.version: Platform update 25
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
---

# Clean up the batch job history

[!include [banner](../includes/banner.md)]

When you run a batch job, a history is recorded. This history can be used to monitor the correct execution of jobs. However, when several batch jobs are created, especially batch jobs with high recurrence, many batch job history entries are generated. Too many entries in the history table can negatively affect the performance of future jobs.

Two pages added to the **System administration** module make it easy to clean up the batch job history:

- System administration > Periodic tasks > Batch job history clean-up
- System administration > Periodic tasks > Batch job history clean-up (custom)

## Batch job history clean-up

Follow these steps to quickly clean up all history entries that are older than a specified number of days.

1. On the **Periodic tasks in System administration** module, select **Batch job history clean-up**.
2. In the **History limit (days)** field, specify the number of days to keep a history of batch jobs.
3. Select **OK**.


## Batch job history clean-up (custom)

The custom batch job lets you apply other filtering, based on criteria such as status, job description, company, or user. You can also add other filter criteria by selecting the **Filter** button.

1. On the **Periodic tasks in System administration** module, select **Batch job history clean-up (custom)**.
2. In the **History limit (days)** field, specify the number of days to keep a history of batch jobs.
3. In the **Records to delete in a transaction** field, input a value ranging from **10** to **100** to indicate the number of records to delete within a single database transaction. The associated job iterates through and removes data in batches of this size until all records are deleted. When the batch job processes a large volume of data, particularly within the parameters and information log fields of related jobs and tasks, it's advisable to enter a smaller number. This approach facilitates deletion in smaller segments and prevents the obstruction of other jobs.
4. On the **Records to include** FastTab, specify any filter criteria that you require, and then select **OK**.
5. Select **OK**.

## Best Practice

- We recommend that you regularly clean up the batch job history, and that you do this cleanup outside of business hours.
- It's advisable to avoid running multiple Batch History Cleanup Jobs simultaneously. This precaution is necessary because simultaneous runs might lead to database deadlocks, especially considering the typically high volume of data involved.
- If you need to run multiple tasks within the **Batch job history clean-up (custom)**, each with different criteria, it's best to run them one after another in sequence. Running these tasks concurrently could result in deadlocks, as the cleanup processes might overlap, particularly when deleting large amounts of data from History tables.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
