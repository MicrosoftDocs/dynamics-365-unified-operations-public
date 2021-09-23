---
# required metadata

title: Export goods that have zero-rated tax
description: This topic explains how to export goods that have zero-rated tax.
author: EricWangChen
ms.date: 06/04/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Export goods that have zero-rated tax

[!include [banner](../includes/banner.md)]

Complete the procedures in this topic to export goods that have zero-rated tax.

## Create a sales order

1. Go to **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create an export order for a taxable item, and save the record.
3. Select **Tax information**.
4. On the **GST** tab, select the **Customer tax information** tab.
5. Select **OK**.
6. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document**.
7. Select **Close**.

## Post the invoice

1. On the **Sales order** page, on the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. In the **Quantity** field, select **All**.
3. Select **OK**.
4. You receive a warning message. Select **Yes** to acknowledge it.

## Validate the sales order voucher

1. On the **Sales order** page, on the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
2. Select **Voucher**.

## Post the export order

1. Go to **Accounts receivable** \> **Orders** \> **Customs export order**.
2. Create an export order for the posted sales order.
3. Select **Shipping bill**.
4. In the **Shipping bill Number** field, enter a value.
5. Select **OK**.

## Validate the shipping bill voucher

1. Select **Inquiries** \> **Shipping bill**.
2. Select **Voucher**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
