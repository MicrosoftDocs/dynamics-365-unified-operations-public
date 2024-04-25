---
title: Warehouse management only mode with external shared warehouses (preview)
description: This article provides information about running Warehouse management only mode with external shared warehouse processing, which enables the integration of the warehouse management (WMS) functionality in separate legal entity handling requests from multiple sales subsidiaries/LEs in Microsoft Dynamics 365 Supply Chain Management.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSEWManagementSystem,  WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage, WHSEWInboundShipmentOrderRequest, WHSEWOutboundShipmentOrderRequest, WHSEWOutboundShipmentOrderUpdate, WHSInventoryOwner, WHSInventoryUpdateLog, WHSExternalInventoryAdjustment
ms.topic: overview
ms.date: 04/27/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse management only mode with external shared warehouses (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

You can use [Warehouse management only mode](wms-only-mode-overview.md) to handle logistic operations in a legal entity dedicated to warehousing operations and connect warehouses between this legal entity and the other legal entities that do all the order and financial processing. In addition, warehouse management processes can track which legal entity owns the inventory for items that are shared across different entities using an owner inventory dimension.

This feature works well in a single-instance deployment model when you want to link multiple tenants and one of them will handle the logistic warehouse processes. You need an integration process like the one described in the [Warehouse management only mode with external ERP system](wms-only-mode-external-erp.md).

[!INCLUDE [preview-note](../includes/preview-note.md)]

## High-level implementation example

The following illustration shows an example system where Warehouse management only mode is active with an external shared warehouse in the legal entity *WOM*, which deals with logistics warehouse operations for two sales subsidiaries that manage order and financial processing in the legal entities *LE1* and *LE2*.

:::image type="content" source="media/wms-only-d365-shared-warehouse-integration.svg" alt-text="Warehouse management only mode with external shared warehouse." lightbox="media/wms-only-d365-shared-warehouse-integration.svg":::

## Inbound process example (shared warehouse)

The following illustration highlights the elements of the inbound process when you are using a shared warehouse.

:::image type="content" source="media/wms-only-shared-warehouse-inbound-process.svg" alt-text="Inbound process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-inbound-process.svg":::

Here's a high-level description of the inbound process. Steps starting with *LE1* are done by a sales subsidiary. Steps starting with *WOM* are done by the warehousing entity.

1. *LE1*: Purchase orders are created and released to the warehouse. The system then creates *external warehouse inbound shipment order requests* that result in inbound shipment order messages being delivered to the *WOM* legal entity. Purchase orders released to the externally managed warehouse can be processed via a periodic background process (set up at **Warehouse management \> Periodic tasks \> Create external warehouse inbound shipment order requests**) or manually by selecting the **Release to warehouse** option on the purchase orders page.
1. *WOM*: Processes the inbound shipment order messages, resulting in the creation of inbound shipment orders.
1. *WOM*: Inbound loads are created manually, automatically, or through import (depending on your configuration).
1. *WOM*: Warehouse workers uses the Warehouse Management mobile app to register the inbound shipment order transactions.
1. *WOM*: Processes [receiving completed](wms-only-mode-shared-and-external-detail-use.md#receiving-completed) operations for the related loads. These operations update the load status to *Received* and generate *external warehouse inbound shipment order updates* for *LE1*. You can enable automatic [message processing](../supply-chain-dev/message-processor.md) for the *External warehouse shipment order updates* message queue.
1. *LE1*: During the processing of the external warehouse inbound shipment order updates, inbound loads and shipments are created and the related purchase order line transactions are updated to *Registered*, which enables further processing of product receipts and invoices.
1. *WOM*: The inbound shipment order line transactions are finalized by running the *Post shipment receipts* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

For a more detailed description of this process and the related processes, see [Work with warehouse management only mode in Supply Chain Management](wms-only-mode-shared-and-external-detail-use.md).

## Outbound example process (shared warehouse)

The following illustration highlights the elements of the outbound process.

:::image type="content" source="media/wms-only-shared-warehouse-outbound-process.svg" alt-text="Outbound process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-outbound-process.svg":::

Here's a high-level description of the inbound process. Steps starting with *LE1* are done by a sales subsidiary. Steps starting with *WOM* are done by the warehousing entity.

1. *LE1*: Sales orders are created and released to the warehouse. The system then creates *external warehouse outbound shipment order requests* that result in outbound shipment order messages being delivered to the *WOM* legal entity.
1. *WOM*: The *Outbound shipment order messages* are processed, resulting in the creation of *Outbound shipment orders*.
1. *WOM*: Inventory reservations are created either manually or automatically (depending on your configuration).
1. *WOM*: The orders are released for further warehouse processing, either manually or automatically. If you're using outbound load planning processes, you can create loads by using the outbound load planning workbench before you release the orders.
1. *WOM*: Depending on the setup of your [wave template](wave-templates.md) definitions, warehouse work might be created and released immediately.
1. *WOM*: Outbound warehouse work is processed, and the status of the related outbound shipment order line transactions is updated to *Picked*.
1. *WOM*: The loads are outbound ship confirmed. As a result, external warehouse inbound shipment order updates are generated for *LE1*.
1. *LE1*: During the processing of the external warehouse inbound shipment order updates,  outbound shipment data and the related sales order line transactions are updated. The transactions become *Picked*, thereby enabling the further processing of the packing slip and invoice. You can enable automatic [message processing](../supply-chain-dev/message-processor.md) for the *External warehouse shipment order updates* message queue.
1. *WOM*: Outbound shipment order line transactions are finalized by running the *Post shipment packing slips* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md). 

For a more detailed description of this process and the related processes, see [Work with warehouse management only mode in Supply Chain Management](wms-only-mode-shared-and-external-detail-use.md).

> [!WARNING]
> [*Allow load split during ship confirm*](confirm-and-transfer.md) for outbound loads isn't supported for previous flow in the *WOM* legal entity.

> [!NOTE]
> When you release orders or loads to warehouse in the *LE1* legal entity, the shipments that are created are locked with **Outbound shipment processing ownership** set to *External* until order data from the *WOM* legal entity is returned. If this doesn't happen, or if there are other problems, you can get update rights for the shipments by choosing **Claim processing ownership** on the shipments. Only admin roles should be granted permission to use this action.

## On-hand adjustments

<!-- KFM: Continue here -->

Changes in on-hand inventory resulting from inbound and outbound shipment orders are handled when *Receive external warehouse inbound shipment order update* and *Receive external warehouse outbound shipment order update* operations are processed by the [message processor](../supply-chain-dev/message-processor.md) in the *LE1* legal entity. However, other warehouse movements, such as warehouse counting operations, also need to ensure that on-hand inventory is the same between the *WOM* legal entity and any related order processing legal entities such as *LE1*. For this, the *Warehouse management only mode* records all the changes in the warehouse inventory in the **Warehouse management \> Inquiries and reports \> Physical inventory reconciliation \> Warehouse inventory update log** and this data will be used to automatically create the **External inventory adjustments** for the relevant legal entities via the *Publish warehouse inventory update log updates* [process automation background process](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) (running every 10 minutes by default).

You can use the **Warehouse management \> Periodic tasks \> Create external inventory adjustment journals** process to generate the real *Inventory adjustment journals* that will be used to update the on-hand inventory and thus keeping it synchronized between the two legal entities.

To automatically post the created *Inventory adjustment journals* use the **Warehouse management \> Periodic tasks \> Post external inventory adjustment journals**

:::image type="content" source="media/wms-only-shared-warehouse-inventory-process.svg" alt-text="Internal process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-inventory-process.svg":::

### <a name="warehouse-inventory-update-logs"></a>Warehouse inventory update logs

The Warehouse inventory update log (at **Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Warehouse inventory update log**) collects all the inventory transaction updates that lead to on-hand updates that are of interest for the related legal entities. For example, you might want to handle the information about inventory status changes.

> [!WARNING]
> If the *Source systems* are related to *External warehouse management systems*, turn off the *Enable warehouse inventory update logs* for the *Inbound and Outbound shipment orders*. This will prevent your inventory on-hand from being updated by inventory adjustment journal processing.

## Setup example using external shared warehouse processing in Supply Chain Management

To use the Warehouse management only mode in the way shown above, you need to have at least two legal entities, *LE1* and *WOM*.
In the *WOM* legal entity you create a [*Source system*](wms-only-mode-setup.md#source-systems) - let's call this *SS-LE1* to handle the shipment orders and inventory on-hand update processes.

In legal entity *LE1* you need to set up an *External warehouse management system* with the type `Legal entity` and link it to the [*Source system*](wms-only-mode-setup.md#source-systems) *SS-LE1* in the *WOM* legal entity. You do this setup in the **Warehouse management \> Setup \> Warehouse management integration \> External warehouse management systems** page.

You can now go to the *LE1* **Warehouse management \> Setup \> Warehouse \> Warehouses** page and choose the warehouses that you want to handle externally and specify the *External warehouse management system* and the *External warehouse* name from *WOM*. You should select a *Default location* that does not use license plates. This location will be used for all the inventory changes from the external warehouses in the *LE1* legal entity.
> [!NOTE]
> The warehouses in both legal entities must have *Use warehouse management processes* enabled.

### Product master and reference data

You need to have all the required warehouse management setup in the *WOM* legal entity defined for any warehouse management process, including the product master data. Note that the same *Product*/*Product variant* can be used for the *Released products* in all legal entities, in this case you must use a separate *Source system* as the source for managing the product master data, including creating the necessary [*Source system items*](wms-only-mode-exchange-data.md#master-data) data if you share products between multiple sales subsidiaries/legal entities. In this example, we will create a new *Source system* called *PIM-D365* and make sure to assign this *Source system* as the *Product master source system* for the *SS-LE1* source system. You also need to make sure that the products have a *Tracking dimension group* with the *Owner* dimension enabled. This makes it possible to track the ownership of the inventory for each of the related legal entities.
You don't have to turn on the *Owner* tracking dimension for the *Released product* in the *LE1* company for this example setup, but if you do this the legal entity owner dimension value will be automatically assigned to the purchase and sales order lines, and you won't be able to change it.

You can find more details about the product master data [here](wms-only-mode-exchange-data.md#master-data), but a key point to keep in mind is to use the *Non-valuated* inventory model for the products in the *WOM* legal entity and to enable the *Owner* inventory tracking dimension.
> [!NOTE]
> The products need to be linked to a *Storage dimension group* that has the **Use warehouse management processes** option turned on.

To use the *Owner* dimension you must create a record in **Warehouse management \> Setup \> Warehouse management integration \> Warehouse inventory owner** which you as well can assign as the *Default inventory owner* for a [*Source system*](wms-only-mode-setup.md#source-systems).

If you use this setup example in an environment where you already have some released products, please ensure that you create the data for the *Released products and variants* in the [*Source system items*](wms-only-mode-exchange-data.md#master-data) page.

> [!TIP]
> When you *Release* products to the *WOM* legal entity, the *Source system item* data will be created for you automatically if you set the **Product maintenance rule** to *Maintain source system items* on the *PIM-D365* source system in *WOM*.
