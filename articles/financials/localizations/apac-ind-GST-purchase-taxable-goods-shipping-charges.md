---
# required metadata

title: Purchase of taxable goods with shipping charges
description:  This topic provides information about the purchase of taxable goods that include shipping charges. 
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

# Purchase of taxable goods with shipping charges

1. Click **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Create a purchase order for a taxable item.
3. On **Purchase order lines** FastTab, click **Financials** \> **Maintain charges**.
4. Select the charges code, and in the **Charges value** field, enter a value.
5. Select the **Assessable value** check box.
6. Save and close the record.

> [!NOTE]
> Freight charges are added to the assessable value.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document**.
2. On the **Tax details** FastTab, review the tax calculation. For example, it might look similar to this:

- Line amount: 10,000.00
- CGST: 10 percent
- SGST: 10 percent
- CESS: 1 percent

3. Click **Close**.
4. Click **Confirm**.

### Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Default quantity for lines** field, select **Ordered quantity**.
3. Enter the invoice number.
4. On the Action Pane, click **Post** \> **Post**.
5. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**. 
6. On the **Overview** tab, click **Voucher**.

![](media/Annotation-2019-05-16-102702.png)



