---
# required metadata

title: Manage subcontracting work in production
description: This topic explains how subcontracted operations are managed in Microsoft Dynamics 365 for Operations. In other words, it explains how production operations that are allocated to a resource are managed by a vendor.
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LeanDocumentServiceCreation, PlanActivity, ProdBOMVendorListPage, ProdRoute, ProdTable, ProdTableListPage, PurchAgreementSubcontractorLookup, RouteTable, WrkCtrResourceGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2094
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 268174
ms.assetid: fe47c498-4f48-42a2-a0cf-5436c19ab3ea
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: conradv
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manage subcontracting work in production

[!include[banner](../includes/banner.md)]


This topic explains how subcontracted operations are managed in Microsoft Dynamics 365 for Operations. In other words, it explains how production operations that are allocated to a resource are managed by a vendor.

In [production processes](production-process-overview.md), work can be done by resources that are owned or administered by vendors. Typically, vendor resources are used to level periodic excess demand that surpasses the available capacity of a company's own resources. The vendor might also be able to offer specific [resource capabilities](resource-capabilities.md)or resources at a lower price.  

Depending on the vendor resources that are used in a production process, a [route](routes-operations.md) often has additional logistic requirements, because the material and semi-finished products must first be transported to the vendor's site. Then the result of the subcontracted operation must be transported either to the location that is allocated to the next operation or to a finished goods warehouse.  

When subcontracting operations or activities are used, they affect all stages of operations, from the definition of the operations that are required in production, costing, forecasting, planning, and scheduling, to the management of logistics for materials, semi-finished products, and finished goods. Finally, these resources require their own processes for accounting and cost control.  

For internal resources, a fixed cost rate is typically allocated for a period. By contrast, the cost of subcontracted resources is based on the purchase price of the related service. The service is defined as another product, and is used to drive the procurement and purchase processes for a given subcontracted operation.  

Currently, there is no explicit concept of semi-finished products in Microsoft Dynamics 365 for Operations. For a production order that requires more than one operation in order to transform raw materials into a finished good, the finished good is posted back into inventory only in the last operation. The semi-finished products that the earlier operations produce are accounted in work in progress (WIP), but they aren't posted or tracked in inventory. Although you can split the routes and bills of materials (BOMs) into multiple smaller units, this approach increases the number of products, BOMs, and routes that must be managed.  

There are two methods for modeling subcontracting work for production operations. These methods differ in the way that the subcontracting process can be modeled, the way that semi-finished products are represented in the process, and the way that cost control is managed.

-   Subcontracting of route operations in production orders or batch orders
    -   The service product must be a stocked product, and it must be part of the BOM.
    -   This method supports first in, first out (FIFO) or standard cost.
    -   Semi-finished products are represented by the service product in the process.
    -   Cost control allocates the costs that are associated with subcontracted work to the material costs.
-   Subcontracting of production flow activities in a lean production flow
    -   The service is a non-stocked service product, and it isn't part of the BOM.
    -   This method uses purchase agreements as service agreements.
    -   This method uses backflush costing.
    -   This method allows for aggregated and asynchronous procurement. (Material flow is independent of the procurement process.)
    -   Cost control allocates subcontracted work in its own cost breakdown block.

## Subcontracting of route operations
To use subcontracting of route operations for production or batch orders, the service product that is used for the procurement of the service must be defined as a product of the **Service** type. Additionally, it must have an item model group that has the **Stocked product** option under **Inventory policy** set to **Yes**. This option defines whether a product is accounted as inventory on product receipt (**Stocked product** = **Yes**), or whether the product is expensed on a profit and loss account (**Stocked product** = **No**). Although this behavior might seem contradictory, it's based on the fact that only products that have this policy will create inventory transactions that can be used in cost control to calculate planned cost and determine the actual cost when a production order is ended.  

To be considered in planning and cost calculation, the service must be added to the BOM. The BOM line must be of the **Vendor** type, and it must be allocated to the route operation that the service is allocated to. This route operation must have a costing resource and resource requirement that point to a resource of the **Vendor** type that connects the operation and the related service to the corresponding vendor account.  

When this configuration is used, a purchase order is created for the related service product, based on estimation of a production order. The purchase order of the service is used as an anchor for the subcontracted operations. The subcontracted work can be managed through the **Subcontracted work** list page in Production control. The subcontracted work is used to ship raw material and, eventually, a semi-finished product to the vendor in preparation for the operation. It's also used to receive the resulting product of the subcontracted operation in item arrival, where the service product is used to identify the arrival of the semi-finished product. When the purchase order line is received, the production operation is updated as completed.  

A production order can have many operations, and each operation can be allocated to a different vendor. Therefore, an end-to-end production order might trigger multiple purchase orders.

