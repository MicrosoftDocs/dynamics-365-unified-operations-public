---
# required metadata

title: Sale of taxable goods with tax on shipping charges
description:  This topic provides information about selling taxable goods that include tax on the shipping charges. 
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

# Sale of taxable goodswith tax on shipping charges

1. Click **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create a sales order for a taxable item.
3. On the **Lines details** FastTab, on the **Address** tab, in the **Delivery address** field, select a value and then save the record.
4. Click **Tax information**
5. Click the **GST** tab.
6. Click the **Customer tax information** tab.
7. In the **Location** field, select the value that you selected for the delivery address in step three, and then click **OK**.
8. On the **Sales order lines** FastTab, click **Financials** \> **Maintain charges**.
9. Select a charges code, and in the **Charges value** field, enter a value.
10. Save the record.
11. Click **Tax information**.
12. Click the **GST** tab.

> [!NOTE]
> The **SAC** field is automatically set, based on the charges code that you selected. The default setting is defined in the charges code master.

13. Click the **Customer tax information** tab.
14. Click OK, and on the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document** to review the calculated taxes. For example, you might see something similar to the following:

  - Line amount: 10,000.00
  - IGST: 20 percent
  - CESS: 1 percent
  - Miscellaneous charges: 1,000.00
  - IGST: 25 percent
  - CESS: 1 percent

15. Click **Close**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Quantity** field, select **All**.
3. Select the **Print invoice** check box.
4. Click **OK**, and then click **Yes** to acknowledge the warning message.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
2. Click **Voucher**.

![](media/Annotation-2019-05-20-152724.png)



