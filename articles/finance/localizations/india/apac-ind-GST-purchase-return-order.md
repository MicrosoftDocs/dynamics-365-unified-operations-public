---
title: Purchase return orders
description: Learn about return orders on purchases, including step-by-step processes for validating tax details and posting purchase invoices.
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

# Purchase return orders

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Create a purchase order.
3. In the **Purchase type** field, select **Returned order**.
4. In the **RMA number** field, enter a value.
5. Select **OK**.
4. Create purchase order lines that have a negative quantity, and then save the record.
5. Select **Tax information**.
6. Select the **GST** FastTab.
7. Select the **Vendor tax information** FastTab.
8. Select **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
2. Select **Close**, and then select **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. In the **Default quantity for lines** field, select **Ordered quantity**.
3. Enter the invoice number.
4. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
5. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
6. On the **Overview** tab, select **Voucher**.

![Example.](../media/Annotation-2019-05-16-113209.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
