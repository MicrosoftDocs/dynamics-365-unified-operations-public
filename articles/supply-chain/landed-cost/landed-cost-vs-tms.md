---
# required metadata

title: How Landed cost compares with Transportation management
description: Supply Chain Management provides two different modules for working with transportation (Transportation management (TMS) and Landed cost). This topic summarizes the functionality the two modules have in common and highlights the differences between them.
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

# How Landed cost compares with Transportation management

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Supply Chain Management provides two different modules for working with transportation: Transportation management (TMS) and Landed cost. This topic summarizes the functionality the two modules have in common and highlights the differences between them. You can use this information to decide which solution best fits your business practices. You may find some business practices work better for TMS while others work best with Landed cost. Depending on your business needs, you might choose to use one module or the other exclusively, or to combine them.

This is not a comprehensive review of all features of either module, but rather a highlight of the functionality available as it pertains to the transportation of goods from a vendor to your business's warehouse for consumption.

## Terminology, reference data, and reporting differences

### Terminology comparison

To help make it more clear which terms apply to each system, the two systems use contrasting terminology for similar concepts. The following table summarizes these terms and how they are used in the two products.

| **TMS term** | **Landed cost term** | **Notes** |
|-------------------------|-------------------------|-------------------------|
| **Load**</br></br>A <em>load</em> a collection of shipments transported simultaneously on the same transportation unit (such as a truck or ship). A load can be either inbound or outbound. | **Voyage**</br></br>A <em>voyage</em> is typically a single vessel, which typically travels along a single <em>journey</em>. A voyage can contain multiple <em>shipping containers</em> and can also include inbound orders from different legal entities of your organization. A voyage can only be inbound. | TMS also uses the term &quot;voyage number&quot;, which is an information field where you can enter an identifier. However, there is no functionality associated with the TMS field, nor is it related to the voyage concept in the Landed cost. |
| **Route**</br></br>A route is the physical path of a transport from origin to destination. | **Journey**</br></br>A journey is also a physical path of a transport from origin to destination. Each voyage must be assigned to a journey. |  |
| **Route segments**</br></br>A route can have multiple <em>route segments</em>, each of which represents a segment of the journey. A route can include multiple carriers or services, each of which is considered a segment. | **Legs**</br></br>Each journey can have multiple <em>legs</em>, each of which represents a segment of the journey. A leg can be part of transportation, duty handling, or other activity. |  |
| **Containers**</br></br>A container can be any kind of package or packaging used by TMS. | **Shipping containers**</br></br>A <em>shipping container</em> is a literal, physical shipping container, as known from container ships. |  |
| **Commodity codes**</br></br>In TMS (and elsewhere in Supply Chain Management), <em>commodity codes</em> identify types of commodities, which can affect tariffs, hazardous material handling, and so on. | **Commodity codes**</br></br>In the Landed cost module, <em>commodity codes</em> are established at the level of legal entity. They are mostly used for reporting. | The Landed cost module can also use the commodity codes that are used for TMS and Supply Chain Management. However, the Landed cost codes are only used by the Landed cost module. |

### Some reference data isn't shared

The TMS and Landed cost modules don't share reference data for entities such as cost setup, journeys, and legs. If you use both solutions, you must recreate the unshared reference data.

### <a name="intercompany-reports"></a>Intercompany reports don't work with goods in transit

The following reports don't work in conjunction with the goods in transit feature provided by the Landed cost module:

- [Intercompany goods in transit totals report](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/intercompany-goods-in-transit-totals-report-intercompanygoodsintransittotals)
- [Intercompany goods in transit totals report](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/intercompany-goods-in-transit-totals-report-intercompanygoodsintransittotals)

These reports assume that goods are put in transit as soon as you issue a sales packing slip, and are taken into inventory from in-transit upon receipt. However, goods in transit are not processed in this way, so when you use the goods in transit and intercompany features together, the results for both of these reports will be incorrect.

## Using the two solutions together

