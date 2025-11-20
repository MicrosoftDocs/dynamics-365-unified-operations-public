---
title: Cash application in advanced bank reconciliation
description: Learn how to complete cash application in advanced bank reconciliation, including prerequisites and step-by-step processes.
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 11/19/2025
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

This article explains how to complete cash application in advanced bank reconciliation using the **Modern bank reconciliation** feature. 

There might be customer or vendor payments on bank statements in the app. This feature lets users complete cash application in advanced bank reconciliation.

## Prerequisites

- Turn on the **Modern bank reconciliation** feature in the **Feature management** workspace.
- Complete the setup of the default customer payment journal name and the default vendor payment journal name for the bank account.
- Import a bank statement.
- As of version 10.0.42, if the **Enable prepayment and posting profile when generating payment journal in advanced bank reconciliation** feature is enabled, a prepayment option and a posting profile option are available when users generate a customer payment journal and a vendor payment journal from the bank reconciliation worksheet. Users can also configure those two options in the setup of reconciliation matching rules.
- As of version 10.0.42, if the **Enable default descriptions for advanced bank reconciliation** feature is enabled, default descriptions for automatic payment journal posting and voucher posting are enabled in advanced bank reconciliation.

> [!NOTE]
> When applying cash in advanced bank reconciliation, only journal names without approval workflow enabled are supported.

## Complete cash application on the reconciliation worksheet

To manually complete cash application on the reconciliation worksheet, follow these steps.

1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
2. Open or create a bank reconciliation worksheet.
3. On the **Unmatched transactions** tab, select the bank statement transactions to post to the general ledger.
4. Select **Generate payment journal**.
5. In the dialog box that appears, set the following fields:

    - **Payment type** – Specify whether the payment is a customer payment or a vendor payment.
    - **Customer account** or **vendor account**
    - **Method of payment**
    - **Accounting date**
    - **Bank transaction type**
    - **Financial dimensions** (if applicable)
    - **Financial tags** (if applicable)

6. Select **Generate payment** to post the bank statement transaction as a customer payment journal or vendor payment journal, but without settling any open invoices.
7. Select **Settle transactions** to further settle this bank statement transaction with open invoices under the selected customer account or vendor account.

## Complete cash application by using matching rules

### Settle customer invoices

To use matching rules to automatically settle open customer invoices, including project invoices, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
2. Select **New** to create a matching rule.
3. Set the **Matching rule code** and **Name** fields.
4. In the **Action** field, select **Settle customer invoice**
5. On the **Step 1: Find statement lines to generate customer payment journals** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
6. On the **Step 2: Match open invoices** FastTab, define the criteria. This step matches bank statement lines with the open customer invoices in the current legal entity. If open customer invoices can be successfully matched, a customer payment journal is posted with the customer account that is found on the open customer invoice. The posted customer payment journal is settled with the open customer invoice.
7. On the **Step 3: Customer payment journal parameters** FastTab, set the following fields per legal entity:

    - **Default method of payment**
    - **Default bank transaction type**
    - **Accounting date**
    - **Financial dimensions**

8. Select **Save** and then **Activate**.
9. Optional: You can include the matching rule in matching rule sets.
10. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
11. Open or create a bank reconciliation worksheet.
12. Select **Run matching rules**.
13. Select either the matching rule or a matching rule set that contains the matching rule.
14. Select **OK** to run the automatic matching.

### Generate customer payments

To use matching rules to automatically generate customer payments without settling customer invoices, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
2. Select **New** to create a matching rule.
3. Set the **Matching rule code** and **Name** fields.
4. In the **Action** field, select **Generate customer payment**.
5. On the **Step 1: Find statement lines to generate customer payment journals** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
6. On the **Step 2 (Optional): Identify customer account through invoice matching** FastTab, define the criteria. This step matches bank statement lines with the open or closed customer invoices in the current legal entity. If open or closed customer invoices can be successfully matched, a customer payment journal is posted with the customer account that is found on the open customer invoice. This rule doesn't settle the customer payment journal with the matched customer invoice.
7. On the **Step 3: Customer payment journal parameters** FastTab, set the following fields:

    - **Automatic customer account matching**

        - If this parameter is turned on, the rule tries to match International Bank Account Number (IBAN) and bank account number fields in customer master data with the information on bank statement lines. If matching is successful, the relevant customer account is used to post the customer payment journal.
        - If this parameter is turned off, a customer account must be specified before the customer payment journal can be posted.

    - **Customer account** 
    - **Accounting date**
    - **Default method of payment**
    - **Default bank transaction type**
    - **Financial dimensions**

