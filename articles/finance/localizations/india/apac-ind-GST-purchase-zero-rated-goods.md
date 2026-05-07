---
title: Purchase of zero-rated goods
description: Learn about the purchase of zero-rated goods, including step-by-step processes for validating tax details and posting purchase orders.
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

# Purchase of zero-rated goods

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Create a purchase order for a zero-rated item, and save the record.
1. Select **Tax information**.
1. Select the **GST** FastTab.
1. Select **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
1. Verify that the **Tax computed** field is set to **0.00**.
1. Select **Close**, and then select **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Enter the invoice number.
1. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. On the **Overview** tab, select **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-16-095042.png" alt-text="Screenshot of the voucher example.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
