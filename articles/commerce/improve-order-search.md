---
title: Improve the performance of Commerce order search
description: Learn how to improve the performance of order search and order history in Dynamics 365 Commerce by scheduling the Calculate sales totals job.
author: ashishMSFT
ms.date: 11/20/2026
ms.topic: how-to
ms.author: asharchw
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
ai-usage: ai-assisted
---

# Improve the performance of Commerce order search

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to improve the performance of order search and order history in Dynamics 365 Commerce by setting up and scheduling the **Calculate sales totals** job.

When an order search or order history request runs, Commerce needs the total amounts for each sales order, including tax, discounts, and charges. If precalculated totals exist for an order, Commerce uses them. If they don't exist, Commerce calculates the totals while the request runs. That calculation can make order search slow or cause it to time out. For example, it can affect the **Recall order** operation in the point of sale (POS), the **Order history** page on an e-commerce site, and integrations that retrieve sales orders.

The **Calculate sales totals** batch job calculates these totals ahead of time. This improvement is part of the product, and you don't have to turn it on in **Feature management**. However, you must set up and schedule the **Calculate sales totals** job.

## Set up and schedule the Calculate sales totals job

To set up and schedule the **Calculate sales totals** job, follow these steps:

1. In Commerce headquarters, go to **Sales and marketing** > **Periodic tasks** > **Calculate sales totals**.
1. In the **Calculate sales totals** dialog box, set the **Calculate totals for sales orders** option to **Yes**.
1. If you also need totals for sales quotations, set the **Calculate totals for sales quotations** option to **Yes**.
1. In the **Ignore documents updated before (days)** field, enter the number of days of history to include. The job skips documents that were last updated more than this number of days ago. Select a value that covers the order history that customers and store staff need to search. For example, enter **365** to include orders that were last updated within the past year.
1. Optionally, in the **Number of threads** field, enter the number of threads to use. For more information, see [Improve the speed of calculations](#improve-the-speed-of-calculations).
1. On the **Run in the background** FastTab, set the **Batch processing** option to **Yes**.
1. Select **Recurrence**, and set up a recurrence so that totals stay current. The recurrence dialog defaults to every 10 minutes.
1. Select **OK** to schedule the job.
1. Go to **Batch job history**, and confirm that the job runs correctly.

> [!NOTE]
> Order search and order history might be slower for orders until the job calculates their totals.

## Improve the speed of calculations

If you have many sales orders and quotations, you can speed up the calculation of totals by using the **Number of threads** field in the **Calculate sales totals** dialog box. This field sets the maximum number of threads that the job uses when it runs in a batch.

- If you set the value to **0** (zero) or **1**, the job uses a single thread.
- If you set a value greater than **1**, the job evenly distributes the selected orders and quotations across multiple threads.

The number of threads that the job uses never exceeds the maximum number of batch threads that are configured for your system. If calculations take too long, increase the value. To leave more resources for other processes, decrease the value.

## Troubleshoot slow order search or order history

If order search or order history is slow or times out, first check the **Calculate sales totals** job:

- Confirm that the job is set up with the **Calculate totals for sales orders** option set to **Yes**.
- Confirm that the job has a recurrence and runs correctly in **Batch job history**.
- Confirm that the **Ignore documents updated before (days)** value covers enough days to include the orders that users search for.

If the issue persists and occurs as a timeout on an e-commerce site, you can increase the data action timeout values. For more information, see [Platform settings file](e-commerce-extensibility/platform-settings.md). Changing these timeout settings affects all Retail API calls.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
