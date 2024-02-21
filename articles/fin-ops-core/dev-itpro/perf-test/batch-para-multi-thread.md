---
title: Batch parallelism and multi-threading in Dynamics 365 finance and operations
description: This article describes batch parallelism and multi-threading in Dynamics 365 finance and operations
author: twheeloc
ms.date: 02/20/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: twheeloc
ms.search.validFrom: 2024-02-24
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 7b605810-e4da-4eb8-9a26-5389f99befcf
---

# Batch parallelism and multi-threading in Dynamics 365 finance and operations

[!include [banner](../includes/banner.md)]

This article describes the different approaches available to break large batch jobs into small fragments in Dynamics 365 finance and operations.

There are three approaches to break up large batch jobs:
1. Individual task modeling
2. Batch bundling
3. Top picking pattern

There are pros and cons to using each of these approaches:
Individual task modeling pros: 
   - Works well with a small number of work items of any type
   - Simple to write
   - Best fits to create dependency among the work items
Cons: 
  - When there's a large number of tasks, the extra overhead impedes performance due to the batch throttling mechanism and delays between batch task runs
  - Negatively affects other batch jobs 

Batch bundling pros: 
  - Works well for a simple even workload
  - No need for a staging table, no extra maintenance by the application code
  - Doesn't overpollute the batch table
  - Bypasses batch throttling mechanism when bundle size is chosen properly
Cons: 
  - When distribution of the work is not equal, performance degrades since batch tasks finish processing with a huge difference in time
  - In some cases, it's possible to distribute the workload evenly.
 
Top picking pattern pros:
 - Bypasses batch throttling mechanism
 - Works well with an uneven workload
 - Not over-pollutes the batch table
Cons:
 - An extra staging table needed to track the progress
 - When a very large number of small work items need to be processed, tracking the work items through the staging table affects the performance a bit.


### Current journal batch processing 

Currently, journal batch posting uses a bundling mechanism to schedule batch tasks. This leads to an excessive number of bundles being generated, especially if there's a high volume of journals to be posted. Each of these bundles create a batch task and the concurrent execution of numerous batch tasks contributes to a high DTU load and affects overall performance. While it's possible to manually adjust the bundle size to a fixed value, this approach lacks flexibility to manage varying volumes of journal posting. 

### Why use top picking pattern in journal batch posting? 
The benefits of using top picking pattern in journal posting are: 
 - Reduced DTU usage: By limiting the number of batch tasks, DTU is decreased.
 - Optimal performance: Each task starts processing the next journal as soon as it completes the previous one. The workload of each task is balanced, the performance is optimized based on the number of batch tasks scheduled.
During global journal posting and when the selected journals span multiple companies, the top picking feature isn't used to avoid creating an excessive number of tasks across multiple companies.

### Changes in journal posting process when using top picking

The posting journal process has the following changes when using the top picking pattern: 
 - Adding a journal:
     - Every individual journal is added to the journal post job
     - When journals are split into multiple journals, the split journals are added to the journal post job
 - Retrieving journal:
     - The journal posting process retrieves one journal from the queue and posts
 - Delete record:
     - Cleanup all records older than 14 days
     - Remove records from posting queue after retrieved the record
 - Posting:
     - Each batch task continues posting journals until all journals are posted from the posting queue


### Related class and table 
LedgerJournalMultiPost: 
  - Add selected journal to top picking queue
  - Schedule limit number of batch tasks for the top picking batch post
LedgerJournalBatchPost:
 - Retrieve a record from the top picking queue
 - Post one by one until the top picking queue is empty
LedgerJournalPostQueue:
 - Top picking queue for journal posting
 - Each batch job has a unique GUID stored in this queue
LedgerJournalPostTopPickingFeature:
 - Journal batch posting using top picking feature class
LedgerJournalMultiCompanyPostController:
 - When posting journals starts from this controller indicates it's multi-company journal post, top picking won't be used.



