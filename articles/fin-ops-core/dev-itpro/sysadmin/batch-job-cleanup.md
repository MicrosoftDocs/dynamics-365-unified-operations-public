---
# required metadata

title: Clean up the batch job table
description: This article describes how to clean up the batch job table.
author: snagamalla
ms.date: 03/15/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.tgt_pltfrm: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: snagamalla
ms.search.validFrom: 2024-03-15
ms.dyn365.ops.version: Platform update 63

---

# Clean up the batch job table

[!include [banner](../includes/banner.md)]

Over time, new batch jobs are created for specific user actions, one-time jobs are run, and batch jobs are re-created. As a result, many abandoned or unused batch jobs accumulate in the system. Accumulated batch jobs can eventually lead to the growth of the batch job table and related tables. This growth can negatively affect the performance of other jobs.

In version 10.0.39 (Platform update 63), the **System administration** module includes a **Batch job clean-up** page that simplifies the process of cleaning up the batch job table. To open this page, go to **System administration** \> **Periodic tasks** \> **Batch job clean-up**.

> [!NOTE]
> We recommend that you regularly clean up the batch job table, and that you do this cleanup outside business hours.

## Run batch job cleanup

To quickly clean up the records in the batch job table, follow these steps.

1. Go to **System administration** \> **Periodic tasks** \> **Batch job clean-up**.
1. In the **Retain jobs (days)** field, specify the number of days to keep the records of batch jobs.
1. In the **Records to delete in a transaction** field, enter a value from **1** through **200** to specify the number of records to delete in a single transaction.
1. In the **Caption** field, specify the caption of the batch job to delete.
1. In the **Class** field, specify the class name of a batch task for the batch job to delete.
1. Enable the **Delete by end date time** field if the cleanup should consider the end date/time of the last execution to determine which batch jobs to delete. By default, the cleanup considers the creation date/time.
1. In the **Created by** field, specify the user ID of the person who created the job.
1. In the **Withhold**, **Error**, **Finished**, and **Canceled** terminal status fields, select at least one option to delete the batch jobs.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
