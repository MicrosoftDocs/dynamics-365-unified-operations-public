---
title: Production process overview
description: This article gives an overview of the production processes. It describes the various stages of production orders, batch orders, and kanbans, from order creation to closing of the financial period. 
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: JmgShopSupervisorWorkspace, Kanban, ProdTable, ProdTableOverview, EcoResProductDiscreteManufacturingWorkspace, KanbanPrepareProductForLeanWorkspace, EcoResProductProcessManufacturingWorkspace, OpResLifecycleManagementWorkspace, ProdParmCostEstimation, ProdParmRelease, ProdSchedule, ProdTableListPage
ms.topic: overview
ms.date: 01/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Production process overview

[!include [banner](../includes/banner.md)]

This article gives an overview of the production processes. It describes the various stages of production orders, batch orders, and kanbans, from order creation to closing of the financial period.

The production of products, a process that is also known as the production life cycle, follows specific steps that are required to complete the manufacture of an item. The life cycle begins with the creation of the production order, batch order, or kanban. It ends with a finished, manufactured item that is ready for either a customer or another phase of production. Each step in the life cycle requires different kinds of information to complete the process. As each step is completed, the production order, batch order, or kanban shows a change in the production status. Different types of products require different manufacturing processes.

The **Production control** module is linked to other modules, such as **Product information management**, **Inventory management**, **General ledger**, **Warehouse management**, **Project accounting**, and **Organization administration**. This integration supports the information flow that is required to complete the manufacturing of a finished item.

The production process is typically influenced by the cost accounting and inventory valuation methods that are chosen for a specific production process. Supply Chain Management supports both actual cost (first in, first out \[FIFO\]; last in, first out \[LIFO\]; moving average; and periodic weighted average) and standard cost methods. Lean manufacturing is implemented based on the backflush costing principle.

The choice of the cost measurement methods also defines the requirements for reporting about material and resource consumption during the production process. Typically, actual cost methods require accurate reporting on the job level, whereas periodic costing methods allow for less granular reporting of material and resource consumption.

## Mixed mode manufacturing

Different products and production topologies require the application of different order types. Supply Chain Management can apply the various order types in a mixed mode. In other words, all order types can occur during the end-to-end process of producing one finished product.

- **Production order** – This is the classic order type to produce a specific product or product variant in a given quantity on a specific date. Production orders are based on bills of materials (BOMs) and routes.
- **Batch order** – This order type is used for process industries and discrete processes where the manufacturing conversion is based on a formula, or where co-products and by-products can be end products, either in addition to or instead of the main product. Batch orders use **Formula** type BOMs and routes.
- **Kanban** – Kanbans are used to signal repetitive lean manufacturing processes that are based on production flows, kanban rules, and BOMs.
- **Project** – A manufacturing project combines products and services with a given schedule and budget. The manufacturing part of a project can be delivered through any of the other order types.

## Manufacturing principles

To select the manufacturing principle that best applies to a particular product and related market, you must consider the requirements of production and logistics, and also customer expectations about delivery lead times.

- **Make to stock** – This is the classic manufacturing principle, where products are produced for stock, based on forecast or minimum stock refill (the latter is typically calculated based on forecast or historic consumption).
- **Make to order** – Standard products are made to order or finished to order. Although pre-production might be done by using the Make to stock principle, expensive steps of the value chain, or steps that create variants, are triggered by a sales order or transfer order.
- **Configure to order** – As for the Make to order principle, the final operations of the value chain are made to order. The actual product variant that is produced isn't predefined but is created at the time of order entry, based on the configuration model of the sales product. The Configure to order principle requires a certain level of process unification for a given product line.
- **Engineer to order** – Engineer to order processes are typically addressed by a project and usually start with the engineering phase. During the engineering phase, the actual products that are required fulfill the order are designed and described. Production orders, batch orders, or kanbans can then be created to produce the products.

## Overview of the production life cycle

The following steps in the production life cycle can occur for all order types of mixed mode manufacturing. However, not all of them are represented as an explicit order status.