You can use TMS for both inbound and outbound operations. Landed cost provides the same basic functionality as TMS for inbound operations (with a few exceptions) but also adds additional functionality for inbound operations. You might therefore consider using TMS for outbound operations and Landed cost for inbound operations.

In general, we don't recommend using both solutions together for inbound operations, so you should usually choose the one that best meets your needs. If you do choose to use them together, you must not share source documents between the two modules (for example, don't use the same purchase order for both a load in TMS and a voyage in Landed cost). In particular, you must be sure not to set the system to create inbound loads automatically. Items from purchase orders included in a voyage can't be handled as part of a load.

## Goods in transit

One of the primary features of the Landed cost module is its ability to process *goods in transit*. Goods in transit processing lets you take financial ownership of shipped items before they are physically received at the destination warehouse. Goods in transit processing is often required for international trade.

### TMS goods in transit features

TMS does not currently support goods in transit processing.

### Landed cost goods in transit features

Goods in transit processing is a primary feature of Landed cost, which provides the following goods in transit functionality:

- **Goods in transit warehouses** – Each warehouse in Supply Chain Management can have a goods in transit warehouse associated with it. Goods in transit warehouses are where goods are transferred after the original purchase order is invoiced. Here, items can be physically reserved to make them unavailable for consumption until they are received at their physical warehouse. This allows you to take financial ownership of goods by invoicing the purchase order.

- **Goods in transit general ledger account** – Landed cost adds a specific general ledger posting account to the purchase order posting profile to handle goods in transit processing. This goods in transit general ledger account acts as a goods invoiced not received type of account. At the time the original purchase order is invoiced and the goods in transit order is created, the direct purchase order cost is posted to the goods in transit general ledger account until goods are received at their final physical location.

- **Tracking control updates** – Goods in transit orders support tracking control functionality within Landed cost. With tracking control, you can update the expected date of arrival of goods while they are in transit. Tracking control will then flow through and update the voyage and the associated purchase order lines. The expected delivery date is then available for master planning and logistics.

- **Trigger over/under transactions** – When there is a variance between the expected goods on a voyage line and the actual goods received at the warehouse, Landed cost will resolve these variances by creating over and/or under transactions. You can then manage these transactions based on how you would like to process them, either via a purchase order or a movement journal. The over and under transactions provide a link back to the voyage, the original purchase order, and the new movement journal or purchase order for the variance.

- **Goods in transit orders** – Landed cost introduces a new source document called a *goods in transit order*. With a goods in transit order, you can invoice the original purchase order to take financial ownership of the items. At the time the purchase order is invoiced, the new source document will be created for each purchase order line with inventory dimension combination. Goods will then be physically moved to a goods in transit warehouse where they will be physically reserved against the goods in transit order and can't be consumed except through the receiving of the goods in transit orders.

## Miscellaneous charges and shipment costs

One of the most important aspects associated with shipping and shipment management of goods is the recognition of the overhead costs of that shipment. These overhead costs are not the direct inventory costs that are associated with a purchase order and a shipment or voyage; rather, they are additional costs that are introduced by the nature of the movement of the goods from the vendor to your organization. These costs can include things like freight costs associated with the shipment of goods from one physical location to another, or duty costs associated with the import of goods from a foreign vendor. Landed cost handles these costs by creating a new type of cost structure called *auto costs*. TMS handles these costs using miscellaneous charges functionality.

### TMS charges and costs features

TMS utilizes miscellaneous charges to manage these additional costs for loads allocated to the related source document lines. These miscellaneous charges can be set at the purchase line or purchase order header.

The miscellaneous charges within transportation management can be apportioned, or divided, by the weight, volume, or quantity of the inventory. Charges could be divided by freight or accessorial charges. Additional apportionment methods will require further development to be utilized within TMS.

### Landed cost charges and costs features

Landed cost provides a set of cost functions that handle additional costs associated with shipping goods. These costs, called *auto costs*, are applied at the time of initial shipment invoicing using the estimated cost amount, with each cost type managed in its own posting. Then, once the actual invoices for overhead costs are posted, the estimate costs are automatically updated to reflect the actual costs. Additionally, the overhead costs associated with the shipment of goods can be invoiced during the voyage from the port of origin or any time after the goods have been received. This provides greater flexibility for allowing the consumption of goods. The following list outlines some of the concepts of the charges and cost features in Landed cost:

