---
# required metadata

title: Reverse posted lease transactions
description: This topic explains how to reverse a posted lease transaction. Any transaction that is created through Asset leasing can be reversed.
author: moaamer
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeaseLeaseTransactions
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14

---

# Reverse posted lease transactions

[!include [banner](../includes/banner.md)]

Any transaction that is created through Asset leasing can be reversed. Transactions that are reversed through Asset leasing update your lease data. Therefore, they also update the carrying values of the lease liability and right-of-use (ROU) asset.

To create a reversing transaction for a lease, follow these steps.

1. On either the **Asset transactions** page or the **Liability transactions** page, select the transaction, and then select **Reverse transaction**.
2. In the dialog box that appears, you can edit the date when the reversing entry will be posted. By default, the **Date** field is set to the transaction posting date of the transaction that you selected. The reversing entry can't be posted earlier than the original posting date of the selected transaction.
3. Select **OK**. A journal entry is posted that reverses the entry that you selected. The reversal is shown on the **Asset transactions** or **Liability transactions** page, and the net total of the current balance that is shown on the page is updated.

When you select **Reverse tracing**, a dialog box appears that shows both the original transactions and the reversed transactions, together with a linked number that is known as a *trace number*. To make the reversals easier to understand and to improve visibility, you can also track reversals by using the lease schedules.

The **Latest journal number** field on the **Schedule** page shows the journal numbers of transactions. When a transaction is reversed, this field is updated with the journal number of a reversing transaction. Additionally, the **Reversed** check box is selected to indicate that the transaction is reversed, and the **Posted** field is selected.

## Revoke a reversed transaction

To revoke a reversed transaction, follow these steps.

1. On either the **Schedule** page or the **Transactions** page, select the original transaction.
2. Follow one of these steps:

    - If you selected the transaction on the **Schedule** page, follow the steps for creating a journal in [Create monthly journal entries in a batch](create-monthly-journals-batch.md). You must manually post the journal.
    - If you selected the transaction on the **Transactions** page, select **Reverse transaction**. You receive a message that states that this revocation is a revocation of an earlier reversal, and that you can edit the posting date for this revocation. However, general business validations affect the dates that can be entered in the **Date** field. 

3. Select **OK**. A journal entry is posted that reverses the entry that you selected. The reversal is shown on the **Transactions** page, and the net total current balance is restored to what it was before the first reversal. Therefore, the impact that the reversal had on the balances is negated.

When you select **Reverse tracing**, a dialog box appears that shows both the original transactions and the reversed transactions, together with a linked trace number.

You can also track revocations by using the appropriate **Schedules** page. The **Reverse** field is cleared, whereas the **Journal posted** field is selected. Additionally, the **Latest journal number** field is updated with the journal number of the revocation transaction, and the **Journal number** field is updated with the reversal journal number.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
