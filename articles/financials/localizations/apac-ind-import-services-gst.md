---
# required metadata

title: Import services that have GST
description:  This topic provides information about how to import services that include GST.
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

# Import services that have GST

Complete the procedures in this topic to import services that have GST.

1. Click **Accounts payable** \> **Invoices** \> **Invoice journal**.
2. Create a journal.
3. Click **Lines**.
4. Create a purchase of services for a foreign vendor and then save the record.
5. Click **Tax information**.
6. On the **GST** tab, in the **SAC** field, select a value.
7. Click the **Vendor tax information** tab.
8. Click **OK**.

### Validate the tax details

1. Click **Tax document**.

For example, the tax document might look like this:

- Taxable value: 20,000.00
- IGST: 20 percent
- Normal exchange rate: 1 USD = 60 INR

2. Click **Close**.
3. Click **Post** \> **Post**.
4. Close the message.
5. Click **Inquiries** \> **Voucher**.

![](media/Annotation-2019-05-21-104142.png)
