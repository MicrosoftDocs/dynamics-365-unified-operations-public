---
title: Purchases of fixed assets
description: Learn about purchases of fixed assets, including step-by-step processes for validating tax detials and financial entries.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 04/30/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Purchases of fixed assets

[!include [banner](../../includes/banner.md)]

1. Go to **General ledger** \> **Journals** \> **General journal**.
1. Create a journal, and name it.
1. Select **Lines**.
1. In the **Account type** field, select **Fixed assets**. Then, in the **Account** field, select a value.
1. In the **Debit** field, enter a value.
1. In the **Offset account type** field, select **Vendor**. Then, in the **Offset account** field, select a value.
1. Save the record.
1. Select **Tax information**.
1. On the **GST** FastTab, in the **HSN code** field, select a value.
1. Select the **Vendor tax information** FastTab.
1. Select **OK**.

## Validate the tax details

1. Select **Tax document**.
1. Select **Close**.
1. Select **Post** \> **Post**.
1. Close the message that you receive.

## Validate the financial entries

To validate the financial entries, select **Inquiries** \> **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-16-110044.png" alt-text="Screenshot of the voucher financial entries.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