- **Cost area:** Costs and charges can be assigned to different levels, or cost areas, on a voyage. The cost can be applied at the voyage level and broken down to each item within. Additionally, costs can be applied at the container, purchase order, item, or transfer order level. Each cost charge can be managed separately across the various areas and is broken down to a per-item cost.

- **Apportionment methods:** Several apportionment methods are available in the Landed cost module. Cost charges can be apportioned by quantity, dollar amount, value, weight, volume, measurement, or a user-defined volumetric measure.

- **Clearing/variance control:** Cost charges are set up as their own cost code type within the Landed cost module. Each cost code type lets you define a clearing account for estimate costs charges, as well as accrual and purchase price variance accounts for variances in estimate versus actual costs. The estimate costs are initially posted with a credit to the clearing accounts. Once the actual invoices are posted, the actual cost charges are posted and the estimate costs are debited out of the clearing account.

## Match freight bills and invoices

### TMS bills and invoice matching

TMS can match freight bills (with estimated costs and invoices) with the actual cost of the freight. Invoices can be received electronically or on paper. Matching variance (between the estimated and actual cost) does not affect the inventory valuation.

For more information, see [Reconcile freight in transportation management](../transportation/reconcile-freight-transportation-management.md).

### Landed cost bills and invoice matching

Landed cost can match freight bills to estimate cost charges and invoice the actual cost charges to the estimate costs. At the time of invoicing, the freight charges are in an invoice journal and the estimate costs are cleared out of the clearing account. Additionally, the actual cost charges post against the cost of goods sold for the item, along with the variances of the estimate versus actual charges. This allows for flexibility in the invoice process.

## Tracking

The ability to track and identify where goods are in the journey from the point of origin to the final destination warehouse is an important feature of both TMS and Landed cost. Tracking allows you to follow and update where the goods are located, and when they are expected to arrive at the warehouse for consumption. Landed cost provides that status of goods on their journey from the point of origin to the final destination, along with expected and actual dates on each step of the journey.

### TMS tracking features

TMS provides limited features for tracking incoming loads. It shows dates and makes it possible to build integration for finding the exact position (for example, on the **Transportation status** page).

Each route segment allows you to enter estimated schedules and arrival times.

### Landed cost tracking features

Landed cost can provide tracking control for each voyage as it starts from the port of origin until it reaches its final destination. Tracking control sets the status of the voyage (whether it is sailing, at customs for inspection, or in local delivery on its way to the final warehouse). The status can be set at the purchase order line, the container, and the header of the voyage for greater granularity in control. Additionally, each step of a journey has a confirmed expected date associated with it based on specified lead times. These confirmed and expected delivery dates are added to the purchase order line and goods in transit orders and can be used for master planning and logistics. Along with the expected dates, the actual dates can be updated and have the subsequent steps in a journey update.

## Multi-leg journeys

The journey concept identifies where in the process the goods are and controls the status of the goods while in transit. Additionally, goods can go through several legs of a journey and you can associate various costs to a particular leg of a journey, such as a freight cost on the sailing of a vessel and local transport costs on the transport of goods from the port to the destination.

### TMS multi-leg journey features

In TMS, *routes* can be broken down into*route segments*, which thereby represent multi-leg journeys. TMS can allocate spot rates and accessorial charges to individual segments of a route.

For more information, see [Plan freight transportation routes with multiple stops](../transportation/plan-freight-transportation-routes-multiple-stops.md).

### Landed cost multi-leg journey features

Landed cost provides a framework to move goods from the point of origin to the destination through a series of stops or steps in a journey. The steps of a journey are identified as the *legs* of the journey. The legs are combined to create journey templates, or routes, which define how goods move from the vendor to your organization. Within each leg of a journey, you can further define the status of each purchase order line and the lead times associated with it. The combination of each leg's lead time is used to identify the estimated delivery date. However, goods in transit processing is required for multi-leg journeys to apply. The journey of goods on a voyage are managed within a table specific to Landed cost.

