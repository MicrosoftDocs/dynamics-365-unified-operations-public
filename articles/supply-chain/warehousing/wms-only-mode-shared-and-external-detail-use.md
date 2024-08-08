---
title: Work with Warehouse management only mode in Supply Chain Management
description: Learn how to use Warehouse only mode to perform day-to-day warehousing tasks, including an outline on monitoring integrations.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 04/27/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSEWManagementSystem,  WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage, WHSEWInboundShipmentOrderRequest, WHSEWOutboundShipmentOrderRequest, WHSEWOutboundShipmentOrderUpdate, WHSInventoryOwner
---

# Work with Warehouse management only mode in Supply Chain Management

[!include [banner](../includes/banner.md)]

This article explains how to use Warehouse only mode to perform day-to-day warehousing tasks.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Monitor the integration

To monitor the integration between the external systems or legal entities with Microsoft Dynamics 365 Supply Chain Management, go to **Warehouse management** \> **Workspaces** \> **Warehouse integration monitoring**. From the **Warehouse integration monitoring** page, you can perform the following tasks:

- Get an overview of integration messages.
- Go to pages that have related information and functionality, such as the [**Message processor messages**](warehouse-message-processor-messages.md) page.

## <a name="inbound-shipment-orders"></a>Maintain inbound shipment orders

To review and maintain your inbound shipment orders, go to **Warehouse management** \> **Inbound shipment orders** \> **Inbound shipment orders**. The documents that are listed on the **Inbound shipment orders** page provide information about the expected product receipts. The page provides a **Header** view and a **Lines** view of the available shipment orders as seen from Supply Chain Management. For each line, you can view detailed information about the receiving status, inventory transactions, and associated warehouse work. You can also view the receiving status on the order header and lines, and use it to follow the inbound progress of the orders.

The following **Receiving status** values are available:

- *Open* – No quantities have been fully received.
- *Partially received* – Some, but not all, quantities have been fully received.
- *Received* – All quantities have been fully received.

If you're already familiar with Supply Chain Management, you might recognize that this document resembles a simplified purchase order. However, inbound shipment orders don't make any financial postings for the [general ledger](../../finance/general-ledger/general-ledger.md).

> [!WARNING]
> For inbound shipment order lines, you can select **Update line** \> **Delivery remainder** to update expected order line transaction quantities. Make sure that you have the correct user role security privilege for this process, because this update (like message editing) allows for potential inconsistencies between the external systems and Supply Chain Management.

> [!NOTE]
> The internal inbound shipment order number must be unique. You can configure the system to use the external order numbers as internal numbers. In this way, you don't have to use a [number sequence](wms-only-mode-setup.md#number-sequences) for the order. To ensure unique numbers across external systems, consider using the **Order number prefix/suffix** options.

## Enable manual inbound shipment order creation

In addition to using entity messages to create inbound shipment orders, you can enable manual inbound shipment order creation for one or more source systems. Users can then create inbound shipment orders directly on the **Inbound shipment orders** page. To enable manual inbound shipment order creation, go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**, and set the **Enable manual inbound shipment order creation** option to *Yes* for the relevant source system. This setting activates the **New** button on the **Inbound shipment orders** page.  For shipment orders that are created without message processing, the **Order type** field has the value *Manual order* instead of *Inbound shipment order*.

## Maintain outbound shipment orders

To review and maintain documents that contain information about products that have been requested for dispatch, go to **Warehouse management** \> **Outbound shipment orders** \> **Outbound shipment orders**. The **Outbound shipment orders** page provides a **Header** view and a **Lines** view of the available shipment orders as seen from Supply Chain Management. For each line, you can view detailed information about the release status, shipment status, inventory transactions, and associated warehouse work. You can also view and edit the release status and shipment status on the order header, and use them to follow the outbound progress of the orders.

The following **Release status** values are available:

- *Open* – No quantities have been [released to the warehouse](release-to-warehouse-process.md).
- *Partially released* – Some, but not all, quantities have been [released to the warehouse](release-to-warehouse-process.md).
- *Released* – All quantities have been [released to the warehouse](release-to-warehouse-process.md).

The following **Shipment status** values are available:

- *Open* – No quantities have been shipped confirmed.
- *Partially shipped* – Some, but not all, quantities have been shipped confirmed.
- *Shipped* – All quantities have been shipped confirmed.

