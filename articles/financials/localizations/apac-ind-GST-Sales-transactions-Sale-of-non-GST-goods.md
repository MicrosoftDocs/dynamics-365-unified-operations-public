---
# required metadata

title: Sale of non-GST goods
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

# Sale of non-GST goods

1. Click **Accounts receivable > Sales orders > All sales orders**.
2. Create a sales order, and define **VAT tax groups**.
3. Select the record.
4. Click **Tax information**
5. In the **Tax information** field, select a value that has a **Tax Identification Number** (TIN) associated with it.
6. Click the **GST** tab
7. Click the **Customer tax information** tab.
8. Click **OK**.
9. On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Sales tax**.
10. Click **Close**.

### Post the invoice

11. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
12. In the **Quantity** field, select **All**.
13. Click OK.
14. Click Yes to acknowledge the warning message

### Validate the voucher

15. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
16. Click **Voucher**.

![](media/Annotation-2019-05-20-150809.png)



