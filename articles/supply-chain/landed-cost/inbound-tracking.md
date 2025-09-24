---
title: Track inbound voyages and shipping container journeys
description: Learn how you can use the Inbound tracking page to track the progress of your voyages and shipping container journeys with an outline on filtering activity lists.
author: prasungoel 
ms.author: prasungoel 
ms.reviewer: kamaybac
ms.search.form: ITMContainerActivityTable
ms.topic: how-to
ms.date: 09/19/2025
ms.custom: 
  - bap-template
---

# Track inbound voyages and shipping container journeys

[!include [banner](../../includes/banner.md)]

The **Inbound tracking** page lets you track the progress of your voyages and shipping container journeys. Each voyage and journey is broken down by *activities*, each of which has its own row on the page. You can use the page to view and enter estimated dates and actual dates by activity.

Typically, depending on the setup in the [Tracking control center](delivery-information-setup.md#tracking-control-center), these activities automatically show the estimated landing date at the final destination. Also depending on the setup, the final date usually updates the delivery date or confirmed date on purchase order lines. For transfer order lines, you can set up the system to update the receipt date.

To open the **Inbound tracking** page, go to **Landed cost \> Tracking \> Inbound tracking**.

## Filter the activities list

You can use the **Voyage** and **Shipping container** fields at the top of the **Inbound tracking** page to filter the page so that it shows only activities that are associated with the selected voyage and/or shipping container.

## Update tracking information

To update the schedule for a voyage or journey, enter the start date for the first activity. The estimated end date of the last activity is then updated. The setup for each leg and journey template in the [Tracking control center](delivery-information-setup.md#tracking-control-center) determines the estimated lead times. The estimated end dates use the lead time from the start date of the activity. Then, when you record the actual end date, the start date of the next activity updates to the same date as the previous activity's actual end date. The actual lead time updates so that comparison and analysis can be done. You can enter additional notes in the **Note** field.

The order of the activities in the grid is determined by the order of the legs in the relevant journey template. If you change the order of the legs in the attached journey, the tracking control also changes.

You can update the dates for all containers by selecting **Update start date** or **Update actual end date** on the Action Pane. Alternatively, you can enter the dates per container on the shipment. This approach allows for greater flexibility, because containers can be split in a multi-journey environment.

> [!NOTE]
> The Landed cost tracking control center feature doesn't consider vendor lead times on individual purchase lines when calculating expected delivery dates.

## Buttons on the Action Pane

Use the buttons on the Action Pane of the **Inbound tracking** page to work with inbound voyages and journeys. The following table describes the buttons that are available.

| Button | Description |
|---|---|
| Edit | Edit a voyage or shipping container journey. |
| New | Create a new voyage or shipping container journey. |
| Delete | Delete a selected voyage or shipping container journey. |
| Update start date | Update the start date of an activity for all containers in a voyage. When you update the start date of a specific activity or leg of a journey, the subsequent estimated start dates are updated based on the specified lead time. |
| Update actual end date | Update the end date of an activity for all containers in a voyage. When you update the end date of a specific activity, the subsequent activities are updated based on the specified lead time. |
| Add activities | Manually add an activity to a voyage. For example, you might add a fumigation activity. The addition might cause the confirmed delivery date of the goods in the vessel or voyage to change. When you add an activity to the journey, the estimated days aren't entered until the start date of a journey leg is updated. |

## Information and settings on the Overview tab

The **Overview** tab shows a list of all the activities that belong to the voyage and/or shipping container selected at the top of the page. The following table describes the fields that are available for each activity.

| Field | Description |
|---|---|
| Leg | The leg ID for the activity, as defined by the journey template. |
| Mode of delivery | The expected delivery method for the activity. |
| Activity | This field usually identifies the job or task that is associated with the activity. Typical examples include *Sailing* and *Clearance*. |
| Description | A longer description of the activity. |
| Start date | This field initially shows the estimated start date of the activity. However, after you enter the previous activity's actual end date, it shows the actual start date. This field is used to determine the estimated end date, based on the lead time. |
| Estimated end date | The system calculates the value of this field based on the start date and lead time. You usually don't edit the value directly. |
| Actual end date | Update this field as soon as possible after the activity occurs. The actual lead time is then updated. |
| Estimated days | The estimated time (in days) that is required to complete the activity. |
| Actual days | The actual time (in days) that is required to complete the activity. |
| Note | Use this field to add miscellaneous notes and details about the activity. |

## Information and settings on the General tab

The **General** tab shows information about the leg selected on the **Overview** tab. Although it repeats some of the information that appears on the **Overview** tab, it also includes additional information about the selected leg.
