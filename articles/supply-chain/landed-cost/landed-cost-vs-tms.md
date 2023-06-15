---
# required metadata

title: Landed cost vs. Transportation management
description: Microsoft Dynamics 365 Supply Chain Management provides two different modules for working with transportation, Transportation management (TMS) and Landed cost. This article summarizes the functionality that the two modules have in common and highlights the differences between them.
author: Weijiesa
ms.date: 12/04/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2020-12-04
ms.dyn365.ops.version: 10.0.17
---

# Landed cost vs. Transportation management

[!include [banner](../../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management provides two different modules for working with transportation: **Transportation management** (TMS) and **Landed cost**. This article summarizes the functionality that the two modules have in common and highlights the differences between them. You can use this information to decide which module best fits your business practices. You might find that some business practices work better with TMS, whereas others work best with Landed cost. Then, depending on your business requirements, you might choose to use one module exclusively, or you might combine the two modules.

This article isn't a comprehensive review of all the features of either module. Instead, it highlights the available functionality as it pertains to the transportation of goods from a vendor to your business's warehouse, where it can be consumed.

## Terminology, reference data, and reporting differences

### Terminology comparison

TMS and Landed cost use different terms for similar concepts. The following table summarizes these terms and their usage in the two modules.

| TMS term | Landed cost term | Notes |
|----------|------------------|-------|
| **Load**<p>A *load* is a collection of shipments that are transported simultaneously on the same transportation unit (such as a truck or a ship). Loads can be either inbound or outbound.</p> | **Voyage**<p>Typically, a *voyage* is a single vessel that travels along a single *journey*. A voyage can contain multiple *shipping containers*, and it can also include inbound orders from different legal entities of your organization. Voyages can only be inbound.</p> | TMS also uses the term *voyage number*, which refers to an information field where you can enter an identifier. However, no functionality is associated with the TMS field, and it's unrelated to the *voyage* concept in Landed cost. |
| **Route**<p>A *route* is the physical path of a transport from origin to destination.</p> | **Journey**<p>A *journey* is the physical path of a transport from origin to destination. Each voyage must be assigned to a journey.</p> | |
| **Route segments**<p>A route can have multiple *route segments*, each of which represents a step of the journey. A route can include multiple carriers or services, each of which is considered a route segment.</p> | **Legs**<p>Each journey can have multiple *legs*, each of which represents a step of the journey. A leg can be part of transportation, duty handling, or another activity.</p> | |
| **Containers**<p>A *container* can be any kind of package or packaging that is used by TMS.</p> | **Shipping containers**<p>A *shipping container* is a literal, physical shipping container, as known from container ships.</p> | |
| **Commodity codes**<p>In TMS (and in other places in Supply Chain Management), *commodity codes* identify types of commodities. They can affect tariffs, handling of hazardous materials, and so on.</p> | **Commodity codes**<p>In Landed cost, *commodity codes* are established at the level of the legal entity. They are mostly used for reporting.</p> | Landed cost can also use the commodity codes that are used for TMS and other places in Supply Chain Management. However, the Landed cost commodity codes are used only by Landed cost. |

### Some reference data isn't shared

TMS and Landed cost don't share reference data for entities such as cost setup, journeys, and legs. If you use both modules, you must re-create the unshared reference data.

### <a name="intercompany-reports"></a>Intercompany reports don't work with goods in transit

The following reports don't work in conjunction with the goods in transit feature that Landed cost provides:

- [Intercompany goods in transit totals report](/dynamicsax-2012/appuser-itpro/intercompany-goods-in-transit-totals-report-intercompanygoodsintransittotals)
- [Intercompany goods in transit transactions report](/dynamicsax-2012/appuser-itpro/intercompany-goods-in-transit-transactions-report-intercompanygoodsintransittransactions)

These reports assume that goods are put in transit as soon as you issue a sales packing slip, and that they are taken into inventory from transit upon receipt. However, goods in transit aren't processed in this way. Therefore, if you use the goods in transit and intercompany features together, the results for both these reports will be incorrect.

## Using the two modules together

You can use TMS for both inbound and outbound operations. Although Landed cost provides most of the same basic functionality as TMS for inbound operations, it also adds some functionality. Therefore, you might want to consider using TMS for outbound operations and Landed cost for inbound operations.

In general, we don't recommend that you use both modules together for inbound operations. You should use the module that best meets your requirements. If you do use the two modules together, you must not share source documents between them. For example, don't use the same purchase order for both a load in TMS and a voyage in Landed cost. In particular, you must ensure that you don't set up the system to create inbound loads automatically. If items from purchase orders are included in a voyage, they can't be handled as part of a load.

## Goods in transit

One of the primary features of Landed cost is its ability to process goods in transit. Goods in transit processing lets you take financial ownership of shipped items before they are physically received at the destination warehouse. Goods in transit processing is often required for international trade.

### TMS goods in transit features

TMS doesn't currently support goods in transit processing.

### Landed cost goods in transit features

Goods in transit processing is a primary feature of Landed cost and provides the following functionality:

- **Goods in transit warehouses** – A goods in transit warehouse can be associated with each warehouse in Supply Chain Management. Goods are transferred to goods in transit warehouses after the original purchase order is invoiced. Items that are physically reserved there become unavailable for consumption until they are received at their physical warehouse. Therefore, you can take financial ownership of goods by invoicing the purchase order.
- **Goods in transit general ledger account** – Landed cost adds a specific general ledger posting account to the purchase order posting profile to handle goods in transit processing. This goods in transit general ledger account acts as an account of the "goods invoiced not received" type. When the original purchase order is invoiced, and the goods in transit order is created, the direct purchase order cost is posted to the goods in transit general ledger account until the goods are received at their final physical location.
- **Tracking control updates** – Goods in transit orders support tracking control functionality in Landed cost. Tracking control lets you update the expected date of arrival of goods while they are in transit. Tracking control then updates the voyage and the associated purchase order lines. The expected delivery date is then available for master planning and logistics.
- **Triggering of over/under transactions** – If a variance occurs between the expected goods on a voyage line and the actual goods that are received at the warehouse, Landed cost resolves it by creating over and/or under transactions. You can then manage these transactions, based on that way that you want to process them, through either a purchase order or a movement journal. The over and under transactions provide a link back to the voyage, the original purchase order, and the new movement journal or purchase order for the variance.
- **Goods in transit orders** – Landed cost introduces a new source document that is known as a *goods in transit order*. A goods in transit order lets you invoice the original purchase order to take financial ownership of the items. When the purchase order is invoiced, the new source document is created for each purchase order line that has a combination of inventory dimensions. Goods are then physically moved to a goods in transit warehouse, where they are physically reserved against the goods in transit order and can't be consumed unless goods in transit orders are received.

## Miscellaneous charges and shipment costs

One of the most important aspects of shipping and shipment management for goods is recognition of the overhead costs that are associated with shipments. These overhead costs aren't the direct inventory costs that are associated with a purchase order and a shipment or voyage. Instead, they are additional costs that are introduced by the nature of the movement of the goods from the vendor to your organization. These costs can include freight costs that are associated with the shipment of goods from one physical location to another, or duty costs that are associated with the import of goods from a foreign vendor.

Landed cost handles these costs by creating a new type of cost structure that is known as *auto costs*. TMS handles these costs by using miscellaneous charge functionality.

### TMS charge and cost features

TMS uses miscellaneous charges to manage additional costs for loads that are allocated to the related source document lines. These miscellaneous charges can be set at the level of either the purchase order line or the purchase order header.

In TMS, miscellaneous charges can be apportioned, or divided, by the weight, volume, or quantity of the inventory. Charges can be divided by freight or accessorial charges. Further development will be required to use additional apportionment methods in TMS.

### Landed cost charge and cost features

Landed cost provides a set of cost functions that handle additional costs that are associated with the shipment of goods. These costs are known as auto costs, and they are applied at the time of initial shipment invoicing by using the estimated cost amount. Each cost type is managed in its own posting. After the actual invoices for overhead costs are posted, the estimated costs are automatically updated to reflect the actual costs.

Additionally, the overhead costs that are associated with the shipment of goods can be invoiced during the voyage from the port of origin or any time after the goods are received. This capability provides greater flexibility for the consumption of goods.

The following list outlines some concepts for the charge and cost features in Landed cost:

- **Cost area** – Costs and charges can be assigned to different levels, or *cost areas*, on a voyage. The cost can be applied at the voyage level and broken down to each item in the voyage. Additionally, costs can be applied at the level of the container, purchase order, item, or transfer order. Each cost charge can be managed separately across the various areas and is broken down to a per-item cost.
- **Apportionment methods** – Several apportionment methods are available in Landed cost. Cost charges can be apportioned by quantity, dollar amount, value, weight, volume, measurement, or a user-defined volumetric measure.
- **Clearing/variance control** – Cost charges are set up as their own cost code type in Landed cost. Each cost code type lets you define a clearing account for estimated costs charges, and also accrual and purchase price variance accounts for variances in estimated costs versus actual costs. When the estimated costs are initially posted, there is a credit to the clearing account. After the actual invoices are posted, the actual cost charges are posted, and the estimated costs are debited out of the clearing account.

## Matching freight bills and invoices

### TMS bill and invoice matching features

TMS can match freight bills that contain estimated costs and invoices with the actual cost of the freight. Invoices can be received either electronically or on paper. Matching variance between the estimated cost and actual cost doesn't affect the inventory valuation.

For more information, see [Reconcile freight in transportation management](../transportation/reconcile-freight-transportation-management.md).

### Landed cost bill and invoice matching features

Landed cost can match freight bills to estimated cost charges and can invoice the actual cost charges to the estimated costs. At the time of invoicing, the freight charges are in an invoice journal, and the estimated costs are cleared out of the clearing account. Additionally, the actual cost charges are posted against the cost of goods sold for the item, together with the variances between the estimated charges and actual charges. This behavior allows for flexibility in the invoicing process.

## Tracking

An important feature of both TMS and Landed cost is the ability to track goods and identify where they are in the journey from the point of origin to the final destination warehouse. Tracking lets you follow and update where the goods are located and when they are expected to arrive at the warehouse for consumption. In addition to the status of goods during their journey, Landed cost provides expected and actual dates for each step of the journey.

### TMS tracking features

TMS provides limited features for tracking incoming loads. It shows dates and enables an integration to be built to find the exact position (for example, on the **Transportation status** page).

For each route segment, you can enter estimated schedules and arrival times.

### Landed cost tracking features

Landed cost can provide tracking control for each voyage, from the port of origin to the final destination. Tracking control sets the status of the voyage. The status indicates whether the voyage is sailing, at customs for inspection, or in local delivery on its way to the final warehouse. The status can be set at the level of the purchase order line, the container, and the header of the voyage. Therefore, you have more granular control.

Additionally, a confirmed expected date that is based on specified lead times is associated with each step of a journey. The confirmed and expected delivery dates are added to the purchase order line and goods in transit orders, and can be used for master planning and logistics. In addition to the expected dates, the actual dates can be updated. The subsequent steps in a journey will then be updated accordingly.

## Multi-leg journeys

The journey concept identifies where the goods are in the process and controls the status of the goods while they are in transit. Goods can go through several legs of a journey, and you can associate various costs with a specific leg. Examples include a freight cost on the sailing of a vessel and local transport costs on the transport of goods from the port to the destination.

### TMS multi-leg journey features

In TMS, routes can be broken down into route segments to represent multi-leg journeys. TMS can allocate spot rates and accessorial charges to individual route segments.

For more information, see [Plan freight transportation routes with multiple stops](../transportation/plan-freight-transportation-routes-multiple-stops.md).

### Landed cost multi-leg journey features

Landed cost provides a framework for moving goods from the point of origin to the destination through a series of legs, which are the stops or steps in a journey. The legs are combined to create journey templates, which define how goods move from the vendor to your organization.

In every leg of a journey, you can further define the status of each purchase order line and the lead times that are associated with it. The combined lead time for all the legs is used to identify the estimated delivery date. However, goods in transit processing is required for multi-leg journeys to apply. The journey of goods on a voyage is managed in a table that is specific to Landed cost.

## Receiving by container

It can be important to manage how goods are split and stored on a vessel. On a vessel, goods can be kept in one container or multiple containers. When goods are received, they are received in containers, and different containers on a voyage might be received at different times or on different dates.

Both TMS and Landed cost provide functionality for managing the receipt of goods in a container. TMS uses the concept of loads to manage the goods, purchase orders, and transfer orders that are associated with a shipment container. TMS supports receiving on the basis of a packaging structure that is received through an advance shipping notice (ASN). Landed cost uses the concept of shipping containers to process purchase orders and control overhead costs that are associated with a container on a vessel.

### TMS receiving by container features

TMS supports inbound ASNs, all variants of receiving through the Warehouse Management mobile app, and all methods of receiving through the Supply Chain Management client.

### Landed cost receiving by container features

To support receiving by container, Landed cost creates shipping container records and associates purchase orders with a specific shipping container by using its container ID. Overhead costs can then be applied to that shipping container and broken down so that they are associated with the relevant purchase orders.

Containers in Landed cost can be received through a new type of receipt that is known as a *goods in transit receipt*, through arrival journals, or through mobile device receiving. When arrival journals are used, the quantities can be initialized from the goods in transit order or the original purchase order lines in the container. Landed cost provides two work types for receiving through the Warehouse Management mobile app.

Landed cost doesn't provide an ASN for the electronic receipt of goods. Additionally, it doesn't support Warehouse Management mobile app flows that process load receiving, license plate receiving, or mixed license plate receiving.

## Rate shopping by vendor

Rate shopping enables a company to select a transportation vendor based on the lowest price, the fastest route, or a combination of both considerations.

### TMS rate shopping features

TMS lets you identify vendor and routing solutions for inbound and outbound orders. For example, you can identify the fastest route or the least expensive rate for a shipment.

TMS provides full rate shopping and freight optimization through the rate route workbench, flexible rating options through the rating engine, a rating engine API for integration with external parties, and support for volumetric weight.

For more information, see [Transportation management engines](../transportation/transportation-management-engines.md).

### Landed cost rate shopping features

Landed cost provides only limited support for rate shopping by vendor. Although you can enter freight forwarder values, Landed cost doesn't compare them across multiple vendors.

## Driver check-in/check-out with appointment scheduling

Driver check-in/check-out features enable the system to monitor arrivals and prevent congestion at the loading docks.

### TMS driver check-in/check-out features

TMS lets you create *appointments*. An appointment represents events that occur at a dock for receiving a purchase order, shipping a sales order, or processing an inbound or outbound load on a specific date and at a specific time. Appointments ensure that docks are available for loading and unloading goods, and they help prevent situations where multiple carriers arrive at a location at the same time.

The system supports allowing drivers to check in at a specific dock door.

### Landed cost driver check-in/check-out features

Landed cost can store estimates for the date and time when a container will be delivered.

## Transfer orders and additional costs

Often, businesses must be able to transfer goods between warehouses. When this type of transfer occurs, costs are associated with it, and you might want to recognize those costs. In Landed cost, transfer orders can be added to a voyage or vessel to track the movement of goods from one warehouse or site to another, estimate the delivery time and expected delivery date, and add overhead costs to the transfer of goods.

### TMS transfer order cost features

TMS supports the creation of freight charges that are connected to transfers. Although these charges can be viewed from the transfer order, the landed cost isn't added to the item cost. Freight reconciliation is supported through the creation of a freight bill that is based on these charges. This freight bill is then matched against a vendor freight invoice.

### Landed cost transfer order cost features

Landed cost lets you add transfer orders to a vessel or voyage. In this way, you can add shipment costs to the voyage as inventory settlements at the time of transfer order receipt. The overhead costs can be invoiced for the actual costs and tracked against a voyage to update the cost of goods sold. Although transfer orders don't use goods in transit processing in the standard release, they can be added to voyages. The landed cost is added to the total cost of each item.