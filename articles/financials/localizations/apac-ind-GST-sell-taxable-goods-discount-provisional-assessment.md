---
# required metadata

title: Sale of taxable goods where there is a discount and a provisional assessment
description:  This topic provides information about selling taxable goods with a discount and a provisional assessment.
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

# Sale of taxable goods where there is a discount and a provisional assessment

### Create a sales order

1. Click **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create a sales order for a taxable item.
3. Click **Header view**, and on the **Price and discount** FastTab, in the **Total discount %** field, enter 10.00.
4. Click **Line view**.
5. On the **Lines details** FastTab, on the **Address** tab, in the **Delivery address** field, select a value, and then save the record.
6. Click **Tax information**.
7. Click the **GST** tab.
8. Click the **Customer tax information** tab.
9. Click **OK**.
10. On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document**.
11. Verify that the tax that is calculated considers the discount and then click **Close**.


## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Quantity** field, select **All**.
3. Select the **Print invoice** check box.
4. Select the **Provisional assessment** check box.
5. Click **OK**, and then click **Yes** to acknowledge the warning message.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
2. Click **Voucher**

![](media/Annotation-2019-05-20-151407.png)



