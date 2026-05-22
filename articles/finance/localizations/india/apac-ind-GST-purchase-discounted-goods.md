---
title: Purchases of discounted goods 
description: Learn about the purchase of goods where there is a discount, including processes for validating tax details and posting purchase invoices.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 04/30/2026
ms.custom:
ms.reviewer: johnmichalak  
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Purchases of discounted goods 

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Create a purchase order for a taxable item.
1. In the **Discount percent** field, enter a value, and then save the record.

  :::image type="content" source="../media/Annotation-2019-05-15-175044.png" alt-text="Screenshot of the All purchase orders page.":::

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
1. Verify that the tax that is calculated considers the discount.
1. Select **Close**, and then select **Confirm**.


## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Enter the invoice number.
1. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
1. On the **Overview** tab, select **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-15-174500.png" alt-text="Screenshot of an example voucher.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
