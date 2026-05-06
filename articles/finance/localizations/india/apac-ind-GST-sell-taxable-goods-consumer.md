---
title: Sales of taxable goods to consumers
description: Learn about the sale of taxable goods to a consumer, including step-by-step processes for posting invoices and validating vouchers.
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

# Sales of taxable goods to consumers

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts receivable** \> **Sales orders** \> **All sales orders**.
1. Create a sales order for a taxable item, and save the record.
1. Select **Tax information**.

    :::image type="content" source="../media/Capture.PNG" alt-text="Screenshot of the Tax information dialog box.":::

1. Select the **GST** FastTab.

    :::image type="content" source="../media/Capture02.PNG" alt-text="Screenshot of the GST FastTab.":::

1. Select the **Customer tax information** FastTab.

    :::image type="content" source="../media/Capture05.PNG" alt-text="Screenshot of the Customer tax information FastTab.":::

    > [!NOTE]
    > The **Tax information** field is blank. Therefore, the dealer is an unregistered dealer.

1. Select **OK**.
1. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document** to review the calculated taxes.

    What you see might resemble the following example:

    - **Taxable value:** 40,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent

    :::image type="content" source="../media/Capture04_upd.png" alt-text="Screenshot of the Tax document page.":::

1. Select **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Quantity** field, select **Packing slip**.
1. Select the **Print invoice** check box, and then select **OK**.
1. Select **Yes** to acknowledge the warning message that you receive.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. Select **Voucher**.

The following illustration shows the financial entries for both the intrastate transactions and the interstate transactions.

:::image type="content" source="../media/Annotation-2019-05-20-100324.png" alt-text="Screenshot of financial entries for intrastate and interstate transactions.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
