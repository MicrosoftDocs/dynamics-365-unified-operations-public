---
# required metadata

title: Create a debit note against a purchase invoice
description: This topic explains how to create a debit note against a purchase order invoice.
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

# Create a debit note against a purchase invoice

[!include [banner](../includes/banner.md)]

1. Go to **General ledger** \> **Journals** \> **General journal**.
2. Create a journal, and name it.
3. Select **Lines**.
4. In the **Account type** field, select **Vendor**. Then, in the **Account** field, select a value.
5. In the **Credit** field, enter a value.
6. In the **Offset account type** field, select **Ledger**. Then, in the **Offset account** field, select a value.
7. On the **General** tab, in the **Original purchase invoice** section, in the **Original invoice number** field, select a value.
8. Verify that the **Original invoice date** field is automatically set, based on the original invoice.

    > [!NOTE]
    > You can post a revised debit note by selecting **Revised** in the **Invoice type** field and then adding a reference to the original debit note.

9. Select **Tax information**.
10. On the **GST** FastTab, in the **HSN code** field, select a value.
11. Select the **Vendor tax information** FastTab.
12. Select **OK**.

## Validate the tax details

1. Select **Tax document**.
2. Select **Close**.
3. Select **Post** \> **Post**.
4. Close the message that you receive.

### Validate the financial entries

To validate the financial entries, select **Inquiries** \> **Voucher**.

![Example.](media/Annotation-2019-05-16-110919.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