## Receiving by container 

It can be important to manage how goods are split and stored on a vessel. Within a vessel, goods can be contained in one or multiple containers. When goods are received, they are received in containers and different containers on a voyage may be received at different times or on different dates. Both TMS and Landed cost provide functionality to manage the receiving of goods in a container. TMS utilizes the concept of loads to manage the goods, purchase orders, and transfer orders associated with a shipment container. TMS supports receiving on the basis of a packaging structure received via an advance shipping notice (ASN). Landed cost utilizes the concept of shipping containers to process purchase orders and control overhead costs associated with a container on a vessel.

### TMS receiving by container features

TMS supports inbound ASN, all variants of receiving through the warehousing app, and all methods of receiving using the Supply Chain Management client.

### Landed cost receiving by container features

Landed cost supports receiving by container by creating *shipping container* records and associating purchase orders with a particular shipping container using its container ID. Overhead costs can then be applied to that specific container and broken down to be associated with the relevant purchase orders.

Containers in Landed cost can be received via a new type of receipt called a *goods in transit receipt*, by arrival journal, or via mobile device receiving. With arrival journals, the quantities can be initialized from the goods in transit order or the original purchase order lines within the container. Landed cost provides two work types for receiving using the warehouse app.

Landed cost doesn't provide an ASN for the electronic receipt of goods. Additionally, there is no support for warehouse app flows that process load receiving, license plate receiving, or mixed license plate receiving.

## Rate shopping by vendor

Rate shopping enables a company to select a transportation vendor based on the lowest price, fastest route, or a combination of both considerations.

### TMS rate shopping features

TMS lets you identify vendor and routing solutions for inbound and outbound orders. For example, you can identify the fastest route or the least expensive rate for a shipment.

The TMS solution provides full rate shopping and freight optimization using the rate route workbench, flexible rating options using the rating engine, a rating engine API for integrating with external parties, and support for volumetric weight.

For more information, see [Transportation management engines](../transportation/transportation-management-engines.md).

### Landed cost rate shopping features

Landed cost provides only limited support for rate shopping by vendor. It lets you input freight forwarder values, but does not compare them across multiple vendors.

## Driver check in/out with appointment scheduling

Driver check in/out features enable the system to monitor arrivals and prevent congestion at the loading docks.

### TMS driver check in/out features

TMS lets you create an *appointment*, which represents events that occur at a dock for receiving a purchase order, shipping a sales order, or processing an inbound or outbound load at a specific date and time. The appointments ensure that there is availability of docks for the loading and unloading of goods and avoids situations where multiple carriers arrive at a location at the same time.

The system provides support for allowing drivers to check in at a specific dock door.

### Landed cost driver check in/out features

Landed cost can store date and time estimates for when a container will be delivered.

## Transfer orders and additional costs

Often, businesses need the ability to transfer goods between different warehouses. When this transfer occurs, there are costs associated with the transfer that you may want to recognize. With this, Landed cost allows for the addition of transfer orders to a voyage or vessel to track the movement of goods from one warehouse or site to another, estimate the delivery time and expected delivery date, and add overhead costs to the transfer of goods.

### TMS transfer order cost features

TMS supports creating freight charges in connection with transfers. The charges can be viewed from the transfer order, but the landed cost is not added to the item cost. Freight reconciliation is supported by creating a freight bill based on these charges, which is matched against a vendor freight invoice.

### Landed cost transfer order cost features

Landed cost allows you to add transfer orders to a vessel or voyage. With the addition of a transfer order to a vessel or voyage, you can add shipment costs to the voyage as inventory settlements at the time of transfer order receipt. The overhead costs can be invoiced for the actual costs and tracked against a voyage to update to cost of goods sold. Transfer orders will not use goods in transit processing in the standard release but will allow for the addition of transfer orders to voyages.

The Landed cost module adds landed cost to the total cost of each item.
