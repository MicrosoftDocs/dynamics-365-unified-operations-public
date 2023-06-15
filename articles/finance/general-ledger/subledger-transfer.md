---
# required metadata

title: Subledger transfer to the general ledger
description: This article describes capabilities that are related to the subledger transfer process in General ledger.
author: RyanCCarlson2
ms.date: 02/08/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalSetup, LedgerJournalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2020-01-18
ms.dyn365.ops.version: AX 10.0.8

---

# Subledger transfer to the general ledger

[!include [banner](../includes/banner.md)]

This article describes capabilities that are related to the rules for transferring batches of subledger journal entries.

In version 8.1, changes were made to allow the transfer of rules, which deprecated the **Synchronous** option. For more information, see [Removed or deprecated features for finance and operations](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md?toc=%2fdynamics365%2ffinance%2ftoc.json#finance-and-operations-81-with-platform-update-20).

The following options are available for transferring subledger batches:

- **Asynchronous** – Transfer of the subledger accounting entries to the general ledger is scheduled immediately. The General ledger voucher will be recorded as soon as resources are available to process the request on the server.
- **Scheduled batch** – The subledger accounting entries that must be transferred are added to the processing queue in General ledger. The entries in the queue will be processed in the order that they are received in. Each General ledger voucher will update accounts at the scheduled time if resources are available to process the batch job on the server.

Improvements were made to enhance the performance of the **Asynchronous** option. This feature is enabled under the feature name **Subledger transfer to General Ledger performance optimization**.

The functionality for asynchronous transfer of subledger batches helps improve the transfer of data from the subledger to the general ledger. By grouping sets of smaller transactions and transferring the transactions in groups, the functionality processes transactions more efficiently. When transactions are grouped, the batch server's resources are used more efficiently.

Asynchronous transfer of subledger batches requires that the batch server is set up, online, and working because batch tasks are created for immediate execution on the batch server. When the  **Subledger transfer to General Ledger performance optimization** feature is enabled, the **Process automation** system batch job named **Process automation polling system job** must also be enabled. For more information, see [Process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

The efficiency change at the batch level uses a single recurring batch job for all legal entities in the system. At runtime, a new batch job is created to process the required records that haven't yet been transferred. More settings can be controlled from the **Process automation** page in system administration. On that page, you can modify the background process, change the frequency, and define a sleep period. 

>[!NOTE]
>Review any scheduled batch jobs of **"Batch transfer for subledger journals"** that could conflict with this new process automation job. If you only use Asynchronous transfer for all document types, you'll no longer need this batch job running. The use of scheduled batch for transfer to General Ledger should only be required in special cases when you wish to control a specific document type that is transfered to the General Ledger at a specific times. 

For more information about process automation setup, see [Process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

