---
title: Generate voucher in advanced bank reconciliation
description: This article provides information about generating vouchers in advanced bank reconciliation.
author: EricWang
ms.date: 01/08/2024
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

This article provides information about posting voucher to general ledger in advanced bank reconciliation under feature **Modern bank reconciliation** starting from 10.0.39. 

There may be some bank statement transactions not relating to specific customer or vendor payments, such as bank interest income, bank fee, etc. Uses can leverage this feature enhancement to post this kind of bank statement transactions to general ledger directly.

## Prerequisites
-   Turn on feature **Modern bank reconciliation** in feature management workspace.
-   Complete **bank transaction types** setup.
-   Complete **Number sequences** setup of reference **Bank statement reversal** in **Cash and bank management parameters**.
-   Import a **Bank statement**.

## Generate voucher on reconciliation worksheet

User can manually post bank statement transactions to general ledger on reconciliation worksheet by following the steps below:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
2. Open or create a **bank reconciliation worksheet**.
3. Switch to **Unmatched transactions** tab on reconciliation worksheet.
4. Select the **bank statement transactions** to be posted to general ledger.
5. Click **Generate voucher** button.
6. A sidebar will be populated. Specify the values for following fields:
   - **Accounting date**
   - **Bank transaction type**
   - **Offset account**
   - Voucher **description**
   - **Sales tax group** if applicable
   - **Item sales tax group** if applicable
   - **Financial dimensions** if applicable
   - **Financial tags** if applicable

7. Click **OK** button.

## Generate voucher using matching rules

User can post bank statement transactions to general ledger automatically by using matching rules.

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.

2. Click **New** button to create a new matching rule.

3. Enter the **matching rule code** and **name**.

4. In the **Action** field, select **Generate voucher**.

5. Define the posting criteria in **Find statement lines to generate voucher** Fast Tab.

6. Define the parameter values in **Voucher parameters** Fast Tab:

   - **Accounting date**
   - **Bank transaction type**
   - **Offset account**
   - Voucher **description**
   - **Sales tax group** if applicable
   - **Item sales tax group** if applicable
   - **Financial dimensions** if applicable

7. **Save** and **activate** the matching rule.

8. [Optional] You can include this matching rule to matching rule sets.

9. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.

10. Open or create a **bank reconciliation worksheet**.

11. Click **Run matching rules** button on the top of the worksheet.

12. Select the **matching rule** or **matching rule set** containing the one you defined.

13. Click **OK** to run the automatic matching.

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
