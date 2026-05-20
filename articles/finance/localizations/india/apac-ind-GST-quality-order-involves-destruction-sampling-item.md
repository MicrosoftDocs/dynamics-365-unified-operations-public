---
title: Quality orders that involve destruction of the sampling item
description: Learn about quality orders that involve destroyed sample items, including step-by-step processes for validating tax details and posting packing slips.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 04/30/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak  
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Quality orders that involve destruction of the sampling item

[!include [banner](../../includes/banner.md)]

## Purchase order page

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Create a purchase order.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.

    What you see should resemble the following example:

    - **Taxable value:** 10,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent

1. Select **Close**.
1. Select **Confirm**.

## Post the packing slip

1. On the Action Pane, on the **Receive** tab, in the **Generate** group, select **Product receipt**.
1. In the **Quantity** field, select **Ordered quantity**.
1. In the **Product receipt** field, enter a value.
1. Select **OK**, and then select **Show**.

## Quality order form

1. Select **Results**.
1. Update the **Result quantity** field.
1. Select **Validate**, and then select **Close**.
1. Select **Tax document**.

    > [!NOTE]
    > Tax is calculated for the quantity that was used for the quality check and destroyed.

1. Select **Close**, and then select **Validate**.
1. In the **Validate by** field, select a value.
1. Select **OK**, and close the **Quality orders** page.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. Enter the invoice number.
1. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
1. On the **Overview** tab, select **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-16-113025.png" alt-text="Screenshot of the example annotation.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
