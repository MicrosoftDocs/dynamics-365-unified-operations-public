---
title: Sales invoices that are split based on delivery addresses
description: Learn about sales invoices that are split based on delivery addresses, including step-by-step processes for posting packing slips and validating vouchers.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 05/01/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Sales invoices that are split based on delivery addresses

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts receivable** > **Sales orders** > **All sales orders**.
1. Create a sales order for taxable items.
1. On the **Lines details** FastTab, select the **Address** tab.
1. Save the record.
1. Select order line 1, and then select **Tax information**.
1. Select the **GST** FastTab.
1. Select the **Customer tax information** FastTab.
1. Select **OK**.
1. Select order line 2, and then select **Tax information**.
1. Select the **GST** FastTab.
1. Select the **Customer tax information** FastTab.
1. Select **OK**.
1. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document** to review the calculated taxes.

    What you see might resemble the following example:

    **Order line 1**

    - **Taxable amount:** 10,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent
    - **CESS:** 1 percent

    **Order line 2**

    - **Taxable amount:** 5,000.00
    - **IGST:** 20 percent
    - **CESS:** 1 percent

1. Select **Close**.

## Post the packing slip

1. On the Action Pane, on the **Pick and pack** tab, in the **Generate** group, select **Packing slip**.
1. Select **OK**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Quantity** field, select **All**.

    > [!NOTE]
    > The invoice is split based on the delivery addresses.

1. Select **OK**, and then select **Yes** to acknowledge the warning message that you receive.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. Select a record that has an invoice amount of **12,100.00**.
1. Select **Voucher**.

    :::image type="content" source="../media/Annotation-2019-05-20-163117.png" alt-text="Screenshot of financial entries for the record that has an invoice amount of 12,100.00.":::

1. Select **Close**.
1. Select a record that has an invoice amount of **6,050.00**.
1. Select **Voucher**.

    :::image type="content" source="../media/Annotation-2019-05-20-163156.png" alt-text="Screenshot of financial entries for the record that has an invoice amount of 6,050.00.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
