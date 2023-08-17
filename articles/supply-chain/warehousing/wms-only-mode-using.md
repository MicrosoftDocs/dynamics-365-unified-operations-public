---
title: Work with warehouse management only mode in Supply Chain Management
description: XXXX
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

# Work with warehouse management only mode in Supply Chain Management

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

## Monitor the integration

To monitor the integration between the external systems and Supply Chain Management, go to **Warehouse management > Workspaces > Warehouse integration monitoring** page. From here, you can do the following:

- Get an overview of integration messages
- Navigate to pages with related information and functionality, such as the [Message processor messages](warehouse-message-processor-messages.md) page.

## <a name="inbound-shipment-orders"></a>Review inbound shipment orders

To review your inbound shipment orders, go to **Warehouse management > Inquiries and reports > Inbound shipment orders**. The documents listed here provide information about the expected product receipts. The **Inbound shipment orders** page provides a **Header** and **Lines** view of the available shipment orders as seen from Supply Chain Management. For each of the lines, you can view detailed information about the **Receiving status**, **Inventory transactions**, and associated **Warehouse work**. You can also view and edit the **Receiving status** on the order header and use it to follow the inbound progress of the orders. 

The following **Receiving status** values are available:

- *Open* – No quantities have been fully received.
- *Partially received* – Some, but not all, quantities have been fully received.
- *Received* – All quantities have been fully received.

If you're already familiar with Supply Chain Management, you might recognize this document as being similar to a simplified purchase order. However, inbound shipment orders won't make any financial postings for the [general ledger](../../finance/general-ledger/general-ledger.md).

> [!WARNING]
> On the *Inbound shipment order lines* you can use the option **Update line > Delivery remainder** to update expected order line transaction quantities. Make sure to have the proper user role security privilege assigned for this process, because this will (like the messages editing) allow for potential inconsistencies between the external systems and Supply Chain Management.

