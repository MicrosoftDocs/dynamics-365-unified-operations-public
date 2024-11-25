---
title: Clear reversal company transactions in advanced bank reconciliation
description: Learn about how to clear transactions in advanced bank reconciliation, including prerequisites and various step-by-step processes.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 01/22/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2024-01-29
ms.search.form:
ms.dyn365.ops.version:   
---

# Clear reversal company transactions in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article explains how to clear reversal company transactions in advanced bank reconciliation. As of Microsoft Dynamics 365 Finance version 10.0.39, the **Modern bank reconciliation** feature provides this functionality. 

There might be payment journals that are reversed in the system, but that don't have any records at the bank. This feature lets users clear reversal company transactions in advanced bank reconciliation without matching them to bank statement transactions.

## Prerequisites

- Turn on the **Modern bank reconciliation** feature in the **Feature management** workspace.
- Import a bank statement.

## Clear reversal company transactions on the reconciliation worksheet

To manually clear reversal company transactions on the reconciliation worksheet, follow these steps.

1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. On the **Unmatched transactions** tab, select the company transactions to match. The total amount of the selected company transactions must be 0 (zero).
1. Select **Match**.

## Clear reversal company transactions by using matching rules

To use matching rules to automatically clear reversal company transactions, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **matching rule code** and **Name** fields.
1. In the **Action** field, select **Clear reversal company transaction**.
1. On the **Step 1: Find reversal company transactions** FastTab, define the criteria.
1. On the **Step 2: Find original company transactions** FastTab, define the criteria. The following fields are available:

    - **Require manual matching when multiple original company transactions are found** – Select this option to manually review and confirm the correct original company transaction that should be matched. Otherwise, the matching rule matches the first transaction that's found.
    - **Transaction type**, **Payment reference**, and **Document type** – The value of these fields must match the reversal and original company transactions.

1. Select **Save** and then **Activate**.
1. Optional: You can include the matching rule in matching rule sets.
1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either the matching rule that you defined or a matching rule set that contains that matching rule.
1. Select **OK** to run the automatic matching.