If you're already familiar with Supply Chain Management, you might recognize that this document resembles a simplified sales order that uses some of the same reservation and [release to warehouse](release-to-warehouse-process.md) processes. Use the [Source systems](wms-only-mode-setup.md#source-systems) settings to control whether you want to automatically trigger reservations when documents are imported, and/or automatically reject shipment orders that can't be partly or fully reserved.

> [!WARNING]
> For outbound shipment order lines, you can select **Update line** \> **Delivery remainder** to update expected order line transaction quantities. Make sure that you have the correct user role security privilege for this process, because this update (like message editing) allows for potential inconsistencies between the external systems and Supply Chain Management.

> [!NOTE]
> The internal outbound shipment order number must be unique. You can configure the system to use the external order numbers as internal numbers. In this way, you don't have to use a [number sequence](wms-only-mode-setup.md#number-sequences) for the order. To ensure unique numbers across external systems, consider using the **Order number prefix/suffix** options.

### Enable manual outbound shipment order creation

In addition to using entity messages to create outbound shipment orders, you can enable manual outbound shipment order creation for one or more source systems. Users can then create inbound shipment orders directly on the **Outbound shipment orders** page. To enable manual outbound shipment order creation, go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**, and set the **Enable manual outbound shipment order creation** option to *Yes* for the relevant source system. This setting activates the **New** button on the **Inbound shipment orders** page. For shipment orders that are created without message processing, the **External order type** field has the value *Manual order* instead of *Outbound shipment order*.

## <a name="receiving-completed"></a>Receiving completed process

