---
title: Cash application in advanced bank reconciliation
description: This article provides information about the feature enhancements in advanced bank reconciliation in 10.0.39.
author: EricWang
ms.date: 01/08/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: 
ms.author: wangchen
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 
ms.custom: 
ms.search.form:  
---

# Cash application in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article provides information about cash application in advanced bank reconciliation under feature **Modern bank reconciliation** starting from 10.0.39. 

There may be some customer or vendor payments on bank statement not existing in the application. Users can leverage this feature enhancement to complete cash application in advanced bank reconciliation.

## Prerequisites
-   Turn on feature **Modern bank reconciliation** in feature management workspace.
-   Complete default **customer payment journal** name and default **vendor payment journal** name setups on bank account.
-   Import a **Bank statement**.

## Cash application on reconciliation worksheet

User can manually complete cash application on reconciliation worksheet by following the steps below:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
2. Open or create a **bank reconciliation worksheet**.
3. Switch to **Unmatched transactions** tab on reconciliation worksheet.
4. Select the **bank statement transactions** to be posted to general ledger.
5. Click **Generate payment journal** button.
6. A sidebar will be populated. Specify the values for following fields:
   - **Payment type** to specific this is a customer payment or vendor payment
   - **Customer account** or **vendor account**
   - **Method of payment**
   - **Accounting date**
   - **Bank transaction type**
   - **Financial dimensions** if applicable
   - **Financial tags** if applicable

7. Click **Generate payment** button to post this bank statement transaction as customer payment journal or vendor payment journal without settling any open invoices.

8. Click **Settle transactions** button to further settle this bank statement transaction with open invoices under the selected customer account or vendor account.

## Cash application using matching rules

User can complete cash application automatically by using matching rules.

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
2. Click **New** button to create a new matching rule.
3. Enter the **matching rule code** and **name**.
4. In the **Action** field, select one of the following action types:
   1. **Generate customer payment**: This action type will post the bank statement transaction as customer payment journal only without settling any open customer invoices.

   2. **Generate vendor payment**: This action type will post the bank statement transaction as vendor payment journal only without settling any open vendor invoices.

   3. **Settle customer invoice**: This action type will post the bank statement transaction as customer payment journal and settle with matched open customer invoices.

5. Define the criteria in **Find statement lines to generate customer payment** Fast Tab or **Find statement lines to generate vendor payment** Fast Tab
6. Define the parameter values in **Customer payment parameters** Fast Tab or **Vendor payment parameters** Fast Tab:

   - **Customer account** or **Vendor account**
   - **Accounting date**
   - **Method of payment**
   - **Bank transaction type**
7. Define the criteria in **Match open invoices** Fast Tab if the action type is **Settle customer invoice**.
8. **Save** and **activate** the matching rule.
9. [Optional] You can include this matching rule to matching rule sets.
10. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
11. Open or create a **bank reconciliation worksheet**.
12. Click **Run matching rules** button on the top of the worksheet.
13. Select the **matching rule** or **matching rule set** containing the one you defined.
14. Click **OK** to run the automatic matching.
