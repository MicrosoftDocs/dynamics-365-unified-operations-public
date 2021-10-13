---
title: Pause dual-write for maintenance
description: This topic explains error logs and alert notifications that can help you troubleshoot issues.
author: nhelgren
ms.date: 10/13/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: nhelgren
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Pause dual-write for maintenance

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Pausing a table map lets you address planned or unplanned maintenance. To ensure business continuity, especially during planned or unplanned maintenance, you can pause table maps, manually or automatically via rules. This lets users continue to do their work and create records while the app is being recovered from maintenance.

When you pause a table map that is in the **Running** state, all records created or updated are queued until you resume the table map. The queued records are stored in secure Azure storage and replayed back when you resume and put the table map back into **Running** state.

> [!NOTE]
> When a table map is in the **Paused** state, there are limits to the number of records and amount of time you can queue the records. Whichever limits occurs first will apply. We will start with soft limits and eventually enforce harder limits to protect you from exceeding the storage limits.

Records created or updated for a table map in the **Paused** state can be viewed under **Queued records** for each table map.

![Queued records insights.](media/Queued-Insights1.png "Queued records insights")

The **Total queued record count** shows the total number of records queued for a given table map. You can click on **Load more** to see additional records in the paginated view. You can also filter the records on the integration key.

When you resume the table map, it switches from the **Pause** state to the **Running** state and writes the records from the queue to the destination application. It is possible that some records error out and fail to write due to various reasons including business validations on destination app. In these cases, the records will continue to remain in the queue and can be viewed under the **Catch-up errors** tab.

![Queued records retry selected.](media/Queued-Insights-retry-selected3.png "Queued records retry selected")

The detailed Error message will help you fix the underlying issue after which you could **Retry selected** records or **Retry All** records. Once the retry is successful, **Retry status** will be marked as **Completed**.

![Queued records completed.](media/Queued-Insights-retry-selected4.png "Queued records retry selected")

> [!NOTE]
> Errored records will be available in the queue for 7 days after which will the queue will be purged. In some cases, you may no longer need these records and they can be deleted from the queue.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
