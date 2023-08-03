---
title: Warehouse management only mode overview
description: XXXX
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage
ms.topic: overview
ms.date: 08/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse management only mode overview

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

*Warehouse management only mode* provides several deployment options to support the actual business needs of running your [warehouse management](warehouse-management-overview.md) processes.

![High level integrations](./media/high-level-integrations.png)

One example being a dedicated LCS Supply Chain Management cloud deployment only handling the warehouse operations and all integrations related to orders and financial processing handled outside this deployment. With this implementation concept, you must configure the processes around warehouse management as part of the Supply Chain Management cloud deployment.  

![Warehouse management only mode to ERP/Order system, example 1](./media/scm-wom-2-erp.png)

Another example is a more Supply Chain Management integrated implementation methodology, having the warehouses enabled for Supply Chain Management processes like sales, purchase, production orders, etc. and at the same time handling warehouse operations for other ERP/order processing systems. With this type of implementation, the same warehouse instance can handle all the logistic warehouse processes for both internal and external integrations.

![Warehouse management only mode to ERP/Order system, example 2](./media/scm-wms-scm-2-erp.png)

And then everything between the two previous example deployment options, which for example could be running a dedicated legal entity within an existing Supply Chain Management deployment that only handles the warehouse management processes for external systems. All-in-all you can use the **Warehouse management only mode** exactly as needed.

## Inbound process

![Warehouse management only mode inbound process](./media/inbound-wom-process.png)

The high-level process for inbound processing is as follows:

