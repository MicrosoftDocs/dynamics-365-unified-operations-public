---
title: Sort sales invoice lines by packing slip
description: Learn how to set up and print accompanying invoices that include required packing slips details, including an outline on printing accompanying invoices.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2019-11-29
ms.search.form: 
ms.dyn365.ops.version: 10.0.8
---

# Sort sales invoice lines by packing slip

[!include [banner](../../includes/banner.md)]

In Italy, companies often need to issue *accompanying invoices*. Accompanying invoices combine an ordinary invoice with a transport document or packing slip (documento di trasporto, or DDT).

## Prerequisites

- The primary address of the legal entity is in Italy.
- In the **Feature management** workspace, the **Sales invoice lines sorting by packing slips** feature is turned on. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- Customer invoices use the new **SalesInvoice.Report\_IT** layout. Go to **Accounts receivable** > **Setup** > **Forms** > **Form setup**. On the **General** tab, select **Print management**. On the **Print management setup** page, under **Module - accounts receivable > Customer invoice**, select **Original <Default>**. Then, in the **Report format** field, select **SalesInvoice.Report\_IT**.

    :::image type="content" source="../media/emea-ita-exil-invoice-packing-slip-pic2.jpg" alt-text="Screenshot of the new layout selected for customer invoices.":::

> [!NOTE]
> When you turn on the **Sales invoice lines sorting by packing slips** feature, the system ignores the setting of the **Print packing slip specifications** check box on the **Invoice** tab of the **Form setup** page (**Accounts receivable > Setup > Forms > Form setup**). Even if you select this check box, the system treats it as if it's cleared.
>
> :::image type="content" source="../media/emea-ita-exil-invoice-packing-slip-pic3.jpg" alt-text="Screenshot of the Print packing slip specifications check box.":::

## Printing accompanying invoices

After you turn on and set up the feature, the printed invoice report includes invoice lines that are grouped and sorted by packing slip.

:::image type="content" source="../media/emea-ita-exil-invoice-packing-slip-pic.jpg" alt-text="Screenshot of an invoice where invoice lines are grouped and sorted by packing slip.":::

> [!NOTE]
> The new layout applies only to invoices that are based on sales orders. It doesn't apply to free-text invoices, because they don't use packing slips.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
