---
title: Improve the performance of Commerce order search
description: This article explains how to help improve the performance of Commerce order search by enabling the use of intermediate order totals in Microsoft Dynamics 365 Commerce.
author: ashishMSFT
ms.date: 01/03/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-02-28

---

# Improve the performance of Commerce order search

[!include [banner](../includes/banner.md)]

This article explains how to enable and use the **Improve Performance of Commerce Order search** feature. This feature helps improve search order performance by enabling the use of intermediate order totals that are calculated by the **Calculate sales totals** job. To use this feature, you must schedule a batch job.

## Enable the Improve Performance of Commerce Order search feature

To enable the **Improve Performance of Commerce Order search** feature in Commerce headquarters, follow these steps.

1. Open the **Feature management** workspace (**Systems administration \> Workspaces \> Feature management**).
1. Search for the **Improve Performance of Commerce Order search** feature, and then select it.
1. In the right pane, select **Enable now**.

## Create and schedule the Calculate sales totals job

To create and schedule the **Calculate sales totals** job, follow these steps.

1. In Commerce headquarters, go to **System administration \> Inquiries \> Batch Jobs**.
1. Select **New**.
1. In the **Job description** field, enter **Calculate sales totals**.
1. While the new job has a status of **Withhold**, follow these steps:

    1. Under **Batch tasks**, select **New**.
    1. In the **Task description** field, enter a name that's similar to the name of the batch job.
    1. In the **Class name** field, enter **SalesTotalsCalculateBatch**.
    1. In the **Company** field, select the company.
    1. In the task parameters, set both the **Calculate totals for sales orders** option and the **Calculate totals for sales quotations** option to **Yes**.
    1. Schedule the recurrence so that the job is run every 5–10 minutes.

1. Change the status to **Waiting**.
1. Go to **Batch job history**, and confirm that the job has been run correctly.

## Improve the speed of calculations

To help improve the speed of calculations, Microsoft recommends that you enable the **Calculate sales totals using multiple threads** feature. In this way, you can speed up the processing of totals when there are many sales orders and quotations.

The **Calculate sales totals using multiple threads** feature helps improve performance by enabling the system to use parallel processing when it calculates sales totals in a batch. The feature adds a new **Number of threads** field to the **Calculate sales totals** dialog box. If you choose to run the calculations in a batch, you can use this field to set the maximum number of threads. If you set the value to **0** (zero) or **1**, a single thread will be used. Values above **1** enable multithreading.

### Enable the Calculate sales totals using multiple threads feature

To enable the **Calculate sales totals using multiple threads** feature in Commerce headquarters, follow these steps.

1. Open the **Feature management** workspace (**Systems administration \> Workspaces \> Feature management**).
1. Search for the **Calculate sales totals using multiple threads** feature, and then select it.
1. In the right pane, select **Enable now**.
