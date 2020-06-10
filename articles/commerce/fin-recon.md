---
# required metadata

title: Financial reconciliation in retail stores
description: This topic describes financial reconciliation in retail stores for POS for Dynamics 365 Commerce.
author: anpurush
manager: AnnBe
ms.date: 06/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-05-21
ms.dyn365.ops.version: 

---

# Financial reconciliation in retail stores

[!include [banner](includes/banner.md)]


In Dynamics 365 Commerce versions 10.0.10 and earlier, the functionality for end of day processes in retail stores in the point of sale (POS) client allows a store clerk and store manager to perform end of day operations such as tender declaration, blind close shift, reconcile shift transactions, and close shift. There is no capability in POS to finalize the financial information for shifts that can  be used to post the financials in Commerce headquarters. 

Typically, store managers have the responsibility to complete this task. They are required to review, make corrections, and finalize the totals for a shift before they sign off on it. The finalized totals should then get posted in Commerce headquarters financial modules. 

In versions 10.0.10 and earlier, store managers can review and make certain adjustments to statement lines in Commerce headquarters. The capability is limited, though, and store managers seldom have access to the Commerce headquarters client. Moreover, the financial retail statement review and adjustment actions can only be done when the statements are created in Commerce headquarters. That process is typically a nightly process and store managers would need to wait for the shift signoff when financial retail statements are created in Commerce headquarters. 

In Commerce versions 10.0.11 and later, store managers can review, make adjustments, and finalize their shifts in the POS client itself. That data is then used to create and post financial retail statements in Commerce headquarters.  

> [!NOTE]
> For the functionality relating to financial reconciliation in retail stores to work, trickle feed-based order creation must be enabled. For more information, read [Trickle feed-based order creation for retail store transactions](trickle-feed.md). 
  
## Set up financial reconciliation

Follow the steps below to use the financial reconciliation functionality.

1. In the **Feature management** workspace, enable “Retail statements - Trickle feed”.
1. In the POS functionality profile for the appropriate store, set the parameter **Enable financial reconciliation in store** to **Yes**.

## More information about financial reconciliation
When financial reconciliation functionality is enabled, some of the parameters that are defined in the **Statement/closing** FastTab on the **Retail stores** page in Commerce headquarters are synchronized to the channel database. The same set of calculation criteria and amount thresholds used for retail statements is enforced.

When the **Close shift** operation is invoked, the system will validate if there is a difference between the system-computed amounts and the declared amounts. If the difference is beyond the defined thresholds, the user will be prompted and can make adjustments as needed. 

Adjustments can be made for each tender. When a tender is selected, the user can view the totals for different transaction types and edit the totals for a specific transaction type. When editing, the system displays the original computed amount and the over-ridden amount for that transaction type. The user can also capture notes as a part of the editing process. Notes can be used for audit purposes.  

Users can ignore the validation prompts and messages and proceed with closing the shift. However, if a user ignores validation prompts, the same issues will arise and need to be fixed when the shift posts financial statements in Commerce headquarters. 

The **Close shift** operation in POS will also validate and warn users if there are transactions in the offline database that are not synchronized to the channel database. This occurence may be the cause of the incorrect computation of the system amounts. In such a scenario, the user can end the **Close shift** operation and try to synchronize the offline transactions to the channel database. Alternatively, the user can adjust the system-computed amounts manually to account for the transactions that are not synchronized, so that the right set of financial numbers are finalized and posted. 	

With trickle feed statement posting, separating the posting of transactions from the posting of financials, choosing to adjust the system-computed amounts for missing offline transactions will ensure that financials are always accounted and posted correctly, regardless of missing transactions. Offline transactions can be synchronized to the channel database and Commerce headquarters and posted later, separate from the financial postings. 

Details of the financial reconciliation for a shift are synchronized to Commerce headquarters by using the P-job.

Financial retail statements in Commerce headquarters do not compute totals to show the details on the statement lines. Instead, the finalized amounts in the POS client are used to create and post financial retail statements.
