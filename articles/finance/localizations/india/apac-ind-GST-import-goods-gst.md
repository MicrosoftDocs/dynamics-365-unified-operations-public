---
title: Import goods that have GST
description: Learn how to import goods that have Goods and Services Tax (GST), including processes for validating tax details and updating the invoice registration.
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

# Import goods that have GST

[!include [banner](../../includes/banner.md)]

To import goods that have Goods and Services Tax (GST), complete the procedures in this article.

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. Create a purchase order for a foreign vendor account, and save the record.
1. Select **Tax information**.

    :::image type="content" source="../media/Capture2019052101.PNG" alt-text="Screenshot of the Tax information page.":::

1. Select the **GST** FastTab.
1. Select the **Customs** FastTab.

    :::image type="content" source="../media/Capture2019052104.PNG" alt-text="Screenshot of the Customs FastTab.":::

1. Select the **Vendor tax information** FastTab.

    :::image type="content" source="../media/Capture2019052103.PNG" alt-text="Screenshot of the Vendor tax information FastTab.":::

1. Select **OK**.
1. Select **Functions** > **Maintain charges**.
1. In the **Charges code** field, select a charges code.
1. Select the **Assessable value** check box.
1. In the **Charges value** field, enter a value.

    :::image type="content" source="../media/Capture2019052105_upd.png" alt-text="Screenshot of the Maintain charges page.":::

1. Save the record, and then select **Close**.

> [!NOTE]
> The assessable value is calculated as net amount + miscellaneous charges + 1 percent of the landing charges that are defined in **Accounts payable parameters**.

### Validate the tax details

1. On **Purchase orders**, on the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
1. On the **Tax details** FastTab, review the tax calculation.

    Here's an example:

    - **BCD:** 10 percent
    - **LOI:** 100 percent
    - **IGST:** 20 percent
    - **Import exchange rate:** 1 USD = 52 INR

    > [!NOTE]
    > By extending the configuration, you can calculate Integrated Goods and Services Tax (IGST) on Assessable value + Basic Custom Duty (BCD) tax amount.

1. Select **Close**.
1. Select **Confirm**.

### Update the invoice registration

1. On **Purchase orders**, on the Action Pane, on the **Customs** tab, in the **Maintain** group, select **Invoice registration**.
1. In the **Import invoice number** field, select a value.
1. Select **Update**.

### Post the bill of entry

1. On **Purchase orders**, on the Action Pane, on the **Customs** tab, in the **Generate** group, select **Bill of entry**.
1. In the **Import invoice number** field, select a value.
1. In the **Bill of entry number** field, select a value.
1. On the **Lines** tab, in the **Quantity** field, enter a value.
1. Close the message that you receive.
1. Select **Tax document**.
1. Select **Close**.
1. Select **OK**.

### Post the product receipt

1. On **Purchase orders**, on the Action Pane, on the **Receive** tab, in the **Generate** group, select **Product receipt**.
1. In the **Quantity** field, select **Bill of entry quantity**.
1. In the **Product receipt** field, enter the product receipt.
1. Select **OK**.

The following illustration shows an example of a journal entry for an import purchase order that has GST.

:::image type="content" source="../media/Annotation-2019-05-20-165539.png" alt-text="Screenshot of a journal entry for an import purchase order that has GST.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