## Subcontracting of production flow activities
The [lean manufacturing](lean-manufacturing-overview.md)solution models the subcontracting work as a service that is related to an activity of a [production flow](http://ax.help.dynamics.com/en/wiki/create-a-production-flow-version/) (Task guide topic). Therefore, this type of subcontracting is also referred to as [activity-based subcontracting.](activity-based-subcontracting.md) A special cost group type, **Direct outsourcing**, has been introduced, and the subcontracting services aren't part of the BOM of the finished goods. When you use lean manufacturing, all activities are defined by kanbans that can be related to one or multiple production flow activities. So far, that explanation sounds just like an explanation of production orders. However, whereas production orders must always end with a finished product, you can create kanbans to supply a semi-finished product. You don't have to introduce a new product and BOM level.  

Because kanban rules can be very dynamic, you can model different variants of supply for the same product on a production flow. When you use lean subcontracting, the material flow and the financial flow are strictly separated. All material flow is represented by kanban activities. The purchase orders for the service products and the receipt postings of those services can be automated, based on the status of kanban jobs in the production flow. Kanban jobs can be started and completed even before the purchase orders are created. The subcontracting documents (purchase order and purchase receipt of the service) can be aggregated by period and service. Therefore, the number of purchase documents and lines can be kept small, even in highly repetitive operations where vendors provide subcontracted services in a single-piece flow.

### Modeling subcontracting in a production flow

In a [lean production flow](lean-manufacturing-modeling-lean-organization.md), a process activity can be defined as subcontracted when it's allocated to a work cell (resource group) that has a single vendor resource. When a work cell is subcontracted, the related process activities must be linked to an active purchase agreement line that contains the service item and the price of the service. The service agreement of the activity also defines the calculation ratio between the product quantity of the kanban job and the resulting service quantity. You can select whether the service quantity is calculated based on the number of jobs, the good product quantity that is reported on the jobs, or the total product quantity (this total quantity includes scrapped products).  

Transfer activities can also be defined as subcontracted. This definition occurs implicitly when you select the responsible party for the shipping in the transfer activity. When you select **Shipper** or **Recipient**, if the corresponding source or target warehouse is a vendor-managed warehouse, the activity is considered subcontracted. When you select **Carrier**, the activity is always subcontracted. Like subcontracted process activities, a subcontracted transfer activity must be connected to a service agreement before the production flow can be activated.

### Backflush costing

The cost accounting of subcontracted work is completely integrated into the costing for the lean manufacturing solution (backflush costing). When the purchase order receipt of the service is posted, or when invoicing occurs, the cost of the service is allocated to the production flow. For backflush costing, the variance of subcontracted services is calculated by offsetting the subcontracting block of the standard cost of the received products against the actual received and invoiced service quantities.

## Material supply for subcontracted operations
Semi-finished products and other related materials must be transferred to the location where the work is physically performed. When you use subcontracted operations and activities, this transfer is often related to additional transport to a vendor-operated site. By allocating material in the BOM to the subcontracted operation, you declare that the material must be staged at the input location of the resource group for the allocated resource. Master planning or lean replenishment then provisions the material to that location.  

To model the inventory that is located at a vendor site, it's a best practice in the industry to define a vendor-managed warehouse. You can easily define a vendor-managed warehouse by creating a new warehouse and assigning the vendor account. To document that material must be transferred to the vendor before an operation can be performed, you should allocate the vendor-managed warehouse to the input warehouse of the resource group that holds the resource.  

To replenish material at this warehouse, you can use multiple strategies:

-   Transfer orders
-   Transfer journals
-   Withdrawal kanbans
-   Direct purchase to the vendor location

Semi-finished products are the exception to this rule. To transfer semi-finished products, you're limited to these options:

-   For production and batch orders, semi-finished products can only be transferred logically by using the Picking list journal from the **Subcontracted work** list page. This journal will create a delivery note document that can be used to transfer semi-finished and raw material to the vendor.
-   For subcontracted operations in production flows, the transfer of semi-finished products is documented by the receipt of withdrawal or production kanbans at the vendor location. To model an explicit transfer activity, you can end a production kanban with an additional transfer activity.

**Note:** A production route for a single production order can't cross multiple sites. This rule also applies to the subcontracted work. Therefore, the warehouses that represent the vendor-managed material locations must be defined in the same site as the internal resources that are used in the route. Although production flows can cross sites, they can't transport semi-finished products from one site to another, because that operation implies a change of cost context.  

Typically, the output warehouse and location of a subcontracted resource group are directly allocated to the warehouse and location of the next step of the operation in the route or production flow. This setup helps reduce the amount of job reporting that occurs or the number additional transfer operations that must be modeled.



