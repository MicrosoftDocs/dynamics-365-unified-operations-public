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

*Warehouse management only mode* lets you take advantage of the core warehouse management (WMS) functionality offered by Dynamics 365 Supply Chain Management while continuing to leverage your existing investments in third-party ERP and order-management systems. Regardless of which ordering or ERP systems you have in place, you can now rapidly deploy our advanced WMS without having to set up or maintain areas of Supply Chain Management that you don't need. Then you'll be ready to benefit from advanced WMS features such as automation integration, carrier integration, the Warehouse Management mobile app, and more.

The integration of Supply Chain Management WMS functionality with external ERP and ordering systems is made possible by lightweight source documents dedicated to inbound and outbound shipment orders. These documents focus exclusively on warehouse management and are therefore able to replace multiple types of more general-purpose documents (such as sales orders, purchase orders, transfer orders, and so on) from a pure warehouse-management perspective.

## Deployment options

Warehouse management only mode provides several deployment options to support the business needs of running your [warehouse management](warehouse-management-overview.md) processes.

The following image provides a high-level diagram of the various elements and processes of an integrated system.

:::image type="content" source="media/wms-only-high-level-integrations.svg" alt-text="High level integration diagram." lightbox="media/wms-only-high-level-integrations.svg":::

The solution is very flexible, so you can choose the configuration of features and systems that best fits your business needs. Here are a few examples of how you could integrate Supply Chain Management warehouse management mode with other systems:

- Use Supply Chain Management only for handling warehouse operations, with all orders and financial processing handled by an external system. With this implementation concept, you must configure the processes around warehouse management as part of Supply Chain Management.  
- Use Supply Chain Management to handle warehousing plus a wider range or processes (such as sales, purchase, production orders, and so on) while also using Supply Chain Management to handle warehouse operations for other ERP and order-processing systems. With this type of implementation, the same warehouse instance can handle all the logistic warehouse processes for both internal and external integrations.
- Use a combination of these two approaches. For example, you could set up a dedicated legal entity in Supply Chain Management deployment that only handles the warehouse management processes for external systems.

## Inbound process

The following illustration highlights the various elements of the inbound process.

:::image type="content" source="media/wms-only-inbound-wom-process.svg" alt-text="Warehouse management only mode inbound process." lightbox="media/wms-only-inbound-wom-process.svg":::

Here's a high-level description of the inbound process:

