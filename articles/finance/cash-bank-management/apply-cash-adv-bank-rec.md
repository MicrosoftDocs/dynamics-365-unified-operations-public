---
title: Cash application in advanced bank reconciliation
description: Learn how to complete cash application in advanced bank reconciliation, including prerequisites and an step-by-step processes.
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

# Cash application in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article explains how to complete cash application in advanced bank reconciliation. As of Microsoft Dynamics 365 Finance version 10.0.39, the **Modern bank reconciliation** feature provides this functionality. 

There might be customer or vendor payments on bank statements in the app. This feature lets users complete cash application in advanced bank reconciliation.

## Prerequisites

- Turn on the **Modern bank reconciliation** feature in the **Feature management** workspace.
- Complete the setup of the default customer payment journal name and the default vendor payment journal name for the bank account.
- Import a bank statement.

## Complete cash application on the reconciliation worksheet

To manually complete cash application on the reconciliation worksheet, follow these steps.

1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
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

### Settle customer invoicee ###

To use matching rules to automatically settle open customer invoices, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **Matching rule code** and **Name** fields.
1. In the **Action** field, select **Settle customer invoice**
1. On the **Step 1: Find statement lines to generate customer payment journals** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
1. On the **Step 2: Match open invoices** FastTab, define the criteria. This step tries to match bank statement line with the open customer invoices in the current legal entity. If an open customer invoices can be successfully matched, then a customer payment journal is posted with the customer account found on the open customer invoice. The posted customer payment journal is settled with the open customer invoice.
1. On the **Step 3: Customer payment journal parameters** FastTab, set the following fields per legal entity:

    - **Default method of payment**
    - **Default bank transaction type**
    - **Accounting date**
    - **Financial dimensions**

1. Select **Save** and then **Activate**.
1. Optional: You can include the matching rule in matching rule sets.
1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either the matching rule that you defined or a matching rule set that contains that matching rule.
1. Select **OK** to run the automatic matching.

### Generate customer payment ###

To use matching rules to automatically generate customer payment without settling any customer invoice, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **Matching rule code** and **Name** fields.
1. In the **Action** field, select **Generate customer payment** 
1. On the **Step 1: Find statement lines to generate customer payment journals** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
1. On the **Step 2 (Optional): Identify customer account through invoice matching** FastTab, define the criteria. This step tries to match bank statement line with the open or closed customer invoices in the current legal entity. If an open or closed customer invoices can be successfully matched, then a customer payment journal is posted with the customer account found on the open customer invoice. Notice that this rule does not settle the customer payment journal with the matched customer invoice.
1. On the **Step 3: Customer payment journal parameters** FastTab, set the following fields:

    - **Automatic customer account matching**.
        - If this parameter is turned on, then the rule tries to match IBAN and bank account number fields on customer master data with the info on bank statement lines. If matched, then the relevant customer account is used to post the customer payment journal.
        - If this parameter is turned off, then the user must specify a customer account to post the customer payment journal.
    - **Customer account** 
    - **Accounting date**
    - **Default method of payment**
    - **Default bank transaction type**
    - **Financial dimensions**

1. Select **Save** and then **Activate**.
1. Optional: You can include the matching rule in matching rule sets.
1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either the matching rule that you defined or a matching rule set that contains that matching rule.
1. Select **OK** to run the automatic matching.

### Generate vendor payment ###

To use matching rules to automatically generate customer payment without settling any customer invoice, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **Matching rule code** and **Name** fields.
1. In the **Action** field, select **Generate vendor payment** 
1. On the **Step 1: Find statement lines to generate vendor payment** FastTab, define the criteria. This step filters the relevant bank statement lines to run against this rule.
1. On the **Step 2: Vendor payment parameters** FastTab, set the following fields:

    - **Vendor account** 
    - **Accounting date**
    - **Method of payment**
    - **Bank transaction type**
    - **Financial dimensions**

1. Select **Save** and then **Activate**.
1. Optional: You can include the matching rule in matching rule sets.
1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either the matching rule that you defined or a matching rule set that contains that matching rule.
1. Select **OK** to run the automatic matching.
