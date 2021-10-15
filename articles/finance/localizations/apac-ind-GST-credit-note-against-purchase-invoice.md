---
# required metadata

title: Create a credit note against a purchase invoice
description: This topic explains how to create a credit note against a purchase order invoice.
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

# Create a credit note against a purchase invoice

[!include [banner](../includes/banner.md)]

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Create a purchase order.
3. On the Action Pane, on the **Purchase** tab, select **Create credit note**.
4. Select the invoice to issue a credit note against, and then select **OK**.
5. Verify that the **Original invoice number** and **Original invoice date** fields are automatically set on the order line.
6. Select **Tax information**.
7. Select the **GST** FastTab.
8. Select the **Vendor tax information** FastTab.
9. Select **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
2. Select **Close**, and then select **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. In the **Default quantity for lines** field, select **Ordered quantity**.
3. Enter the invoice number.
4. On the **Lines** FastTab, verify that the **Invoice type** field is set to **Original**.

    > [!NOTE]
    > You can post a revised credit note by selecting **Revised** in the **Invoice type** field and then adding a reference to the original credit note.

5. On the Action Pane, select **Post** \> **Post**.
6. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
7. On the **Overview** tab, select **Voucher**.

![Example.](media/Annotation-2019-05-16-110655.png)

> [!NOTE]
> The general journal also lets you create a purchase credit note that has details of the original invoice.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
