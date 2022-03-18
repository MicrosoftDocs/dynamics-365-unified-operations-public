---
# required metadata

title: Purchases of taxable goods that have shipping charges
description: This topic provides information about the purchase of taxable goods that have shipping charges. 
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

# Purchases of taxable goods that have shipping charges

[!include [banner](../includes/banner.md)]

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Create a purchase order for a taxable item.
3. On **Purchase order lines** FastTab, select **Financials** \> **Maintain charges**.
4. Select the charges code, and then, in the **Charges value** field, enter a value.
5. Select the **Assessable value** check box.
6. Save and close the record.

> [!NOTE]
> Freight charges are added to the assessable value.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
2. On the **Tax details** FastTab, review the tax calculation.

    What you see might resemble the following example:

    - **Line amount:** 10,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent
    - **CESS:** 1 percent

3. Select **Close**.
4. Select **Confirm**.

### Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. In the **Default quantity for lines** field, select **Ordered quantity**.
3. Enter the invoice number.
4. On the Action Pane, select **Post** \> **Post**.
5. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
6. On the **Overview** tab, select **Voucher**.

![Example.](media/Annotation-2019-05-16-102702.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
