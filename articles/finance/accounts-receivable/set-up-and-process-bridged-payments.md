---
# required metadata

title: Set up and process bridged payments
description: This topic describes how to set up and process bridged customer payments. A bridged payment is a payment that is posted to the general ledger in two steps.
author: raprofit
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPaymMode, VendPaymMode, LedgerJournalTable, LedgerJournalTransCustPaym, LedgerJournalTransVendPaym, LedgerJournalTransDaily
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
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

You can create bridged payments from either Accounts payable or Accounts receivable. A bridged payment is a payment that is posted to the general ledger in two steps. This option is typically used when the method of payment is set to **Bank** and you need to post transactions to the bank account only when the transaction has cleared the bank. However, you can use this option with ledger account in which case the system moves the amount from one main account to another main account when the bridging posting is processed. This topic provides details on how to configure bridging posting for Accounts receivable. You can follow similar steps for Accounts payable transactions.

## Set up bridging posting

To use bridging posting, you will need to set up one or more methods of payment to use the **Bridging posting** method, and then select a **Bridging account**.

1.  Open **Accounts receivable &gt; Payment setup &gt; Methods of payment**.

2.  Select the method of payment to enable bridging posting for or create a new one.

3.  Select the **Bridging posting** check box.

4.  In the **Bridging account** field, select the main account to post the payments to prior to clearing the payment to the bank account.

5.  Close the page.

## Process and transfer bridging posting

To create and process bridging posting, follow these steps.

1.  Open **Accounts receivable &gt; Payments &gt; Customer payment journal**.

2.  Click **New** to create a new journal and select a name in the **Name** field.

3.  Add lines to the **Customer payment journal** and select the **Method of payment** that is configured for bridging posting.

4.  Post the journal. The transactions will be posted to the main account selected in the **Bridging account** field.

When the transactions have cleared the bank and you want to transfer the payment from the Br**idging account** to the **Payment account** specified on the method of payment, follow these steps.

1.  Open **General ledger &gt; Journal entries &gt; General journals**.

2.  Click **New** to create a new journal and select the desired **Name**.

3.  Click **Lines** to open the journal details.

4.  Click **Functions &gt; Select bridged transactions**.

5.  Mark each payment that has cleared, and then click **Accept**.

6.  Post the journal.
