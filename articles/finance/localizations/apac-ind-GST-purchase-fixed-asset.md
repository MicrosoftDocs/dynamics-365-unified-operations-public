---
# required metadata

title: Purchases of fixed assets
description: This topic provides information about purchases of fixed assets.
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

# Purchases of fixed assets

[!include [banner](../includes/banner.md)]

1. Go to **General ledger** \> **Journals** \> **General journal**.
2. Create a journal, and name it.
3. Select **Lines**.
4. In the **Account type** field, select **Fixed assets**. Then, in the **Account** field, select a value.
5. In the **Debit** field, enter a value.
6. In the **Offset account type** field, select **Vendor**. Then, in the **Offset account** field, select a value.
7. Save the record.
8. Select **Tax information**.
9. On the **GST** FastTab, in the **HSN code** field, select a value.
10. Select the **Vendor tax information** FastTab.
11. Select **OK**.

## Validate the tax details

1. Select **Tax document**.
2. Select **Close**.
3. Select **Post** \> **Post**.
4. Close the message that you receive.

## Validate the financial entries

To validate the financial entries, select **Inquiries** \> **Voucher**.

![Example.](media/Annotation-2019-05-16-110044.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
