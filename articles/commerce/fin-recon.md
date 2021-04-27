---
# required metadata

title: Financial reconciliation in retail stores
description: This topic describes financial reconciliation in retail stores for POS for Microsoft Dynamics 365 Commerce.
author: anpurush
ms.date: 06/09/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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

In Microsoft Dynamics 365 Commerce version 10.0.10 and earlier, the functionality that the point of sale (POS) client provides for end-of-day processes in retail stores lets store clerks and store managers perform end-of-day operations. For example, they can do tender declarations, blind-close shifts, reconcile shift transactions, and close shifts. However, there is no capability in POS to finalize the financial information for shifts, so that it can be used to post the financials in Commerce headquarters. Typically, store managers are responsible for completing this task. Before they can sign off on a shift, they must review the information, make any corrections that are required, and finalize the totals for that shift. The finalized totals should then be posted in financial modules in Commerce headquarters.

Additionally, in Commerce version 10.0.10 and earlier, store managers can review and make some adjustments to statement lines in Commerce headquarters. However, the capability is limited, and store managers rarely have access to the Commerce headquarters client. Moreover, financial retail statement review and adjustment can be done only when the statements are created in Commerce headquarters. However, that process is typically a nightly process. Therefore, store managers must wait for the shift sign-off when financial retail statements are created in Commerce headquarters.

In Commerce version 10.0.11 and later, store managers can review, adjust, and finalize their shifts in the POS client itself. That data is then used to create and post financial retail statements in Commerce headquarters.

> [!NOTE]
> The functionality that is related to financial reconciliation in retail stores works only if trickle feed–based order creation is turned on. For more information, see [Trickle feed-based order creation for retail store transactions](trickle-feed.md).

## Set up financial reconciliation

Follow these steps to use the financial reconciliation functionality.

1. In the **Feature management** workspace, turn on the **Retail statements - Trickle feed** feature.
1. In the POS functionality profile for the appropriate store, set the **Enable financial reconciliation in store** option to **Yes**.

## More information about financial reconciliation

When the financial reconciliation functionality is turned on, some of the parameters that are defined on the **Statement/closing** FastTab of the **Retail stores** page in Commerce headquarters are synced to the channel database. The same set of calculation criteria and amount thresholds that is used for retail statements is enforced.

When the **Close shift** operation is invoked, the system validates that the system-computed amounts and the declared amounts match. If they differ, and the difference exceeds defined thresholds, the user is prompted and can make the required adjustments.

Adjustments can be made for each tender. When a tender is selected, the user can view the totals for different transaction types and edit the totals for a specific transaction type. During editing, the system shows the original computed amount and the overridden amount for that transaction type. The user can also capture notes as a part of the editing process. Notes can be used for auditing purposes.

Users can ignore the validation prompts and messages, and can proceed to close the shift. However, if a user ignores the validation prompts, the same issues will arise and will have to be fixed when the shift posts financial statements in Commerce headquarters.

The **Close shift** operation in POS also validates that all transactions in the offline database are synced to the channel database. If any transactions aren't synced, the user receives a warning message, because this situation can cause the system amounts to be incorrectly computed. In this situation, the user can end the **Close shift** operation and try to sync the offline transactions to the channel database. Alternatively, the user can manually adjust the system-computed amounts to account for the transactions that aren't synced, so that the correct set of financial numbers is finalized and posted.	

When trickle feed statement posting is used, so that the posting of transactions is separated from the posting of financials, you can choose to adjust the system-computed amounts for missing offline transactions. In this way, you ensure that financials are always accounted and posted correctly, regardless of missing transactions. Offline transactions can be synced to the channel database and Commerce headquarters, and then posted later, separately from the financial postings.

Details of the financial reconciliation for a shift are synced to Commerce headquarters by using the P-job.

Financial retail statements in Commerce headquarters don't compute totals to show the details on the statement lines. Instead, the finalized amounts in the POS client are used to create and post financial retail statements.


[!INCLUDE[footer-include](../includes/footer-banner.md)]