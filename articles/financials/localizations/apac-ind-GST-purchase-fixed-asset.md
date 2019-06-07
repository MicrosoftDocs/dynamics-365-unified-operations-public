---
# required metadata

title: Purchase of a fixed asset
description:  This topic provides information about fixed asset purchases.
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

# Purchase of a fixed asset

1. Click **General ledger** \> **Journals** \> **General journal**.
2. Create and name a new journal and then click **Lines**.
3. In the **Account type** field, select **Fixed assets**.
4. In the **Account** field, select a value.
5. In the **Debit** field, enter a value.
6. In the **Offset account type** field, select **Vendor**.
7. In the **Offset account** field, select a value.
8. Save the record.
9. Click **Tax information**, and on the **GST** tab, in the **HSN code** field, select a value.
10. Click the **Vendor tax information** tab.
11. Click OK.

## Validate the tax details

1. Click **Tax document**.
2. Click **Close**.
3. Click **Post** \> **Post**.
4. Close the message.

## Validate the financial entries

To validate the financial entries, click **Inquiries** \> **Voucher**

![](media/Annotation-2019-05-16-110044.png)



