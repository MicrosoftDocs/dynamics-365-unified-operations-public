---
title: Copy a batch job
description: Learn about copying a batch job and batch tasks, including step-by-step processes detailing on copying and creating batch jobs.
author: Peakerbl
ms.author: johnmichalak
ms.topic: article
ms.date: 03/13/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-08-15
ms.search.form: 
ms.dyn365.ops.version: Platform update 20
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
---

# Copy a batch job

[!include [banner](../includes/banner.md)]

When you want to create the same jobs for different legal entities, use the copy batch job functionality to copy an existing batch job and the batch tasks, including recurrences.

You can set the description, company, schedule start date and time, the recurrence, and the run by account at the same time. When you copy the batch job, the process copies any alerts and dependencies from the source job.

>[!NOTE]
>This feature is available as of Platform update 20.

## Copy a batch job

Complete the following steps to copy a batch job.

1. Select **System administration** > **Inquiries** > **Batch jobs**.
2. Select the job that you want to copy, and on the Action Pane, select **Batch Job** > **Copy batch job**.

:::image type="content" source="./media/copy-batch-function.png" alt-text="Screenshot of the Copy Batch Function.":::

1. Enter or add any changes. If you set **View tasks** to **Yes**, when you select **OK** you go directly to the **Batch tasks** page for the copied job.

:::image type="content" source="./media/copy-batch-form.png" alt-text="Screenshot of the Copy Batch Form.":::

>[!IMPORTANT]
>The process creates the copied batch job with a **Withhold** status, so you need to enable it. You can also set the **Run by** user to give this user the privilege to run the job without being a Sys Admin.

## Enable the batch job

Complete the following steps to enable a batch job.

1. On **Batch job**, on the action pane, select **Batch job** > **Change status**.
2. Select the **Waiting** status, and then select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
