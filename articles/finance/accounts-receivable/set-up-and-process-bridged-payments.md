---
title: Set up and process bridged payments
description: Learn how to set up and process bridged customer payments. A bridged payment is a payment that is posted to the general ledger in two steps.
author: mukumarm
ms.author: mukumarm
ms.topic: how-to
ms.date: 07/20/2026
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-01-03
ms.search.form: CustPaymMode, VendPaymMode, LedgerJournalTable, LedgerJournalTransCustPaym, LedgerJournalTransVendPaym, LedgerJournalTransDaily
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
---

# Set up and process bridged payments

[!INCLUDE [banner](../includes/banner.md)]

A bridged payment is a payment that you post to the general ledger in two steps. Typically, use this approach when you set the method of payment to **Bank** and you must post transactions to the bank account only when the transaction clears the bank. However, you can also use it for a ledger account. In this case, the amount moves from one main account to another main account when the bridging posting is processed.

You can create bridged payments from either Accounts payable or Accounts receivable. Although this article explains how to configure bridging posting for Accounts receivable, the steps for Accounts payable transactions are similar.

## Set up bridging posting

To use bridging posting, set up one or more methods of payment so that they use the **Bridging posting** method. Then, select a bridging account.

1. Go to **Accounts receivable > Payment setup > Methods of payment**.
1. Select an existing method of payment to enable bridging posting for. Alternatively, create a new method of payment.
1. Select the **Bridging posting** checkbox.
1. In the **Bridging account** field, select the main account that payments should be posted to before they clear to the bank account.
1. Close the page.

## Process and transfer bridging posting

To create and process a bridging posting, follow these steps:

1. Go to **Accounts receivable > Payments > Customer payment journal**.
1. Select **New** to create a journal.
1. In the **Name** field, select a name.
1. Add lines to the customer payment journal, and select the method of payment that is configured for bridging posting.
1. Post the journal. The transactions are posted to the main account that you selected in the **Bridging account** field in the previous procedure.

In Microsoft Dynamics 365 Finance version 10.0.49, the **Improved performance for selecting bridge transactions during the bank clearance process** feature improves performance and streamlines transaction filtering when clearing bridge transactions. The feature optimizes how bridge transactions are queried and selected during the bank clearance process, enabling faster and more efficient transaction matching.

When the transactions clear the bank, and you want to transfer the payment from the bridging account to the payment account that you specified for the method of payment, follow these steps:

1. Go to **General ledger > Journal entries > General journals**.
1. Select **New** to create a journal.
1. In the **Name** field, select a name.
1. Select **Lines** to open the journal details.
1. Select **Functions > Select bridged transactions**. When you enable the **Improved performance for selecting bridge transactions during the bank clearance process** feature, you can filter the bridge transactions that are required for clearing during the bank clearance process.
1. Mark each payment that clears, and then select **Accept**.
1. Post the journal.
