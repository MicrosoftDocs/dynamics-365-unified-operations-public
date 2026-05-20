---
title: Include GST when calculating tax deductions
description: Learn how to include Goods and Services Tax (GST) on a calculated tax deduction, including processes for creating purchase orders and validating tax details.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Include GST when calculating tax deductions

[!include [banner](../../includes/banner.md)]

## Set up GST requirements

1. Go to **Tax** > **Indirect Tax** > **Withholding tax** > **Withholding tax groups**.
1. Select a withholding tax group.
1. On the **General** FastTab, in the **Include GST tax components for TDS or TCS calculation** field, select the required Goods and Services Tax (GST) components.
1. Select **Close**.

## Create a purchase order

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. Create a purchase order.
1. Select **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document** to review the calculated taxes.

    Here's an example of what you should see:

    - **Taxable value:** 10,000.00
    - **IGST:** 20 percent

1. Select **Close**.
1. Select **Withholding tax**.
1. Select **Close**.
1. Select **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Enter the invoice number.
1. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. On the **Overview** tab, select **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-21-134817.png" alt-text="Screenshot of an example annotation.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
