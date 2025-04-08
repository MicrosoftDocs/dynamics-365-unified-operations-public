---
title: Sales where prices include and exclude tax
description: Learn about sales where the prices on some order lines include sales tax and the prices on other order lines exclude sales tax.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/04/2019
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Sales where prices include and exclude tax

[!include [banner](../../includes/banner.md)]

## Create a sales order

1. Go to **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create a sales order for taxable goods, and add two sales order lines:

    - For order line 1, clear the **Prices include sales tax** check box.
    - For order line 2, select the **Prices include sales tax** check box.

3. Save the records.
4. Select order line 1, and then select **Tax information**.
5. Select the **GST** FastTab.
6. Select the **Customer tax information** FastTab.
7. Select **OK**.
8. Repeat steps 4 through 7 for order line 2.
9. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document**.

    What you see might resemble the following example:

    **Order line 1**

    - **Taxable amount:** 10,000
    - **CGST:** 10 percent
    - **SGST:** 10 percent
    - **CESS:** 1 percent

    **Order line 2**

    - **Taxable amount:** 5,000
    - **CGST:** 10 percent
    - **SGST:** 10 percent
    - **CESS:** 1 percent
    - Price inclusive

10. Select **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. In the **Quantity** field, select **All**.
3. Select **OK**, and then select **Yes** to acknowledge the warning message that you receive.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
2. Select **Voucher**.

![Example.](../media/Annotation-2019-05-20-153808.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
