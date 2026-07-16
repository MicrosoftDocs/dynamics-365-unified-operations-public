---
title: Set up bank reconciliation matching rules
description: Learn how to set up reconciliation matching rules and reconciliation matching rule sets to help with the bank reconciliation process.
author: mukumarm 
ms.author: mukumarm
ms.topic: article
ms.date: 07/02/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: BankReconciliationMatchRule, BankReconciliationMatchRuleSet
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b5073f83-31dc-404f-af42-3fd84a02a7c6
---

# Set up bank reconciliation matching rules

[!include [banner](../includes/banner.md)]

This article explains how to set up reconciliation matching rules and reconciliation matching rule sets to help with the bank reconciliation process. Reconciliation matching rules are a set of criteria that filter bank statement lines and bank document (transaction) lines during the reconciliation process.

Use reconciliation matching rules and reconciliation matching rule sets to help with the bank reconciliation process. A reconciliation matching rule is a set of criteria that filter bank statement lines and Dynamics 365 Finance bank transaction lines during the reconciliation process. Use the **Reconciliation matching rules** page to set up the reconciliation matching rules. You can set up more than one matching rule and then create a reconciliation matching rule set on the **Reconciliation matching rule sets** page.

> [!NOTE]
> Use bank reconciliation matching rules if you reconcile an electronic bank statement by using advance bank reconciliation.

On the **Reconciliation matching rules** page, select which actions and selection criteria to use when the matching rule runs. In the **Actions** field group, select the action that the matching rule performs during the reconciliation process.  

By default, matching rules match to the first bank document (transaction) that meets the matching rule criteria. If multiple bank documents (transactions) meet the rule criteria, turn on the parameter to require manual matching by going to **Cash and bank management > Setup > Cash and bank management parameters > Bank reconciliation > Require manual matching when advanced bank reconciliation matching rules find multiple documents that match on amount**.

To create a bank reconciliation matching rule, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
1. Select **New** and enter a name and description.
1. In the **Actions** field group, choose the action the rule performs.
1. In the **Matching type** field, choose how records are matched.
1. Define the selection criteria on the step FastTabs that appear for your chosen action.
1. Select **Save**.
1. Select **Activate** to activate the reconciliation matching rule.

> [!NOTE]
> **Modern-only actions** require the **Modern bank reconciliation** feature and an imported statement. Payment actions also need default customer or vendor payment journals on the bank account, and **Generate voucher** needs bank transaction types plus the **Bank statement reversal reference** number sequence.

## All actions

| Action | Availability | What it does | Setup steps or key fields |
|---|---|---|---|
| **Match with bank document** | Base | Matches bank statement lines to Finance bank transactions. | **Step 1 – Define the matching rule** Which statements match to which transactions. **Step 2 (optional) – Filter which statement lines the rule runs against**. |
| **Mark new transactions** | Base *(not available when Modern is on)* | Flags statement lines with no matching bank document as new transactions. | **Step 1 – Find statement lines**. **Step 2 – Find finance and operations** if none found, the line is marked new. |
| **Generate customer payment** | Modern | Posts a **Customer payment journal** from a statement line (incoming customer payment). | Worksheet **Generate payment journal**: Payment type = **Customer**, **Customer account**, **Method of payment**, **Accounting date**, **Bank transaction type**, **Dimensions**, **Tags**. **Generate payment** (post only) or **Settle transactions** (also settle invoices). |
| **Generate vendor payment** | Modern | Posts a **vendor payment journal** from a statement line (outgoing vendor payment). | Same **Generate payment journal** flow with Payment type = **Vendor** and **Vendor account**. |
| **Settle customer invoice** | Modern | Generates a customer payment journal and settles the matched open customer or project invoice. | **Action = Settle customer invoice.** **Step 1 – Find statement lines to generate customer payment journals**. **Step 2 – Match open invoices**. **Step 3 – Customer payment journal parameters**: **Default method of payment**, **Default bank transaction type**, **Accounting date**, **Financial dimensions**, and **Apply cash discount**. |
| **Generate voucher** | Modern | Posts nonpayment statement lines (bank **interest, fees**) directly to the general ledger. | **Action = Generate voucher.** **Find statement lines to generate voucher** – posting criteria. **Voucher parameters** – Accounting date, Bank transaction type, **Offset account**, Description, Sales tax group / Item sales tax group (if applicable), Financial dimensions. |
| **Clear reversal statement lines** | Base *(enhanced in Modern)* | Clears offsetting **reversal bank statement lines** caused by a bank error, without matching to a company transaction. | **Step 1 – Find reversal statement lines** - the **Reversal** line = **Yes**. **Step 2 – Find original statement lines** -  the **Document number** and  **Payment reference** must match. **Step 3 optional – Find bank transactions**. |
| **Clear reversal company transaction** | Modern | Clears reversed company payment journals that have no matching record at the bank. | **Step 1 – Find reversal company transactions**. **Step 2 – Find original company transactions** - The **Transaction type**, **Payment reference**, **Document type** must match. There's an option to require manual matching. The selected transactions must net to zero. |

## Set up bank reconciliation matching rule sets

A matching rule set is a group of reconciliation matching rules that run in sequence during the bank reconciliation process. Instead of running each rule one at a time, bundle them into a set so the whole sequence executes in one pass.

To create a matching rule set, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rule sets**.
1. Select **New** and enter a **name** and **description** for the set.
1. Add the **matching rules** to the **set** in the order they should run - the set executes its rules top to bottom.
1. Select **Save**.

## Put the rule set to work

You can run a set in three ways:

| How it runs | Where |
|---|---|
| **As the account default** | On the **Bank account → Reconciliation** FastTab, set it as the **Default matching rule set**. |
| **Automatically on import** | With **Reconcile after import = Yes**, the account's **default matching rule set** runs as soon as a statement is imported. |
| **On demand** | On the **Bank reconciliation worksheet**, select **Run matching rules**, and then choose the rule set (or a single rule). |

For more information about how matching rules are applied during reconciliation, see:

- [Cash application in advanced bank reconciliation](apply-cash-adv-bank-rec.md)
- [Clear reversal company transactions in advanced bank reconciliation](clear-reverse-comp-trans.md)
- [Generate a voucher in advanced bank reconciliation](vouchers-adv-bank-rec.md)
  
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
