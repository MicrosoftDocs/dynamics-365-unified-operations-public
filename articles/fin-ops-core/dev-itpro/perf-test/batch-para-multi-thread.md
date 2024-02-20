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

There are three common approaches to break up large batch jobs:
1. Individual task modeling
2. Batch bundling
3. Top picking pattern

### Individual task modeling 
There are some advantages to using individual task modeling to break up batch jobs:
 - Works well with a small number of work items of any type
 - Simple to write
 - Best fits to create dependency among the work items

Some disadvantages of using individual task modeling:
 - When the number of tasks is big, the extra overhead impedes the performance due to the batch throttling mechanism and delays between batch task runs
 - Negatively affects other batch jobs as it's putting pressure on the framework tables.

### Batch bundling 
There are some advantages to using batch bundling:
 - Works well for a simple even workload
 - No need for a staging table, no extra maintenance by the application code
 - Not over-pollutes the batch table.
 - Bypasses batch throttling mechanism when bundle size is chosen properly

Some disadvantages when using batch bundling:
 -  When distribution of the work is not equal, performance degrades since batch tasks finish processing with a huge difference in time
 -  In some cases, it's possible to distribute the workload evenly.
 
### Top picking pattern

Advantages to using top picking pattern: 
 - Bypasses batch throttling mechanism
 - Works well with an uneven workload
 - Not over-pollutes the batch table

 Disadvantages using top picking pattern:
 - An extra staging table needed to track the progress
 - When a very large number of small work items need to be processed, tracking the work items through the staging table affects the performance a bit.

### Current mechanism for Journal batch processing 

Currently, journal batch posting uses bundling mechanism to schedule batch tasks. This approach leads to an excessive number of bundles being generated, especially if there is a high volume of journals to be posted.
Each of these bundles create a batch task, and the concurrent execution of numerous batch tasks contributes to a high DTU load and affects the system’s overall performance. While it is possible to manually adjust 
the bundle size to a fixed value, this approach lacks flexibility to manage varying volumes of journal posting. 

### Why use Top-picking pattern in journal batch posting? 
The benefit of using top picking pattern in journal posting: 
 - Reduced DTU usage - By limiting the number of batch tasks, DTU is decreased.
 - Optimal performance - Each task in this pattern starts processing the next journal as soon as it completes the previous one. The workload of each task is balanced, the performance will be optimal based on number
of batch tasks scheduled.

The top-picking pattern is utilized when the feature is enabled and the posting process is running in the batch mode. 
There is a limitation: During global journal posting, especially when selected journals span multiple companies, the top picking feature won’t be applied to avoid creating an excessive number of tasks across 
multiple companies.

### Changes in journal posting process when using top-picking

Posting journals have the following changes when using the top-picking pattern: 
 - Adding a journal to queue:
     - Every individual journal is added to the journal post queue
     - When journal are split into multiple journals, the split journals are added to the journal post queue.
 - Retrieving journal from queue:
     - Journal posting task consistently retrieves one journal from the queue and proceed to post
 - Delete record from queue:
     - Cleanup any record older than 14 days
     - Remove records from queue after retrieved the record
 - Posting:
     - Each batch task continues posting journals until no journal can be retrieved from queue
     - The actual posting process remains unchanged.

### Related class and table 
LedgerJournalMultiPost: 
  - Add selected journal into top picking queue
  - Schedule limit number of batch tasks for top picking batch post
LedgerJournalBatchPost:
 - Retrieve record from top picking queue
 - Post one by one until nothing in the top picking queue
LedgerJournalPostQueue:
 - Top picking queue for journal posting
 - Each batch job has a unique GUID stored in this queue
LedgerJournalPostTopPickingFeature:
 - Journal batch posting using top picking feature class
LedgerJournalMultiCompanyPostController:
 - When posting journals starts from this controller indicates it's multi-company journal post, top picking won't be used.

Step 3: Add a reference link on this page. Financial journal posting performance - Finance | Dynamics 365 | Microsoft Learn

