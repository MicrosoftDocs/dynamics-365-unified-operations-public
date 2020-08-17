---
# required metadata

title: Reverse posted lease transactions
description: This transaction lists the steps for reversing a posted lease transaction, since any transaction that's created in Asset leasing can be reversed.  
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

2. A dialogue will open where you can edit the date that the reversing entry will be posted on. The transaction posting date of the transaction you selected is the default entry on the **Date** field. Note that the reversing entry can't be posted earlier than the original posting date of the selected transaction.

   When you click **OK**, a journal entry will be posted reversing the entry you selected. The reversal is shown in the **Asset transactions** or **Liability transactions** and the net total of the current balance of which displayed on the page is updated.

   When you click **Reverse tracing**, a new page opens and displays the original and reversed transactions with a linked number known as trace number. You can also track reversals using the lease schedules for ease of understanding and visibility.

   When a transaction is reversed, the **Latest journal number** field in relevent schedule form shows the journal number of the reversal transactions, and is updated with journal number. The **Reversed** check box is marked to indicate the transaction is reversed and the **Posted** field is marked concurrently.

3. To revoke a reversed transaction, select either the original transaction on the **Schedule** to follow the process of **Create journal** and the journal will be created and need to be posted manually, or by selecting original transaction on the **Transactions** form and click **Reverse transaction** again. A parameter page appears that tells you that this is a revocation of an earlier reversal, and that you can edit the date for posting for this revocation. However the **Date** field has general business validations for allowed dates.

   When you click **OK**, a journal entry will be posted reversing the selected entry. The reversal is shown in the transactions form and the net total current balance on form is updated and re-instated as it was before the first reversal thus negating the impact of reversal on the balances.

   When you click **Reverse tracing**, a dialog opens that displays both the original and reversed transactions with a linked number, known as trace number.

   You can also track revocations using the respective **Schedules** page. The **Reverse** field is cleared while the **Journal** posted field is marked, and the **Latest journal number** field is updated with the journal number of the revocation transaction and **Journal number** updated with reversal journal number.
