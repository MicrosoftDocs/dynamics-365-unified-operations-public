---
title: Purchases of non-GST goods
description: Learn about the purchase of goods that aren't subject to Goods and Services Tax (GST), including a step-by-step process on validating tax details.
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

# Purchases of non-GST goods

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Create a purchase order, and define value-added tax (VAT) tax groups for the record.
1. Save the record.
1. Select **Tax information**.
1. In the **Tax Information** field, select the Tax Identification Number (TIN).
1. On the **VAT** FastTab, in the **Non recoverable pct.** field, enter **100.00**.

    :::image type="content" source="../media/Annotation-2019-05-16-095850.png" alt-text="Screenshot of the VAT FastTab.":::

1. Select **OK**.
1. On the **Line details** FastTab, on the **Setup** tab, in the **Item sales tax group** and **Sales tax groups** fields, select values.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Sales tax**.

    > [!NOTE]
    > The **Tax document** button isn't available.

1. Verify that VAT is calculated.
1. Select **Close**, and then select **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Enter the invoice number.
1. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. On the **Overview** tab, select **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-16-095645.png" alt-text="Screenshot of an example voucher.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
