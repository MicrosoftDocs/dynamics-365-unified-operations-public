---
# required metadata

title: Import of services where there is GST
description:  This topic includes information about Indis GST Whitepaper in Microsoft Dynamics 365 for Finance and Operations.
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
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Import of services where there is GST

1. Click **Accounts payable > Invoices > Invoice journal**.
2. Create a journal.
3. Click **Lines**.
4. Create a purchase of services for a foreign vendor
5. Save the record.
6. Click **Tax information**
7. On the **GST** tab, in the **SAC** field, select a value
8. Click the **Vendor tax information** tab
9. Click OK.

### Validate the tax details

10. Click **Tax document**.

Example:

- Taxable value: 20,000.00
- IGST: 20 percent
- Normal exchange rate: 1 USD = 60 INR

11. Click Close.
12. Click **Post > Post**.
13. Close the message.
14. Click **Inquiries > Voucher**

![](media/Annotation-2019-05-21-104142.png)
