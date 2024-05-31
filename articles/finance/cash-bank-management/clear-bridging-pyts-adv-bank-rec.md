---
title: Clear bridging payments using advanced bank reconciliation
description: Learn how to clear bridge payaments in advanced bank reconciliation in Microsoft Dynamics 365 Finance version 10.0.39, including prerequisites and various outlines.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 01/22/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2024-01-29
ms.search.form:
ms.dyn365.ops.version:    
---

# Clear bridging payments using advanced bank reconciliation 

[!include [banner](../../includes/banner.md)]

This article explains how to clear bridging payments in advanced bank reconciliation. As of Microsoft Dynamics 365 Finance version 10.0.39, the **Automatic clear bridged transactions through advanced bank reconciliation** feature provides this functionality.

A bridging payment is a payment that's posted to the general ledger in two steps. Typically, the method of payment is **Bank**, and transactions are posted to the bank account only after the transaction clears the bank. However, you can also use it for a ledger account. In this case, the amount is moved from one main account to another main account when the bridging posting is processed.

Before you use the **Automatic clear bridged transactions through advanced bank reconciliation** feature, all bridging payments must be cleared in the general journal. This feature automatically clears bridging payments when the advanced bank reconciliation worksheet is marked as reconciled.

## Prerequisites

- Turn on the **Automatic clear bridged transactions through advanced bank reconciliation** feature in the **Feature management** workspace.
- Set the **Bridging account by bank account** parameter on the **Methods of payment** page. 

    - If this parameter is turned on, the bridging account on the payment bank account is used as the offset account during payment journal posting.
    - If this parameter is turned off, the bridging account on the method of payment is used as the offset account during payment journal posting.

- Set up the bridging account on the **General** tab of the **Bank accounts** page.
- Set the **Clear bridged transactions during reconciliation** parameter on the **Reconciliation** tab of the **Bank accounts** page.

    - If this parameter is turned on, a clearing journal is automatically posted to the general ledger when a bridging payment is reconciled on the reconciliation worksheet and the worksheet is later marked as reconciled.
    - If this parameter is turned off, users must clear the bridging payments in the general ledger. For more information, see [Process and transfer bridging posting](../accounts-receivable/set-up-and-process-bridged-payments.md#process-and-transfer-bridging-posting).

- Set the **Clearing journal name** parameter on the **Bank reconciliation** tab of the **Cash and bank management parameters** page.

## Create a bridging payment on a payment journal

To create and process a bridging posting, follow these steps.

1. Go to **Accounts receivable** \> **Payments** \> **Customer payment journal**.
1. Select **New** to create a journal.
1. In the **Name** field, select a name.
1. Add lines to the customer payment journal, and select the method of payment that's configured for bridging posting.
1. Post the journal. The transactions are posted to the main account that you configured in the prerequisite steps.

## Clear a bridging payment on the reconciliation worksheet

To clear a bridging payment on the reconciliation worksheet, follow these steps.

1. Complete the bank statement reconciliation. For more information, see [Reconcile bank statements by using advanced bank reconciliation](../cash-bank-management/reconcile-bank-statements-advanced-bank-reconciliation.md).
1. On the reconciliation worksheet, select **Mark as reconciled**.

After the reconciliation worksheet is marked as reconciled, clearing journals are automatically posted to general ledger. The payment amount is moved from the bridging account to the bank main account in the clearing journals.

## Clear a bridging payment by using a batch job

If clearing journals have posting errors during bank reconciliation, you can fix the posting failures and then rerun clearing bridging payments.

To fix posting failures, follow these steps.

1. Go to **Cash and bank management** \> **Periodic tasks** \> **Clear bridged transactions**.
1. Select the **Reconciliation ID** value of the reconciliation that contains the clearing payments that you want to clear.
1. Select **OK** to submit the batch job.
