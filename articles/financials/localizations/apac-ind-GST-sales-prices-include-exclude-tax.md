---
# required metadata

title: Sales where prices include and exclude tax
description:  This topic provides information about sales that include or exclude sales tax.
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

# Sales where prices include and exclude tax

## Createa sales order 
1. Click **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create a sales order for taxable goods and add two sales order lines:

  - For order line 1, clear the **Prices include sales tax** check box.
  - For order line 2, select the **Prices include sales tax** check box.

3. Save the records.
4. Select order line one, and then click **Tax information**.
5. Click the **GST** tab
6. Click the **Customer tax information** tab and then click **OK**.
8. Repeat steps 4 through 6 for order line 2.
9. On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document**. For example, you might see something similar to the following:

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

10. Click **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Quantity** field, select **All**.
3. Click **OK** and then click **Yes** to acknowledge the warning message.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
2. Click **Voucher**.

![](media/Annotation-2019-05-20-153808.png)



