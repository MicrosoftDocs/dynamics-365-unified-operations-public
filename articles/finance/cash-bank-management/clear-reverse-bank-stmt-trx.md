---
title: Clear reversal bank statement transactions in advanced bank reconciliation
description: Learn about how to clear bank statement transactions in advanced bank reconciliation, including prerequisites and a process for clearing reversal bank transactions.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 01/18/2024
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2024-01-29
ms.search.form: 
ms.dyn365.ops.version: 
---

# Clear reversal bank statement transactions in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article explains how to clear reversal bank statement transactions in advanced bank reconciliation. 

In some cases, bank statement transaction reversals aren't recorded on the company side. Users can clear reversal bank statement transactions in advanced bank reconciliation without matching them to any company transaction.

## Prerequisites

- Import a bank statement.

## Clear reversal bank statement transactions on the reconciliation worksheet

To manually clear reversal bank statement transactions on the reconciliation worksheet, follow these steps.

1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. On the **Unmatched transactions** tab, select the bank statement transactions to match. The total amount of the selected company transactions must be 0 (zero).
1. Select **Match**.

## Clear reversal bank statement transactions by using matching rules

To use matching rules to automatically clear reversal bank statement transactions, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **Matching rule code** and **Name** fields.
1. In the **Action** field, select **Clear reversal statement lines**.
1. On the **Step 1: Find reversal statement lines** FastTab, define the criteria.

    > [!NOTE]
    > For this step, the **Reversal** field on the bank statement line must be set to **Yes**.

1. On the **Step 2: Find original statement lines** FastTab, define the criteria. The **Document number** and **Payment reference** fields are available. The value of these fields must be the same on the reversal and original statement lines.
1. Optional: On the **Step 3: Find bank transactions** FastTab, define the criteria. You can add selection criteria to match company transactions to bank statement lines.
1. Select **Save** and then **Activate**.
1. Optional: You can include the matching rule in matching rule sets.
1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either the matching rule that you defined or a matching rule set that contains that matching rule.
1. Select **OK** to run the automatic matching.
