---
# required metadata

title: Create a credit note against the purchase invoice
description:  This topic provides information about creating a credit note against a purchase order invoice.
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

# Credit note against the purchase invoice

1. Click **Accounts payable** \> **Purchase orders** \> **All purchase orders** and create a new purchase order.
2. On the Action Pane, on the **Purchase** tab, click **Create credit note**.
3. Select the invoice to issue a credit note against and then click **OK**.
4. Verify that the **Original invoice number** and **Original invoice date** fields are automatically set on the order line.
5. Click **Tax information**.
6. Click the **GST** tab.
7. Click the **Vendor tax information** tab.
8. Click **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document**.
2. Click **Close**, and then click **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Default quantity for lines** field, select **Ordered quantity**.
3. Enter the invoice number.
4. On the Lines FastTab, verify that the **Invoice type** field is set to **Original**.

  > [!NOTE]
  > You can post a revised credit note by selecting **Revised** in the **Invoice type** field and adding a reference to the original credit note.
  
5. On the Action Pane,  click **Post** \> **Post**.
6. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**. 
7. On the **Overview** tab, click **Voucher**.

![](media/Annotation-2019-05-16-110655.png)

> [!NOTE]
>The general journal also lets you create a purchase credit note that has details of the original invoice.

