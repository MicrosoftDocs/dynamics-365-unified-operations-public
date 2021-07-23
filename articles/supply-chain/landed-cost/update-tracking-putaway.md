---
title: Update tracking for put away
description: Update tracking identifies voyages that have received all inventory transactions, and voyages that don't have an actual end date. It then populates the actual end date with the current date.
author: XXXX
ms.date: MM/DD/YYYY
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: XXXX
ms.search.validFrom: YYYY-MM-DD
ms.dyn365.ops.version: 10.0.18
---

# Update tracking for put away

[!include [banner](../includes/banner.md)]

Update tracking for put away is a periodic task designed to be run as a nightly recurring batch. It identifies which voyages have received all inventory transactions, and which don't have a value for actual end date. It then populates the actual end date with the current date if needed.

*Container activities* are created for each *leg* of a journey for each *shipping container*. These values are defined by  the journey template selected when creating a voyage. Each container activities record can record a **Start date**, **Estimated end date**, and an **Actual end date**. These fields can be updated on receiving confirmation that a leg has commenced or been completed.

Information related to confirmed dates is typically provided by a third party, such as a freight forwarder, as these actions are maintained outside of Dynamics 365 Supply Chain Management. Tracking the arrival of goods from a journey leg into the warehouse (as marked by the put away of goods) does not require information from a third party and can therefore be determined based on information within Dynamics 365 Supply Chain Management.

To set up and run update tracking for put away, do the following steps:

1. Go to **Landed Cost \> Periodic tasks \> Update tracking for put away**.
1. The **Update tracking for put away** dialog opens. Make the following settings in the **Parameters** section:
    - **Leg** – Select the unique identification name/number for the part of a journey you want to update tracking for. The selected value must represent the arrival of the voyage at the warehouse.
    - **Activity** – Select the activity undertaken during the selected leg. These values are assigned per journey template line from within the tracking control center.
1. To limit the set records that should be included in the update, expand the **Records to include** FastTab and select the **Filter** button. A standard query dialog opens, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management. The fields here are read-only and show values that are related to your query.
1. On the **Run in the background** FastTab, set up batch and scheduling options as you require, just as you might do for other types of jobs in Supply Chain Management.
1. Select **OK** to apply your settings and run or schedule the update.
