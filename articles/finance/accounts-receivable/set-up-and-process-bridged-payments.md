---
# required metadata

title: Set up and process bridged payments
description: This article explains how to set up and process bridged customer payments. A bridged payment is a payment that is posted to the general ledger in two steps.
author: rachel-profitt
ms.date: 02/23/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPaymMode, VendPaymMode, LedgerJournalTable, LedgerJournalTransCustPaym, LedgerJournalTransVendPaym, LedgerJournalTransDaily
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-01-03
ms.dyn365.ops.version: AX 7.0.0

---

# Set up and process bridged payments

[!include [banner](../includes/banner.md)]

A bridged payment is a payment that is posted to the general ledger in two steps. Typically, this approach is used when the method of payment is set to **Bank**, and you must post transactions to the bank account only when the transaction has cleared the bank. However, you can also use it for a ledger account. In this case, the amount will be moved from one main account to another main account when the bridging posting is processed.

You can create bridged payments from either Accounts payable or Accounts receivable. Although this article explains how to configure bridging posting for Accounts receivable, the steps for Accounts payable transactions are similar.

## Set up bridging posting

To use bridging posting, you must set up one or more methods of payment so that they use the **Bridging posting** method. You must then select a bridging account.

1. Go to **Accounts receivable &gt; Payment setup &gt; Methods of payment**.
2. Select an existing method of payment to enable bridging posting for. Alternatively, create a new method of payment.
3. Select the **Bridging posting** checkbox.
4. In the **Bridging account** field, select the main account that payments should be posted to before they are cleared to the bank account.
5. Close the page.

## Process and transfer bridging posting

To create and process bridging posting, follow these steps.

1. Go to **Accounts receivable &gt; Payments &gt; Customer payment journal**.
2. Select **New** to create a journal.
3. In the **Name** field, select a name.
4. Add lines to the customer payment journal, and select the method of payment that is configured for bridging posting.
5. Post the journal. The transactions will be posted to the main account that you selected in the **Bridging account** field in the previous procedure.

When the transactions have cleared the bank, and you want to transfer the payment from the bridging account to the payment account that is specified for the method of payment, follow these steps.

1. Go to **General ledger &gt; Journal entries &gt; General journals**.
2. Select **New** to create a journal.
3. In the **Name** field, select a name.
4. Select **Lines** to open the journal details.
5. Select **Functions &gt; Select bridged transactions**.
6. Mark each payment that has cleared, and then select **Accept**.
7. Post the journal.
