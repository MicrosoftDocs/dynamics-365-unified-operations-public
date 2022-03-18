---
# required metadata

title: Sales invoices that are split based on delivery addresses
description: This topic provides information about sales invoices that are split based on delivery addresses.
author: EricWangChen
ms.date: 06/04/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Sales invoices that are split based on delivery addresses

[!include [banner](../includes/banner.md)]

1. Go to **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Create a sales order for taxable items.
3. On the **Lines details** FastTab, select the **Address** tab.
4. Save the record.
5. Select order line 1, and then select **Tax information**.
6. Select the **GST** FastTab.
7. Select the **Customer tax information** FastTab.
8. Select **OK**.
9. Select order line 2, and then select **Tax information**.
10. Select the **GST** FastTab.
11. Select the **Customer tax information** FastTab.
12. Select **OK**.
13. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document** to review the calculated taxes.

    What you see might resemble the following example:

    **Order line 1**

    - **Taxable amount:** 10,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent
    - **CESS:** 1 percent

    **Order line 2**

    - **Taxable amount:** 5,000.00
    - **IGST:** 20 percent
    - **CESS:** 1 percent

12. Select **Close**.

## Post the packing slip

1. On the Action Pane, on the **Pick and pack** tab, in the **Generate** group, select **Packing slip**.
2. Select **OK**.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. In the **Quantity** field, select **All**.

    > [!NOTE]
    > The invoice is split based on the delivery addresses.

3. Select **OK**, and then select **Yes** to acknowledge the warning message that you receive.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
2. Select a record that has an invoice amount of **12,100.00**.
3. Select **Voucher**.

    ![Financial entries for the record that has an invoice amount of 12,100.00.](media/Annotation-2019-05-20-163117.png)

4. Select **Close**.
5. Select a record that has an invoice amount of **6,050.00**.
6. Select **Voucher**.

    ![Financial entries for the record that has an invoice amount of 6,050.00.](media/Annotation-2019-05-20-163156.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
