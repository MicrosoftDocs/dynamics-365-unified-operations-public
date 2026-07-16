---
title: Landed cost module overview
description: The Landed cost module helps businesses streamline inbound shipping operations by giving users financial and logistical control over imported freight.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: overview
ms.date: 06/12/2026
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Landed cost module overview

[!include [banner](../../includes/banner.md)]

The **Landed cost** module helps businesses streamline inbound shipping operations by giving users complete financial and logistical control over imported freight, from the manufacturer to the warehouse. For imported goods, landed costs can account for 40 percent or more of the total cost of each imported item. Therefore, the challenge is to provide accurate estimates for landed costs.

Businesses can use Landed cost to complete the following tasks:

- Estimate landed costs at the time of voyage creation.
- Apportion landed costs to multiple items and purchase orders in a single voyage.
- Support the transfer of goods between physical locations by recognizing landed costs.
- Recognize accruals for goods in transit.

Landed cost provides accurate and timely cost estimates for overhead landed costs. At the same time, it provides increased financial and logistical visibility into the extended supply chain. It also helps reduce the administration of costing and costing errors.

## Highlights

### Voyages

In Landed cost, a voyage is a distinct movement from an outbound location, through a specific set of destinations over a specified period, to a specified inbound warehouse location. Purchase orders and order lines can be added to either a single container or multiple containers for a voyage, and the costs are correctly allocated back to the item line.

### Item ownership

In Microsoft Dynamics 365 Supply Chain Management, you typically receive goods at the warehouse destination and then invoice them. However, under most international trade agreements, a business takes ownership of goods from the time when they leave the original port, before they're physically received. Landed cost enables businesses to invoice goods before they're physically received. This concept is known as a *goods in transit order*. It creates a new type of order to manage the receipt of goods after the original purchase order is invoiced.

### Costs

When you create a voyage in Landed cost, costs can automatically be added to it. These costs are set up in Landed cost, and various cost options and cost bases are available for them. Each cost can be set up for different levels of a voyage and apportioned to the item level through apportionment rules that support quantity, volume, weight, amount, and defined volumetric divisors. These estimated costs provide an accurate estimate of all costs for a voyage.

Landed cost then runs a preliminary posting/accrual of the estimated landed costs to ensure that an accurate calculation of estimated costs is available at the time of voyage creation. Estimated landed costs are posted together with the purchase order invoice. Actual costs are posted when the vendor invoice journal is posted.

Actual costs are reverse-estimated costs posted at the time of cost invoicing by using clearing accounts that are set up for each type of cost, such as duty, freight, and insurance. These postings follow the posting behavior that's associated with the specific item. They automatically update inventory posting, regardless of whether the posting type is first in, first out (FIFO), last in, first out (LIFO), moving weighted average, or moving average. All inventory model group posting types are supported. For moving average and standard cost posting, purchase price variance accounts are available to post the differences between estimated costs and actual costs.

### Item and order tracking

As a voyage moves from the originating outbound location to the final destination warehouse, users can update each step, or *leg*, of its journey as required. For each leg, a lead time and a shipment status are identified. Confirmed receipt (or delivery) dates for movement to the next leg of the journey are also identified. Together, these delivery dates provide an estimated delivery date of the goods to the inbound warehouse. Users can change these delivery dates. In this case, the estimated delivery date of the goods is then automatically updated, based on the lead times and legs of the journey. Visibility into goods in transit by voyage and vessel is available on a per-container basis before receipt of the goods. Because the dates are updated on each purchase order line, businesses have more control over logistics and warehouse planning.

## Landed cost concepts

The following table summarizes some core concepts of landed cost.

| Concept | Description |
|---|---|
| Voyage | Typically, a voyage is one vessel. However, depending on your practices and procedures, it can be one vendor or one purchase order. There are no limitations on the use of this concept. |
| Folio | A folio is often determined by customs regulations. It can consist of one vendor's goods for one entity/company per shipment. The goods in a folio can be in one container or spread among multiple containers. |
| Shipping container | Shipping containers store purchase order lines. They're a level below the shipment level. They're typically used if costs are apportioned for goods by container, or if receiving is done per container. |
| Shipping container type | Shipping container types can determine the price for a cost type, such as freight. They also provide useful shipping information. |
| Cost type | Cost types identify costs that are associated with imports, such as duty, freight, and insurance. |
| Auto cost | Auto costs work like trade agreements. An auto cost is linked to a voyage level. |
| Port | Ports are areas where goods are received and transferred from. |
| Vessel | A vessel is the medium that's used to transport goods, such as a ship or an airplane. |
| Goods in transit | Depending on settings, goods are put into an in-transit warehouse after an invoice is updated. |
| Activity | Activities can store each significant step of the journey between two ports. They can update dates. |
| Journey template | Journey templates are routes that goods take between two ports. |

For a comparison of the terminology and features of the **Landed cost** and **Transportation management** (TMS) modules, see [Landed cost vs. Transportation management](landed-cost-vs-tms.md).

## Overview of the landed cost process flow

Landed cost can be run so that it generates goods-in-transit orders. Alternatively, it can be run so that it doesn't generate goods-in-transit orders. Both processes start with an inbound demand source document. Next, a new voyage is created, the source document order line is added to a container in the voyage, and costs are added to the voyage. The source document must be invoiced before estimated landed costs can be posted and a goods-in-transit order can be generated, if applicable. A vendor invoice journal must also be posted before the actual costs can be posted. Product receipt isn't always mandatory and can occur at different points in the flow.

