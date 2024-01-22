---
title: Generate voucher in advanced bank reconciliation
description: This article provides information about generating vouchers in advanced bank reconciliation.
author: EricWang
ms.date: 01/22/2024
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

# Generate voucher in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article provides information about posting voucher to general ledger in advanced bank reconciliation using the **Modern bank reconciliation** feature starting in Dynamics 365 Finance version 10.0.39. 

There might be bank statement transactions that aren't related to specific customer or vendor payments, such as bank interest income or bank fees. Users can post this kind of bank statement transactions to general ledger directly using the **Modern bank reconciliation** feature.

## Prerequisites
-   Turn on **Modern bank reconciliation** in feature management workspace.
-   Set up  **Bank transaction types**.
-   Set up **Number sequences** for **Bank statement reversal** in **Cash and bank management parameters**.
-   Import a **Bank statement**.

## Generate voucher on reconciliation worksheet

To manually post bank statement transactions to general ledger on reconciliation worksheet, follow these steps:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
2. Open or create a **Bank reconciliation worksheet**.
3. Click **Unmatched transactions** on the reconciliation worksheet.
4. Select **Bank statement transactions** to be posted to general ledger.
5. Click **Generate voucher**.
6. A sidebar will be populated. Enter values for following fields:
   - **Accounting date**
   - **Bank transaction type**
   - **Offset account**
   - **Description**
   - **Sales tax group** if applicable
   - **Item sales tax group** if applicable
   - **Financial dimensions** if applicable
   - **Financial tags** if applicable

7. Click **Ok**.

## Generate voucher using matching rules

To post bank statement transactions to general ledger automatically by using matching rules, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
2. Click **New** to create a new matching rule.
3. Enter **Matching rule code** and **Name**.
4. In the **Action** field, select **Generate voucher**.
5. Define the posting criteria in **Find statement lines to generate voucher** Fast Tab.
6. Define the parameter values in **Voucher parameters** Fast Tab:
   - **Accounting date**
   - **Bank transaction type**
   - **Offset account**
   - **Description**
   - **Sales tax group** if applicable
   - **Item sales tax group** if applicable
   - **Financial dimensions** if applicable

7. Click **Save** and **Activate**.
 [Optional] You can include this matching rule to matching rule sets.
8. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
9. Open or create a **Bank reconciliation worksheet**.
10. Click **Run matching rules**.
11. Select **Matching rule** or **Matching rule set** containing the one you defined.
12. Click **OK** to run the automatic matching.

## Reverse posted voucher on reconciliation worksheet

User can reverse the posted bank statement transactions on reconciliation worksheet by following the steps below:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
2. Open the **bank reconciliation worksheet**.
3. Switch to **Matched transactions** tab on reconciliation worksheet.
4. Select the **bank statement transactions** to be reversed.
5. Click **Reverse** button.
6. Confirm the vouchers to be reversed in **Voucher list**.
7. Confirm the reversal **accounting date**, **reason code** and **reason comment**.
8. Click **Reverse** button.
