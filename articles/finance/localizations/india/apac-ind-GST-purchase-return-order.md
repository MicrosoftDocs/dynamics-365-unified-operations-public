---
title: Purchase return orders
description: Learn about return orders on purchases, including step-by-step processes for validating tax details and posting purchase invoices.
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

# Purchase return orders

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. Create a purchase order.
1. In the **Purchase type** field, select **Returned order**.
1. In the **RMA number** field, enter a value.
1. Select **OK**.
1. Create purchase order lines that have a negative quantity, and then save the record.
1. Select **Tax information**.
1. Select the **GST** FastTab.
1. Select the **Vendor tax information** FastTab.
1. Select **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
1. Select **Close**, and then select **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Enter the invoice number.
1. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
1. On the **Overview** tab, select **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-16-113209.png" alt-text="Screenshot of the purchase return order voucher.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
