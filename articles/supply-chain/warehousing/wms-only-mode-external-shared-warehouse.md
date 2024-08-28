---
title: Warehouse management only mode with external shared warehouses
description: Learn how to run Warehouse management only mode with external shared warehouse processing with an outline on a high-level implementation example.
author: Mirzaab
ms.author: mirzaab
ms.topic: overview
ms.date: 04/27/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSEWManagementSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage, WHSEWInboundShipmentOrderRequest, WHSEWOutboundShipmentOrderRequest, WHSEWOutboundShipmentOrderUpdate, WHSInventoryOwner, WHSInventoryUpdateLog, WHSExternalInventoryAdjustment, WHSEWInboundShipmentOrderUpdate
---

# Warehouse management only mode with external shared warehouses

[!include [banner](../includes/banner.md)]

This article explains how to use Warehouse management only mode to support external shared warehouse processing. This approach enables warehouse management (WMS) functionality to be consolidated into a separate legal entity that handles requests from multiple sales subsidiaries (legal entities) in Microsoft Dynamics 365 Supply Chain Management.

You can use [Warehouse management only mode](wms-only-mode-overview.md) to handle logistics operations in a legal entity that's dedicated to warehousing operations. You can then connect warehouses between that legal entity and other legal entities that do all the order and financial processing. In addition, warehouse management processes can use an *owner* inventory dimension to track which legal entity owns the inventory for items that are shared across legal entities.

This feature works without modifications in a single-instance deployment model. If you want to link between multiple instances, one of which handles logistics and warehouse processes, you must set up an integration process like the one that's described in [Warehouse management only mode with external ERP system](wms-only-mode-external-erp.md).

To use *Warehouse management only mode* in a multi-instance deployment, you must use the [standard integration process](/dynamics365/guidance/implementation-guide/integrate-other-solutions).

The following articles provide detailed information about how *Warehouse management only mode* works:

- [Warehouse management only mode with external ERP system](wms-only-mode-external-erp.md)
- [Exchange data between systems](wms-only-mode-exchange-data.md)
- [Create and process message queues and message types](../supply-chain-dev/message-processor.md)

## High-level implementation example

The following illustration shows an example system where Warehouse management only mode is active with an external shared warehouse in the *WOM* legal entity. The *WOM* legal entity handles logistics warehouse operations for two sales subsidiaries that manage order and financial processing in the *LE1* and *LE2* legal entities.

:::image type="content" source="media/wms-only-d365-shared-warehouse-integration.svg" alt-text="Diagram that shows Warehouse management only mode with external shared warehouse." lightbox="media/wms-only-d365-shared-warehouse-integration.svg":::

## Inbound process example (shared warehouse)

The following illustration highlights the elements of the inbound process when you use a shared warehouse.

:::image type="content" source="media/wms-only-shared-warehouse-inbound-process.svg" alt-text="Diagram that shows the inbound process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-inbound-process.svg":::

Here's a high-level description of the inbound process. Steps that start with *LE1* are done by a sales subsidiary. Steps that start with *WOM* are done by the warehousing entity.

