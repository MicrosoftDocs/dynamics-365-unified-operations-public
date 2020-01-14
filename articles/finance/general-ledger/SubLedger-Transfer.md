---
# required metadata

title: General Ledger Parameters
description: This topic describes capabilities in Microsoft Dynamics 365 for Finance related to the subledger transfer process in the general ledger.
author: roschlom
manager: AnnBe
ms.date: 09/09/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalSetup, LedgerJournalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 10.0.0

---

# Subledger transfer to the General ledger process

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes capabilities in Microsoft Dynamics 365 for Finance related to the subledger journal batch transfer rules.

Version 8.1 changed the allowed transfer rules, deprecating the Synchronous option. 
https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features?toc=/dynamics365/finance/toc.json#finance-and-operations-81-with-platform-update-20

The remaining choices are: 
 - Asynchronous - this choice will schedule the transfer of the subledger accounting to the general ledger immediately. The actual recording of the general ledger voucher will occur as soon as resources are free to process this request on the server. 
 - Scheduled batch - this choice will queue the transfer of the subledger accounting to the generel ledger for the next batch job to process. The recording of the general ledger vocher will occur at the schedule defined as long as resources are free to process this batch job on the server. 
 
 
 Version 10.0.8 has improved the performance of the Asynchrounous option. This is a feature that is enabled under the feature name 'Subledger transfer to General Ledger performance optimization'. 
 This functionality improves the the transfer of data from the subledger to the General Ledger. It allows the process to be more efficient and group sets of smaller transactions to transfer together allowing for a more efficient use of the batch server. 
This does require the batch server to be up and functioning for Asynchrounous feature to work. 
