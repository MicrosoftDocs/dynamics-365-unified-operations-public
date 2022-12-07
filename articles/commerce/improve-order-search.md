---
title: Improve the performance of Commerce order search
description: This article explains how to improve the performance of Commerce order search by enabling the use of intermediate order totals in Microsoft Dynamics 365 Commerce.
author: ashishMSFT
ms.date: 12/07/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-02-28

---

# Improve the performance of Commerce order search

[!include [banner](../includes/banner.md)]

This article explains how to improve search order performance by enabling the use of intermediate order totals in Microsoft Dynamics 365 Commerce.

The **Improve Performance of Commerce Order search** feature allows you to improve search order performance by enabling the use of intermediate order totals calculated by the **Calculate sales totals** job. This feature depends on you scheduling a batch job. 

## Enable the Improve Performance of Commerce Order search feature

To enable the **Improve Performance of Commerce Order search** feature in Commerce headquarters, follow these steps. 

1. Go to the **Feature management** workspace (**Systems administration \> Workspaces \> Feature management**). 
1. Search for the **Improve Performance of Commerce Order search** feature, and then select it.
1. In the right pane, select **Enable now**.

## Create and schedule the "Calculate sales totals" job

To create and schedule the "Calculate sales totals" job, follow these steps.

1. In Commerce headquarters, go to **System administration \> Enquiries \> Batch Jobs**.
1. Select **+New**.
1. For **Job description**, enter "Calculate sales totals".
1. While new job is in the **Withhold** state, do the following:
    1. Under **Batch tasks**, select **+New**.
    1. For **Task description**, enter a name similar to the batch job.
    1. For **Class name**, enter "SalesTotalsCalculateBatch".
    1. For Company, select the company from the drop-down menu.
    1. In the task parameters, set both the **Calculate totals for sales orders** and **Calculate totals for sales quotations** toggles to **Yes**.
    1. Schedule the job recurrence to run every 5-10 minutes.
1. Change status to **Waiting**.
1. Go to **Batch job history** and confirm that the job has been executed correctly.

## Improve the speed of calculations 

To improve the speed of calculations, Microsoft recommends that you enable the **Calculate sales totals using multiple threads** feature to speed up totals processing in case there are a large number of sales orders and quotations.

The **Calculate sales totals using multiple threads** feature helps improve performance by enabling the system to use parallel processing when it calculates sales totals in a batch. The feature adds a new **Number of threads** field to the **Calculate sales totals** flyout menu. If you choose to run the calculation in a batch, you can use this field to set the maximum number of threads. If you set the value to **0** (zero) or **1** (one), a single thread will be used. Values above **1** enable multithreading.

### Enable the Calculate sales totals using multiple threads feature

To enable the **Calculate sales totals using multiple threads** feature in Commerce headquarters, follow these steps. 

1. Go to the **Feature management** workspace (**Systems administration \> Workspaces \> Feature management**). 
1. Search for the **Calculate sales totals using multiple threads** feature, and then select it.
1. In the right pane, select **Enable now**.
