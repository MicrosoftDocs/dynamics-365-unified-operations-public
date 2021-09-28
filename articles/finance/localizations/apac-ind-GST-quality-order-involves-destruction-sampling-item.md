---
# required metadata

title: Quality orders that involve destruction of the sampling item
description: This topic provides information about quality orders that involve destroyed sample items.
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

# Quality orders that involve destruction of the sampling item

[!include [banner](../includes/banner.md)]

## Purchase order page

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Create a purchase order.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.

    What you see should resemble the following example:

    - **Taxable value:** 10,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent

2. Select **Close**.
3. Select **Confirm**.

## Post the packing slip

1. On the Action Pane, on the **Receive** tab, in the **Generate** group, select **Product receipt**.
2. In the **Quantity** field, select **Ordered quantity**.
3. In the **Product receipt** field, enter a value.
4. Select **OK**, and then select **Show**.

## Quality order form

1. Select **Results**.
2. Update the **Result quantity** field.
3. Select **Validate**, and then select **Close**.
4. Select **Tax document**.

    > [!NOTE]
    > Tax is calculated for the quantity that was used for the quality check and destroyed.

5. Select **Close**, and then select **Validate**.
6. In the **Validate by** field, select a value.
7. Select **OK**, and close the **Quality orders** page.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
2. Enter the invoice number.
3. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
4. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
6. On the **Overview** tab, select **Voucher**.

![Example.](media/Annotation-2019-05-16-113025.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