1. An external system provides *Inbound shipment order* messages.
2. The messages get processed in *Supply Chain Management Warehouse management only mode* and orders get created.
3. Inbound loads are created manually via [**Inbound load planning workbench**](create-or-modify-an-inbound-load.md#create-an-inbound-load-manually), via [**ASN**](import-asn-data-entity.md), or automatically during [message processing](../supply-chain-dev/message-processor.md) based on the [**Source systems** – **Inbound shipment order policy**](#source-systems) definition.
4. Inventory receiving gets processed and the inbound shipment order transactions get *Registered* via one of the following [Warehouse Management mobile app](configure-mobile-devices-warehouse.md#configure-menu-items-to-create-work-for-another-worker-or-process) processes, each of which requires an inbound load:
    - *License plate receiving (and put away)*
    - *Load item receiving (and put away)*
    - *Mixed license plate receiving (and put away)* (for source document line identification method **Load item receiving**)
    - *Inbound shipment order line receiving* (when assigned to loads)
    - *Inbound shipment item receiving* (when assigned to loads)
    - *Inbound shipment order line receiving (and put away)* (when assigned to loads)
    - *Inbound shipment order item receiving (and put away)* (when assigned to loads)

5. The system runs [**receiving completed**](#receiving-completed) processes related for each relevant load. These processes update the load status to *Received* and generate [**Shipment receipts**](#shipment-receipts) and trigger **Business event** for the external systems.
6. The external systems read and uses the [**Shipment receipts**](#shipment-receipts) data for further processing, like for example purchase order invoicing in case of having purchase orders associated to the *inbound shipment orders* in the external system.
7. The *Inbound shipment orders* get finalized by running the periodic back-ground [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) **Post shipment receipts** job.

## Outbound process

![Warehouse management only mode outbound process](./media/outbound-wom-process.png)

The high-level process for outbound processing is as follows:

1. External system provides *Outbound shipment order* messages
2. The messages is processed in *Supply Chain Management Warehouse management only mode* and orders gets created. Depending on your [**Source system**](#source-systems) configuration, policies reservations are either automatically handled as part of the [message processing](../supply-chain-dev/message-processor.md) or must be processed manually or as part of the release process.
3. The orders is released for further warehouse processing, either manually or automatically via the batch job **Automatic release of outbound shipment orders** and based on the [wave template](wave-templates.md) definitions warehouse work can get created and released immediately.
4. The outbound warehouse work is processed and the related outbound shipment order line transactions get updated to status *Picked*.
5. The loads are outbound ship confirmed, which results in **Business events** and [**Shipment packing slip**](#shipment-packing-slips) data being created for the external systems.
6. The external systems read and use the [**Shipment packing slip**](#shipment-packing-slips) data for further processing, such as sales order invoicing for sales orders that are associated with *outbound shipment orders*.
7. The *Outbound shipment orders* get finalized by running the periodic back-ground [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) **Post shipment packing slips** job.

> [!NOTE]
> Reversal of the shipment confirmation will be supported as long as the related outbound shipment order line transactions have not been finalized.

## Unsupported processes
<!-- Slotting, QMS, x-docking, ... -->
The following high-level processes aren't supported out-of-the-box when Supply Chain Management is integrated with external systems.

| Process | Description |
|--|--|
| [Warehouse slotting](warehouse-slotting.md) processing | The current version doesn't support the ability to include *Outbound shipment orders* as part of the *Slotting templates*. |
| Linked quality order processing | For other type of source documents, such as *Purchase orders*, you can define [*Quality associations*](../inventory/quality-management-for-warehouses-processes.md#quality-associations) to control the triggering for creating quality orders automatically. This capability isn't yet supported for *Inbound shipment orders* |
| Return order processing with disposition codes | When using the *Inbound shipment orders* related to an inbound return process, it isn't possible to use the same process as the [*Sales return orders*](sales-returns.md), which supports the use of *Return reason codes* and *Disposition codes* as part of the *Return order receiving (and put away)* mobile device menu item flow. |
| Cross docking | The *Outbound shipment orders* and *Inbound shipment orders* can't yet be used as part of the [planned cross docking](planned-cross-docking.md) capability. Same limitation applies for the [cross-docking from production orders to outbound docks](../production-control/cross-docking-opportunities.md). |
| Inbound Warehouse management mobile app flows | The Warehouse management mobile app flows against *Inbound shipment orders* don't support the following processes in the same ways as the <!--KFM: word missing? -->:<ul><li>[Goods in transit](../landed-cost/in-transit-processing.md#warehouse-management), having the receiving process handled against a container</li> <li>Mobile device menu items configured like *Purchase/Transfer order item receiving (and put away)* and *Purchase/Transfer order line receiving (and put away)*. You can use the *Inbound shipment order item receiving (and put away)* and *Inbound shipment order line receiving (and put away)* processes as long as the order lines are associated to a load.</li><li>*Report as finished (and put away)* mobile device flow for production </li></ul> |
| Production flows | Production order, batch order, and kanban processing, including material consumption and report as finished via the Warehouse management mobile app aren't supported in the same way against the *Inbound* and *Outbound shipment orders* |
| Outbound load planning with release to warehouse from loads | The current release of the **Warehouse management only mode** doesn't provide out-of-the-box support for associating outbound shipment order lines with loads before the [**Release to warehouse**](release-to-warehouse-process.md) process. This association can only be made when processing warehouse waves. Therefore, Supply Chain Management **Transportation management** integration isn't supported out-of-the-box. |
| Creation of orders from warehouse app | The process of creating *Outbound shipment orders* from the Warehouse management mobile app, similar to the *Create transfer order from license plates* mobile device menu item isn't supported |
| Internal order processing information provided to external systems | When you are using the supported orders in Supply Chain Management (such as transfer, sales, purchase, production, and so on), all the related business process data are automatically maintained within the Supply Chain Management instance, but no business events or related inbound and outbound on-hand information will be provided to external systems for these kinds of processes. This means that if you, for example, create a transfer order and ship inventory out of one warehouse and receive it into another within Supply Chain Management, you must use a method different from the one described for *inbound and outbound shipment orders* to inform the external systems about the operations. |
| [Order-committed reservations](flexible-warehouse-level-dimension-reservation.md) as part of the *Allow reservation on demand order* capability | *Outbound shipment order line* transaction reservations don't support having reservations on inventory dimensions below the location in the reservation hierarchy, as supported for a *Sales order line* transaction. |
| [Owner dimension](../inventory/consignment.md#inventory-owners) values different from operating legal entity | It isn't yet supported to import and process *shipment order lines* and getting an **Owner** tracking dimension value different from the used company/legal entity. |
| Items enabled for [catch weight processing](catch-weight-processing.md) | Items enabled for catch weight processing aren't supported as part of the *Inbound* and *Outbound shipment orders* processing. |
| Policies defined per vendor or customer accounts | The representation of **Vendor** and **Customers** isn't used for the *Inbound and Outbound shipment orders*. Thereby it isn't possible to use related order processing policies with this kind of setup. An example for this is the customer and vendor specific [**Product filters**](filters-and-filter-codes.md). |
| Order line *Registration* and *Pick* update processing | *Inbound* and *Outbound shipment order lines* don't support the manual registration and unregistration process like other order types such as *Purchase*, *Sales*, and *Transfer order lines*. |
| [Item arrival journal](../inventory/arrival-overview.md) processing | In current version, the *Inbound shipment order lines* can get processed via an *Item arrival journal*, but no *Load ID* will be associated with the related inventory transactions. This means that you won't be able to use the out-of-the-box [Shipment receipt](#shipment-receipts) information, nor getting the [*Inbound shipment order status*](#inbound-shipment-orders) updated. |
