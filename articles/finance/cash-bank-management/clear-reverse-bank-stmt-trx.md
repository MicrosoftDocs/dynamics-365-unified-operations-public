---
title: Clear reversal bank statement transactions in advanced bank reconciliation
description: This article provides information about clearing bank statement transactions in advanced bank reconciliation.
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

# Clear reversal bank statement transactions in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article provides information about clearing reversal bank statement transactions in advanced bank reconciliation. 

There might be cases where bank statement transaction reversals that aren't recorded at the company side. Users can complete clearing reversal bank statement transactions in advanced bank reconciliation without matching to any company transaction.

## Prerequisites
-   Import a **Bank statement**.

## Clear reversal bank statement transactions on reconciliation worksheet

To manually clear reversal bank statement transactions on reconciliation worksheet, follow these steps:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
2. Open or create a **bank reconciliation worksheet**.
3. Select the **Unmatched transactions** tab on reconciliation worksheet.
4. Select the **Bank statement transactions** to be matched. The total amount of selected company transactions must be zero.
5. Click **Match**.

## Clear reversal bank statement transactions using matching rules

To complete clearing reversal bank statement transactions automatically by using matching rules, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
2. Click **New** to create a new matching rule.
3. Enter the **Matching rule code** and **Name**.
4. In the **Action** field, select **Clear reversal statement lines**.
5. Define the criteria in **Step 1: Find reversal statement lines** Fast Tab.
>[Note!]
>For this step, the reversal field on bank statement line must be **Yes**.

6. Define the criteria in **Step 2: Find original statement lines** Fast Tab. Following parameters are available:
   1. **Document number**, **payment reference** fields must be the same in the reversal and original statement lines.

7. [Optional] Define the criteria in **Step 3: Find bank transactions** Fast Tab. You can add selection criteria to match company transactions to bank statement lines.
8. **Save** and **Activate** the matching rule.
9. [Optional] You can include this matching rule to matching rule sets.
10. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
11. Open or create a **bank reconciliation worksheet**.
12. Click **Run matching rules**.
13. Select the **Matching rule** or **Matching rule set** containing the one you defined.
14. Click **OK** to run the automatic matching.

