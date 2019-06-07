---
# required metadata

title: Sale of taxable goods where there is a reverse charge
description:  This topic provides information about the sale of taxable goods where there is a reverse charge.
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

# Sale of taxable goods where there is a reverse charge

1. Click **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create a sales order for a taxable item.
3. Save the record, and then click **Tax information**.
4. Click the **GST** tab.
5. Click the **Customer tax information** tab, and then click **OK**.
6. On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document** to review the calculated taxes. For example, you might see something similar to the following:

  - Taxable value: 10,000.00
  - CGST: 10 percent
  - SGST: 10 percent
  - Reverse charge percentage: 70 percent

7. Click **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Quantity** field, select **All**.
3. Select the **Print invoice** check box.
4. Click **OK** and then click **Yes** to acknowledge the warning message.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
2. Click **Voucher**.

- Financial entries for both the intrastate and interstate transactions

![](media/Annotation-2019-05-20-144319.png)