You can date-track the delivery of a goods-in-transit order by using the **Tracking control center** page. To learn more, see [Track inbound voyages and shipping container journeys](inbound-tracking.md). You can use the **Inquiries** feature to look up information across landed cost–enabled orders. For example, you can look up an item or container, and view related information. In addition, you can generate and view various reports by using the **Reports** functionality. To learn more, see [Landed cost reports](landed-cost-reports.md).

### Setup and configuration

To use landed cost with goods-in-transit orders enabled, ensure that the following configurations are in place:

- **Goods-in-transit management** is set to *Yes* on the terms of delivery.
- Terms of delivery are set on the purchase order header.
- Additional goods-in-transit and under-delivery warehouses must be set up.

For more information, see [Goods-in-transit processing and receiving](in-transit-processing.md).

To use landed cost without goods-in-transit orders enabled, set **Goods in transit management** to *No* on the terms of delivery, and don't configure any additional warehouses. Also, you don't need to set terms of delivery on the purchase order.

The costing, financial, and inventory impact of posting estimated and actual costs depends on configurations set in the **Landed cost** module. For more information, see [Landed cost parameters setup](landed-cost-parameters.md) and [Costing parameter values setup](costing-parameters-setup.md).

The following diagram shows the process flow for landed cost when goods-in-transit orders are enabled.

:::image type="content" source="media/landed-cost-with-git-orders.png" alt-text="Diagram that shows the process flow for landed cost with goods-in-transit orders enabled." lightbox="media/landed-cost-with-git-orders.png":::

The following diagram shows the process flow for landed cost when goods-in-transit orders aren't enabled.

:::image type="content" source="media/landed-cost-without-git-orders.png" alt-text="Diagram that shows the process flow for landed cost without goods-in-transit orders enabled." lightbox="media/landed-cost-without-git-orders.png":::

### Create the voyage

After the voyage is created, you can add the purchase order lines to a new or existing shipping container in the voyage.

For more information, see [Manage voyages](manage-voyages.md), [Manage shipping containers](manage-shipping-containers.md), and [Manage folios](manage-folios.md).

### Add the estimated landed cost to the voyage

When you use the **Find auto costs** function, the system automatically finds and adds costs to the voyage, container, item, or order, based on the auto costs setup. You can view the costs that the system adds, and you can manually edit or add any costs.

Learn more in [Estimate and manage landed costs](estimate-manage-landed-costs.md) and [Auto costs setup](auto-cost-setup.md).

### Post estimated costs

#### Post estimated costs for landed cost with purchase orders

If you use purchase orders as the inbound demand source document, then estimated landed costs are also posted when you post a purchase order invoice. Learn more in [Estimate and manage landed costs](estimate-manage-landed-costs.md).

If goods-in-transit is enabled, then the invoicing process generates the required goods-in-transit orders.

#### Post estimated costs for landed cost with transfer orders

Transfer orders can be used with landed cost only if goods-in-transit orders aren't enabled. In this scenario, instead of posting an invoice, you use the *Ship transfer order* functionality to post estimated costs.

### Receive goods

#### Goods receipt for landed cost when goods-in-transit orders aren't enabled

When goods-in-transit isn't enabled, use the **Post product receipt** functionality on the purchase order. The process resembles the normal process for purchase order receiving.

For more information, see [Warehouse handling of inbound loads for purchase and inbound shipment orders](../warehousing/inbound-load-handling.md).

#### Goods receipt for landed cost when goods-in-transit orders are enabled

To receive goods when goods-in-transit orders are enabled, use goods-in-transit receiving-specific menu items in the Warehouse Management mobile app, post an arrival journal, or receive the goods via the goods-in-transit order. The receipt method you use depends on whether warehouse management processes (WMS) and serial/batch tracking are enabled.

For more information, see [Goods-in-transit processing and receiving](in-transit-processing.md).

#### Processing of over and under transactions

Landed cost processes the over-receipt and under-receipt of goods. Over and under transactions occur if the quantity received from a goods-in-transit-enabled purchase order differs from the ordered quantity, and the difference exceeds configured rules and tolerances.

For more information, see [Over/under transactions](over-under-transactions.md).

### Post the vendor invoice journal

This step reflects an invoice received from the vendor in Supply Chain Management. During this step, actual costs are posted.

## Limitations of the Landed cost module

Currently, the **Landed cost** module doesn't support the following items:

- Project purchase orders
- Purchase orders that include catch-weight-enabled items
- Purchase orders that include service/non-stocked items
- Non-deductible tax as part of the voyage costs
- Transfer orders with goods-in-transit orders enabled
- Direct delivery and goods in transit
    - If goods-in-transit isn't enabled for a direct delivery order, direct delivery for landed cost follows the standard behavior.
        - If goods-in-transit is enabled for a direct delivery order, the goods-in-transit processes are skipped. This condition means that the items aren't received in the goods-in-transit warehouse. Posting a purchase order invoice automatically generates the product receipt and also updates the transactions on the sales order. Also, if a purchase order that links to a direct delivery sales order is split across multiple voyages and/or shipping containers, the direct delivery processes don't work.
