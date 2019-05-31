---
# required metadata

title: Indis GST Whitepaper
description:  This topic includes information about Indis GST Whitepaper in Microsoft Dynamics 365 for Finance and Operations.
author: EricWang
manager: RichardLuan
ms.date: 05/31/2019
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

## Revised advance payment that has tax

1. Click **Accounts receivable > Payments > Payment journal**.
2. Create a record.
3. In the **Name** field, select a value.
4. On the **Setup** tab, select the **Amounts include sales tax** check box.
5. Click **Lines**.
6. Create a customer advance payment journal
7. Save the record
8. Click **Tax information**
9. On the **GST** tab, in the **HSN code** field, select a value
10. Click the **Customer tax information** tab
11. Click OK.
12. On the General tab, in the **Invoice type** field, select **Revised**.
13. In the **Original transaction id** field, select a value.
14. Verify that the Original transaction date field is automatically set, based on the original transaction ID that you selected.

### Validate the tax details

15. Click **Tax document**.

Example:

- IGST: 20 percent

16. Click Close.
17. Click **Post > Post**.
18. Close the message.

### Validate the financial entries

19. Click **Inquiries > Voucher**

![](media/GST-Whitepaper/Annotation-2019-05-21-132745.png)



