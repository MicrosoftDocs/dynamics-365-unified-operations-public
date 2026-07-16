---
title: Advanced bank reconciliation setup process
description: Advanced bank reconciliation allows you to import electronic bank statements and automatically reconcile with bank transactions in Microsoft Dynamics 365 Finance.
author: mukumarm
ms.author: mukumarm
ms.topic: install-set-up-deploy
ms.date: 07/02/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:  BankReconciliationMatchRule, BankReconciliationMatchRuleSet
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: ae071f04-f038-4b17-812d-0a241ed15521
---

# Advanced bank reconciliation setup process

[!include [banner](../includes/banner.md)]

When you use advanced bank reconciliation, you can import electronic bank statements and automatically reconcile them with bank transactions in Microsoft Dynamics 365 Finance. This article explains the setup processes for reconciliation.  

Before you use the advanced bank reconciliation functionality, set up several components. For more information about setting up bank statement import, see [Set up the advanced bank reconciliation import using Electronic reporting](../accounts-payable/import-bai2-er.md). The following sections detail the requirements for the reconciliation process.

## Transaction types

A bank transaction type is a code you define to identify and classify the kinds of transactions that hit a bank account. For example, deposits, withdrawals, fees, interest, or nonsufficient funds (NSF). These types are later grouped and used in bank reconciliation and reporting.

To create a bank transaction type, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Bank transaction types**.
1. Select **New** to add a line.
1. In the **Bank transaction type** field, enter a unique code or identifier, such as DEP, NSF, or FEE.
1. In the **Name** field, enter a description. For example, Deposit or Nonsufficient funds.
1. Repeat for each transaction type you need.
1. Select **Save**.

## Transaction code mapping

Use **transaction codes** as part of the **bank reconciliation matching rules**. Transaction codes help match only the same types of transactions between Finance and your bank statement. To use this type of matching, first define transaction types for bank transactions from Finance, and then map those types to statement transaction codes that your bank uses.

After you define your bank transaction codes, map them to the transaction codes used in your electronic bank statements by using the **Transaction code mapping** page. Complete transaction code mapping separately for each bank account.

To create transaction code mapping, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Transaction code mapping**.
1. Select **New** to add a transaction code mapping.
1. In the **Bank account** field, select the bank account.
1. In the **Mappings** area, select **Add** to create a new mapping between statement mapping code and bank transaction type.

## Matching rules and matching rule sets

Matching rules allow you to define criteria for automatic reconciliation between Finance bank transactions and bank statement transactions. Set up matching rules on the **Reconciliation matching rules** page. For more information, see [Set up bank reconciliation matching rules](set-up-bank-reconciliation-matching-rules.md).

Use matching rule sets to define a group of matching rules that run in sequence during the bank reconciliation process. Configure matching rule sets on the **Reconciliation matching rule sets** page.

## Cash and bank management parameters

The **Cash and bank management parameters** page contains parameters specific to the advanced bank reconciliation process. The **Show statement line amount in debit/credit** parameter changes the view of amounts on the **Bank statement** page. If you select this option, the bank statement transaction amounts appear in separate debit and credit columns. If you don't select it, the bank statement transaction amounts appear in a single amount column with the appropriate sign.

The validation options that you set on the **Cash and bank management parameters** page override the selections set on matching rules. For example, you can't manually or automatically match documents beyond the date difference set on the parameters page. Also, if you select the option to **Validate transaction type mapping**, you must map the transaction types between the Finance bank transaction and bank statement transaction in order to manually or automatically match the transactions.  

You must also configure the necessary number sequences on the **Cash and bank management parameters** page. On the **Number sequences** tab, set number sequence codes for the Download **ID, Statement ID, Reconcile ID, and Bank reconciliation** references.

## Bank account reconciliation options

To enable **Advanced bank reconciliation** for the bank account, follow these steps:

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
1. Select the bank account, and then set **Advanced bank reconciliation** to **Yes**.
1. Configure the options described in the following section.

### General settings

| Field | Description | Effect |
|---|---|---|
| **Advanced bank reconciliation** | Enables modern bank reconciliation for this bank account. | Unlocks electronic statement import, automatic matching, and the rest of the fields on this tab. |
| **Use bank statements as confirmation of electronic payment** | Integrates reconciliation with electronic payment statuses. | Creates a bank document when a payment is set to **Sent**, and updates it from **Sent** to **Received** after it's matched, reconciled, and posted. |
| **Allowed penny difference** | Sets the maximum amount variance tolerated when matching a statement line to a Finance transaction. | Amounts differing by no more than this value still match. `0.00` = amounts must match exactly. |
| **Statement format** | Selects the import format or configuration used to bring in this account's electronic statements. | Determines how statement files are parsed. For example, BAI2, MT940, or CAMT.053 (via Electronic reporting), or Excel/CSV (via Data management). |
| **Bank name in statements** | The identifier your bank uses for this account on its electronic statements. | Used to pick this account's transactions when a single statement file contains multiple bank accounts. |
| **Time zone preference** | The time zone applied when interpreting transaction date and time stamps on imported statements. | Aligns statement timestamps to the correct local time. **Auto** uses the system or user default. |
| **Reverse debit credit mark** | Flips the debit or credit sign of imported statement amounts. | Use when the bank reports transactions from its perspective, opposite of your ledger, so debits and credits align during matching. |
| **Clear bridged transactions during reconciliation** | Controls whether bridged or pending transactions are cleared as part of reconciliation. | When **Yes**, the system clears bridged or pending entries during reconciliation instead of in a separate step. |

### Automation

| Field | Description | Effect |
|---|---|---|
| **Reconcile after import** | Automates reconciliation as soon as a statement is imported. | Validates the statement, creates a new reconciliation and worksheet, and runs the default matching rule set - up to the transactions you must match manually. |
| **Default matching rule set** | The matching rule set automatically applied during reconciliation. | Defines which sequence of matching rules runs (used especially with **Reconcile after import**). |
| **Customer payment journal** | The default journal for customer (AR) payments generated during reconciliation. | New customer payments created from reconciliation post to this journal. |
| **Vendor payment journal** | The default journal for vendor (AP) payments generated during reconciliation. | New vendor payments created from reconciliation post to this journal. |
| **Default report configuration** | The default Electronic reporting configuration used for the reconciliation report. | Determines the format and layout of the generated bank reconciliation report. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
