---
title: Work with Warehouse management only mode in Supply Chain Management (preview)
description: This article explains how to use Warehouse only mode to perform day-to-day warehousing tasks.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage
ms.topic: how-to
ms.date: 08/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Work with Warehouse management only mode in Supply Chain Management (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

## Monitor the integration

To monitor the integration between the external systems and Microsoft Dynamics 365 Supply Chain Management, go to **Warehouse management** \> **Workspaces** \> **Warehouse integration monitoring**. From the **Warehouse integration monitoring** page, you can perform the following tasks:

- Get an overview of integration messages.
- Go to pages that have related information and functionality, such as the [**Message processor messages**](warehouse-message-processor-messages.md) page.

## <a name="inbound-shipment-orders"></a>Maintain inbound shipment orders

To review and maintain your inbound shipment orders, go to **Warehouse management** \> **Inbound shipment orders** \> **Inbound shipment orders**. The documents that are listed on the **Inbound shipment orders** page provide information about the expected product receipts. The page provides a **Header** view and a **Lines** view of the available shipment orders as seen from Supply Chain Management. For each line, you can view detailed information about the receiving status, inventory transactions, and associated warehouse work. You can also view and the receiving status on the order header and lines and use it to follow the inbound progress of the orders.

The following **Receiving status** values are available:

- *Open* – No quantities have been fully received.
- *Partially received* – Some, but not all, quantities have been fully received.
- *Received* – All quantities have been fully received.

If you're already familiar with Supply Chain Management, you might recognize that this document resembles a simplified purchase order. However, inbound shipment orders don't make any financial postings for the [general ledger](../../finance/general-ledger/general-ledger.md).

> [!WARNING]
> For inbound shipment order lines, you can select **Update line** \> **Delivery remainder** to update expected order line transaction quantities. Make sure that you have the correct user role security privilege for this process, because this update (like message editing) allows for potential inconsistencies between the external systems and Supply Chain Management.

> [!NOTE]
> The internal inbound shipment order number must be unique. You can configure the system to use the external order numbers as internal numbers. In this way, you don't have to use a [number sequence](wms-only-mode-setup.md#number-sequences) for the order. To ensure unique numbers across external systems, consider using the **Order number prefix/suffix** options.

### Enable manual inbound shipment order creation

Besides using entity messages to create the *Inbound shipment orders* you can *Enable manual inbound shipment order creation* for one or more *Source systems* and thereby users are able to create inbound shipment orders directly in the *Inbound shipment orders* page.
This setting will enable the user interface option for the **New** button and the `Order type` field will contain the value *Manual order* instead of *Inbound shipment order* for shipment orders getting created without message processing.

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

Besides using entity messages to create the *Outbound shipment orders* you can *Enable manual outbound shipment order creation* for one or more *Source systems* and thereby users are able to create outbound shipment orders directly in the *Outbound shipment orders* page.
This setting will enable the user interface option for the **New** button and the `Order type` field will contain the value *Manual order* instead of *Outbound shipment order* for shipment orders getting created without message processing.

## Inbound process

The following illustration highlights the elements of the inbound process.

:::image type="content" source="media/wms-only-inbound-wom-process.svg" alt-text="Inbound process for Warehouse management only mode." lightbox="media/wms-only-inbound-wom-process.svg":::

Here's a high-level description of the inbound process:

1. An external system submits an *inbound shipment order* message to Supply Chain Management.
1. Supply Chain Management processes the message in Warehouse management only mode and creates orders.
1. Inbound loads are created in one of four ways, as established by the [Source systems](wms-only-mode-setup.md#source-systems) settings in Supply Chain Management:

    - Manually, by using the [Inbound load planning workbench](create-or-modify-an-inbound-load.md#create-an-inbound-load-manually)
    - By importing [advanced shipping notices (ASNs)](import-asn-data-entity.md)
    - Automatically during [message processing](../supply-chain-dev/message-processor.md)
    - Automatically during the Warehouse Management mobile app receiving process

1. A warehouse worker using the Warehouse Management mobile app to *register* the inbound shipment transactions.
1. Supply Chain Management runs [receiving completed](wms-only-mode-using.md#receiving-completed) processes that are related to each relevant load. These processes update the load status to *Received*, generate [shipment receipts](wms-only-mode-using.md#shipment-receipts), and trigger *business events* for the external systems.
1. The external systems read and use the [shipment receipt](wms-only-mode-using.md#shipment-receipts) data for further processing. For example, if purchase orders are associated with the inbound shipment orders in the external system, this processing involves purchase order invoicing.
1. Supply Chain Management finalizes the inbound shipment orders by running the *Post shipment receipts* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

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
> - As part of an *Order receiving completed* process which creates loads for registered inventory transaction not being associated to a load. This process is useful when using the [Item arrival journal](../inventory/arrival-overview.md) process. This process can get triggered directly from an *Inbound shipment order* or via a background process **Inbound shipment order receiving completed**.
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

External systems can be informed via [business events](wms-only-mode-exchange-data.md#progress-data-and-business-events) when new data is available. They can read the data via the following data entities:

- `ShipmentReceiptJournalHeaders` – The shipment receipt header data.
- `ShipmentReceiptJournalLines` – The shipment receipt line data.
- `ShipmentReceiptTransactionDimensions` – The detailed shipment receipt line data.

## Outbound process

The following illustration highlights the elements of the outbound process.

:::image type="content" source="media/wms-only-outbound-wom-process.svg" alt-text="Outbound process for Warehouse management only mode." lightbox="media/wms-only-outbound-wom-process.svg":::

Here's a high-level description of the outbound process:

1. An external system submits an *outbound shipment order* message.
1. Supply Chain Management processes the message in Warehouse management only mode and creates orders.
1. Inventory reservations are created in one of two ways, as established by the [Source systems](wms-only-mode-setup.md#source-systems) settings in Supply Chain Management:

    - Automatically by the [message processor](../supply-chain-dev/message-processor.md)
    - Manually, as part of the release process

1. The orders are released for further warehouse processing, either manually or automatically (by running the *Automatic release of outbound shipment orders* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md)).
1. Depending on the setup of your [wave template](wave-templates.md) definitions, warehouse work might be created and released immediately.
1. The outbound warehouse work is processed, and the status of the related outbound shipment order line transactions is updated to *Picked*.
1. The loads are outbound ship confirmed. As a result, *business events* and a [*shipment packing slip*](wms-only-mode-using.md#shipment-packing-slips) are created for the external system.
1. The external system reads the shipment packing slip and uses its data for further processing (such as for sales order invoicing for sales orders that are associated with outbound shipment orders).
1. Supply Chain Management finalizes the outbound shipment order by running the *Post shipment packing slips* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

> [!NOTE]
> You can reverse the shipment confirmation only if the related outbound shipment order line transactions haven't yet been finalized.

## <a name="shipment-packing-slips"></a>Shipment packing slips

To view detailed line transactions that are related to shipped inventory, and to print a report, go to **Warehouse management** \> **Outbound shipment orders** \> **Shipment packing slips**, and select **Preview/Print**. To control the printed inventory dimension values, go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**, and then, on the **Reports** tab, select an option for **Shipment packing slip**.

Shipment packing slip data is version controlled, and you can follow the posting status on the header. The **Posting status** value is changed from *Ready for posting* to *Posted* as part of the *Post shipment packing slips* [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) job. This job is automatically initialized as part of the [Source systems](wms-only-mode-setup.md#source-systems) setup. The Source systems setup also lets you schedule the batch job to ensure that related outbound shipment order line transactions are moved to a finalized transaction state for the **Warehouse management** module.

To view all the background processes that you have running, go to [**System administration** \> **Setup** \> **Process automations**](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

> [!NOTE]
> If no language is defined for an order, the report uses the company-specific language settings.

External systems can be informed via [business events](wms-only-mode-exchange-data.md#progress-data-and-business-events) when new data is available. They can read the data via the following data entities:

- `ShipmentPackingSlipJournalHeaders` – The shipment packing slip header data.
- `ShipmentPackingSlipJournalLines` – The shipment packing slip line data.
- `ShipmentPackingSlipTransactionDimensions` – The detailed shipment packing slip line data.

## <a name="maintain-messages"></a>View and maintain shipment order messages

In Warehouse management only mode, you can both view, update, and create shipment order messages. Therefore, you can quickly test integrations during the implementation process. When a external created message is in a *Failed* message state, you can update all field values except the order header and line numbers. Go to one of the following pages to view and maintain the messages:

- **Warehouse management** \> **Inbound shipment orders** \> **Inbound shipment order messages**
- **Warehouse management** \> **Outbound shipment orders** \> **Outbound shipment order messages**

To easily tryout the creation process of inbound and outbound shipment orders via messages, you can set *Enable manual outbound shipment order message creation* and *Enable manual inbound shipment order message creation* to `Yes` for a *Source system* record. This will make it possible to create the shipment order messages directly within the **Outbound shipment order messages** and **Inbound shipment order messages** pages. You will be able to follow the *Message origin* which can be *Manual entry* or *Integration*.

Use the **Processing status** field to monitor the progress of each shipment order message. The following **Processing status** values are available:

- *Receiving* – The message is in the process of being imported.
- *Received* – The message has been received and is in a *Queued* state in the [message processor](../supply-chain-dev/message-processor.md). It's now ready to be picked up for processing.
- *Accepted* – The message processor state is *Processed*. Therefore, a shipment order has been created.
- *Failed* – The [message processor](../supply-chain-dev/message-processor.md) processed the message, but one or more errors occurred. You can create a copy of the message when you save it after you edit it.
- *Draft* – The message is a copy or manually created message that can be updated. To reprocess the message, move it into the *Queued* message state by selecting the **Queue** option.
- *Canceled* – The message has been manually canceled.

> [!TIP]
> Select **Show old versions** to follow manual message updates based on the value of the **Replaced by message** field.

> [!WARNING]
> Manual message creation and field updates in production environments can cause data inconsistency between the external source system and Supply Chain Management. For example, you might change an item number to a value that isn't known to the external system. This type of update will probably cause issues in progress information flows. The issues might even be impossible to correct in the external system. We recommend that you use user roles and security privileges to restrict access to this functionality to as few people as possible.