1. **Created** – You can create a production order, batch order, or kanban manually, or you can configure the system to generate them based on various demand signals. Master planning creates production orders, batch orders, or kanbans by firming planned orders. Other demand signals are sales orders or pegged supply signals from other production orders or kanbans. For fixed-quantity kanbans, demand signals are generated when kanbans are registered as empty.
1. **Estimated** – You can calculate estimates for material and resource consumption. The estimation generates inventory transactions for raw materials that have a status of **On order**. The receipts for main products, co-products, and by-products are generated when production orders or batch orders are estimated. If the BOM contains lines of the **Pegged supply** type, purchase orders for materials or subcontracted operation services are generated and pegged to the production order or batch order. Items or orders are reserved according to the reservation strategy of the production order, and the price of the finished goods is calculated based on parameter settings.
1. **Scheduled** – You can schedule production based on operations, individual jobs, or both.

    - **Operations scheduling** – This scheduling method provides a rough, long-term plan. By using this method, you can assign start and end dates to production orders. If the production orders are attached to route operations, you can assign them to cost center groups.
    - **Job scheduling** – This scheduling method provides a detailed plan. Each operation is broken down into individual jobs that have specific dates, times, and assigned operations resources. If finite capacity is used, jobs are assigned to operations resources based on availability. You can view and change the schedule in a Gantt chart.
    - **Kanban schedule** – Kanban jobs are scheduled on the kanban schedule board or automatically scheduled based on the automatic planning configuration of the kanban rules.

1. **Released** – You can release the production order or batch order when the schedule is finished and the material is available to be picked or prepared. The material availability check helps the shop floor supervisor assess the availability of material for the production orders or batch orders. You can also print the production order documents, such as the pick lists, job card, route card, and route job. When the production order is released, the status of the order changes to indicate that the production can begin. When warehouse management is used, release of the production order or batch order releases the production BOM lines to warehouse management. Warehouse waves and warehouse work are then generated according to the setup of the warehouse.
1. **Prepared**/**Picked** – When all materials and resources have been staged at the production location, the production BOM lines or kanban lines are updated to a status of **Picked**. Pegged supply orders and related warehouse work are typically completed at this stage. The kanban cards or job cards that are required to report production progress should be assigned and printed.
1. **Started** – When a production order, batch order, or kanban is started, you can report material and resource consumption against the order. The system can be configured to automatically post the material and resource consumption that are allocated to the order when the order is started. This allocation is known as preflushing, forward flushing, or autoconsumption. You can manually allocate materials to production orders or batch orders by creating additional picking list journals. You can also manually allocate labor and other route costs to the order. If you're using operations scheduling, you can allocate these costs by creating a route card journal. If you're using job scheduling, you can allocate the costs by creating a job card journal. Production orders or batch orders can be started in batches of the requested final quantity. Within a production order, batch order, or kanban, the jobs that are created can be started and reported separately through journals, the manufacturing execution terminal (MES Terminal), or the kanban boards.
1. Report progress/**Complete** jobs – Use the MES Terminal, production journals, kanban boards, or mobile scanning capabilities to report the production progress by job or resource. Material and resource consumption will be posted, and the status of the related kanbans, production orders, and batch orders might be updated to **Received** or **Reported as finished**. Put-away work for the warehouse might be created, depending on the warehouse configuration.
1. **Reported as finished** (the product receipt) – When a production order or batch order is reported as finished, the quantity of the finished goods that were completed is updated in inventory. This quantity includes the quantity of relevant co-products and by-products. If you're using work-in-process (WIP) accounting, a ledger journal is generated to reduce the WIP accounts and increase the inventory of the finished goods. When the cost of a production order is calculated, the actual cost of the production is posted. If the material and labor costs that are associated with a production aren't already allocated in a journal or by preflushing, they can be automatically allocated through back-flushing. Allocation through back-flushing involves the post-deducting of inventory transaction processes. If the production order is completed, select the **End job** check box to change the remaining status to **Ended**. Otherwise, leave the field empty to enable reporting of additional quantities that are produced.
1. **Quality assessment** – A product receipt can trigger the creation of quality orders, depending on the configuration of test processes and the quality rules that are established for specific products. Because a quality order can update the inventory status or the batch attributes of the tested products, quality assessment is a mandatory process in many industries.
1. **Put away** and **Ship to order** – After product receipt and quality assessment, optional put-away work directs the received products to the next point of consumption, to a finished goods warehouse, or to a shipment zone if there are ship-to-order requirements.
1. **Ended** – Before production is ended, actual costs are calculated for the quantity that was produced. All estimated costs of material, labor, and overhead are reversed and replaced with actual costs. If you select the **End job** check box when you run the cost calculation, the production order status changes to **Ended**. This status prevents any additional costs from being posted to a completed production order.
1. **Period closure** – Some cost accounting principles, such as periodic average, back-flush costing, FIFO, or LIFO, require periodic activities to close the inventory or financial period. Typically, the system tries to report all material and resource consumption, and also corrections of inventory and scrap, before the periods are closed. This reporting is typically done by using inventory movement journals or adjustment journals. The goal is to assess the economic performance of operating units per period. In some cases, when long-running production orders are used that span the financial reporting periods, production journals are used to report the production progress and resource consumption by the end of the period.

## Additional resources

- [Production feedback](production-feedback.md)
- [Product configuration models overview](../pim/product-configuration-models.md)
- [Lean manufacturing overview](lean-manufacturing-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
