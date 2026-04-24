---
title: Cash application in advanced bank reconciliation
description: Learn how to complete cash application in advanced bank reconciliation, including prerequisites and step-by-step processes.
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 03/30/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2024-01-29
ms.search.form:
ms.dyn365.ops.version: 
---

# Cash application in advanced bank reconciliation

[!include [banner](../../includes/banner.md)]

This article explains how to complete cash application in advanced bank reconciliation by using the **Modern bank reconciliation** feature.

There might be customer or vendor payments on bank statements in the app. This feature lets users complete cash application in advanced bank reconciliation.

## Prerequisites

- Turn on the **Modern bank reconciliation** feature in the **Feature management** workspace.
- Set up the default customer payment journal name and the default vendor payment journal name for the bank account.
- Import a bank statement.
- As of version 10.0.42, if you enable the **Enable prepayment and posting profile when generating payment journal in advanced bank reconciliation** feature, a prepayment option and a posting profile option are available when you generate a customer payment journal and a vendor payment journal from the bank reconciliation worksheet. You can also configure those two options in the setup of reconciliation matching rules.
- As of version 10.0.42, if the **Enable default descriptions for advanced bank reconciliation** feature is enabled, default descriptions for automatic payment journal posting and voucher posting are enabled in advanced bank reconciliation.

> [!NOTE]
> When you apply cash in advanced bank reconciliation, only journal names without approval workflow enabled are supported.

## Complete cash application on the reconciliation worksheet

To manually complete cash application on the reconciliation worksheet, follow these steps:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. On the **Unmatched transactions** tab, select the bank statement transactions to post to the general ledger.
1. Select **Generate payment journal**.
1. In the dialog box that appears, set the following fields:

    - **Payment type** – Specify whether the payment is a customer payment or a vendor payment.
    - **Customer account** or **vendor account**
    - **Method of payment**
    - **Accounting date**
    - **Bank transaction type**
    - **Financial dimensions** (if applicable)
    - **Financial tags** (if applicable)

1. Select **Generate payment** to post the bank statement transaction as a customer payment journal or vendor payment journal, but without settling any open invoices.
1. Select **Settle transactions** to further settle this bank statement transaction with open invoices under the selected customer account or vendor account.

## Complete cash application by using matching rules

### Settle customer invoices

To use matching rules to automatically settle open customer invoices, including project invoices, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **Matching rule code** and **Name** fields.
1. In the **Action** field, select **Settle customer invoice**.
1. On the **Step 1: Find statement lines to generate customer payment journals** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
1. On the **Step 2: Match open invoices** FastTab, define the criteria. This step matches bank statement lines with the open customer invoices in the current legal entity. If open customer invoices are successfully matched, a customer payment journal is posted with the customer account that is found on the open customer invoice. The posted customer payment journal is settled with the open customer invoice.
1. On the **Step 3: Customer payment journal parameters** FastTab, set the following fields per legal entity:

    - **Default method of payment**
    - **Default bank transaction type**
    - **Accounting date**
    - **Financial dimensions**

1. Select **Save** and then **Activate**.
1. (Optional) Include the matching rule in matching rule sets.
1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either the matching rule or a matching rule set that contains the matching rule.
1. Select **OK** to run the automatic matching.

> [!IMPORTANT]
> If you enable the **Enable cash discount support for settle customer invoice matching rules** feature, the system supports automatic application of customer cash discounts during bank reconciliation settlement when customer invoices are settled through reconciliation rules. This enhancement ensures that cash discounts are applied consistently, whether invoices are settled manually or automatically through bank reconciliation, eliminating residual open balances caused by unapplied discounts.
> A new parameter is available on the **Settle customer invoice** bank reconciliation rule that defines if invoice cash discounts are applied. When the **Search for invoice cash discount** field is set to **Yes**, the reconciliation process evaluates whether a cash discount applies during settlement.
> If a grace period is defined on the **Method of payment** selected during invoice posting, it's also taken into consideration when applying cash discount.

### Generate customer payments

