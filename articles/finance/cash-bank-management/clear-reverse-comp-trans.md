---
title: Clear reversal company transactions in advanced bank reconciliation
description: This article provides information about how to clear transactions in advanced bank reconciliation.
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

# Clear reversal company transactions in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article provides information about clearing reversal company transactions in advanced bank reconciliation under feature **Modern bank reconciliation** starting from 10.0.39. 

There may be some payment journals reversed in the application without any records at the bank side. Users can leverage this feature enhancement to complete clearing reversal company transactions in advanced bank reconciliation without matching to any bank statement transaction.

## Prerequisites
-   Turn on feature **Modern bank reconciliation** in feature management workspace.
-   Import a **Bank statement**.

## Clear reversal company transactions on reconciliation worksheet

User can manually clear reversal company transactions on reconciliation worksheet by following the steps below:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
2. Open or create a **bank reconciliation worksheet**.
3. Switch to **Unmatched transactions** tab on reconciliation worksheet.
4. Select the **Company transactions** to be matched. The total amount of selected company transactions must be zero.
5. Click **Match** button.

## Clear reversal company transactions using matching rules

User can complete cash application automatically by using matching rules.

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
2. Click **New** button to create a new matching rule.
3. Enter the **matching rule code** and **name**.
4. In the **Action** field, select **Clear reversal company transaction**.
5. Define the criteria in **Step 1: Find reversal company transactions** Fast Tab.
6. Define the criteria in **Step 2: Find original company transactions** Fast Tab. Following parameters are available:
   1. **Require manual matching when multiple original company transactions are found**: turn on this parameter if you want to manual review and confirm the correct original company transaction to be matched. Otherwise, the matching rule will match the first found transaction,
   2. **Transaction type**, **payment reference**, **document type** fields must be the same in the reversal and original company transactions.

7. **Save** and **activate** the matching rule.
8. [Optional] You can include this matching rule to matching rule sets.
9. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
10. Open or create a **bank reconciliation worksheet**.
11. Click **Run matching rules** button on the top of the worksheet.
12. Select the **matching rule** or **matching rule set** containing the one you defined.
13. Click **OK** to run the automatic matching.

