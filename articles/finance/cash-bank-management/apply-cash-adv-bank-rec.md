---
title: Cash application in advanced bank reconciliation
description: Learn how to complete cash application in advanced bank reconciliation, including prerequisites and a step-by-step processes.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 07/18/2024
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

This article explains how to complete cash application in advanced bank reconciliation. As of Microsoft Dynamics 365 Finance version 10.0.39, the **Modern bank reconciliation** feature provides this functionality. 

There might be customer or vendor payments on bank statements in the app. This feature lets users complete cash application in advanced bank reconciliation.

## Prerequisites

- Turn on the **Modern bank reconciliation** feature in the **Feature management** workspace.
- Complete the setup of the default customer payment journal name and the default vendor payment journal name for the bank account.
- Import a bank statement.
- Starting version 10.0.42, if feature **Enable prepayment and posting profile when generating payment journal in advanced bank reconciliation** is enabled, prepayment option and posting profile when generating customer payment journal and vendor payment journal from bank reconciliation worksheet is available. User can also configure these two options on reconciliation matching rule setup.
- Starting version 10.0.42, if feature **Enable default descriptions for advanced bank reconciliation** is enabled, default descriptions for automatic payment journal posting and voucher posting are enabled in advanced bank reconciliation.

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

To use matching rules to automatically settle open customer invoices, follow these steps.

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
