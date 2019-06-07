---
# required metadata

title: Tax amount adjustment
description:  This topic provides information about adjusting tax amounts on purchase and sales orders during invoicing.
manager: RichardLuan
ms.date: 06/05/2019
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

# Tax amount adjustment

1. Click **General ledger** \> **Journals** \> **General journal** and create a new journal.
2. Click **Lines**.
3. In the **Account type** field, select **Customer**, and in the **Account** field, select a value.
4. In the **Debit** field, enter a value.
5. In the **Offset account type** field, select **Ledger**, and in the **Offset account** field, select a value.
6. Click **Tax information**, and on the **GST** tab, in the **HSN code** field, select a value.
7. Click the **Customer tax information** tab and then click **OK**.

## Validate the tax details and reset the adjustment

1. Click **Tax document**
2. On the **Adjustment** tab, in the **Tax amount (Adjusted)** field, modify the value to override the tax amount that the system calculated.
3. Click **Apply adjustment** to apply the new tax amount.
4. On the **Tax details** tab, select **Recalculate** to reset the taxes to the amounts that were originally calculated.

## Adjust the tax applicability from interstate to intrastate

1. Select the **GST** node.
2. Click **Tax applicability** to override the tax applicability that the system determined.
3. Clear the **IGST** check box and select the **CGST** and **SGST** check boxes.
4. Click **OK**.
5. Click **Apply adjustment** to apply your changes.

  > [!NOTE]
  > Click Recalculate to reset the tax applicability to its original value.
  
6. Click **Post** \> **Post**
7. Click **Inquiries** \> **Voucher**.

![](media/Annotation-2019-05-21-142658.png)

Note: Tax adjustment functionality is available for purchase orders and sales orders at the invoicing stage
