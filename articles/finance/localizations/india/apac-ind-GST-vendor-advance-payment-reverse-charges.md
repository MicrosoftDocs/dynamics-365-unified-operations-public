---
title: Vendor advance payments where there are reverse charges
description: Learn how to create vendor advance payments that have reverse charges, including a step-by-step process for validating tax details.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Vendor advance payments where there are reverse charges

[!include [banner](../../includes/banner.md)]

1. Go to **Accounts payable** \> **Payments** \> **Vendor Payment journal**.
1. Create a record.
1. In the **Name** field, select a value.
1. Select **Lines**.
1. Create a vendor advance payment journal, and then save the record.
1. Select **Tax information**.
1. On the **GST** FastTab, in the **HSN code** field, select a value.
1. Select the **Vendor tax information** FastTab.
1. Select **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.

    What you see should resemble the following example:

    - **CGST:** 10 percent
    - **SGST:** 10 percent
    - **CESS:** 1 percent
    - **Reverse charge percentage:** 70 percent for all the three components

1. Select **Close**.
1. Select **Post** \> **Post**.
1. Close the message that you receive.

## Update the transaction ID

1. Select **Functions** \> **GST transaction ID**.
1. In the **Date** field, enter a value.
1. In the **Text** field, enter a value.
1. Select **Close**.

## Validate the financial entries

To validate the financial entries, select **Inquiries** \> **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-16-113421.png" alt-text="Screenshot of the financial entries voucher results.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
