---
title: Petty cash
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

# Clear reversal bank statement transactions in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article provides information about clearing reversal bank statement transactions in advanced bank reconciliation. 

There may be some bank statement transaction reversals without any records at the company side. Users can leverage this feature to complete clearing reversal bank statement transactions in advanced bank reconciliation without matching to any company transaction.

## Prerequisites
-   Import a **Bank statement**.

## Clear reversal bank statement transactions on reconciliation worksheet

User can manually clear reversal bank statement transactions on reconciliation worksheet by following the steps below:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
2. Open or create a **bank reconciliation worksheet**.
3. Switch to **Unmatched transactions** tab on reconciliation worksheet.
4. Select the **Bank statement transactions** to be matched. The total amount of selected company transactions must be zero.
5. Click **Match** button.

## Clear reversal bank statement transactions using matching rules

User can complete clearing reversal bank statement transactions automatically by using matching rules.

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
2. Click **New** button to create a new matching rule.
3. Enter the **matching rule code** and **name**.
4. In the **Action** field, select **Clear reversal statement lines**.
5. Define the criteria in **Step 1: Find reversal statement lines** Fast Tab.
   1. Note: For bank statement line to be found in this step, reversal field on bank statement line must be Yes

6. Define the criteria in **Step 2: Find original statement lines** Fast Tab. Following parameters are available:
   1. **Document number**, **payment reference** fields must be the same in the reversal and original statement lines.

7. [Optional] Define the criteria in **Step 3: Find bank transactions** Fast Tab. You can add selection criteria to match company transactions to bank statement lines.
8. **Save** and **activate** the matching rule.
9. [Optional] You can include this matching rule to matching rule sets.
10. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
11. Open or create a **bank reconciliation worksheet**.
12. Click **Run matching rules** button on the top of the worksheet.
13. Select the **matching rule** or **matching rule set** containing the one you defined.
14. Click **OK** to run the automatic matching.

