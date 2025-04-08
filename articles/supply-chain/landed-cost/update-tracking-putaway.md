---
title: Update tracking for put away
description: Learn how to set up and run the Update tracking for put away periodic task, including a step-by-step process running periodic tasks.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 08/02/2021
ms.reviewer: kamaybac
ms.search.form:
---

# Update tracking for put away

[!include [banner](../includes/banner.md)]

The *Update tracking for put away* periodic task is designed to be run as a nightly recurring batch. It identifies which voyages have received all inventory transactions, and which voyages don't have a value for the actual end date. It then sets the actual end date to the current date as required.

*Container activities* are created for each *leg* of a journey for each *shipping container*. These values are defined by the journey template that is selected when a voyage is created. For each container activities record, values can be set for the **Start date**, **Estimated end date**, and **Actual end date** fields. These fields can be updated when confirmation is received that a leg has begun or has been completed.

Typically, information that is related to confirmed dates is provided by a third party, such as a freight forwarder, because these actions are maintained outside Microsoft Dynamics 365 Supply Chain Management. However, information from a third party isn't required to track the arrival of goods from a journey leg into the warehouse (as marked by the putaway of goods). Therefore, tracking can be determined based on information in Dynamics 365 Supply Chain Management.

To set up and run the *Update tracking for put away* periodic task, follow these steps:

1. Go to **Landed Cost \> Periodic tasks \> Update tracking for put away**.
1. In the **Update tracking for put away** dialog box, in the **Parameters** section, set the following fields:

    - **Leg** – Select the unique identification name/number for the part of a journey that you want to update tracking for. The selected value must represent the arrival of the voyage at the warehouse.
    - **Activity** – Select the activity that was undertaken during the selected leg. These values are assigned per journey template line in the tracking control center.

1. To limit the set of records that should be included in the update, on the **Records to include** FastTab, select the **Filter** button. A standard query dialog box appears, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management. The fields here are read-only and show values that are related to your query.
1. On the **Run in the background** FastTab, set up batch and scheduling options as you require, just as you might do for other types of jobs in Supply Chain Management.
1. Select **OK** to apply your settings, and to run or schedule the update.
