---
# required metadata

title: Sales where prices include and exclude tax
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

# Sales where prices include and exclude tax

### Sales order form

1. Click **Accounts receivable > Sales orders > All sales orders**.
2. Create a sales order for taxable goods.
3. Add two sales order lines:

- For order line 1, clear the **Prices include sales tax** check box.
- For order line 2, select the **Prices include sales tax** check box.

4. Save the records.
5. Select order line 1.
6. Click **Tax information**
7. Click the **GST** tab
8. Click the **Customer tax information** tab
9. Click OK.
10. Repeat steps 5 through 9 for order line 2.
11. On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document**.

Example:

Order line 1:

- Taxable amount: 10,000
- CGST: 10 percent
- SGST: 10 percent
- CESS: 1 percent

Order line 2:

- Taxable amount: 5,000
- CGST: 10 percent
- SGST: 10 percent
- CESS: 1 percent
- Price inclusive

12. Click **Close**.

### Post the invoice

13. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
14. In the **Quantity** field, select **All**.
15. Click OK.
16. Click Yes to acknowledge the warning message.

### Validate the voucher

17. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
18. Click **Voucher**.

![](media/Annotation-2019-05-20-153808.png)



