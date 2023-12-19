---
# required metadata

title: Clean up the batch job table 
description: This article provides information about how to clean up the batch job table.
author: snagamalla
ms.date: 15/03/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: 
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

Over time, many orphaned or unused Batch jobs accumulate in the system due to the creation of new Batch jobs on certain user actions, one-time executed jobs, and recreation of Batch jobs. This can eventually lead to the growth of Batch Job and related tables, which can negatively impact the performance of other jobs.

The System administration module in platform update 10.0.39 (PU 63) now includes a Batch job clean-up page that simplifies the process of cleaning up the batch job table.
To navigate to this page, go to System administration > Periodic tasks > Batch job clean-up.

> [!NOTE]
> We recommend that you regularly clean up the batch job table, and that you do this cleanup outside of business hours.

## Batch job clean-up

Follow these steps to quickly clean up the Batch job table records based on options provided as below.

1. On the **Periodic tasks in System administration** module, select **Batch job clean-up**.
2. In the **Retain jobs (days)** field, specify the number of days to keep the records of batch jobs.
3. In the **Records to delete in a transaction** field, specify the no of records (1 - 200 records) to delete in a transaction.
4. In the **Caption** field, specify the caption of Batch job to delete.
5. In the **Class** field, specify the class name of a batch task whose respective Batch job to delete.
6. In the **Delete by end datetime** field, enable this flag to specify if batch jobs to be deleted based on End date time of last execution, else by default it considers the Created date time to delete the jobs.
7. In the **Created by** field, specify the userId who have created the job.
8. In **Withhold**, **Error**, **Finished** and **Cancelled** terminal status fields, select atleast one option to delete the batch jobs.
9. Select **OK**.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]