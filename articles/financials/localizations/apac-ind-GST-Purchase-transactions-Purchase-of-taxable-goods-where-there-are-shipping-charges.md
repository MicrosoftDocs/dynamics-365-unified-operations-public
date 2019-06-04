---
# required metadata

title: Purchase of taxable goods where there are shipping charges
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

# Purchase of taxable goods where there are shipping charges

1. Click **Accounts payable > Purchase orders > All purchase orders**.
2. Create a purchase order for a taxable item.
3. On **Purchase order lines** FastTab, click **Financials > Maintain charges**.
4. Select the charges code.
5. In the **Charges value** field, enter a value.
6. Select the **Assessable value** check box.
7. Save the record
8. Click Close.
Note: Freight charges are added to the assessable value.

### Validate the tax details

9. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document**.

10. On the **Tax details** FastTab, review the tax calculation.

    Example:

- Line amount: 10,000.00
- CGST: 10 percent
- SGST: 10 percent
- CESS: 1 percent

11. Click **Close**.
12. Click **Confirm**.

### Post the purchase invoice

13. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
14. In the **Default quantity for lines** field, select **Ordered quantity**.
15. Enter the invoice number.
16. On the Action Pane, click **Post > Post**.
17. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**. Then, on the **Overview** tab, click **Voucher**.

![](media/Annotation-2019-05-16-102702.png)



