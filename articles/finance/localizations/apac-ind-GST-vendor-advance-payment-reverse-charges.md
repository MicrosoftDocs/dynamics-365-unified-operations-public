---
# required metadata

title: Vendor advance payments where there are reverse charges
description: This topic explains how to create vendor advance payments that have reverse charges.
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

# Vendor advance payments where there are reverse charges

[!include [banner](../includes/banner.md)]

1. Go to **Accounts payable** \> **Payments** \> **Vendor Payment journal**.
2. Create a record.
3. In the **Name** field, select a value.
4. Select **Lines**.
5. Create a vendor advance payment journal, and then save the record.
6. Select **Tax information**.
7. On the **GST** FastTab, in the **HSN code** field, select a value.
8. Select the **Vendor tax information** FastTab.
9. Select **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.

    What you see should resemble the following example:

    - **CGST:** 10 percent
    - **SGST:** 10 percent
    - **CESS:** 1 percent
    - **Reverse charge percentage:** 70 percent for all the three components

2. Select **Close**.
3. Select **Post** \> **Post**.
4. Close the message that you receive.

## Update the transaction ID

1. Select **Functions** \> **GST transaction ID**.
2. In the **Date** field, enter a value.
3. In the **Text** field, enter a value.
4. Select **Close**.

## Validate the financial entries

To validate the financial entries, select **Inquiries** \> **Voucher**.

![Example.](media/Annotation-2019-05-16-113421.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