The *receiving completed* process updates the load status to *Received* and generates [shipment receipts](#shipment-receipts). The shipment receipts then trigger a business event for the external systems.

Workers can manually trigger the *receiving completed* process from the load by using either the web client or the Warehouse Management mobile app. To enable workers to use the Warehouse Management mobile app, set up a **Receiving completed confirmation** mobile device menu item. You can add this menu item as part of a [detour](warehouse-app-detours.md) in the inbound receiving flows.

You can specify whether workers should capture a packing slip ID and date for each shipment that's associated with an inbound load. On the **Warehouse management parameters** page, on the **Loads** tab, in the **Capture receiving completed packing slip** field, select one of the following values to specify the system behavior:

- *Never* – Don't prompt for the packing slip ID and date.
- *Always* – Prompt for the packing slip ID and date, and allow the worker to proceed only after values they're specified.
- *Optional* – Prompt for the packing slip ID and date, but allow the worker to proceed without specifying them.

> [!NOTE]
> Depending on your setup on the **Inbound shipment order policies** FastTab of the **Source systems** page (**Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**), inbound loads might be created in any of the following ways:
>
> - Automatically, when an inbound shipment order is imported
> - Automatically, when an ASN is imported
> - Via a manual process
> - As part of the Warehouse Management mobile app receiving process
> - As part of an *Order receiving completed* process, which creates loads for registered inventory transactions that aren't associated with a load. This process is useful when the [item arrival journal](../inventory/arrival-overview.md) process is used. It can be triggered directly from an inbound shipment order or via the **Inbound shipment order receiving completed** background process.
>
> When the system creates load data as a result of processing an inbound shipment order message, the delivery policy controls whether load quantities are adjusted to the received quantities, or whether the received quantities must match the load line quantities, as part of the [*Receiving completed* process](inbound-load-handling.md#receive-complete-confirm).

## <a name="shipment-receipts"></a>Shipment receipts

Go to **Warehouse management** \> **Inbound shipment orders** \> **Shipment receipts** to view the detailed line transactions that are related to received inventory. The data is version controlled, and you can follow the posting status on the header.

The header status is changed from *Ready for posting* to *Posted* as part of the *Post shipment receipts* [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) job. This job is automatically initialized as part of the [Source systems](wms-only-mode-setup.md#source-systems) setup. The Source systems setup also lets you schedule the batch job to ensure that the related inbound shipment order line transactions are moved to a finalized transaction state for the **Warehouse management** module.

To view all the background processes that you have running, go to [**System administration** \> **Setup** \> **Process automations**](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

> [!NOTE]
> You can reverse receiving confirmations only if the related inbound shipment order line transactions haven't yet been finalized.

> [!WARNING]
> If you enable Warehouse management only mode and are already running a periodic *Update product receipts* batch job for loads that are associated with purchase orders, you probably have to update the query for the batch job to exclude inventory transaction updates for inbound shipment orders. To update the query, add the *Load details* entity, and specify a *NotExist* join to the *Loads* entity. Then add a range definition for the **Reference** field, where **Criteria** = *Inbound shipment order*.

External systems can be informed via [business events](wms-only-mode-exchange-data.md#business-events) when new data is available. They can read the data via the following data entities:

- `ShipmentReceiptJournalHeaders` – The shipment receipt header data.
- `ShipmentReceiptJournalLines` – The shipment receipt line data.
- `ShipmentReceiptTransactionDimensions` – The detailed shipment receipt line data.

## <a name="shipment-packing-slips"></a>Shipment packing slips

To view detailed line transactions that are related to shipped inventory, and to print a report, go to **Warehouse management** \> **Outbound shipment orders** \> **Shipment packing slips**, and select **Preview/Print**. To control the printed inventory dimension values, go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**, and then, on the **Reports** tab, select an option for **Shipment packing slip**.

Shipment packing slip data is version controlled, and you can follow the posting status on the header. The **Posting status** value is changed from *Ready for posting* to *Posted* as part of the *Post shipment packing slips* [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) job. This job is automatically initialized as part of the [Source systems](wms-only-mode-setup.md#source-systems) setup. The Source systems setup also lets you schedule the batch job to ensure that related outbound shipment order line transactions are moved to a finalized transaction state for the **Warehouse management** module.

To view all the background processes that you have running, go to [**System administration** \> **Setup** \> **Process automations**](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

> [!NOTE]
> If no language is defined for an order, the report uses the company-specific language settings.

External systems can be informed via [business events](wms-only-mode-exchange-data.md#business-events) when new data is available. They can read the data via the following data entities:

- `ShipmentPackingSlipJournalHeaders` – The shipment packing slip header data.
- `ShipmentPackingSlipJournalLines` – The shipment packing slip line data.
- `ShipmentPackingSlipTransactionDimensions` – The detailed shipment packing slip line data.

> [!NOTE]
> You can reverse the shipment confirmation only if the related outbound shipment order line transactions haven't yet been finalized.

## <a name="maintain-messages"></a>View and maintain shipment order messages

In Warehouse management only mode, you can view, update, and create shipment order messages. Therefore, you can quickly test integrations during the implementation process. When an externally created message is in a *Failed* message state, you can update all field values except the order header and line numbers. Go to one of the following pages to view and maintain the messages:

- **Warehouse management** \> **Inbound shipment orders** \> **Inbound shipment order messages**
- **Warehouse management** \> **Outbound shipment orders** \> **Outbound shipment order messages**

To try out the process of creating inbound and outbound shipment orders via messages, set the **Enable manual outbound shipment order message creation** and **Enable manual inbound shipment order message creation** options to *Yes* for the relevant **Source system** record. You can then create shipment order messages directly on the **Outbound shipment order messages** and **Inbound shipment order messages** pages. In addition, you can follow the **Message origin** value, which can be *Manual entry* or *Integration*.

Use the **Processing status** field to monitor the progress of each shipment order message. The following **Processing status** values are available:

- *Receiving* – The message is in the process of being imported.
- *Received* – The message has been received and is in a *Queued* state in the [message processor](../supply-chain-dev/message-processor.md). It's now ready to be picked up for processing.
- *Accepted* – The message processor state is *Processed*. Therefore, a shipment order has been created.
- *Failed* – The [message processor](../supply-chain-dev/message-processor.md) processed the message, but one or more errors occurred. You can create a copy of the message when you save it after you edit it.
- *Draft* – The message is a manually copied or created message that can be updated. To reprocess the message, move it into the *Queued* message state by selecting **Queue** on the Action Pane.
- *Canceled* – The message has been manually canceled.

> [!TIP]
> Select **Show old versions** to follow manual message updates based on the value of the **Replaced by message** field.

> [!WARNING]
> In a production environment, manually entered messages and field updates can cause data inconsistencies between the external source system and Supply Chain Management. For example, you might change an item number to a value that isn't known to the external system. This type of update will probably cause issues in progress information flows. The issues might even be impossible to correct in the external system. We recommend that you use user roles and security privileges to restrict access to this functionality to as few people as possible.
