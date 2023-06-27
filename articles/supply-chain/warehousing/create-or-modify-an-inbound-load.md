---
# required metadata

title: Create or modify an inbound load
description: This topic explains how to create or modify an inbound load.
author: perlynne
ms.date: 25/05/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form: WHSInboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2023-05-25
ms.dyn365.ops.version: 10.0.36
---

# Create or modify an inbound load

This topic explains how to create or modify an inbound load. You can use a purchase order or a inbound shipment order to create an inbound load automatically or manually. You can also modify an existing inbound load by for example adding more lines or updating the quantities.

In case of wanting to use the inbound load process with transportation planning you can read more in the [Transportation management overview](../transportation/transportation-management-overview.md) section.

## Create an inbound load automatically via purchase orders

To create an inbound load automatically by using a purchase order, follow these steps:

1. Go to **Warehouse management > Setup > Warehouse management parameters**.
2. Go to **Loads**, and then enable the **Automatically create at purchase order entry** setting.
3. [Create a purchase order](../procurement/tasks/create-purchase-order.md) and an inbound load will be created automatically.

## Create an inbound load automatically via inbound shipment orders

To create an inbound load automatically by using an inbound shipment order, follow these steps:

1. Go to **Warehouse management > Setup > Source systems**.
2. Create or modify existing record for an integration making sure having the **Inbound shipment order policies** definition using **Load synchronization policy** = **Full synchronization**.
3. [Import and process an inbound shipment order](warehouse-management-only-mode.md#simple-inbound-shipment-order-message-example) and an inbound load will be created automatically.

## Create an inbound load manually

To create an inbound load manually, follow these steps (prerequisite is to have one or more order lines not already assigned to a load):

1. Go to **Warehouse management > Loads > Inbound load planning workbench**
1. Make sure your filter options will include your order lines and select the wanted order tab: **_Purchase order lines_** or **_Inbound shipment order lines_**.
1. Mark the order lines you would like to assign to a load
1. Select **Supply and demand > To new load**
1. Select a _Load template ID_ and click _OK_.

## Create an inbound load via Advanced shipping notices (ASNs)

Loads can get created automatically as part of an [advanced shipping notices (ASN)](import-asn-data-entity.md) import.
