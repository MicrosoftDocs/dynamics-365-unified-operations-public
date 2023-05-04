---
title: Landed cost module
description: The Landed cost module helps businesses streamline inbound shipping operations by giving users complete financial and logistical control over imported freight, from the manufacturer to the warehouse.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 01/05/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
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

Landed cost then runs a preliminary posting/accrual of the estimated landed costs to ensure that an accurate calculation of estimated costs is provided at the time of voyage creation. As these automatic costs are invoiced, the estimated costs are reversed and replaced by the actual costs, based on cost invoices.

Actual costs are reverse-estimated costs that are posted at the time of cost invoicing by using clearing accounts that are set up for each type of cost (for example, duty, freight, and insurance). These postings follow the posting behavior that is associated with the specific item. They automatically update inventory posting, regardless of whether the posting type is first in, first out (FIFO), last in, first out (LIFO), moving weighted average, or moving average. All inventory model group posting types are supported. For moving average and standard cost posting, purchase price variance accounts are available to post the differences between estimated costs and actual costs.

### Item and order tracking

As a voyage moves from the originating outbound location to the final destination warehouse, users can update each step, or *leg*, of its journey as required. For each leg, a lead time and a shipment status are identified. Confirmed delivery dates for movement to the next leg of the journey are also identified. Together, these delivery dates provide an estimated delivery date of the goods to the inbound warehouse. Users can change these delivery dates. In this case, the estimated delivery date of the goods is then automatically updated, based on the lead times and legs of the journey. Visibility into goods in transit by voyage and vessel is available on a per-container basis before receipt of the goods. Because the dates are updated on each purchase order line, businesses have more control over logistics and warehouse planning.

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
