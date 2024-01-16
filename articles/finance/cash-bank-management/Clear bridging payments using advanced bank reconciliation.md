---
title: Clear bridging payments using advanced bank reconciliation
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

# Clear bridging payments using advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article provides information about clearing bridging payments in advanced bank reconciliation under feature **Automatic clear bridged transactions through advanced bank reconciliation** starting from 10.0.39. 

A bridged payment is a payment that is posted to the general ledger in two steps. Typically, this approach is used when the method of payment is set to **Bank**, and you must post transactions to the bank account only when the transaction has cleared the bank. However, you can also use it for a ledger account. In this case, the amount will be moved from one main account to another main account when the bridging posting is processed.

Bridging payments must be cleared in general journal prior to this feature. With this feature, bridging payments can be automatically cleared when the advanced bank reconciliation worksheet is marked as reconciled.

## Prerequisites
-   Turn on feature **Automatic clear bridged transactions through advanced bank reconciliation** in feature management workspace.
- Complete **Bridging account by bank account** setup on **Methods of payment** page. 

  -   If this parameter is turned on, bridging account on the payment bank account will be used as the offset account on payment journal posting.
  -   If this parameter is turned off, bridging account on method of payment will be used as the offset account on payment journal posting.

- Complete **Bridging account** setup on **Bank accounts** page. You can find this field on **General** tab.
- Complete **Clear bridged transactions during reconciliation** setup on **Bank accounts** page. You can find this field on **Reconciliation** tab. 

  -   If this parameter is turned on, when a bridging payment is reconciled in the reconciliation worksheet and the worksheet is marked as reconciled afterwards, a clearing journal will be posted in general ledger automatically.
  -   If this parameter is turd off, user must clear the bridging payments in general ledger. Refer to this article for the detail steps. [Set up and process bridged payments - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/accounts-receivable/set-up-and-process-bridged-payments#process-and-transfer-bridging-posting)

- Complete **Clearing journal name** setup on **Bank reconciliation** tab on **Cash and bank management parameters** page in **Cash and bank management** module.

## Bridging payment on payment journal

To create and process bridging posting, follow these steps.

1. Go to **Accounts receivable > Payments > Customer payment journal**.
2. Select **New** to create a journal.
3. In the **Name** field, select a name.
4. Add lines to the customer payment journal, and select the method of payment that is configured for bridging posting.
5. Post the journal. The transactions will be posted to the main account that you configured in the prerequisite steps.

The steps are applicable for Accounts payable transactions too.

## Clear bridging payment on reconciliation worksheet

To clear bridging payment on reconciliation worksheet, follow these steps.

1. Complete bank statement reconciliation. Refer to this article for details [Reconcile bank statements by using advanced bank reconciliation - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/cash-bank-management/reconcile-bank-statements-advanced-bank-reconciliation).
2. Click **Mark as reconciled** on the reconciliation worksheet.
3. After the reconciliation worksheet is marked as reconciled, clearing journals will be posted to general ledger automatically. The payment amount will be moved from bridging account to bank main account in the clearing journals.

## Clear bridging payment using batch job

There may be cases that clearing journals have posting errors during bank reconciliation. In this case, user can fix the root cause of posting failures and rerun clearing bridging payments using batch job. Follow these steps:

1. Go to **Cash and bank management** > **Periodic tasks** > **Clear bridged transactions**.
2. Select **Reconciliation ID** which contains the clearing payments you want to clear again.
3. Click **OK** to submit the batch job.