---
# required metadata

title: Transportation management statuses
description: This topic explains how to create a transportation status and map that status to a carrier status.
author: Weijiesa
ms.date: 10/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:TMSTransportationStatus,TMSTransportationStatusMaster
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2020-09-08
ms.dyn365.ops.version: 10.0.14
---

# Transportation management statuses

[!include [banner](../includes/banner.md)]

Set up master codes for transportation statuses to interpret codes that are provided by your shipping carriers. This lets you integrate with shipping carriers to provide a status. The transportation status that you provide for a transportation master status code can help you track the status of a load, shipment, or container. The specific transportation status for a load, shipment, or container can only be updated through data integration and not manually through the user interface.

## Create a transportation status

To create a transportation status, follow these steps:

1. Go to **Transportation management \> Setup \> Transportation status masters**.
1. Select **New** to create a transportation status master.
1. In the **Transportation status master** field, enter a unique code for the transportation status.
1. In the **Transportation type** field, select either *Shipping carrier* or *Hub* as the type of transportation.
1. Enter a name and transportation status.
1. Close the page.

## Map a transportation status to a carrier status

To map a transportation status to a carrier status, follow these steps:

1. Go to **Transportation management \> Setup \> Carriers \> Carrier transportation status**.
1. Select **New** to map a code from a shipping carrier to a transportation status master code.
1. Select the unique ID for the shipping carrier and the carrier service.
1. Select the transportation status code that you want to map to the selected shipping carrier's code.
1. Enter the external code that is used by the shipping carrier.
1. Close the page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]