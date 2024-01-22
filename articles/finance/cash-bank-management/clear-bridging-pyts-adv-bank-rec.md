---
title: Clear bridging payments using advanced bank reconciliation
description: This article provides information about clearing bridge payaments in advanced bank reconciliation in Dynamics 365 Finance version 10.0.39.
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

# Clear bridging payments using advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article provides information about clearing bridging payments in advanced bank reconciliation using the **Automatic clear bridged transactions through advanced bank reconciliation** feature in Dynamics 365 Finance version 10.0.39. 

A bridged payment is a payment posted to the general ledger in two steps. Typically, the method of payment is **Bank**, and transactions are posted to the bank account only when the transaction has cleared the bank. However, you can also use it for a ledger account. In this case, the amount is moved from one main account to another main account when the bridging posting is processed.

Before using the **Automatic clear bridged transactions through advanced bank reconciliation** feature, all bridging payments must be cleared in general journal. With this feature, bridging payments are automatically cleared when the advanced bank reconciliation worksheet is marked as reconciled.

## Prerequisites
-   Turn on feature **Automatic clear bridged transactions through advanced bank reconciliation** in feature management workspace.
-   Set up **Bridging account by bank account** on the **Methods of payment** page. 

  -   If this parameter is turned on, the bridging account on the payment bank account will be used as the offset account on payment journal posting.
  -   If this parameter is turned off, the bridging account on method of payment will be used as the offset account on payment journal posting.

- Set up the **Bridging account** on the **Bank accounts** page > **General** tab.
- Set up **Clear bridged transactions during reconciliation** on the **Bank accounts** page > **Reconciliation** tab. 

  -   If this parameter is turned on, when a bridging payment is reconciled in the reconciliation worksheet and the worksheet is marked as reconciled afterwards, a clearing journal will be posted in general ledger automatically.
  -   If this parameter is turned off, users must clear the bridging payments in general ledger. For more information, see [Set up and process bridged payments](../accounts-receivable/set-up-and-process-bridged-payments.md#process-and-transfer-bridging-posting).

- Set up **Clearing journal name** on **Cash and bank management parameters** page > **Bank reconciliation** tab.

## Bridging payment on payment journal

To create and process bridging posting, follow these steps:

1. Go to **Accounts receivable > Payments > Customer payment journal**.
2. Click **New** to create a journal.
3. In the **Name** field, select a name.
4. Add lines to the customer payment journal, and select the method of payment that is configured for bridging posting.
5. Post the journal. The transactions will be posted to the main account that you configured in the prerequisite steps.


## Clear bridging payment on reconciliation worksheet

To clear bridging payment on reconciliation worksheet, follow these steps:

1. Complete the bank statement reconciliation. For more information, see [Reconcile bank statements by using advanced bank reconciliation](../cash-bank-management/reconcile-bank-statements-advanced-bank-reconciliation.md).
2. On the reconciliation worksheet, click **Mark as reconciled**.
3. After the reconciliation worksheet is marked as reconciled, clearing journals are posted to general ledger automatically. The payment amount is moved from the bridging account to bank main account in the clearing journals.

## Clear bridging payment using batch job

If clearing journals have posting errors during bank reconciliation, users can fix posting failures and rerun clearing bridging payments. 
To fix posting failures, follow these steps:

1. Go to **Cash and bank management** > **Periodic tasks** > **Clear bridged transactions**.
2. Select **Reconciliation ID** which contains the clearing payments you want to clear again.
3. Click **OK** to submit the batch job.
