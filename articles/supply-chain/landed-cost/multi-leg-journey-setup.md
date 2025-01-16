---
title: Multi-leg journey setup
description: Learn how to set up multi-leg journeys for the Landed cost module, including an outline on legs and a table that defines various fields.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: ITMLegTable, ITMJourneyTable, ITMActivityTable
ms.topic: how-to
ms.date: 07/30/2024
ms.custom: 
  - bap-template
---

# Multi-leg journey setup

[!include [banner](../../includes/banner.md)]

This article describes how to set up multi-leg journeys for the **Landed cost** module.

## Legs

Legs are used to identify separate parts of a journey. Each leg is built by selecting the "to" and "from" shipping ports, and the transportation method that is used for that leg. Lead times can be associated with each leg. Lead times can help track a shipment and can also be used to calculate the estimated delivery date of the goods on a voyage. Additionally, when a leg of a journey is completed, the status of the voyage, shipping container, and associated purchase order lines can be updated through the tracking control setup. Legs can be used by a single journey template, or they can be reused by multiple journey templates. Container loading, customs, and local transport are generally set up as legs, and a nonspecific shipping port is used for them.

To work with legs, go to **Landed cost \> Multi-leg journey setup \> Legs**. There, you can view, open, create, and delete records for legs. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Leg | Enter a unique identification name/number for the journey leg. |
| Description | Enter a description of the journey leg. Typically, this description identifies the "to" and "from" ports, or the step of the journey. |
| From port | Enter the point of origin of the goods on the leg. |
| To port | Enter the point of destination of the goods on the leg. |
| Delivery method | Enter the method of transport for the leg. |

## Journey templates

A journey template defines the multi-leg journey between two ports that goods travel during a voyage. The legs of the journey are combined to identify the amount of time that will be required for goods to travel from the vendor's point of origin to the final warehouse destination. When the legs are put on the journey template in a specific order, the lead times will identify the date of each leg and status of the voyage, container, and purchase lines for the voyage. You use the [Tracking control center](delivery-information-setup.md) to set up the lead times that are associated with each leg that makes up the journey template. The journey template is also used when the automatic costs of a voyage are set up. When a journey is defined, the cost that is associated with the transport of the goods can be defined on the auto costs page.

To work with journey templates, go to **Landed cost \> Multi-leg journey setup \> Journey templates**. There, you can view, open, create, and delete journey templates.

For each journey template, set the following fields on the header.

| Field | Description |
|---|---|
| Journey template | Enter a unique identification name/number for the journey template. The journey template typically describes the point of origin and point of destination for the journey. |
| Description | Enter a description of the journey template. The description typically indicates the "to" and "from" ports, and the type of travel. |

In the **Lines** section, add a line for each leg of the journey, and put the lines in order. Use the **Up** and **Down** arrows on the toolbar to change the order of the lines. The following table describes the fields that are available for each line.

| Field | Description |
|---|---|
| Leg | Select a leg to add to the journey. |
| Description | The description of the leg. |
| From port | The port that is the point of origin of the goods on the leg. This port is the "to" port that is used to determine the auto costs for a voyage. |
| To port | The final destination port of the goods on the leg. |
| Mode of delivery | The mode of delivery that is used for the leg. |
| Journey from port | If the port that is specified for the leg is used to determine the auto costs, select this check box to identify it as the "journey from" port. This port will be shown on the voyage header. |
| Journey to port | If the port that is specified for the leg is used to determine the auto costs, select this check box to identify it as the "journey to" port. This port will be shown on the voyage header. |
| Shipping company | Select the shipping company that is used for the leg. |

## Activities

The settings on the **Activities** page establish the types of activities that can occur at the destination port of a leg. Users who work on the **All shipping containers** page can select among these values when they estimate the duration of each activity and record the actual duration for comparison purposes.

To set up your activities, go to **Landed cost \> Multi-leg journeys setup \> Activities**. There, you can add, remove, and edit activities by using the buttons on the Action Pane.

The following table describes the fields that are available for each activity in the grid.

| Field | Description |
|---|---|
| Activity | The name of the activity. |
| Description | A description of the activity. |
| Shipping company | The vendor account of the shipping company that is associated with the activity. |