1. An external system submits an *inbound shipment order* message to Supply Chian Management.
1. Supply Chian Management processes the message in Warehouse management only mode and creates orders.
1. Inbound loads are created in one of three ways (as established by the [**Source systems** settings](wms-only-mode-setup.md#source-systems) in Supply Chain Management):
    - Manually, using the [Inbound load planning workbench](create-or-modify-an-inbound-load.md#create-an-inbound-load-manually)
    - By importing [advanced shipping notices (ASNs)](import-asn-data-entity.md)
    - Automatically during [message processing](../supply-chain-dev/message-processor.md)
1. A warehouse worker using the Warehouse management mobile app to *register* the inbound shipment transactions using one following [processes](configure-mobile-devices-warehouse.md#configure-menu-items-to-create-work-for-another-worker-or-process) (each of which requires an inbound load): <!--KFM: Should we call these processes or flows? -->
    - *License plate receiving (and put away)*
    - *Load item receiving (and put away)*
    - *Mixed license plate receiving (and put away)* (for source document line identification method **Load item receiving**)
    - *Inbound shipment order line receiving* (when assigned to loads)
    - *Inbound shipment item receiving* (when assigned to loads)
    - *Inbound shipment order line receiving (and put away)* (when assigned to loads)
    - *Inbound shipment order item receiving (and put away)* (when assigned to loads)

1. Supply Chian Management runs [receiving completed](wms-only-mode-using.md#receiving-completed) processes related for each relevant load. These processes update the load status to *Received* and generate [shipment receipts](wms-only-mode-using.md#shipment-receipts) and trigger *business events** for the external systems.
1. The external systems read and uses the [shipment receipts](wms-only-mode-using.md#shipment-receipt) data for further processing, such as purchase order invoicing if you have purchase orders associated with the inbound shipment orders in the external system.
1. Supply Chian Management finalizes the inbound shipment orders by running the *Post shipment receipts* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

## Outbound process

The following illustration highlights the various elements of the outbound process.

:::image type="content" source="media/wms-only-outbound-wom-process.svg" alt-text="Warehouse management only mode outbound process." lightbox="media/wms-only-outbound-wom-process.svg":::

Here's a high-level description of the outbound process:

1. An external system submits an *outbound shipment order* messages.
1. Supply Chian Management processes the message in Warehouse management only mode and creates orders.
1. Inventory reservations are created in one of two ways (as established by the [**Source systems** settings](wms-only-mode-setup.md#source-systems) in Supply Chain Management):
    - Automatically, by the [message processor](../supply-chain-dev/message-processor.md)
    - Manually, as part of the release process
1. The orders is released for further warehouse processing, either manually or automatically (by running the *Automatic release of outbound shipment orders* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md)).
1. Depending on how your [wave template](wave-templates.md) definitions are set up, warehouse work may be created and released immediately. <!--KFM: In the original, this was combined with the above sentence. Please review to confirm whether I have understood correctly. Also, what else might happen here? -->
1. The outbound warehouse work is processed and the status of the related outbound shipment order line transactions are updated *Picked*. <!--KFM: How is it processed, and by whom? workers? -->
1. The loads are outbound ship confirmed, which results in *business events* and a [*shipment packing slip*](wms-only-mode-using.md#shipment-packing-slips) being created for the external system.
1. The external system reads the shipment packing slip and uses its data for further processing (such as for sales order invoicing for sales orders that are associated with outbound shipment orders).
1. Supply Chian Management finalizes the outbound shipment order by running the *Post shipment packing slips* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

> [!NOTE]
> You'll be able to reverse the shipment confirmation until the related outbound shipment order line transactions is finalized, but not thereafter.

## Unsupported processes
<!-- Slotting, QMS, x-docking, ... KFM: Do we need this comment still? -->
The following high-level processes aren't supported out-of-the-box when Supply Chain Management is integrated with external systems.

| Process | Description |
|--|--|
| [Warehouse slotting](warehouse-slotting.md) processing | The current version isn't able to include outbound shipment orders in slotting templates. |
| Linked quality order processing | For other type of source documents (such as purchase orders) you can define [quality associations](../inventory/quality-management-for-warehouses-processes.md#quality-associations) to create quality orders automatically. This capability isn't yet supported for inbound shipment orders. |
| Return order processing with disposition codes | When using the inbound shipment orders related to an inbound return process, it isn't possible to use the process used by [sales return orders](sales-returns.md), which supports return-reason codes and disposition codes as part of the *Return order receiving (and put away)* mobile device menu item flow. |
| Cross docking | Outbound shipment orders and inbound shipment orders can't yet be used with [planned cross docking](planned-cross-docking.md) or [cross-docking from production orders to outbound docks](../production-control/cross-docking-opportunities.md). |
| Inbound Warehouse management mobile app flows | The Warehouse management mobile app flows for inbound shipment orders don't support the following processes in the same ways as the <!--KFM: word missing? -->:<ul><li>[Goods in transit](../landed-cost/in-transit-processing.md#warehouse-management), having the receiving process handled against a container<!--KFM: please clarify--></li> <li>Mobile device menu items configured to use the *Purchase/Transfer order item receiving (and put away)* or *Purchase/Transfer order line receiving (and put away)* process. You can use the *Inbound shipment order item receiving (and put away)* and *Inbound shipment order line receiving (and put away)* processes as long as the order lines are associated to a load.</li><li>The *Report as finished (and put away)* mobile device process for production. </li></ul> |
| Production flows | Production order, batch order, and kanban processing, including material consumption and report-as-finished via the Warehouse management mobile app aren't supported in the same way against the inbound shipment orders and outbound shipment orders. <!--KFM: please clarify--> |
| Outbound load planning with release to warehouse from loads | The current release of the Warehouse management only mode doesn't provide out-of-the-box support for associating outbound shipment order lines with loads before the [release to warehouse](release-to-warehouse-process.md) process. This association can only be made when processing warehouse waves. Therefore, Supply Chain Management Transportation management integration isn't supported out-of-the-box. |
| Creation of orders from warehouse app | The process of creating outbound shipment orders from the Warehouse management mobile app (similar to the *Create transfer order from license plates* process for mobile devices) isn't supported. <!--KFM: please confirm the parenthetical statement--> |
| Internal order processing information provided to external systems | When you are using the supported orders in Supply Chain Management (such as transfer, sales, purchase, production, and so on), all the related business process data are automatically maintained within Supply Chain Management, but no business events or related inbound and outbound on-hand information will be provided to external systems for these kinds of processes. This means that if you, for example, create a transfer order and ship inventory out of one warehouse and receive it into another within Supply Chain Management, you must use a method different from the one described for inbound shipment orders and outbound shipment orders to inform the external systems about the operations. |
| [Order-committed reservations](flexible-warehouse-level-dimension-reservation.md) as part of the *allow reservation on demand order* capability | *Outbound shipment order line* transaction reservations don't support having reservations on inventory dimensions below the location in the reservation hierarchy, as supported for a *Sales order line* transaction. <!--KFM: clarify the closing phrase --> |
| [Owner dimension](../inventory/consignment.md#inventory-owners) values different from operating legal entity | It isn't yet supported to import and process shipment order lines where the *Owner* tracking dimension value is different from the used legal entity (company). <!--KFM: please confirm this edit --> |
| Items enabled for [catch weight processing](catch-weight-processing.md) | Items enabled for catch weight processing aren't supported for inbound shipping orders or outbound shipping orders. |
| Policies defined per vendor or customer accounts | Representations of vendors and customers aren't used for inbound shipping orders or outbound shipping orders. Therefore, it isn't possible to use related order processing policies with this kind of setup. For example, you can't use customer- or vendor-specific [product filters](filters-and-filter-codes.md). |
| Order line *Registration* and *Pick* update processing | Inbound shipment order lines and outbound shipment order lines don't support the manual registration and unregistration processes supported by other types or order lines (such as purchase, sales, and transfer). |
| [Item arrival journal](../inventory/arrival-overview.md) processing | In the current version, inbound shipment order lines can be processed via an item arrival journal, but no load ID will be associated with the related inventory transactions. This means that you won't be able to use the out-of-the-box [shipment receipt](wms-only-mode-using.md#shipment-receipts) information, nor have the [inbound shipment order status](#inbound-shipment-orders) updated. <!--KFM: please clarify. Where is the link supposed to go? --> |
