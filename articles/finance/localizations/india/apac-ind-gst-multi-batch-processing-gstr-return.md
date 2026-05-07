---
title: Enable multi-batch processing for GSTR reports
description: Learn how to enable multi-batch processing for Goods and Services Tax return (GSTR) reports with an outline on turning on the multi-batch processing feature.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 04/30/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-09-03
ms.dyn365.ops.version: 10.0.6
---

# Enable multibatch processing for GSTR reports

[!include [banner](../../includes/banner.md)]

You can run many tasks in Microsoft Dynamics 365 Finance as part of a batch job. Typically, you create batch jobs for tasks such as processing reports, coordinating scheduled maintenance, and creating and sending documents like invoices. By using batch jobs, you avoid slowing down your computer or the server during typical working hours. The tasks in a batch job can run either sequentially or at the same time.

In India, every legal entity must file Goods and Services Tax (GST) returns. Typically, the transaction volume is very high because all details of sales and purchase invoices are reported to the government. Currently, you can generate GST return (GSTR) reports either directly from the report dialog box or by using the batch process. However, report generation can sometimes take quite a while. To make the process more dynamic and efficient, the multibatch processing feature is provided for GSTR reports. This feature significantly improves the performance of report generation.

## Turn on the multibatch processing feature

- Go to **Workspaces** > **Feature management**, and turn on the **Enable multibatch processing for GSTR reports** feature.

:::image type="content" source="../media/Multi-batchprocessing-001.png" alt-text="Screenshot of the Enable multibatch processing for GSTR reports feature turned on.":::

## Generate a GSTR report

1. Go to **Tax** > **Inquiries and reports** > **Sales tax reports** > **GER export to GSTR CSV**.
1. On the **Run in the background** FastTab, set the **Batch processing** option to **Yes**.
1. On the **Parameters** FastTab, in the **Number of days per batch** field, enter a number that's greater than **0**.
1. Select **OK**.

:::image type="content" source="../media/Multi-batchprocessing-002.png" alt-text="Screenshot of the GER export to GSTR CSV dialog box.":::

## Get CSV files

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.
1. Select the comma-separated values (CSV) files that you want. For example, select **GER export to GSTR CSV__Merged**. This file is generated as a merged file.

:::image type="content" source="../media/Multi-batchprocessing-003.png" alt-text="Screenshot of the Get CSV Files page.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
