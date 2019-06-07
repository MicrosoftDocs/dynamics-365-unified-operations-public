---
# required metadata

title: Create a debit note against the purchase invoice
description:  This topic provides information about how to create a debit note against a purchase order invoice.
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

# Debit note against the purchase invoice

1. Click **General ledger** \> **Journals** \> **General journal**.
2. Create a journal, name it, and then click **Lines**.
3. In the **Account type** field, select **Vendor**.
4. In the **Account** field, select a value.
5. In the **Credit** field, enter a value.
6. In the **Offset account type** field, select **Ledger**, and in the **Offset account** field, select a value.
7. On the **General** tab, in the **Original purchase invoice** field group, in the **Original invoice number field**, select a value.
8. Verify that the **Original invoice date** field is automatically set, based on the original invoice.

  > [!NOTE]
  > You can post a revised debit note by selecting **Revised** in the **Invoice type** field and adding a reference to the original debit note.
  
9. Click **Tax information** and on the **GST** tab, in the **HSN code** field, select a value.
10. Click the **Vendor tax information** tab.
11. Click **OK**.

## Validate the tax details

1. Click **Tax document**.
2. Click **Close**.
3. Click **Post** \> **Post**.
4. Close the message.

### Validate the financial entries
To validate the financial entries, click **Inquiries** \> **Voucher**.

![](media/Annotation-2019-05-16-110919.png)



