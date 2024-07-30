---
title: Sales of taxable goods that have a discount and a provisional assessment
description: Learn about sales of taxable goods that have a discount and a provisional assessment, including processes for creating sales orders and posting invoices.
author: epodkolzina
ms.author: epodkolzina
ms.topic: article
ms.date: 06/04/2019
ms.reviewer: johnmichalak  
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Sales of taxable goods that have a discount and a provisional assessment

[!include [banner](../../includes/banner.md)]

## Create a sales order

1. Go to **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create a sales order for a taxable item.
3. Select **Header view**.
4. On the **Price and discount** FastTab, in the **Total discount %** field, enter **10.00**.
5. Select **Line view**.
6. On the **Lines details** FastTab, on the **Address** tab, in the **Delivery address** field, select a value.
7. Save the record.
8. Select **Tax information**.
9. Select the **GST** FastTab.
10. Select the **Customer tax information** FastTab.
11. Select **OK**.
12. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document**.
13. Verify that the tax that is calculated considers the discount, and then select **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. In the **Quantity** field, select **All**.
3. Select the **Print invoice** check box.
4. Select the **Provisional assessment** check box.
5. Select **OK**, and then select **Yes** to acknowledge the warning message that you receive.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
2. Select **Voucher**.

![Example.](../media/Annotation-2019-05-20-151407.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
