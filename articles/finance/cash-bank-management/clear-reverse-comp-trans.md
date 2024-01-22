---
title: Clear reversal company transactions in advanced bank reconciliation
description: This article provides information about how to clear transactions in advanced bank reconciliation.
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

# Clear reversal company transactions in advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article provides information about clearing reversal company transactions in advanced bank reconciliation. Starting in Dynamics 365 Finance version 10.0.39, the **Modern bank reconciliation** feature provides this functionality. 

There might be payment journals that are reversed in the application without any records at the bank. Users can leverage this feature to complete clearing reversal company transactions in advanced bank reconciliation without matching to bank statement transactions.

## Prerequisites
-   Turn on feature **Modern bank reconciliation** in feature management workspace
-   Import a **Bank statement**

## Clear reversal company transactions on reconciliation worksheet

User can manually clear reversal company transactions on reconciliation worksheet by following the steps below:

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
2. Open or create a **Bank reconciliation worksheet**.
3. Go to **Unmatched transactions** tab on reconciliation worksheet.
4. Select the **Company transactions** to be matched. The total amount of selected company transactions must be zero.
5. Click **Match**.

## Clear reversal company transactions using matching rules

User can complete cash application automatically by using matching rules.

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Reconciliation matching rules**.
2. Click **New** to create a new matching rule.
3. Enter a **matching rule code** and **Name**.
4. In the **Action** field, select **Clear reversal company transaction**.
5. Define the criteria in **Step 1: Find reversal company transactions** Fast Tab.
6. Define the criteria in **Step 2: Find original company transactions** Fast Tab. The following parameters are available:
 - **Require manual matching when multiple original company transactions are found** - Select this parameter to manually review and confirm the correct original company transaction to be matched. Otherwise, the matching rule matches the first found transaction.
 - **Transaction type**, **Payment reference** and **Document type** fields must match the reversal and original company transactions.

7.  Click **Save** and **Activate** to save and activate the matching rule.
8. [Optional] You can include this matching rule to matching rule sets.
10. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank reconciliation**.
11. Open or create a **Bank reconciliation worksheet**.
12. Click **Run matching rules**.
13. Select **Matching rule** or **Matching rule set** containing the one you defined.
14. Click **OK** to run the automatic matching.

