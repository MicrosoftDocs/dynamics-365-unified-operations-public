---
title: Pause dual-write for maintenance
description: Learn how to pause a dual-write table map for maintenance, how to resume syncronization, and skip to live synchronization.
author: nhelgren
ms.author: jaredha
ms.topic: article
ms.date: 04/03/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
ms.custom: 
  - bap-template
  - sfi-image-nochange
---

# Pause dual-write for maintenance

[!include [banner](../../includes/banner.md)]

You can pause table maps either manually or automatically through rules. Pausing table maps helps ensure business continuity, especially during planned or unplanned maintenance. While the app is being maintained, users can continue to do their work and create records.

When you pause a table map that's in the **Running** state, the system queues all created or updated records until you resume the table map. The system stores the queued records in secure Microsoft Azure storage. When you resume the table map and put it back into the **Running** state, the system plays back the queued records.

> [!NOTE]
> While a table map is in the **Paused** state, the following limits apply:
>
> - A pause can be active for a maximum of only one day.
> - There's a maximum size of 1 GB worth of records that can be queued.
>
> You must reactivate paused maps in less than one day from the pause start date, or else pending changes can be lost, impacting data consistency.
> Reaching either one of these limits results in a block on all additional records until the sync is resumed and the queued records are caught up. Users must manually resume the job to complete the catch up.

You can view records that you created or updated for a table map that's in the **Paused** state on the **Queued records** tab for each table map.

:::image type="content" source="media/Queued-Insights1.png" alt-text="Screenshot of the Queued records tab.":::

The **Total queued record count** line shows the total number of records that the system queued for a given table map. Select **Load more** to view more records in the paginated view. You can also filter the records by the integration key.

## Resume synchronization

When you resume the table map, its state changes from **Paused** to **Running**, and the process writes records from the queue to the destination app. Three options affect how queued records are managed when synchronization resumes:

- **Catch up synchronization of queued records** - The process handles records in the queue before resuming live synchronization of new records. New records created for the map continue to be added to the queue rather than synchronized through live synchronization until all records in the queue are processed. Live synchronization for new records of the mapped tables continues when all records in the queue are processed.
- **Skip to live synchronization preserving queued records to catch up errors for retry** - Live synchronization of new records for the table map resumes immediately. The process moves queued records to the **Catch-up errors** list where you can retry processing of the records. Records in the **Catch-up errors** list that are retried are processed asynchronously.
- **Skip to live synchronization and discard queued records** - Live synchronization resumes immediately for the new records created for the table map. The process discards any queued records from the queue and doesn't synchronize them with the destination app.

Some records might error out and fail to be written for various reasons. For example, business validations in the destination app. In these cases, the records remain in the queue and you can view them on the **Catch-up errors** tab. For more information, see [Catch-up errors from pausing a table map](errors-and-alerts.md#catch-up-errors-from-pausing-a-table-map).

## Skip to live synchronization

The **Skip to live sync** action is available for a table map while it's resuming and queued records are being processed. When you resume the table map, if you select the **Catch up synchronization of queued records** option, the process handles records in the queue before resuming live synchronization of new records. It's possible that the queue might be processed more slowly than desired. For example, there might be a high number of records in the queue, or a high volume of new records being created, adding records to the queue faster than the queue is being processed. When the queue processes more slowly than desired, you can skip to live synchronization.

When you select the **Skip to live sync** action, live synchronization of new records for the table map resumes immediately rather than adding new records to the queue. If you select the **Preserve queued records to catch-up errors** option, the process moves all remaining records in the queue to the **Catch-up errors** list where you can retry processing of the records. Records in the **Catch-up errors** list that are retried are processed asynchronously. If you don't select the **Preserve queued records to catch-up errors** option, the process discards any records remaining in the queue and doesn't synchronize them with the destination app.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
