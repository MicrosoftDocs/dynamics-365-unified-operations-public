---
# required metadata

title: Multi-leg journey setup
description: This topic describes how to set up legs for a multi-leg journey
author: mkirknel
manager: tfehr
ms.date: 12/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mkirknel
ms.search.validFrom: 2020-12-04
ms.dyn365.ops.version: Release 10.0.17
---

# Multi-leg journey setup

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

## Legs

Legs are used to identify separate parts of a journey. Each leg is built by selecting the to and from shipping ports along with the transportation method used for that leg. Each leg can have lead times associated with it, which can assist with shipment tracking and to calculate the estimated delivery date of the goods on a voyage. Additionally, when a leg of a journal is completed, the status of the voyage, shipping container, and associated purchase order lines can be updated through the tracking control setup. Legs can be used by a single journey template or re-used within multiple journey templates. Container loading, customs, and local transport are also generally set up as legs by using a non-specific shipping port for these legs.

To work with the legs, go to **Landed cost \> Multi-leg journey setup \> Legs**. Here you can view, open, create, and delete legs records. The following table describes the settings available for each record.

| **Setting** | **Description** |
| --- | --- |
| **Leg** | Enter a unique identification name/number for the journey leg. |
| **Description** | Enter a description of the journey leg, typically describing the to and from port or the step of the journey. |
| **From port** | Enter the point of origin of the goods on the voyage. <!-- KFM: Do we mean really mean voyage, or should this be journey leg? --> |
| **To port** | Enter the point of destination of the goods on the voyage. <!-- KFM: Do we mean really mean voyage, or should this be journey leg? --> |
| **Delivery method** | Enter the method of transport for the leg. |

## Journey templates

A journey template defines the multi-leg journey between two ports that goods travel during a voyage. The legs of the journey are combined together to identify the length of time it will take for goods to travel from the vendor's point of origin to the final warehouse destination. By placing the legs onto the journey template in a particular order, the lead times will identify the date of each leg and status of the voyage, container, and purchase lines within the voyage. use the [Tracking control center](delivery-information-setup.md) to set up the lead times associated with each leg that makes up the journey template. The journey is also used when setting up automatic costs of a voyage. By defining the journey, the cost associated with the transport of the goods can be defined in the auto costs form.

To work with journey templates, go to **Landed cost \> Multi-leg journey setup \> journey templates**. Here you can view, open, create, and delete journey templates.

For each journey template, make the following settings in the header:

| **Setting** | **Description** |
| --- | --- |
| **Journey template** | Enter a unique identification name/number for the journey template. The journey template typically describes the point of origin and point of destination of the journey. |
| **Description** | Enter a description of the journey template, typically describing the to and from port and the type of travel. |

In the **Lines** section of the page, add a row for each leg of the journey and place them in order. Use the **Up** and **Down** arrows in the **Lines** toolbar to change the order of the lines. The following table describes the settings available for each line.

| **Setting** | **Description** |
| --- | --- |
| **Leg** | Select a leg to add to the journey. |
| **Description** | The description of the selected leg. |
| **From port** | The point of origin of the goods in the voyage. <!-- KFM: Do we mean really mean voyage, or should this be journey leg? --> This is the to port used when identifying auto costs for a voyage. |
| **To port** | The final destination port of the goods in a voyage.<!-- KFM: Do we mean really mean voyage, or should this be journey leg? --> |
| **Mode of delivery** | The mode of delivery used for the specified leg of a voyage. |
| **Journey from port** | If the port specified in the selected leg is used to determine the auto costs, select this check box to identify it as the journey from port. This will be the port that is displayed on the voyage header. |
| **Journey to port** | If the port specified in the selected leg is used to determine the auto costs, select this check box to identify it as the journey to port. This will be the port that is displayed on the voyage header.
 |
| **Shipping company** | Select the shipping company used for the designated leg of the journey. |