---
title: Sales of taxable goods that have a discount and a provisional assessment
description: Learn about sales of taxable goods that have a discount and a provisional assessment, including processes for creating sales orders and posting invoices.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak  
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Sales of taxable goods that have a discount and a provisional assessment

[!include [banner](../../includes/banner.md)]

## Create a sales order

1. Go to **Accounts receivable** \> **Sales orders** \> **All sales orders**.
1. Create a sales order for a taxable item.
1. Select **Header view**.
1. On the **Price and discount** FastTab, in the **Total discount %** field, enter **10.00**.
1. Select **Line view**.
1. On the **Lines details** FastTab, on the **Address** tab, in the **Delivery address** field, select a value.
1. Save the record.
1. Select **Tax information**.
1. Select the **GST** FastTab.
1. Select the **Customer tax information** FastTab.
1. Select **OK**.
1. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document**.
1. Verify that the tax that is calculated considers the discount, and then select **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Quantity** field, select **All**.
1. Select the **Print invoice** check box.
1. Select the **Provisional assessment** check box.
1. Select **OK**, and then select **Yes** to acknowledge the warning message that you receive.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. Select **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-20-151407.png" alt-text="Screenshot of the voucher example.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
