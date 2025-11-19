---
title: Generate a voucher in advanced bank reconciliation
description: Learn how to generate vouchers in advanced bank reconciliation, including prerequisites and an outline on on generating a voucher on the reonciliation worksheet.
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 02/24/2025
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2024-01-29
ms.search.form: 
ms.dyn365.ops.version:  
---

# Generate a voucher in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article explains how to post vouchers to the general ledger in advanced bank reconciliation using the **Modern bank reconciliation** feature. 

There might be bank statement transactions that aren't related to specific customer or vendor payments. Examples include bank interest income and bank fees. This feature lets users post bank statement transactions of this type directly to the general ledger.

## Prerequisites

- Turn on the **Modern bank reconciliation** feature in the **Feature management** workspace.
- Set up bank transaction types.
- Set up number sequences for the **Bank statement reversal** reference in Cash and bank management parameters.
- Import a bank statement.
- If the **Enable offset account financial dimensions for general ledger voucher posting during bank account reconciliation** feature is enabled, users can define offset financial dimensions for general ledger vouchers posted manually during bank account reconciliation or automatically if a reconciliation rule for voucher generation is created.

## Generate a voucher on the reconciliation worksheet

To manually post bank statement transactions to the general ledger on the reconciliation worksheet, follow these steps.

1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
2. . Open or create a bank reconciliation worksheet.
3. . On the **Unmatched transactions** tab, select the bank statement transactions to post to the general ledger.
4. . Select **Generate voucher**.
5. . In the dialog box that appears, set the following fields:

    - **Accounting date**
    - **Bank transaction type**
    - **Offset account**
    - **Description**
    - **Sales tax group** (if applicable)
    - **Item sales tax group** (if applicable)
    - **Financial dimensions** (if applicable)
    - **Financial tags** (if applicable)

6. Select **OK**.

## Generate a voucher by using matching rules

To use matching rules to automatically post bank statement transactions to the general ledger, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
2. Select **New** to create a matching rule.
3. Set the **Matching rule code** and **Name** fields.
4. In the **Action** field, select **Generate voucher**.
5. On the **Find statement lines to generate voucher** FastTab, define the posting criteria.
6. On the **Voucher parameters** FastTab, set the following fields:

    - **Accounting date**
    - **Bank transaction type**
    - **Offset account**
    - **Description**
    - **Sales tax group** (if applicable)
    - **Item sales tax group** (if applicable)
    - **Financial dimensions** (if applicable)

7. Select **Save** and then **Activate**.
8. Optional: You can include the matching rule in matching rule sets.
9. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
10. Open or create a bank reconciliation worksheet.
11. Select **Run matching rules**.
12. Select either the matching rule that you defined or a matching rule set that contains that matching rule.
13. Select **OK** to run the automatic matching.
 

## Reverse a posted voucher on the reconciliation worksheet

To reverse posted bank statement transactions on the reconciliation worksheet, follow these steps.

1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
2. . Open the bank reconciliation worksheet.
3. . On the **Matched transactions** tab, select the bank statement transactions to reverse.
4. . Select **Reverse**.
5. . In the voucher list, confirm the vouchers that should be reversed.
6. . Confirm the **Accounting date**, **Reason code**, and **Reason comment** values for the reversal.
7. . Select **Reverse**.
