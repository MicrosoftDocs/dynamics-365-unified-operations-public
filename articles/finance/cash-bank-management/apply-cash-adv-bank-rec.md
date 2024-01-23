---
title: Cash application in advanced bank reconciliation
description: This article explains how to complete cash application in advanced bank reconciliation.
author: EricWang
ms.date: 01/18/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: 
ms.author: wangchen
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 
ms.custom: 
ms.search.form: 
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

To use matching rules to automatically complete cash application, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Advanced bank reconciliation setup** \> **Reconciliation matching rules**.
1. Select **New** to create a matching rule.
1. Set the **Matching rule code** and **Name** fields.
1. In the **Action** field, select one of the following action types:

    - **Generate customer payment** – Post the bank statement transaction as a customer payment journal only, without settling any open customer invoices.
    - **Generate vendor payment** – Post the bank statement transaction as a vendor payment journal only, without settling any open vendor invoices.
    - **Settle customer invoice** – Post the bank statement transaction as a customer payment journal, and settle it with matched open customer invoices.

1. On the **Find statement lines to generate customer payment** or **Find statement lines to generate vendor payment** FastTab, define the criteria.
1. On the **Customer payment parameters** or **Vendor payment parameters** FastTab, set the following fields:

    - **Customer account** or **Vendor account**
    - **Accounting date**
    - **Method of payment**
    - **Bank transaction type**

1. If you selected **Settle customer invoice** as the action type, on the **Match open invoices** FastTab, define the criteria.
1. Select **Save** and then **Activate**.
1. Optional: You can include the matching rule in matching rule sets.
1. Go to **Cash and bank management** \> **Bank statement reconciliation** \> **Bank reconciliation**.
1. Open or create a bank reconciliation worksheet.
1. Select **Run matching rules**.
1. Select either the matching rule that you defined or a matching rule set that contains that matching rule.
1. Select **OK** to run the automatic matching.
