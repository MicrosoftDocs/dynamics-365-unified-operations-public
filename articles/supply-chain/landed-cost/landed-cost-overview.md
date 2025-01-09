---
title: Landed cost module
description: The Landed cost module helps businesses streamline inbound shipping operations by giving users financial and logistical control over imported freight.
author: lisascholz91
ms.author: lisascholz
ms.topic: overview
ms.date: 01/27/2025
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Landed cost module

[!include [banner](../../includes/banner.md)]

The **Landed cost** module helps businesses streamline inbound shipping operations by giving users complete financial and logistical control over imported freight, from the manufacturer to the warehouse. For imported goods, landed costs can account for 40 percent or more of the total cost of each imported item. Therefore, the challenge is to provide accurate estimates for landed costs.

Businesses can use Landed cost to complete the following tasks:

- Estimate landed costs at the time of voyage creation.
- Apportion landed costs to multiple items and purchase orders or transfer orders in a single voyage.
- Support the transfer of goods between physical locations by recognizing landed costs.
- Recognize accruals for goods in transit.

Landed cost provides accurate and timely cost estimates for overhead landed costs. At the same time, it provides increased financial and logistical visibility into the extended supply chain. It also helps reduce the administration of costing and costing errors.

## Highlights

### Voyages

In Landed cost, a voyage is a distinct movement from an outbound location, through a specific set of destinations over a specified period, to a specified inbound warehouse location. Purchase orders and order lines can be added to either a single container or multiple containers for a voyage, and the costs will be correctly allocated back to the item line.

### Item ownership

In Microsoft Dynamics 365 Supply Chain Management, goods are typically received at the warehouse destination and then invoiced. However, under most international trade agreements, a business takes ownership of goods from the time when they leave the original port, before they've been physically received. Landed cost enables businesses to invoice goods before they've been physically received. This concept is known as a *goods in transit order*. It creates a new type of order to manage the receipt of goods after the original purchase order has been invoiced.

### Costs

When you create a voyage in Landed cost, costs can automatically be added to it. These costs are set up in Landed cost, and various cost options and cost bases are available for them. Each cost can be set up for different levels of a voyage and apportioned to the item level through apportionment rules that support quantity, volume, weight, amount, and defined volumetric divisors. These estimated costs provide an accurate estimate of all costs for a voyage.

Landed cost then runs a preliminary posting/accrual of the estimated landed costs to ensure that an accurate calculation of estimated costs is provided at the time of voyage creation. Estimated landed costs are posted along with posting the purchase or transfer order invoice. Actual costs are posted when the vendor invoice journal is posted.

Actual costs are reverse-estimated costs that are posted at the time of cost invoicing by using clearing accounts that are set up for each type of cost (for example, duty, freight, and insurance). These postings follow the posting behavior that is associated with the specific item. They automatically update inventory posting, regardless of whether the posting type is first in, first out (FIFO), last in, first out (LIFO), moving weighted average, or moving average. All inventory model group posting types are supported. For moving average and standard cost posting, purchase price variance accounts are available to post the differences between estimated costs and actual costs.

### Item and order tracking

As a voyage moves from the originating outbound location to the final destination warehouse, users can update each step, or *leg*, of its journey as required. For each leg, a lead time and a shipment status are identified. Confirmed receipt (or delivery) dates for movement to the next leg of the journey are also identified. Together, these delivery dates provide an estimated delivery date of the goods to the inbound warehouse. Users can change these delivery dates. In this case, the estimated delivery date of the goods is then automatically updated, based on the lead times and legs of the journey. Visibility into goods in transit by voyage and vessel is available on a per-container basis before receipt of the goods. Because the dates are updated on each purchase order line, businesses have more control over logistics and warehouse planning.

## Landed cost concepts

The following table summarizes some core concepts of Landed cost.

| Concept | Description |
|---|---|
| Voyage | Typically, a voyage is one vessel. However, depending on your practices and procedures, it can be one vendor or one purchase order. There are no limitations on the use of this concept. |
| Folio | A folio is often determined by customs regulations. It can consist of one vendor's goods for one entity/company per shipment. The goods in a folio can be in one container or spread among multiple containers. |
| Shipping container | Shipping containers store purchase order lines. They're a level below the shipment level. They're typically used if costs are apportioned for goods by container, or if receiving is done per container. |
| Shipping container type | Shipping container types can determine the price for a cost type (for example, freight). They also provide useful shipping information. |
| Cost type | Cost types identify costs that are associated with imports, such as duty, freight, and insurance. |
| Auto cost | Auto costs work like trade agreements. An auto cost is linked to a voyage level. |
| Port | Ports are areas where goods are received and transferred from. |
| Vessel | A vessel is the medium that is used to transport goods, such as a ship or an airplane. |
| Goods in transit | Depending on settings, goods are put into an in-transit warehouse after an invoice is updated. |
| Activity | Activities can be used to store each significant step of the journey between two ports. They can be used to update dates. |
| Journey template | Journey templates are routes that goods take between two ports. |

