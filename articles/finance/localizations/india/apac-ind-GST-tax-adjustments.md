---
title: Tax amount adjustment
description: Learn how to adjust tax amounts on purchase and sales orders during invoicing, including a process on validating tax details and resetting adjustments.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.custom: 
audience: Application User 
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Tax amount adjustment

[!include [banner](../../includes/banner.md)]

1. Go to **General ledger** > **Journals** > **General journal**.
1. Create a journal.
1. Select **Lines**.
1. In the **Account type** field, select **Customer**. Then, in the **Account** field, select a value.
1. In the **Debit** field, enter a value.
1. In the **Offset account type** field, select **Ledger**. Then, in the **Offset account** field, select a value.
1. Select **Tax information**.
1. On the **GST** tab, in the **HSN code** field, select a value.
1. Select the **Customer tax information** tab, and then select **OK**.

## Validate the tax details and reset the adjustment

1. Select **Tax document**.
1. On the **Adjustment** tab, in the **Tax amount (Adjusted)** field, change the value to override the tax amount that the system calculated.
1. Select **Apply adjustment** to apply the new tax amount.
1. On the **Tax details** tab, select **Recalculate** to reset the taxes to the amounts that were originally calculated.

## Adjust the tax applicability from interstate to intrastate

1. Select the **GST** node.
1. Select **Tax applicability** to override the tax applicability that the system determined.
1. Clear the **IGST** check box, and select the **CGST** and **SGST** check boxes.
1. Select **OK**.
1. Select **Apply adjustment** to apply your changes.

    > [!NOTE]
    > To reset the tax applicability to its original value, select **Recalculate**.

1. Select **Post** \> **Post**.
1. Select **Inquiries** \> **Voucher**.

    :::image type="content" source="../media/Annotation-2019-05-21-142658.png" alt-text="Screenshot of the voucher example.":::

> [!NOTE]
> Tax adjustment functionality is available only for purchase orders and sales orders that are at the invoicing stage.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