> [!NOTE]
> The internal inbound shipment order number must be unique. You can define to use the external order numbers as internal numbers and thereby not needing to use a [number sequence](wms-only-mode-setup.md#number-sequences) for the order. To ensure unique numbers across external systems you can consider using the *Order number prefix/suffix* options.

## Review outbound shipment orders

To view documents with information about products requested for dispatch, go to **Warehouse management > Inquiries and reports > Outbound shipment orders**. The **Outbound shipment orders** page provides a **Header** and **Lines** view of the available shipment orders as seen from Supply Chain Management. For each of the lines, you can view detailed information about **Release status**, **Shipment status**, **Inventory transactions**, and associated **Warehouse work**. You can also view and edit the **Release status** and **Shipment status** on the order header and use it to follow the outbound progress of the orders.

The following **Release status** values are available:

- *Open* – No quantities have been [released to warehouse](release-to-warehouse-process.md).
- *Partially released* – Some, but not all, quantities have been [released to warehouse](release-to-warehouse-process.md).
- *Released* – All quantities have been [released to warehouse](release-to-warehouse-process.md).

The following **Shipment status** values are available:

- *Open* – No quantities have been shipped confirmed.
- *Partially shipped* – Some, but not all, quantities have been shipped confirmed.
- *Shipped* – All quantities have been shipped confirmed.

> [!NOTE]
> The internal outbound shipment order number must be unique. You can define to use the external order numbers as internal numbers and thereby not needing to use a [number sequence](wms-only-mode-setup.md#number-sequences) for the order. To ensure unique numbers across external systems, consider using the **Order number prefix/suffix** options.

If you're already familiar with Supply Chain Management, you might recognize this document as being similar to a simplified sales order that uses some of the same reservation and [release to warehouse](release-to-warehouse-process.md) processes. Use the [Source systems](wms-only-mode-setup.md#source-systems) settings to control whether to trigger reservations automatically when importing documents and/or to automatically reject shipment orders that can't be partly or fully reserved.

In the current release, outbound shipment order lines don't provide out-of-the-box support for being associated with loads before they are [released to warehouse](release-to-warehouse-process.md). This association can only occur during the warehouse waving process.

> [!WARNING]
> On outbound shipment order lines, you can use the **Update line > Delivery remainder** option to update expected order line transaction quantities. Make sure that you have the proper user role security privilege assigned for this process, because (as with message editing) this allows for potential inconsistencies between the external systems and Supply Chain Management. <!--KFM: Clarify this sentence. What are the "proper user roles". It this the right terminology? How does "this" allow for inconsistencies? I generally don't get it. -->

## Inbound process

The following illustration highlights the various elements of the inbound process.

:::image type="content" source="media/wms-only-inbound-wom-process.svg" alt-text="Warehouse management only mode inbound process." lightbox="media/wms-only-inbound-wom-process.svg":::

Here's a high-level description of the inbound process:

1. An external system submits an *inbound shipment order* message to Supply Chian Management.
1. Supply Chian Management processes the message in Warehouse management only mode and creates orders.
1. Inbound loads are created in one of three ways (as established by the [Source systems](wms-only-mode-setup.md#source-systems) settings in Supply Chain Management):
    - Manually, using the [Inbound load planning workbench](create-or-modify-an-inbound-load.md#create-an-inbound-load-manually)
    - By importing [advanced shipping notices (ASNs)](import-asn-data-entity.md)
    - Automatically during [message processing](../supply-chain-dev/message-processor.md)
1. A warehouse worker using the Warehouse Management mobile app to *register* the inbound shipment transactions.
1. Supply Chian Management runs [receiving completed](wms-only-mode-using.md#receiving-completed) processes related for each relevant load. These processes update the load status to *Received* and generate [shipment receipts](wms-only-mode-using.md#shipment-receipts) and trigger *business events** for the external systems.
1. The external systems read and uses the [shipment receipts](wms-only-mode-using.md#shipment-receipt) data for further processing, such as purchase order invoicing if you have purchase orders associated with the inbound shipment orders in the external system.
1. Supply Chian Management finalizes the inbound shipment orders by running the *Post shipment receipts* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

## <a name="receiving-completed"></a>The receiving completed process

The *receiving completed* process updates the load status to *Received* and generates [shipment receipts](#shipment-receipts), which trigger a business event for the external systems.

Workers can trigger the receiving completed process manually from the load using either the web client or the Warehouse Management mobile app. To enable workers to use the Warehouse Management mobile app, set up a *Receiving completed confirmation* mobile device menu item, which you can add as part of a [detour](warehouse-app-detours.md) within the inbound receiving flows.

<!--KFM: This isn't clear. Where are these settings? --> Depending on the setting **Capture receiving completed packing slip**, as part of the **Warehouse management parameters - Loads** section, it's possible to capture a *packing slip ID* and a *date* for each of the shipments associated with an inbound load. The following settings are supported for the **Capture receiving completed packing slip**:

- *Never* – Don't prompt for packing slip ID and date.
- *Always* – Prompt for packing slip ID and date and only proceed when they are specified.
- *Optional* – Prompt for the packing slip ID and date, but allow the worker to proceed without specifying them.

> [!NOTE]
> In the current version, load line quantities must be fulfilled according to over-delivery and under-delivery settings and *Receiving completed* must be triggered manually.

## <a name="shipment-receipts"></a>Shipment receipts

Go to **Warehouse management > Inquiries and reports > Shipment receipts** to view the detailed line transactions related to received inventory. The data is version controlled and you can follow the **Posting status** on the header.

The header status is moved from *Ready for posting* to *Posted* as part of the [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) *Post shipment receipts* job, which is automatically initialized as part of the [Source systems](wms-only-mode-setup.md#source-systems) setup. The source system setup also lets you schedule the batch job, which ensures that the related inbound shipment order line transactions are moved to a finalized transaction state for the Warehouse management module.

To see all of the background processes that you have running, go to [**System administration > Setup > Process automations**](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

> [!NOTE]
> You can reverse receiving confirmations provided the related inbound shipment order line transactions have not yet been finalized.

> [!WARNING]
> If you enable Warehouse management only mode and are already running a periodic *Update product receipts* batch job for loads associated with purchase orders, you probably need to update the query for the batch job to exclude inventory transaction updates for inbound shipment orders. You can do this by adding the *Load details* entity with a *NotExist* join to the *Loads* entity followed by a range definition for the **Reference** field with *Criteria = Inbound shipment order*.

## Outbound process

The following illustration highlights the various elements of the outbound process.

:::image type="content" source="media/wms-only-outbound-wom-process.svg" alt-text="Warehouse management only mode outbound process." lightbox="media/wms-only-outbound-wom-process.svg":::

Here's a high-level description of the outbound process:

1. An external system submits an *outbound shipment order* messages.
1. Supply Chian Management processes the message in Warehouse management only mode and creates orders.
1. Inventory reservations are created in one of two ways (as established by the [Source systems](wms-only-mode-setup.md#source-systems) settings in Supply Chain Management):
    - Automatically, by the [message processor](../supply-chain-dev/message-processor.md)
    - Manually, as part of the release process
1. The orders is released for further warehouse processing, either manually or automatically (by running the *Automatic release of outbound shipment orders* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md)).
1. Depending on how your [wave template](wave-templates.md) definitions are set up, warehouse work may be created and released immediately.
1. The outbound warehouse work is processed and the status of the related outbound shipment order line transactions are updated *Picked*.
1. The loads are outbound ship confirmed, which results in *business events* and a [*shipment packing slip*](wms-only-mode-using.md#shipment-packing-slips) being created for the external system.
1. The external system reads the shipment packing slip and uses its data for further processing (such as for sales order invoicing for sales orders that are associated with outbound shipment orders).
1. Supply Chian Management finalizes the outbound shipment order by running the *Post shipment packing slips* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

> [!NOTE]
> You'll be able to reverse the shipment confirmation until the related outbound shipment order line transactions is finalized, but not thereafter.

## <a name="shipment-packing-slips"></a>Shipment packing slips

Go to **Warehouse management > Inquiries and reports > Shipment packing slips** to view detailed line transactions related to shipped inventory and print a report using the **Preview/Print** option. You can control the printed inventory dimension values by going to **Warehouse management > Setup > Warehouse management parameters - Reports - Shipment packing slip**. <!--KFM: Clarify this path -->

Shipment packing slip data is version controlled and you can follow the **Posting status** on the header. The **Posting status** changes from *Ready for posting* to *Posted* as part of the *Post shipment packing slips* [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) job, which is automatically initialized as part of the [Source systems](wms-only-mode-setup.md#source-systems) setup. The source system setup also lets you schedule the batch job, which ensures that related outbound shipment order line transactions are moved to a finalized transaction state for the Warehouse management module.

To see all of the background processes that you have running, go to [**System administration > Setup > Process automations**](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

> [!NOTE]
> If no language is defined for an order, the report will fall back to use the company specific language settings.

## <a name="maintain-messages"></a>Viewing and maintaining shipment order messages

In Warehouse management only mode, you can both view and update shipment order messages, which can be a quick way to test integrations during the implementation process.  When a message is in a *Failed* message state, you can update all field values except the order header and line numbers. Go to one of the following pages to view and maintain the messages:

- **Warehouse management > Inquiries and reports > Inbound shipment order messages**
- **Warehouse management > Inquiries and reports > Outbound shipment order messages**

Use the **Processing status** field to monitor the progress of each shipment order message. The following **Processing status** values are available:

- *Receiving* – The message is in the process of getting imported.
- *Received* – The message has been received and is in a *Queued* state in the [message processor](../supply-chain-dev/message-processor.md), ready to be picked up for processing.
- *Accepted* – The message processor state is *Processed* and therefore a shipment order has been created.  
- *Failed* – The [message processor](../supply-chain-dev/message-processor.md) processed the message but one or more errors occurred. You can create a copy of the message when you save it after editing.
- *Draft* – The message is a copy that can get updated. To reprocess the message, move it into the *Queued* message state by selecting the **Queue** option.

<!-- 
- (*Canceled*) – New planned state in future version instead of using the *Failed* state for messages that have been canceled. You can resend a message (for the same order) from the external system.
 -->
> [!TIP]
> Select the **Show old versions** option to follow manual message updates based on the **Replaced by message** field value.

> [!WARNING]
> Making manual message field updates in production environments can result in data inconsistency between the external source system and Supply Chain Management. For example, you might change an **Item number** to a value that isn't known to the external system. This type of update will probably cause problems in progress information flows and it might even be impossible to correct it in the external system. Make sure to have the proper user role security privilege assigned for this process. <!--KFM: This last sentence doesn't seem to fit here. What do we mean? -->
