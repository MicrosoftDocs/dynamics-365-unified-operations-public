---
# required metadata

title: Export services that have zero-rated tax
description: This topic explains how to export services that have zero-rated tax.
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

# Export services that have zero-rated tax

[!include [banner](../includes/banner.md)]

Complete the procedures in this topic to export services that have zero-rated tax.

1. Go to **General journal** \> **Journals** \> **Invoices** \> **General journal**.
2. Create a journal.
3. Select **Lines**.
4. Create a sale of services for a foreign customer.
5. Save the record.
6. Select **Tax information**.
7. On the **GST** FastTab, in the **SAC** field, select a value.
8. Select the **Customer tax information** FastTab.
9. Select **OK**.

## Validate the tax details

1. Select **Tax document**.

    **Example**

    - **Taxable value:** 10,000.00
    - **IGST:** 0.00 percent

2. Select **Close**.
3. Select **Post** \> **Post**.
4. Close the message that you receive.
5. Select **Inquiries** \> **Voucher**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
