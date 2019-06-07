---
# required metadata

title: Purchase of non-GST goods
description:  This topic provides information about the purchase of non-GST goods.
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

# Purchase of non-GST goods

1. Click **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Create a purchase order, and the define value-added tax (VAT) tax groups for the record.
3. Save the record.
4. Click **Tax information**, and in the **Tax Information** field, select the Tax Identification Number (TIN).
5. On the **VAT** tab, in the **Non recoverable pct.** field, enter **100.00**.

![](media/Annotation-2019-05-16-095850.png)

6. Click **OK**.
7. On the **Line details** FastTab, on the **Setup** tab, select values in the **Item sales tax group** and **Sales tax groups** fields.

## Validate the tax details

1. On the **Action** Pane, on the **Purchase** tab, in the **Tax** group, click **Sales tax**.

  > [!NOTE]
  >The **Tax document button** isn’t enabled.

2. Verify that VAT is calculated.
3. Click **Close**, and then click **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Default quantity for lines** field, select **Ordered quantity**
3. Enter the invoice number.
4. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, click **Post** \> **Post**.
5. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**. 
6. On the **Overview** tab, click **Voucher**.

![](media/Annotation-2019-05-16-095645.png)



