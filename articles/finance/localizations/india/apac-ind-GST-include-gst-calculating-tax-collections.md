---
title: Include GST when calculating tax collections
description: Learn how to include Goods and Services Tax (GST) when you calculate tax collections, including processes for setting up GST requirements and creating sales orders.
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

# Include GST when calculating tax collections

[!include [banner](../../includes/banner.md)]

## Set up GST requirements

1. Go to **Tax** > **Indirect Tax** > **Withholding tax** > **Withholding tax groups**.
1. Select a withholding tax group.
1. On the **General** FastTab, in the **Include GST tax components for TDS or TCS calculation** field, select the required Goods and Services Tax (GST) components.
1. Select **Close**.

## Create a sales order

1. Go to **Accounts receivable** > **Sales orders** > **All sales orders**.
1. Create a sales order.
1. Select **OK**.

### Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document** to review the calculated taxes.

    Here's an example of what you should see:

    - **Taxable value:** 10,000.00
    - **IGST:** 20 percent

1. Select **Close**.
1. Select **Product and supply** > **Withholding tax**.
1. Select **Close**.

### Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. Select **OK**.
1. Select **OK**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. On the **Overview** tab, select **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-21-134958.png" alt-text="Screenshot of the example voucher result.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
