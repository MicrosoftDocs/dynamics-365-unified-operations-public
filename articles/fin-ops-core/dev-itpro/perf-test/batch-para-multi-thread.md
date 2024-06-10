---
title: Batch parallelism and multi-threading in Dynamics 365 finance and operations apps
description: Learn about batch parallelism and multi-threading in Microsoft Dynamics 365 finance and operations apps, including a table that outlines pros and cons for approaches.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 06/07/2024
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2024-02-24
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 7b605810-e4da-4eb8-9a26-5389f99befcf
---

# Batch parallelism and multi-threading in Dynamics 365 finance and operations apps

[!include [banner](../includes/banner.md)]

This article describes the different approaches that are available for breaking large batch jobs into small fragments in Microsoft Dynamics 365 finance and operations apps.

Three approaches can be used to break up large batch jobs:

- Individual task modeling
- Batch bundling
- Top picking pattern

Each approach has pros and cons, as described in the following table.

| Approach | Pros | Cons |
|---|---|---|
| Individual task modeling | <ul><li>It works well with a few work items of any type.</li><li>It's simple to write.</li><li>It's the best fit for creating dependency among the work items.</li></ul> | <ul><li>When there's a large number of tasks, the extra overhead impedes performance because of the batch throttling mechanism and delays between batch task runs.</li><li>It negatively affects other batch jobs.</li></ul> |
| Batch bundling | <ul><li>It works well with a simple, even workload.</li><li>There's no need for a staging table and no extra maintenance by the application code.</li><li>It doesn't over-pollute the batch table.</li><li>It bypasses the batch throttling mechanism when the appropriate bundle size is selected.</li></ul> | <ul><li>When the work isn't evenly distributed, performance degrades because batch tasks finish processing at different times.</li><li>In some cases, it's possible to distribute the workload evenly.</li></ul> |
| Top picking pattern | <ul><li>It works well with an uneven workload.</li><li>It doesn't over-pollute the batch table.</li><li>It bypasses the batch throttling mechanism.</li></ul> | <ul><li>An extra staging table is needed to track the progress.</li><li>When a large number of small work items must be processed, tracking the work items through the staging table affects performance.</li></ul> |

## Current journal batch processing

Currently, journal batch posting uses a bundling mechanism to schedule batch tasks. As a result, an excessive number of bundles is generated, especially if a high volume of journals must be posted. Each bundle creates a batch task, and the concurrent execution of numerous batch tasks contributes to a high database transaction unit (DTU) load and affects overall performance. Although the bundle size can be manually adjusted to a fixed value, this approach lacks the flexibility to manage varying volumes of journal posting.

## Benefits of using the top picking pattern in journal batch posting

Use of the top picking pattern in journal posting has the following benefits:

- **Reduced DTU use** – Because the number of batch tasks is limited, DTU use is reduced.
- **Optimal performance** – Each task starts to process the next journal as soon as it completes the previous journal. The workload of each task is balanced. The performance is optimized based on the number of batch tasks that are scheduled.

When global journals are posted, if the selected journals span multiple companies, the top picking pattern isn't used. This behavior prevents an excessive number of tasks from being created across multiple companies.

### Changes in the journal posting process when the top picking pattern is used

>[!IMPORTANT]
> Beginning with Dynamics 365 release 10.0.39, users can select top picking pattern for batch job posting, which provides additional performance gains, reducing system usage and a more balanced workload on tasks by optimizing the concurrent tasks.

The journal posting process has the following changes when the top picking pattern is used:

- Adding a journal:

    - Every individual journal is added to the journal posting job.
    - When journals are split into multiple journals, the split journals are added to the journal posting job.

- Retrieving a journal:

    - The journal posting process retrieves one journal from the queue and posts it.

- Deleting a record:

    - The journal posting process cleans up all records that are older than 14 days.
    - The process removes records from the posting queue after the record is retrieved.

- Posting:

    - Each batch task continues to post journals until all journals are posted from the posting queue.

- Batch job history:

    - The top picking posting mechanism splits the posting process into multiple parallel sub-tasks to improve the overall performance. If one of the sub-tasks fails, other tasks continue to work. The overall status of the batch job is shown as **Ended**.
    - For all log messages, go to the batch job history, and select **Log** to view the full message.
    - To view the log for an individual batch task, go to the batch job history, select **View tasks**, and then select **Log** for the individual batch task.
    - For more information, see [Create a batch job](../../fin-ops/sysadmin/create-batch-job.md).

### Related classes and tables

- LedgerJournalMultiPost:

    - Add the selected journal to the top picking queue.
    - Schedule a limited number of batch tasks for the top picking batch post.

- LedgerJournalBatchPost:

    - Retrieve a record from the top picking queue.
    - Post one record at a time until the top picking queue is empty.

- LedgerJournalPostQueue:

    - Use the top picking queue for journal posting.
    - For each batch job, a globally unique identifier (GUID) is stored in this queue.

- LedgerJournalPostTopPickingFeature:

    - Journal batch posting uses the top picking feature class.

- LedgerJournalMultiCompanyPostController:

    - When journal posting starts from this controller, it's multicompany journal posting. Top picking isn't used.
