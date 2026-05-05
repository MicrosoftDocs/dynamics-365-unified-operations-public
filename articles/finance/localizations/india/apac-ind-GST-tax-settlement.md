---
title: Rule-based tax settlement
description: Learn how to set up and work with rule-based tax settlements, including a step-by-step process for setting up rule-based tax settlements.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 05/01/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
audience: Application User 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Rule-based tax settlement

[!include [banner](../../includes/banner.md)]

## Set up rule-based tax settlement

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Settle and post sales tax**.
1. Enter the appropriate values, and then select **OK**.

:::image type="content" source="../media/Capture2019052109_upd.png" alt-text="Screenshot of the Sales tax settlement including corrections dialog box.":::

## Validate tax settlement voucher entries

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax settlement periods**.
1. Select the settlement period, and then select **Sales tax payments**.
1. Verify that the settlement for the selected registration for the period is successfully posted.
1. Select **Print report**.

:::image type="content" source="../media/Capture2019052110_upd.png" alt-text="Screenshot of the Sales tax payments report.":::

## GST authority payment

1. Go to **Accounts payable** \> **Payments** \> **Payment journal**.
1. Create a journal.
1. Select **Lines**.
1. Create a journal voucher for the authority account.
1. Select **Settle transactions**.
1. Select the appropriate transaction, and then select **Post** \> **Post**.
1. Select **Inquiries** \> **Voucher**.

## Update challan information

To update challan information, select **Functions** \> **Challan information**.

## Manually adjust a tax settlement

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Settle and post sales tax**.
1. Enter the appropriate values.
1. Select **Tax adjustment**.

## Exclude transactions from the settlement

1. Expand the **GST** node.
1. Select the **CGST** node, and then select **Transaction**.
1. Cancel the selection of the transaction that should be excluded from the settlement.
1. Select **Update**.

> [!NOTE] 
> When the tax set-off rule is recalculated, the components are adjusted accordingly.

## Partial settlement of the transactions

1. Select the **SGST** node, and then select **Transaction**.
1. Select the transaction, and then update the **Recoverable amount to settle** field.
1. Select **Update**.

    > [!NOTE]
    > - When the tax set-off rule is recalculated, the components are adjusted accordingly.
    > - Excess recoverable, unsettled transactions, and partially settled transactions should be part of the next settlement period.

1. Select **Close**.
1. Select the **Update** check box.
1. Select **OK**, and close the report.

## Validate the tax settlement voucher entries

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax settlement periods**.
1. Select the settlement period, and then select **Sales tax payments**.
1. Verify that the settlement for the selected registration for the period is successfully posted.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
