---
# required metadata

title: Activity-based subcontracting
description: This topic describes, in detail, how to use subcontracted activities in a production flow for lean manufacturing.
author: YuyuScheller
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: KanbanJobSchedulingListPage, LeanRuleReassignmentWizard, PlanActivity, ReqSupplyDemandSchedule
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 121
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 267034
ms.assetid: 15c76a51-fa6d-42d2-994a-c67df6bae6a9
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: conradv
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Activity-based subcontracting

This topic describes, in detail, how to use subcontracted activities in a production flow for lean manufacturing.

In Microsoft Dynamics 365 for Operations, there are two approaches for subcontracting: production orders and lean manufacturing. In the lean manufacturing approach, the subcontracting work is modeled as a service that is related to an activity of a production flow. A special type of cost group type that is named **Direct outsourcing** has been introduced, and the subcontracting services are no longer part of a bill of materials (BOM). The cost accounting of subcontracted work is fully integrated into the costing solution for lean manufacturing.

## Production flows that involve subcontractors
The basic principle of a production flow doesn't change when activities are subcontracted. Material still flows between locations, process activities convert material to products, and transfer activities move material or products from one location to another. You can model locations and work cells as vendor-managed by assigning the vendor account to a warehouse or to a resource of a resource group.  

Based on these capabilities, lean manufacturing doesn't require any specific features in order to support the flow of material and products. All possible scenarios that involve vendors as providers of production or transport services can be modeled based on the architecture of production flow and activities.  

For example, a subcontractor works out of a supermarket that is located at the subcontractor. When handling units are emptied at the subcontractor, the kanban cards are returned to the assembly cell together with the next shipment. The supermarket at the subcontractor is then replenished. The transfers to and from the subcontractor can be modeled as explicit transfer activities to support a picking and shipment process. If an explicit registration isn't required in order to support the physical transport, the transfer activities can be omitted.  

A subcontractor can be used to load balance the overall capacity of the production flow. For example, a production flow is modeled by using scheduled kanban rules. The planner uses the kanban scheduling board to schedule and load level both work cells on demand. The planner also monitors the consolidated supply schedule for the supermarket on the **Supply schedule** page. Multiple subcontractors can be modeled in one or multiple production flows, and there might be multiple kanban rules that can be used to supply the same product to the same location through different activities. The planner can convert kanbans to an alternative kanban rule to reschedule a kanban that was originally created for internal production to an alternative process. In fact, the subcontracted nature of the work cell has no impact on the production flow. The same working principle applies for two parallel internal work cells or for two subcontracted cells.   

Like any other activity in a production flow, subcontracted activities can consume and supply inventoried, non-inventoried (work in process \[WIP\]), and semi-finished material and products. In all cases, the processes for scheduling and executing subcontracted activities are the same. Additionally, these process the same as the processes for internal work.

## Purchase process for subcontracted activities (services)
The purchase process for subcontracted activities is based on the physical material flow that is registered by kanban job progress, for example, Start or Complete. The financial flow, for example, cost of subcontracted work, is a secondary flow that follows the physical flow. At the same time, the purchase process is an independent process that allows for manual adjustment of the purchase documents at every step. Here is the purchase process for subcontracted activities:

1.  Create a purchase agreement. The purchase agreement is created for the service and connected to the activity of the production flow.
2.  Create a purchase order. A release purchase order can be created for the service, based on the scheduled kanban jobs. Jobs for the same service can be grouped to purchase order lines by day, week, or month. The purchase order lines can be created at any time after the kanban jobs are created. Purchase order lines can even be created after the fact. This option is usually selected if a subcontractor provides services without additional notice, based on the kanbans or kanban cards that the subcontractor receives. In this case, deviations between the purchase order and the invoice can be minimized.
3.  Generate kanban cards, material, and a picking list to send to the subcontractor to prepare for processing. Based on the detailed modeling of the production flow, the preparation is done on the kanban board for process activities by using the picking list and the preparation function. Alternatively, the preparation is done on the kanban board for transfer jobs by using the picking list and start or completion. For inventoried material, both processes can be supported by a WMS-Picking and Shipment process. A bill of lading can be created on demand.
4.  Generate kanban handling units and kanban cards. After processing, cards are returned from the subcontractor. Usually, the cards include a delivery note that specifies the physical material that has been shipped. A reference to the provided services isn't required. The arrival of the material or product at the customer is registered on the kanban board, depending on the kanban cards. (Either the kanban board for process activities or the kanban board for transfer jobs is used, depending on the modeled activities.).
5.  Create a receipt advisory. The receipt advisory can be used to replace a packing slip document for the received services. Receipt advisories can be generated based on the completed kanban jobs for the subcontracting activity for a selected period. For each job receipt, advisories are created for the related purchase order line. The receipt advisory can be printed and sent to the subcontractor as confirmation of receipt.
6.  Generate an invoice.

