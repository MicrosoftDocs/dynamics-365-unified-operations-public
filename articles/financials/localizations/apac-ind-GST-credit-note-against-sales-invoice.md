---
# required metadata

title: Create a credit note against a sales invoice
description: This topic provides information about creating a credit note against a sales invoice.
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

# Credit note against the sales invoice

## Create a sales order

1. Click **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create a sales credit note for a taxable item.
3. In the **Original invoice number** field, select a value.
4. Verify that the **Original invoice date** field is automatically set based on the original invoice number that you selected, and then save the record.
5. Click **Tax information**, and then click the **GST** tab.
6. Click the **Customer tax information** tab
7. Click OK.
8. On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document**. For example, you might see something like the following:

  - Taxable amount: -5,000
  - IGST: 20 percent
  - CESS: 1 percent

9. Click **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Quantity** field, select **All**.
3. On the **Others** tab, verify that the **Invoice type** field is set to **Original**.

> [!NOTE]
> You can post a revised credit note by selecting **Revised** in the **Invoice type** field and adding a reference to the original credit note.

4. Click **OK**, and then click **Yes** to acknowledge the warning message.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
2. Click **Voucher**.

![](media/Annotation-2019-05-20-162812.png)

> [!NOTE]
> You can create a sales credit note through the general ledger and a free text invoice.



