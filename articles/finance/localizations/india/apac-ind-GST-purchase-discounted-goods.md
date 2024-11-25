---
title: Purchases of discounted goods 
description: Learn about the purchase of goods where there is a discount, including processes for validating tax details and posting purchase invoices.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 06/04/2019
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
2. Create a purchase order for a taxable item.
3. In the **Discount percent** field, enter a value, and then save the record.

  ![All purchase orders page.](../media/Annotation-2019-05-15-175044.png)

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
2. Verify that the tax that is calculated considers the discount.
3. Select **Close**, and then select **Confirm**.


## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. In the **Default quantity for lines** field, select **Ordered quantity**.
3. Enter the invoice number.
4. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
5. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
6. On the **Overview** tab, select **Voucher**.

![Example.](../media/Annotation-2019-05-15-174500.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
