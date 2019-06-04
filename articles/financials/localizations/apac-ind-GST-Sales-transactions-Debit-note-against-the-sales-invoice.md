---
# required metadata

title: Debit note against the sales invoice
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

# Debit note against the sales invoice

1. Click **General ledger > Journals > General journal**.
2. Create a journal, and define a journal name.
3. Click **Lines**
4. In the **Account type** field, select **Customer**.
5. In the **Account** field, select a value.
6. In the **Debit** field, enter a value.
7. In the **Offset account type** field, select **Ledger**.
8. In the **Offset account** field, select a value.
9. Click **Tax information**
10. On the **GST** tab, in the **HSN code** field, select a value
11. Click the **Customer tax information** tab
12. Click **Tax Document**
13. In **Header -> Tax document**, in **Transaction type** field, select **revised**
14. Select **Original transaction id** field and **Original transaction date** field
15. Click **OK**.

### Validate the tax details

16. Click **Tax document**
17. Click Close.
18. Click **Post > Post**.
19. Close the message

### Validate the financial entries

20. Click **Inquiries > Voucher**

![](media/Annotation-2019-05-20-161336.png)