The process ends when the subcontractor is invoiced for a period. The invoice match is done against the receipt advisories that are created. Because the receipt advisories represent the exact physical receipt of material, the three-way matching is simplified.

## Configuring activities for subcontracting
The following sections describe how to configure activities for subcontracting.

### Subcontracted services

The payment item that is used in activity-based subcontracting must be a product that has the following properties:

-   **Product type:** Service
-   **Inventory model group:** Non stocked

This requirement enforces the use of the first in, first out (FIFO) inventory model. **Note:** Cost calculation of the products requires that the standard cost of the service be defined. A purchase agreement with the vendor is required. Otherwise, the service can't be used for activity-based subcontracting.

### Subcontracted process activities

To configure a process activity as a subcontracted activity, follow these steps.

1.  Configure a subcontracted work cell. To configure a work cell as subcontracted, you must create a resource of the **Vendor** type and associate it with the work cell (resource group). A runtime cost category of the **Direct outsourcing** cost group type should be assigned to the work cell. The cost categories for setup and quantity aren't required.
2.  After a process activity is created and related to a subcontracted work cell, you must configure a service for the activity before the production flow version can be activated. You complete this step on the **Activity** **details** page. For activities that are associated with a subcontracted work cell, the **Service terms** FastTab is shown. On this FastTab, add a default service that is valid for all output items. If specific output items require different services or different service calculation parameters (for example, a different service ratio), you can add other services to the activity.

## Subcontracted transfer activities
A transfer activity is configured as a subcontracted activity, depending on the **Freighted by** setting of the transfer activity. The following options are available:

-   **Shipper** – The activity is subcontracted if the transfer from the warehouse is managed by a vendor (as defined by a property of the warehouse). All selected purchase agreements for services must have the same vendor ID as the warehouse.
-   **Recipient** – The activity is subcontracted if the transfer to the warehouse is managed by a vendor (as defined by a property of the warehouse). All selected purchase agreements for services must have the same vendor ID as the warehouse.
-   **Carrier** – The activity is subcontracted to any vendor that provides the service. To be valid, a carrier must be created for warehouse management and must have an assigned vendor account.

As for process activities, you must configure a default service for subcontracted transfer activities on the **Service terms** FastTab of the **Activity** **details** page.

## Service quantity calculation
The whole purchase process is based on an item reference for a service. This item reference is measured in a unit of measure of a service. Services are usually measured either in the number of services (units) or in time. To calculate the service quantity, based on the registered completion of kanban jobs, you can use the following methods:

-   **Calculation that is based on the number of jobs** – One kanban job equals *n* units of service, regardless of the product quantity that is supplied. In lean manufacturing, one job corresponds to one handling unit. This calculation method applies to all services that have a fixed price per handling unit. Therefore, this method usually applies to transfer activities. However, it can also apply to process activities that process whole handling units.
-   **Calculation that is based on the product quantity** – The service quantity is relative to the product quantity that is scheduled/supplied. When the supplied product quantity is calculated, error quantities can be either included or excluded. This calculation method applies to all cases where the service price per unit of processed product is agreed upon.
-   **Calculation that is based on the activity time** – The theoretical activity times are calculated, based on the processing time of the activity, the total processed quantity, and the throughput ratio of the processed product. This calculation method applies to services that are paid by the hour and have a variance in time per processed product.

## Cost accounting of subcontracted services
When the receipt advisory or a vendor packing slip on a purchase order that was created for a production flow (in other words, a purchase order that was generated based on kanban jobs for subcontracted activities) is posted, the value of the receipt is accounted in the WIP accounts of the production flow. Deviations of invoices are also accounted to the production flow. A cost category for subcontracted work has been introduced. This cost category enable transparent tracking of the value of subcontracted work that is allocated to WIP and consumed per period.  

The backflush costing for lean manufacturing at the end of a costing period calculates the actual variances of the products that are produced from the production flow during the costing period.

## Modeling transfers as subcontracted activities
People often consider transport nonproductive and think that it adds no value. However, when the cost of subcontracting is compared to the cost of internal production, the cost of additional transport activities must be considered. A production flow that spans multiple locations and requires transport services should model the transport cost as part of the cost of supplying the products to the customer. 

Activity-based subcontracting in lean manufacturing lets you integrate carriers and transport vendors that move material and products between the locations of a production flow. By modeling a transfer activity, you can assign a carrier or vendor. The transfer activities/job is based on a service and purchase agreement, and you can create purchase orders and receipt advisories, based on the actual transfer jobs. This functionality is the same as the functionality for subcontracted process activities.  

Therefore, Dynamics 365 for Operations now supports BOM calculation that includes transport services, the creation of related purchase orders, integrated receipt registration, and the integration of transport service costs into the production flow costing.

