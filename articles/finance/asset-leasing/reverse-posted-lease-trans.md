---
# required metadata

title: Reverse posted lease transactions
description: This topic lists the steps for reversing a posted lease transaction; any transaction that's created in Asset leasing can be reversed.  
author: moaamer
manager: Ann Beebe
ms.date: 07/29/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-07-29
ms.dyn365.ops.version: 10.0.14

---

# Reverse posted lease transactions

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Any transaction that was created through Asset leasing can be reversed. Transactions reversed through Asset leasing update your lease data, and therefore the carrying values of the lease liability and right-of-use asset.

1. To create a reversing transaction for a lease, select the transaction from either the **Asset transactions** or **Liability transactions** page and click **Reverse transaction**.

2. A dialogue will open where you can edit the date that the reversing entry will be posted on. The transaction posting date of the transaction you selected is the default entry on the **Date** field. The reversing entry can't be posted earlier than the original posting date of the selected transaction.

   When you click **OK**, a journal entry will be posted reversing the entry you selected. The reversal is shown in the **Asset transactions** or **Liability transactions** and the net total of the current balance of which displayed on the page is updated.

   When you click **Reverse tracing**, a new page opens and displays the original and reversed transactions with a linked number known as trace number. You can also track reversals using the lease schedules for ease of understanding and visibility.

   When a transaction is reversed, the **Latest journal number** field on the **Schedule** page shows the journal numbers of transactions, and will be updated with journal number a reversing transaction when a transaction is reversed. The **Reversed** check box is marked to indicate the transaction is reversed and the **Posted** field is marked at the same time.

## Revoke a reversed transaction
To revoke a reversed transaction, either select the original transaction from the **Schedule** page, or select the original transaction from the **Transactions** page. 

- If you’re selecting the transaction from the **Schedule** page, follow the process for creating a journal that described in [Create journal entries in batch](create-monthly-journals-batch.md). You’ll need to post that journal manually.
- If you select the transaction from the **Transactions** page, click **Reverse transaction**. A message will display telling you this is a revocation of an earlier reversal, and that you can edit the posting date for this revocation. However, the **Date** field has general business validations that affect what dates are allowed. 

   When you click **OK**, a journal entry will be posted that reverses the entry you selected. The reversal is shown on the **Transactions** page and the net total current balance will be updated and re-instated as it was before the first reversal thus negating the impact of reversal on the balances.

   When you click **Reverse tracing**, a dialog opens that displays both the original and reversed transactions with a linked number, known as trace number.

   You can also track revocations using the respective **Schedules** page. The **Reverse** field is cleared while the **Journal** posted field is marked, and the **Latest journal number** field is updated with the journal number of the revocation transaction. The **Journal number** field is also updated with reversal journal number.
