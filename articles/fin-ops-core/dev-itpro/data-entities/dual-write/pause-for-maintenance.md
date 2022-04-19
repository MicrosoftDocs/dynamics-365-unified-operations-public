---
title: Pause dual-write for maintenance
description: This topic explains how to pause a table map.
author: nhelgren
ms.date: 02/09/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: nhelgren
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Pause dual-write for maintenance

[!include [banner](../../includes/banner.md)]



You can pause table maps, either manually or automatically via rules. By pausing table maps, you help ensure business continuity, especially during planned or unplanned maintenance. While the app is being maintained, users can continue to do their work and create records.

When you pause a table map that is in the **Running** state, all records that have been created or updated are queued until you resume the table map. The queued records are stored in secure Microsoft Azure storage. They are then played back when you resume the table map and put it back into the **Running** state.

> [!NOTE]
> While a table map is in the **Paused** state, the following limits apply: 
> - A pause can only be active for a maximum of 7 days.
> - There is a maximum size of 1 GB worth of records that can be queued. 
>
> Paused maps must be reactivated in less than 7 days from the pause start date, or else pending changes can be lost impacting data consistancy. 
> Reaching either one of these limits will result in a block on all additional records until the sync is resumed and the queued records are caught up. Users will have to manually resume the job in order for the catch up to be completed.


Records that have been created or updated for a table map that is in the **Paused** state can be viewed on the **Queued records** tab for each table map.

![Queued records tab.](media/Queued-Insights1.png)

The **Total queued record count** line shows the total number of records that have been queued for a given table map. You can select **Load more** to view additional records in the paginated view. You can also filter the records by the integration key.

When you resume the table map, its state is changed from **Paused** to **Running**, and the records are written from the queue to the destination app. Some records might error out and fail to be written for various reasons, such as business validations in the destination app. In these cases, the records will remain in the queue and can be viewed on the **Catch-up errors** tab. For more information, see [Catch-up errors from pausing a table map](errors-and-alerts.md#catch-up-errors-from-pausing-a-table-map).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
