---
title: Reverse a bank reconciliation
description: Learn how to reverse a bank reconciliation and a posted bank statement in Dynamics 365 Finance.
author: mukumarm
ms.author: mukumarm
ms.topic: article
ms.date: 07/02/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
---
# Reverse a bank reconciliation

[!include [banner](../includes/banner.md)]

When you reverse a bank reconciliation, the bank statement and its transactions go back to an **unreconciled** state. You can fix matching mistakes and reconcile again. This process applies to modern bank reconciliation.

## Ordering and dependencies

Reversing bank reconciliation requires following a specific order. To fully reverse a bank reconciliation, follow these steps:

1. Reverse the reconciliation - After reversal, the lines are available on the worksheet for matching and reconciliation.
1. Remove the open reconciliation - and its matched transactions.
1. Reverse the posted bank statement first.
1. Remove the open/imported bank statement.

## 1. Reverse the reconciliation (Advanced bank reconciliation, Modern bank reconciliation)

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
1. Filter to **show reconciled worksheet**.
1. Select the reconciled worksheet. 
1. Select **Reverse reconciliation** > **Yes**. Or, select **Worksheet** to open the worksheet, and then select **Reverse reconciliation**.

The reconciliation is undone and the statement returns to an unreconciled state.

## 2. Reverse the posted bank statement (Advanced bank reconciliation)

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank statements**.
1. Select the statement that has new transactions. For example, bank interest, fees, and charges. 
1. Select **Reverse statement**.
1. Select the vouchers to reverse, and select **Reverse**.

The **Posted** flag is removed and the new transaction vouchers are reversed.

## 3. Reverse a single posted voucher (Modern bank reconciliation)

To reverse an individual general ledger voucher, such as a wrongly posted fee, rather than the whole statement:

1. Open the **Bank reconciliation worksheet**.
1. On the **Matched transactions** tab, select the statement transactions, and then select **Reverse**.
1. Confirm the vouchers and set **Accounting date**, **Reason code**, and **Reason comment**. Select **Reverse**.
