---
# required metadata

title: Landed cost module overview
description: The Landed cost module allows a business to streamline inbound shipping operations by giving users complete financial and logistical control of imported freight from the manufacturer to the warehouse.
author: mkirknel
manager: tfehr
ms.date: 12/07/2020
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
ms.search.validFrom: 2020-12-07
ms.dyn365.ops.version: Release 10.0.17
---

# Landed cost module overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The Landed cost module allows a business to streamline inbound shipping operations by giving users complete financial and logistical control of imported freight from the manufacturer to the warehouse. The challenge is to provide accurate estimated landed costs for imported goods, where landing costs can account for 40% or more of the total cost of each imported item.

With Landed cost, businesses can:

- Estimate landed costs at the time of voyage creation.
- Apportion landed costs to multiple items and purchase orders in a single voyage.
- Support transfer of goods between physical locations by recognizing landed costs.
- Recognize goods in transit accruals.

Landed cost provides accurate and timely cost estimates for overhead landed costs while providing increased financial and logistical visibility into the extended supply chain. Additionally, the module helps to reduce administration of costing and costing errors.

## Highlights

### Voyages

In the Landed cost module, a voyage is a distinct movement from an outbound location through a specific set of destinations over a specified time period to a specified inbound warehouse location. Purchase orders and order lines can be added to single or multiple containers for a voyage, and the costs will be allocated back to the item line correctly. Orders and order lines can also be added across legal entities for a single voyage.

### Item ownership

Typically, in Dynamics 365 Supply Chain Management, goods are received at the warehouse destination and then invoiced. However, with most international trade agreements, a business will take ownership of goods from the time they have left the original port, before they have been received. Landed cost allows businesses to invoice goods before they have been physically received. This concept is identified as a goods in transit order and creates a new type of order to manage the receipt of goods after the original purchase order has been invoiced.

### Costs

When you create a voyage for Landed cost, costs can be added to it automatically. These costs are set up within Landed cost and will have varying cost options and cost basis available. Each cost can be set up for different levels of a voyage and apportioned to the item level by apportionment rules that support quantity, volume, weight, amount, and defined volumetric divisors. These estimated costs provide an accurate estimate of all costs for a voyage.

Landed cost then runs a preliminary posting/accrual of these estimated landed costs to ensure an accurate estimate cost calculation is provided at the time of voyage creation. As these automatic costs are invoiced, the estimated costs are reversed and replaced by the actual costs based on vendor invoices.

Actual costs are reverse estimate costs posted at the time of vendor invoicing using clearing accounts set up for each type of cost (duty, freight, insurance, and so on). These postings follow the posting behavior associated with the item in question and will automatically update inventory posting, whether FIFO, LIFO, moving weighted average, or moving average. All inventory model group posting types are supported. For moving average and standard cost posting, purchase price variance accounts are available for posting the differences between estimated and actual costs.

### Item and order tracking

As a voyage progresses from the originating outbound location to the final destination warehouse, users are able to update each step of its journey as needed. Each step, or leg, will have an identified lead time and shipment status with confirmed delivery dates for movement to the next step of the journey. These delivery dates combined will provide an estimated delivery date of the goods to the inbound warehouse. Users can then change these delivery dates, which automatically updates the estimated delivery date of the goods based on these lead times and legs of a journey. This visibility of goods in transit by voyage and vessel is available on a per-container basis prior to the receipt of the goods. These dates are updated on each purchase order line, allowing for greater control of logistics and warehouse planning.

## Landed cost concepts

This section summarizes a few of the core concepts of Landed cost.

| **Feature** | **Description** |
| --- | --- |
| Voyage | A voyage is typically one vessel, however, depending on your own practices and procedures it could be one vendor or one purchase order, there really is no limitation for its use. |
| Folio | A folio is often determined by the customs regulations. A folio can consist of one vendor&#39;s goods for one entity/company per shipment. Goods in a folio can be spread over one or more containers. |
| Shipping containers | Shipping Containers store purchase order lines, they are a level below a shipment and are typically used if costs are apportioned for goods by container or receiving is done per container. |
| Shipping Container types | The purpose of them is twofold, they can determine a price for a cost type i.e. freight. Secondly, they provide useful shipping information |
| Cost type | Costs associated with importing i.e. duty, freight, insurance |
| Auto cost | Auto costs work like trade agreements. An auto cost is linked to a voyage level |
| Ports | Area where goods are received and transferred from |
| Vessel | Medium used to transport goods e.g. ship or airplane |
| Goods in transit | Goods are placed (depending on settings) into an in-transit warehouse following the update of an invoice |
| Activities | Activities can be used to store each significant step of the journey between two ports. They can be used to update dates |
| Journey templates | Journey templates are routes that the goods take between two ports |

For more information about how the terminology and features of Landed cost compare to those of the Transportation module (TMS), see [How Landed cost compares with Transportation management](landed-cost-vs-tms.md).