---
# required metadata

title: Subledger transfer to the General ledger
description: This topic describes capabilities in Microsoft Dynamics 365 Finance related to the subledger transfer process in the general ledger.
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
ms.search.validFrom: 2020-01-18
ms.dyn365.ops.version: AX 10.0.8

---

# Subledger transfer to the General ledger

[!include [banner](../includes/banner.md)]

This topic describes capabilities in Microsoft Dynamics 365 Finance that are related to the rules for transferring batches of subledger journal entries.

In version 8.1, changes were made to allow the transfer of rules, which deprecated the Synchronous option. For more information, see [Removed or deprecated features for Finance and Operations](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features?toc=/dynamics365/finance/toc.json#finance-and-operations-81-with-platform-update-20).

The following options are available for transferring subledger batches. 

 - Asynchronous – This option will immediately schedule the transfer of the subledger accounting entries to the general ledger. The general ledger voucher will be recorded as soon as resources are free to process this request on the server. 

- Scheduled batch – This option will add the subledger accounting entries that are being transferred to the processing queue in the general ledger, where the entries will be processed in order received. The general ledger voucher will be recorded at the scheduled time if resources are free to process this batch job on the server. 
 
In version 10.0.8, improvements were made to enhance the performance of the Asynchrounous option. This feature is enabled under the feature name **Subledger transfer to General Ledger performance optimization**. 
 
This functionality improves the transfer of data from the subledger to the general ledger. It allows the process to be more efficient, and it groups together sets of smaller transactions to transfer. This allows for a more efficient use of the batch server. 
This functionality requires that the batch server be set up, online, and functioning in order for the Asynchrounous transfer option to work. 
