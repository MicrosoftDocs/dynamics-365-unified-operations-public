---
# required metadata

title: Revise a purchase invoice that has taxable goods
description:  This topic provides information about revising a purchase invoice that contains taxable goods.
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

# Revised purchase invoice that has taxable goods

1. Click **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Create a purchase order for a taxable item.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document**.
2. On the **Tax details** FastTab, review the tax calculation. For example, it might look like the following:

  - Line amount: 10,000.00
  - CGST: 10 percent
  - SGST: 10 percent
  - CESS: 1 percent

3. Click **Close**, and then click **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Default quantity for lines** field, select **Ordered quantity**.
3. On the **Lines** FastTab, enter the invoice number.
4. In the **Invoice type** field, select **Revised**.
5. In the **Original invoice number** field, select a value.
6. Verify that the **Original invoice date field** is automatically set, based on the original invoice number that you selected.
7. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, click **Post** \> **Post**.
8. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**. 
9. On the **Overview** tab, click **Voucher**.

![](media/Annotation-2019-05-16-103252.png)