1. *LE1:* Purchase orders are created and released to the warehouse. The system then creates *external warehouse inbound shipment order requests*. As a result, inbound shipment order messages are delivered to the *WOM* legal entity. Purchase orders that are released to the externally managed warehouse can be processed via a periodic background process. (This background process is set up at **Warehouse management** \> **Periodic tasks** \> **Create external warehouse inbound shipment order requests**.) Alternatively, they can be manually processed by using the **Release to warehouse** option on the purchase orders page.
1. *WOM:* The warehousing entity processes the inbound shipment order messages. As a result of this processing, *inbound shipment orders* are created.
1. *WOM:* Inbound loads are created manually, automatically, or through import (depending on your configuration).
1. *WOM:* Warehouse workers use the Warehouse Management mobile app to register the inbound shipment order transactions.
1. *WOM:* The warehousing entity processes [receiving completed](wms-only-mode-shared-and-external-detail-use.md#receiving-completed) operations for the related loads. These operations update the load status to *Received* and generate *external warehouse inbound shipment order updates* for *LE1*. You can enable automatic [message processing](../supply-chain-dev/message-processor.md) for the *External warehouse shipment order updates* message queue.
1. *LE1:* During the processing of the external warehouse inbound shipment order updates, inbound loads and shipments are created, and the related purchase order line transactions are updated to *Registered*. This status update enables further processing of product receipts and invoices.
1. *WOM:* The warehousing entity finalizes the inbound shipment order line transactions by running the *Post shipment receipts* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

For a more detailed description of this process and the related processes, see [Work with warehouse management only mode in Supply Chain Management](wms-only-mode-shared-and-external-detail-use.md).

## Outbound example process (shared warehouse)

The following illustration highlights the elements of the outbound process when you use a shared warehouse.

:::image type="content" source="media/wms-only-shared-warehouse-outbound-process.svg" alt-text="Diagram that shows the outbound process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-outbound-process.svg":::

Here's a high-level description of the inbound process. Steps that start with *LE1* are done by a sales subsidiary. Steps that start with *WOM* are done by the warehousing entity.

1. *LE1:* Sales orders are created and released to the warehouse. The system then creates *external warehouse outbound shipment order requests*. As a result, outbound shipment order messages are delivered to the *WOM* legal entity.
1. *WOM:* The *Outbound shipment order messages* are processed. As a result of this processing, *outbound shipment orders* are created.
1. *WOM:* Inventory reservations are created either manually or automatically (depending on your configuration).
1. *WOM:* The orders are released for further warehouse processing, either manually or automatically. If you use outbound load planning processes, you can create loads by using the Outbound load planning workbench before you release the orders.
1. *WOM:* Depending on the setup of your [wave template](wave-templates.md) definitions, warehouse work might be created and released immediately.
1. *WOM:* Outbound warehouse work is processed, and the status of the related outbound shipment order line transactions is updated to *Picked*.
1. *WOM:* The loads are outbound ship confirmed. As a result, external warehouse inbound shipment order updates are generated for *LE1*.
1. *LE1:* During the processing of the external warehouse inbound shipment order updates, outbound shipment data and the related sales order line transactions are updated. The transactions become *Picked*. This update enables further processing of the packing slip and invoice. You can enable automatic [message processing](../supply-chain-dev/message-processor.md) for the *External warehouse shipment order updates* message queue.
1. *WOM:* The warehousing entity finalizes the outbound shipment order line transactions by running the *Post shipment packing slips* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

For a more detailed description of this process and the related processes, see [Work with warehouse management only mode in Supply Chain Management](wms-only-mode-shared-and-external-detail-use.md).

> [!IMPORTANT]
> For the preceding flow, the [**Allow load split during ship confirm**](confirm-and-transfer.md) option for outbound loads isn't supported in the *WOM* legal entity. Likewise, planned cross-docking information isn't automatically transferred from the sales subsidiary legal entities to the *Warehouse management only mode* process.

> [!NOTE]
> When you release orders or loads to the warehouse in the *LE1* legal entity, the shipments that are created are locked with **Outbound shipment processing ownership** set to *External* until order data from the *WOM* legal entity is returned. If order data isn't returned, or if other issues occur, you can get update rights for the shipments by selecting the **Claim processing ownership** action on the shipments. Only admin roles should be granted permission to use this action.

## On-hand adjustments

The following illustration shows how on-hand inventory adjustments are handled when Warehouse management only mode is run. 

:::image type="content" source="media/wms-only-shared-warehouse-inventory-process.svg" alt-text="Diagram of the inventory process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-inventory-process.svg":::

Changes in on-hand inventory that are the result of inbound and outbound shipment orders are handled when *Receive external warehouse inbound shipment order update* and *Receive external warehouse outbound shipment order update* operations are processed by the [message processor](../supply-chain-dev/message-processor.md) in the *LE1* legal entity. However, other warehouse movements, such as warehouse counting operations, must also ensure that on-hand inventory is the same between the *WOM* legal entity and any related order processing legal entities, such as *LE1*. Therefore, Warehouse management only mode can record the changes in warehouse inventory in the warehouse inventory update log (**Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Warehouse inventory update log**). This data is used to automatically create external inventory adjustments for the relevant legal entities via the *Publish warehouse inventory update log updates* [process automation background process](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md). (By default, this background process runs every 10 minutes.)

You can use the *Create external inventory adjustment journals* process (**Warehouse management** \> **Periodic tasks** \> **Create external inventory adjustment journals**) to generate the inventory adjustment journals that are used to update the on-hand inventory. In this way, you can keep inventory information synced between the two legal entities.

To automatically post the inventory adjustment journals, go to **Warehouse management** \> **Periodic tasks** \> **Post external inventory adjustment journals**. This process posts the journals that the *Create external inventory adjustment journals* process creates.

### <a name="warehouse-inventory-update-logs"></a>Warehouse inventory update logs

The Warehouse inventory update log (**Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Warehouse inventory update log**) collects all the inventory transaction updates that lead to on-hand updates that are of interest for the related legal entities. For example, you might want to handle information about inventory status changes.

> [!TIP]
>For example, if you want to adjust the inventory in the warehouse only mode legal entity without affecting the order legal entity or causing duplicate adjustments through the warehouse inventory log update process, you can use an Inventory journal name with the *Exclude from warehouse inventory update logs* setting turned on. This will prevent the journal posting from being logged.

> [!IMPORTANT]
> For [source systems](wms-only-mode-setup.md#source-systems) that are related to external warehouse management systems, keep the **Enable warehouse inventory update logs** option turned off for inbound and outbound shipment orders. In this way, you prevent inventory adjustment journal processing from updating your on-hand inventory in the sales subsidiary legal entities.

## Example setup that uses external shared warehouse processing in Supply Chain Management

This section provides an example that shows how to set up and use Warehouse management only mode with external shared warehouse processing in Supply Chain Management.

### Legal entities and source systems

To use Warehouse management only mode as described in this article, you must have at least two legal entities. For this example, the two legal entities are named as *LE1* and *WOM*.

In the *WOM* legal entity, you must create a [source system](wms-only-mode-setup.md#source-systems) to handle shipment orders and the inventory on-hand update processes. For this example, this source system is named *SS-LE1*.

In the *LE1* legal entity, you must set up an external warehouse management system of the *Legal entity* type and link it to the *SS-LE1* [source system](wms-only-mode-setup.md#source-systems) in the *WOM* legal entity. You can complete this setup by going to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **External warehouse management systems**.

In the *LE1* legal entity, you can now go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Warehouses** and select the warehouses that you want to handle externally. Specify the external warehouse management system and the external warehouse name from the *WOM* legal entity. You should select a default location that doesn't use license plates. This location will be used for all inventory changes from the external warehouses in the *LE1* legal entity.

> [!NOTE]
> The **Use warehouse management processes** option must be turned on for the warehouses in both legal entities.

### Product master and reference data

Warehouse management must be fully set up in all legal entities that run warehouse management processes (such as *WOM*). This setup includes product master data. The same products and product variants can be used for the released products in all legal entities. In this case, you must use a separate source system as the source for managing product master data. If you share products among multiple sales subsidiaries or legal entities, you must create the necessary [source system item](wms-only-mode-exchange-data.md#master-data) data. For example, you might create a source system that's named *PIM-D365* and assign it as the *product master source system* for the *SS-LE1* source system.

You must also ensure that the products have a tracking dimension group where the *Owner* dimension is enabled. In this way, the ownership of the inventory can be tracked for each of the related legal entities. For this example setup, you don't have to enable the *Owner* tracking dimension for the released product in the *LE1* legal entity. However, if you enable it, the legal entity owner dimension value is automatically assigned to the purchase and sales order lines, and you can't change it.

You can find more details about the product master data in [Master and reference data](wms-only-mode-exchange-data.md#master-data). However, be sure to use the *Non-valuated* inventory model for the products in the *WOM* legal entity. In addition, be sure to enable the *Owner* inventory tracking dimension.

> [!NOTE]
> The products must be linked to a storage dimension group where the **Use warehouse management processes** option is turned on.

To use the *Owner* dimension, you must create a record on the **Warehouse inventory owner** page (**Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Warehouse inventory owner**). You can then assign that record as the default inventory owner for a [source system](wms-only-mode-setup.md#source-systems).

If you use this example setup in an environment where you already have some released products, ensure that you create the data for the released products and variants on the [**Source system items**](wms-only-mode-exchange-data.md#master-data) page.

> [!TIP]
> Set the **Product maintenance rule** value to *Maintain source system items* on the *PIM-D365* source system in the *WOM* legal entity. In this way, the source system item data is automatically created for you when you release products to the *WOM* legal entity.
