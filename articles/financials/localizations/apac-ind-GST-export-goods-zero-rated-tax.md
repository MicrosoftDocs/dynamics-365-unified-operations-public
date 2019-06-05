---
# required metadata

title: Export goods with zero-rated tax
description:  This topic includes information how to export goods with zero-rated tax.
author: EricWang
manager: RichardLuan
ms.date: 06/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Export goods with zero-rated tax

Complete the procedures in this topic to export goods with zero-rated tax. 

## Sales order form

1. Click **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create an export order for a taxable item and save the record.
3. Click **Tax information**, and on the **GST** tab, select the **Customer tax information** tab.
4. Click **OK**.
5. On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document**
6. Click **Close**.

## Post the invoice

1. On the **Sales order** page, on the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Quantity** field, select **All**.
3. Click OK.
4. Click **Yes** to acknowledge the warning message.

## Validate the voucher

1. On the **Sales order** page, on the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
2. Click **Voucher**.

## Post the export order

1. Click **Accounts receivable** \> **Orders** \> **Customs export order**.
2. Create an export order for the posted sales order.
3. Click **Shipping bill**.
4. In the **Shipping bill Number** field, enter a value and then click **OK**.

## Validate the voucher

1. Click **Inquiries** \> **Shipping bill**.
2. Click **Voucher**.