For a comparison of the terminology and features of the **Landed cost** and **Transportation management** (TMS) modules, see [Landed cost vs. Transportation management](landed-cost-vs-tms.md).

## Landed cost process flow overview

Landed cost can be run both with and without generating goods in transit orders. Both processes start with an inbound demand source document, followed by creating a new voyage, adding the source document order line to a container in that voyage, and adding costs to the voyage. The source document must be invoiced to post estimated landed costs and generate a goods-in-transit order if applicable. A vendor invoice journal must also be posted to post the actual costs. Product receipt isn't always mandatory and can happen at different points in the flow.

The delivery of a goods-in-transit order can be date-tracked using the **Tracking control center** page. Learn more in [Track inbound voyages and shipping container journeys](inbound-tracking.md). You can use the **Inquiries** feature to look up information across landed cost-enabled orders such as looking up an item or container and viewing related information. Various reports can be viewed and generated using the **Reports** functionality [Landed cost reports](landed-cost-reports.md).

### Setup / Configuration

If you're using landed cost with goods in transit orders enabled, the following configurations must be in place:

- Goods in transit management must be set to *Yes* on the **Terms of delivery.**
- **Terms of delivery** must be set on the purchase or transfer order header.
- Additional goods in transit and under-delivery warehouses must be set up.

Learn more in [Goods-in-transit processing](in-transit-processing.md).

If you're using landed cost without goods in transit orders, no additional warehouses need to be configured, and terms of delivery aren't required on the purchase or transfer order.

The costing, financial, and inventory impact of posting estimated and actual costs are based on configurations set within the module. Learn more in [Landed cost parameters setup](landed-cost-parameters.md) and [Costing parameter values setup](costing-parameters-setup.md).

The following diagram shows the process flow for landed cost without goods-in-transit orders enabled.

:::image type="content" source="media/landed-cost-without-git-orders.png" alt-text="Diagram showing the process flow for landed cost without goods-in-transit orders enabled." lightbox="media/landed-cost-without-git-orders.png":::

The following diagram shows the process flow for landed cost with goods-in-transit orders enabled.

:::image type="content" source="media/landed-cost-with-git-orders.png" alt-text="Diagram showing the process flow for landed cost with goods-in-transit orders enabled." lightbox="media/landed-cost-with-git-orders.png":::

### Inbound demand source document

Landed cost works with both purchase and transfer orders as inbound demand source documents.

### Create voyage

After the voyage has been created, you can add the purchase or transfer lines to a new or existing shipping container in the voyage.

Learn more in [Manage voyages](manage-voyages.md), [Manage shipping containers](manage-shipping-containers.md), and [Manage folios](manage-folios.md).

### Add estimated landed cost to voyage

When using the **Find auto costs** function, the system will automatically find and add costs to the voyage, container, item or order based on auto cost setup. You can view the costs added by the system and edit or add any costs manually.

Learn more in [Estimate and manage landed costs](estimate-manage-landed-costs.md) and [Auto costs setup](auto-cost-setup.md).

### Post purchase or transfer order invoice

Posting the purchase or transfer order invoice is a mandatory step in the landed cost flow, and posts estimated landed costs. Learn more in [Estimate and manage landed costs](estimate-manage-landed-costs.md).

For goods in transit-enabled orders, posting the order invoice also generates a goods in transit order. Learn more in [Goods-in-transit processing](in-transit-processing.md).

### Receive goods

#### Goods receipt for landed cost without goods-in-transit order enabled

Receiving goods without goods in transit order enabled can be done using the **Post product receipt** functionality on the purchase or transfer order. The process is similar to normal purchase order receiving.

Learn more in [Warehouse handling of inbound loads for purchase and inbound shipment orders](../warehousing/inbound-load-handling.md)

#### Goods receipt for landed cost with goods-in-transit order enabled

Receiving goods with goods in transit order enabled can be done with the warehouse mobile app using the goods in transit specific menu items, by posting an arrival journal, or by receiving the goods via the goods-in-transit order.

Learn more in [Goods-in-transit processing](in-transit-processing.md).

#### Processing over and under transactions

Landed cost processes the over and under receiving of goods. This happens if the quantity received from a goods in transit enabled purchase or transfer order doesn't match the ordered quantity, and if this difference to ordered quantity exceeds configured rules and tolerances.

Learn more in [Over/under transactions](over-under-transactions.md).

### Post vendor invoice journal

This step reflects an invoice received from the vendor in Supply Chain Management and posts actual costs.

<!--KFM: Add link to new topic when available. -->

## Limitations of the landed cost module

The following aren't supported in the current landed cost module:

- Project purchase orders
- Purchase orders with catch-weight enabled items
- Purchase orders with service / non-stocked items
- Non-deductible tax as part of the voyage costs
