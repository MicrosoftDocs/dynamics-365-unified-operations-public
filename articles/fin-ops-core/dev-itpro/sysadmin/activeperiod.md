---
title: Active batch periods
description: Learn about setting up and working with active batch periods, including a step-by-step process on how to set up active periods for batch jobs.
author: hasaid
ms.author: hasaid
ms.topic: article
ms.date: 03/13/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: Platform update 21
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
---

# Active batch periods

[!include [banner](../includes/banner.md)]

When Platform update 21 was released, it introduced an extra level of control over when batch jobs run. Before this update, you could only schedule a batch job to run every hour for a set number of hours or until a specific date. Now, administrators can add an active period, which means you can:

- Set time ranges when jobs in a batch group can start running.
- Choose to run batch jobs only outside of office hours.
- Decide how often batch jobs run during the active period. For example, an administrator might choose to run the batch jobs every hour but only between 6:00 PM and 8:00 AM.

> [!NOTE]
> This feature is available starting with Platform update 21.

## Set up active periods for batch jobs

1. Go to **System administration** > **Setup** > **Active periods for batch jobs**.
1. Enter the name of the batch job, and specify the start and end dates for when the batch job is active.
1. Select **Save**.

:::image type="content" source="./media/active-periods.png" alt-text="Screenshot of the Active Period Form.":::

## Assign active periods to batch jobs

1. Go to **System administration** > **Inquiries** > **Batch jobs**.
1. Select the batch job that you want to assign a period to, and select **Edit**.
1. In the **Active period** field, select the active period that you want to assign, and then select **Save**.

:::image type="content" source="./media/assign-active-period.png" alt-text="Screenshot of the Assign Active Period form.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
