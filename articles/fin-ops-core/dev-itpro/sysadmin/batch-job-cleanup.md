---
# required metadata

title: Clean up the batch job table 
description: This article provides information about how to clean up the batch job table.
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

# Clean up the batch job records

[!include [banner](../includes/banner.md)]

Over time, many abandoned or unused batch jobs accumulate in the system due to the creation of new batch jobs on certain user actions, one-time executed jobs, and recreation of batch jobs. Accumulated batch jobs can eventually lead to the growth of batch job and related tables, which can negatively impact the performance of other jobs.

The System administration module in platform update 10.0.39 (PU 63) now includes a **Batch job clean-up** page that simplifies the process of cleaning up the batch job table.

To navigate to this page, go to **System administration** > **Periodic tasks** > **Batch job clean-up**.

> [!NOTE]
> We recommend that you regularly clean up the batch job table, and that you do this cleanup outside of business hours.

## Batch job clean-up

To quickly clean-up the batch job table records, follow these steps.

1. On the **Periodic tasks** page in the **System administration** module, select **Batch job clean-up**.
1. In the **Retain jobs (days)** field, specify the number of days to keep the records of batch jobs.
1. In the **Records to delete in a transaction** field, specify the number of records (1 - 200 records) to delete in a transaction.
1. In the **Caption** field, specify the caption of the batch job to delete.
1. In the **Class** field, specify the class name of a batch task for the respective batch job to delete.
1. Enable the **Delete by end date time** field to specify if the batch jobs to be deleted are based on the end date time of last execution. By default it considers the created date time.
1. In the **Created by** field, specify the userId of the person who created the job.
1. In the **Withhold**, **Error**, **Finished**, and **Canceled** terminal status fields, select at least one option to delete the batch jobs.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
