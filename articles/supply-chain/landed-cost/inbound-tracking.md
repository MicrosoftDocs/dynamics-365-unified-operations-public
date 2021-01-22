---
# required metadata

title: Track inbound voyages and shipping container journeys
description: Use the Inbound tracking page to track the progress of your voyages and shipping container journeys.
author: RichardLuan
manager: tfehr
ms.date: 01/13/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ITMContainerActivityTable
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: riluan
ms.search.validFrom: 2021-01-13
ms.dyn365.ops.version: Release 10.0.17
---

# Track inbound voyages and shipping container journeys

[!include [banner](../includes/banner.md)]

Use the **Inbound tracking** page to track the progress of your voyages and shipping container journeys. Each voyage and journey is broken down by *activities*, each of which has its own row on this page. Use it to view and enter estimated dates and actual dates by activity. Depending on your [Tracking control center](delivery-information-setup.md#tracking-control-center) setup, these activities will normally automatically show the estimated landing date at the final destination. Again, depending on the setup, the final date will usually also update the purchase order line delivery date or confirmed date. For transfer order lines, you can set up the system to update the receipt date.

To open the the **Inbound tracking** page, go to **Landed cost \> Tracking \> Inbound tracking**.

## Filter the activities list

Use the **Voyage** and **Shipping container** fields at the top of the **Inbound tracking** page to view only those activities associated with your selected voyage and/or shipping container.

## Update tracking information

To update the schedule for a voyage or journey, enter the start date on the first activity to update the estimated end date on the last activity. The setup in the [Tracking control center](delivery-information-setup.md#tracking-control-center) for each leg and journey template will determine the estimated lead times. The estimated end dates will use the lead time from the start date of that activity. Recording the actual end date will update the start date of the next activity with the same date as the previous activities actual end date. The actual lead time will be updated allowing comparison and analysis to occur. Additional notes can be entered in the note field.

The order of the activities in the grid is determined by the order of the legs in the relevant journey template. If the legs of the attached journey change order, the tracking control will likewise change.

You can update the dates for all containers by selecting **Update start date** or **Update actual end date** on the Action Pane. Alternatively, the dates can be entered per container on the shipment to allow greater flexibility as containers can be split in a multi-journey environment.

## Action Pane commands

The Action Pane of the **Inbound tracking** page provides actions for working with inbound voyages and journeys.

| Action | Description |
| --- | --- |
| **Edit** | Edit a voyage or shipping container journey. |
| **New** | Create a new voyage or shipping container journey. |
| **Delete** | Delete a selected voyage or shipping container journey. |
| **Update start date** | Update the start date for an activity for all containers within a voyage. When the start date of a given activity or leg of a journey is updated, the subsequent estimated start dates will update in accordance with the specified lead time. |
| **Update actual end date** | Update the end date for an activity for all containers within a voyage. When the end date of a given activity is updated, the subsequent activities will update in accordance with the specified lead time. |
| **Add activities** | Manually add an activity to a voyage. An example of this might be fumigation. The addition may result in a change in the confirmed delivery date of the goods within the vessel or voyage. When an activity is added to the journey, the estimated days will not populate until the start date of a journey leg is updated. |

## Information and settings on the Overview tab

The **Overview** tab shows a list of all of the activities that belong to the **Voyage** and **Shipping container** selected at the top of the page. The following table describes each of the settings available for each activity.

| Setting | Description |
| --- | --- |
| **Leg** | Shows the leg ID for the activity, as defined by the journey template. |
| **Mode of Delivery** | The delivery method expected for this activity. |
| **Activity** | Usually identifies the job or task that associated with the activity. Common examples include *Sailing* or *Clearance*. |
| **Description** | A longer description of the activity. |
| **Start Date** | Initially shows the estimated start date for the activity but once the previous activity's actual end date has been entered, this becomes the actual start date. This is used to determine the estimated end date based on the lead time. |
| **Estimated end date** | This is calculated based on the start date and lead time. You wouldn't normally edit it directly here. |
| **Actual end date** | A user should update this as soon as possible once the activity has occurred. The actual lead time is then updated. |
| **Estimated days** | The estimated time (in days) required to complete this activity. |
| **Actual days** | The actual time (in days) required to complete this activity. |
| **Note** | Use this to add miscellaneous notes and details about the activity. |

## Information and settings on the General tab

The **General** tab shows more information about the leg previously selected on the **Overview** tab. It repeats some information from the Overview tab and also provides additional information about the selected leg.
<!-- KFM: There are many fields that are not described here. Add them and follow up with Natalie. -->

| Setting | Description |
| --- | --- |
| **Start date** | This is normally the estimated start date for the activity but once the previous activity's actual end date has been entered this would become the actual started tracking date. This is used to determine the estimated end date based on the lead time. |
| **Estimated end date** | This is not normally adjusted; it comes from the start date and lead time. |
| **Actual end date** | This should be updated as soon as possible once the activity has occurred. The actual lead time is then updated. |
| **Actual days** | Actual number of days for this activity. |
