---
title: Return orders
description: Learn how to create a return order, including step-by-step processes on navigating the return order page and sales order page.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Return orders

[!include [banner](../../includes/banner.md)]

## Return order page

1. Go to **Sales and marketing** \> **Return orders** \> **All return orders**.
1. Create a return order for a taxable item.
1. On the **Line details** FastTab, in the **Disposition code** field, select **Credit only**.
1. On the Action Pane, on the **Return order** tab, in the **Send** group, select **Return order**.
1. Select **OK**, and then close the page.

## Sales order page

1. Go to **Accounts receivable** \> **Sales orders** \> **All sales orders**.
1. Select the record where the **Order type** field is set to **Returned order**.
1. On the Action Pane, on the **Sales order** tab, in the **Maintain** group, select **Edit**.
1. Select **Tax information**.
1. Select the **GST** tab.
1. Select the **Customer tax information** tab.

    > [!NOTE]
    > The **Tax information** value is automatically set, based on the original sales order that the return order was created against.

1. Select **OK**.
1. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document**.

    You should see something that resembles the following example:

    - **Taxable amount:** 10,000
    - **CGST:** 10 percent
    - **SGST:** 10 percent
    - **CESS:** 1 percent

1. Select **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Quantity** field, select **All**.
1. Select **OK**, and then select **Yes** to acknowledge the warning message that you receive.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. Select **Voucher**.

The following illustration shows the financial entry for the **Credit only**/**Replace and scrap**/**Scrap** disposition code.

:::image type="content" source="../media/Annotation-2019-05-20-163321.png" alt-text="Screenshot of the financial entry for the Credit only/Replace and scrap/Scrap disposition code.":::

The following illustration shows the financial entry for the **Credit**/**Replace and credit** disposition code.

:::image type="content" source="../media/Annotation-2019-05-20-163405.png" alt-text="Screenshot of the financial entry for the Credit/Replace and credit disposition code.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
