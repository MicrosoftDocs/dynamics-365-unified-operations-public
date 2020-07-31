---
# required metadata

title: Reverse posted lease transactions
description:  
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

Any transactions created through the Asset leasing module can be reversed. Transactions reversed through the module update the transactions tables and therefore the carrying values of the lease liability and right-of-use asset.

1.	To create a reversing transaction for a lease, select the transaction from the Asset transactions or Liability transactions form and click Reverse transaction in the ribbon of the transactions form.
2.	A parameters page will appear where the user can edit the date on which reversing entry will be posted. The date field is auto populated with the transaction posting date of the selected record. Note, the reversing entry cannot be posted earlier than the original posting date of the selected transaction.
3.	Upon clicking OK, a journal entry will be posted reversing the selected entry. The reversal is shown in the transactions form and the net total current balance on form is updated.
4.	Upon clicking Reverse tracing, a new form opens and displays the original and reversed transactions with a linked number known as trace number. Tracking of reversals is also available on the schedules for ease of understanding and visibility
5.	Upon reversal the Latest journal number field captures the journal number of reversals and is updated with journal number subsequently where the reversal has been revoked. The Reversed check box is marked to indicate the reversal and the Journal posted field is unmarked concurrently.
6.	To revoke a reversed transaction, select either the original transaction or its reversal on the transactions form and click Reverse transaction again. A parameter page appears notifying the user that this is a revocation of an earlier reversal and user can edit the date for posting for this revocation, however the date field has general business validations for allowed dates.
7.	Upon clicking OK, a journal entry will be posted reversing the selected entry. The reversal is shown in the transactions form and the net total current balance on form is updated and re-instated as it was before the first reversal thus negating the impact of reversal on the balances.
8.	Upon clicking Reverse tracing, another form opens and displays the original and reversed transactions with a linked number known as trace number.
9.	Tracking of revocation is also available on the transactions form, the Reverse field is unmarked while Journal posted field is marked concurrently, and the Latest journal number field is updated with the revocation transaction journal number.