To use matching rules to automatically generate customer payments without settling customer invoices, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **Matching rule code** and **Name** fields.
1. In the **Action** field, select **Generate customer payment**.
1. On the **Step 1: Find statement lines to generate customer payment journals** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
1. On the **Step 2 (Optional): Identify customer account through invoice matching** FastTab, define the criteria. This step matches bank statement lines with the open or closed customer invoices in the current legal entity. If open or closed customer invoices are successfully matched, the rule posts a customer payment journal with the customer account that it finds on the open customer invoice. This rule doesn't settle the customer payment journal with the matched customer invoice.
1. On the **Step 3: Customer payment journal parameters** FastTab, set the following fields:

    - **Automatic customer account matching**

        - If you turn on this parameter, the rule tries to match International Bank Account Number (IBAN) and bank account number fields in customer master data with the information on bank statement lines. If matching is successful, the rule uses the relevant customer account to post the customer payment journal.
        - If you turn off this parameter, you must specify a customer account before the customer payment journal can be posted.

    - **Customer account**
    - **Accounting date**
    - **Default method of payment**
    - **Default bank transaction type**
    - **Financial dimensions**

1. Select **Save** and then **Activate**.
1. (Optional) Include the matching rule in matching rule sets.
1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either a matching rule or a matching rule set that contains the matching rule.
1. Select **OK** to run the automatic matching.

> [!NOTE]
> If you enable the **Payment journal cancellation from bank reconciliation worksheet** feature, the **Cancel payment** button is available to reverse incorrectly posted customer payment journals from the reconciliation worksheet. If the invoice is settled during the journal posting (manually or using reconciliation rules), the invoice is also unsettled at the time of payment cancellation.

### Generate vendor payments

To use matching rules to automatically generate vendor payments without settling vendor invoices, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **Matching rule code** and **Name** fields.
1. In the **Action** field, select **Generate vendor payment**.
1. On the **Step 1: Find statement lines to generate vendor payment** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
1. On the **Step 2: Vendor payment parameters** FastTab, set the following fields:

    - **Vendor account**
    - **Accounting date**
    - **Method of payment**
    - **Bank transaction type**
    - **Financial dimensions**

1. Select **Save** and then **Activate**.
1. (Optional) Include the matching rule in matching rule sets.
1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either a matching rule or a matching rule set that contains the matching rule.
1. Select **OK** to run the automatic matching.

## Preview matching results before posting

Starting in Dynamics 365 Finance version 10.0.46, organizations using **Modern bank reconciliation** can enable the **Preview automatic bank reconciliation matching results** feature. This enhancement allows users to review and approve reconciliation matching rule results before transactions are posted and marked as matched.

When you enable the **Preview automatic bank reconciliation matching results** feature, you see a new **Require review before posting** parameter in **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.

- If you set this parameter to **Yes**, the reconciliation matching rule run results appear on the **Bank reconciliation worksheet** > **Pending review** tab.
- You can manually mark transactions for review during journal or voucher creation by setting **Require review before posting** to **Yes**.
- In addition, a new **Default value of Require review before posting** on the **Bank reconciliation rules** page is available. When set to **Yes**, all newly created reconciliation rules have **Require review before posting** enabled by default.

Users with appropriate permissions can:

- Review the results of the reconciliation matching rules.
- Validate associated draft journals and vouchers.
- **Approve** or **Reject** transactions directly within the **Bank reconciliation worksheet**.

After approval, the journals and vouchers are posted, and the matching results move to the **Matched transactions** tab.

> [!NOTE]
> You can't edit customer and vendor payment journals, as well as general ledger vouchers associated with bank statement records and visible in the **Pending review** tab. You must **Reject** and recreate these journals and transactions. You can only post these journals and transactions from the **Bank reconciliation worksheet** page.

## Enable default descriptions for advanced bank reconciliation

When you enable the **Enable default descriptions for advanced bank reconciliation** feature, advanced bank reconciliation provides default descriptions for automatic payment journal posting and voucher posting.

To enter default descriptions for bank reconciliation postings, follow these steps:

1. Go to **General Ledger** > **Journal setup** > **Default descriptions** or **Organization administration** > **Default descriptions**.
1. In the list, find the description type **Bank - reconciliation worksheet**.
1. To configure default descriptions for automatic postings during the bank reconciliation process, see [Set up default descriptions for automatic posting](../general-ledger/set-up-default-descriptions-for-automatic-posting.md). You can add references to **Reconciliation matching rules** and **Bank statement report entry** on the **Default descriptions** parameters tab and include them in the description text.

> [!NOTE]
> The current system assigns descriptions differently between automatic and manual flows:
>
> - For automatic bank reconciliation that uses defined matching rules, when you enable the **Enable default descriptions for advanced bank reconciliation** feature, the system uses the default descriptions.
> - For manual voucher generation, the system uses the bank statement line's **Entry Reference** field for the description.

![Default descriptions](./media/defaultdescriptions.PNG)