8. Select **Save** and then **Activate**.
9. Optional: You can include the matching rule in matching rule sets.
10. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
11. Open or create a bank reconciliation worksheet.
12. Select **Run matching rules**.
13. Select either a matching rule or a matching rule set that contains the matching rule.
14. Select **OK** to run the automatic matching.

> [!NOTE]
> If the **Payment journal cancellation from bank reconciliation worksheet** feature is enabled, the **Cancel payment** button is available to reverse incorrectly posted customer payment journals from the reconciliation worksheet. If the invoice has been settled during the journal posting (manually or using reconciliation rules), the invoice is also unsettled at the time of payment cancellation. 

### Generate vendor payments

To use matching rules to automatically generate vendor payments without settling vendor invoices, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
2. Select **New** to create a matching rule.
3. Set the **Matching rule code** and **Name** fields.
4. In the **Action** field, select **Generate vendor payment**.
5. On the **Step 1: Find statement lines to generate vendor payment** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
6. On the **Step 2: Vendor payment parameters** FastTab, set the following fields:

    - **Vendor account**
    - **Accounting date**
    - **Method of payment**
    - **Bank transaction type**
    - **Financial dimensions**

7. Select **Save** and then **Activate**.
8. Optional: You can include the matching rule in matching rule sets.
9. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
10. Open or create a bank reconciliation worksheet.
11. Select **Run matching rules**.
12. Select either a matching rule or a matching rule set that contains the matching rule.
13. Select **OK** to run the automatic matching.

## Preview matching results before posting

Starting in Dynamics 365 Finance version 10.0.46, organizations using **Modern bank reconciliation** can enable the **Preview automatic bank reconciliation matching results** feature. This enhancement allows users to review and approve reconciliation matching rule results before transactions are posted and marked as matched.

When the **Preview automatic bank reconciliation matching results** feature is enabled, a new **Require review before posting** parameter is available in **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
- If this parameter is set to **Yes**, the results of the reconciliation matching rule run are displayed on the **Bank reconciliation worksheet** > **Pending review** tab .
- Users can manually mark transactions for review during journal or voucher creation by setting **Require review before posting** to **Yes**.
- In addition, a new **Default value of Require review before posting** on the Bank reconciliation rules page is available. When set to **Yes**, all newly created reconciliation rules have **Require review before posting** enabled by default.

Users with appropriate permissions can: 
- Review the results of the reconciliation matching rules.
- Validate associated draft journals and vouchers.
- **Approve** or **Reject** transactions directly within the **Bank reconciliation worksheet**.

Once approved, the journals and vouchers are posted, and the matching results are moved to the **Matched transactions** tab.

> [!NOTE]
> Customer and vendor payment journals, as well as general ledger vouchers associated with bank statement records and visible in the **Pending review** tab, can't be edited. They should be **Rejected** and recreated. These journals and transactions can also only be posted from the **Bank reconciliation worksheet** page.

## Enable default descriptions for advanced bank reconciliation

If the **Enable default descriptions for advanced bank reconciliation** feature is enabled, default descriptions for automatic payment journal posting and voucher posting are available in advanced bank reconciliation. 

To enter default descriptions for bank reconciliation postings, follow these steps:
1. Go to **General Ledger** \> **Journal setup**  \> **Default descriptions** or **Organization administration** \> **Default descriptions**.
2. There is a description type **Bank - reconciliation worksheet** in the list.
3. To configure default descriptions for automatic postings during bank reconciliation process, see [Set up default descriptions for automatic posting](../general-ledger/set-up-default-descriptions-for-automatic-posting.md). References to **Reconciliation matching rules** and **Bank statement report entry** can be added on the **Default descriptions** parameters tab and included in the description text.

> [!NOTE]
> The current system assigns descriptions differently between automatic and manual flows:
> - For automatic bank reconciliation that uses defined matching rules, when the **Enable default descriptions for advanced bank reconciliation** feature is enabled, the default descriptions are used.
> - For manual voucher generation, the bank statement line's **Entry Reference** field is used for the description.

![Default descriptions](./media/defaultdescriptions.PNG)
