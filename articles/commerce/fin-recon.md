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
[!include [banner](../includes/preview-banner.md)]

In Dynamics 365 Commerce versions 10.0.10 and earlier, the functionality for end of day processes in retail stores in the point of sale (POS) client allows a store clerk and store manager to perform end of day operations such as tender declaration, blind close shift, reconcile shift transactions, and close shift. There is no capability in POS to finalize the financial information for shifts which can  be used to post the financials in Commerce headquarters. 

Typically, store managers have the responsibility to complete this task and as such, they are required to review, make corrections, and finalize the totals for a shift before they sign-off on their shifts. The finalized totals should then get posted in Commerce headquarters financial modules. 

In versions 10.0.10 and earlier, store managers can review and make certain adjustments to statement lines in Commerce headquarters. The capability is limited, though, and store managers seldom have access to the Commerce headquarters client. Moreover, the financial retail statement review and adjustment actions can only be done when the statements are created in Commerce headquarters. That process is typically a nightly process and store managers should not be expected to wait for the shift sign-off when financial retail statements are created in Commerce headquarters. 

In Commerce versions 10.0.11 and later, store managers can review, make adjustments, and finalize their shifts in the POS client itself. That data is then used to create and post financial retail statements in Commerce headquarters.  

> [!NOTE]
> For the functionality relating to financial reconciliation in retail stores to work, trickle feed-based order creation must be enabled. For more information, read [Trickle feed-based order creation for retail store transactions](trickle-feed.md). 
  
## Set up financial reconciliation

Follow the steps below to use the financial reconciliation functionality.

1. In the **Feature management** workspace, enable “Retail statements - Trickle feed”.
1. In the POS functionality profile for the appropriate store, set the parameter **Enable financial reconciliation in store** to **Yes**.

## More information about financial reconciliation
When you enable financial reconciliation functionality, parameters as defined in the **Statement/closing** FastTab on the **Retail stores** page in Commerce Headquarters will be synchronized to the channel database. Commerce will enforce the same set of calculation criteria and amount thresholds as in the retail statements.

When the **Close shift** operation is invoked, the system will validate if there is a difference between the system-computed amounts and the declared amounts. If the difference is beyond the defined thresholds, the user will be prompted and can make adjustments as needed. 

3)	The adjustments can be made for each Tender and for the selected Tender for adjustment, the user can see the totals for different transaction types and then choose to edit the totals for a specific transaction type. On editing, the system will show the original computed amount and the over-ridden amount for that transaction type. The user can also capture Notes as a part of this editing process to be able to refer to them for audit purposes.  

4)	Users also have the capability to ignore the validation prompts & messages and proceed with closing the shift. However, this would mean that the concerned Shift will hit the same validation while posting Financial retail statements in HQ and the same will have to be corrected at that time.  

5)	The “Close shift” operation will also validate & warn users if there are transactions in the Offline database that are not synchronized to the Channel database which might be the reason for the wrong computation of the system amounts. In such instances, users can choose to abort the “Close shift” operation and then try and synchronize the offline transactions to the Channel database. Alternatively, they can proceed with choosing to adjust the system computed amounts to account for the transactions that are not synchronized, so that the right set of financial numbers are finalized and posted in HQ. 	

    With trickle feed statement posting process, separating posting of transactions and posting of financials, choosing to adjust the       system computed amounts for missing offline transactions will ensure that financials are always accounted & posted correctly in HQ       independent of missing transactions. The offline transactions can be synchronized to the Channel database & HQ and posted later         independently of the financial postings. 

6)	The details of the financial reconciliation for a shift is synchronized to the HQ using the P-job.

7)	With this feature, the Financial retail statements in HQ do not compute the totals to show the details on the statement lines. Rather, it uses the finalized amounts in the POS client to create and post Financial retail statements.
