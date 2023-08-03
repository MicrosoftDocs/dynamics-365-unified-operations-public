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

## Monitor the integration

The **Warehouse management > Workspaces > Warehouse integration monitoring** page provides an overview of the warehouse integration messages and an easy way to navigate to the related areas, for example to the [**System administration > Message processor > Message processor messages**](warehouse-message-processor-messages.md) page.

## Review inbound shipment orders

**Warehouse management > Inquiries and reports > Inbound shipment orders** are documents that represent information about the expected product receipts. The **Inbound shipment orders** page contains an ‘internal Supply Chain Management warehouse representation' of the available shipment orders in a **Header** and **Lines** view. For each of the lines, you can view detailed information about the **Receiving status**, **inventory transactions**, and any associated **warehouse work**. The **Receiving status** gets as well maintained on the order header and can be used to follow the inbound progress of the orders. The following **Receiving status** values are available:

- *Open* – No quantities has been **Receiving completed**
- *Partially received* – Partly quantities has been **Receiving completed**
- *Received* – All quantities has been **Receiving completed**

If you're already familiar with Supply Chain Management, you might find this document comparable with a minimal purchase order document. No financial postings as part of the [**General ledger**](../../finance/general-ledger/general-ledger.md) will be used for this source document.

> [!WARNING]
> On the *Inbound shipment order lines* you can use the option **Update line > Delivery remainder** to update expected order line transaction quantities.
> Make sure to have the proper user role security privilege assigned for this process, because this will (like the messages editing) allow for potential inconsistencies between the external systems and Supply Chain Management.

> [!NOTE]
> The internal inbound shipment order number must be unique. You can define to use the external order numbers as internal numbers and thereby not needing to use a [number sequence](#number-sequences) for the order. To ensuring unique numbers across external systems you can consider using the *Order number prefix/suffix* options.

## Review outbound shipment orders

**Warehouse management > Inquiries and reports > Outbound shipment orders** are documents that represent information about the requested product dispatch. The **Outbound shipment orders** page contains an ‘internal Supply Chain Management warehouse representation' of the available shipment orders in a **Header** and **Lines** view. For each of the lines, you can view detailed information about **Release status**, **Shipment status**, **inventory transactions**, and any associated **warehouse work**. The **Release status** and **Shipment status** gets as well maintained on the order header and can be used to follow the outbound progress of the orders. The following states are available for the **Release status**:

- *Open* – No quantities has been [released to warehouse](release-to-warehouse-process.md)
- *Partially released* – Partly quantities has been [released to warehouse](release-to-warehouse-process.md)
- *Released* – All quantities has been [released to warehouse](release-to-warehouse-process.md)

And the following states are available for the **Shipment status**:

- *Open* – No quantities has been shipped confirmed
- *Partially shipped* – Partly quantities has been shipped confirmed
- *Shipped* – All quantities has been shipped confirmed

> [!NOTE]
> The internal outbound shipment order number must be unique. You can define to use the external order numbers as internal numbers and thereby not needing to use a [number sequence](#number-sequences) for the order. To ensuring unique numbers across external systems you can consider using the *Order number prefix/suffix* options.

If you're already familiar with Supply Chain Management, you might find this document comparable with a minimal sales order document having some of the same **Reservation** and [**Release to warehouse**](release-to-warehouse-process.md) processes. As part of the [**Source systems**](#source-systems) definitions, you can trigger the reservation as part of the document import and even define to reject a shipment order that can't be partly or fully reserved.

In the first release of the **Warehouse management only mode**, the outbound shipment order lines don't provide out-of-the-box support for getting associated with loads before the [**Release to warehouse**](release-to-warehouse-process.md) process. This association can only occur as part of the processing of the warehouse waving.

> [!WARNING]
> On the *Outbound shipment order lines* you can use the option **Update line > Delivery remainder** to update expected order line transaction quantities.
> Make sure to have the proper user role security privilege assigned for this process, because this will (like the messages editing) allow for potential inconsistencies between the external systems and Supply Chain Management.

## Receiving completed

The **Receiving completed** process updates the load status to *Received* and generates [**Shipment receipts**](#shipment-receipts) which trigger **Business event** for the external systems.

You can trigger the **Receiving completed** manually from the load in the web client and/or via the **Receiving completed confirmation** *Warehouse management mobile app* mobile device menu item, which you can add as part of a [detour](warehouse-app-detours.md) within the inbound receiving flows.

Depending on the setting **Capture receiving completed packing slip**, as part of the **Warehouse management parameters - Loads** section, it's possible to capture a *packing slip ID* and a *date* for each of the shipments associated to the inbound load. The following settings are supported for the **Capture receiving completed packing slip**:

- Never – Don't prompt for *packing slip ID* and date capturing
- Always – Prompt for *packing slip ID* and *date* and only proceed when specified
- Optional – Prompt for the *packing slip ID* and *date*, but allow when not specified

<!-- Delivery policy -->
> [!NOTE]
> In the current version the load line quantities must be fulfilled according to over-/under-delivery settings and the **Receiving completed** must get triggered manually, but in future version it is planned to have a policy to define the process.

## <a name="shipment-receipts"></a> Shipment Receipts

In the **Warehouse management > Inquiries and reports > Shipment receipts** page you can view the detailed line transactions related to the received inventory. The data is version controlled and you can follow the **Posting status** on the header data.

The header is moved from *Ready for posting* to *Posted* as part of the [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) *Post shipment receipts* job, which is automatically  initialized as part of the [source system](#source-systems) setup. The source system setup also lets you schedule the batch job, which ensures that the related inbound shipment order line transactions are moved to a finalized transaction state for the Warehouse management module.

You can see all the *Background processes* running as part of the [**System administration > Setup > Process automations**](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) page.

> [!NOTE]
> Reversal of the receiving confirmation will be supported as long as the related inbound shipment order line transactions have not been finalized.

> [!WARNING]
> If you are enabling the Warehouse management only mode capability and already are running a periodic *Update product receipts* batch job for loads associated with purchase orders, you probably need to update the query for the batch job to exclude the inventory transaction updates for the *inbound shipment orders*. You can do this by adding the *Load details* entity with a *NotExist* join to the *Loads* entity followed by a range definition for the *Reference* field with *Criteria* = Inbound shipment order.

## <a name="shipment-packing-slips"></a>Shipment packing slips

In the **Warehouse management > Inquiries and reports > Shipment packing slips** page you can view the detailed line transactions related to the shipped inventory and print a report of the data via the **Preview/Print** option. You can control the printed inventory dimension values as part of the **Warehouse management > Setup > Warehouse management parameters - Reports - Shipment packing slip**.

The **Shipment packing slip** data is version controlled and you can follow the **Posting status** on the header data.

The header is changed from *Ready for posting* to *Posted* as part of the [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) *Post shipment packing slips* job, which is automatically initialized as part of the [source system](#source-systems) setup. The source system setup also lets you schedule the batch job, which ensures that the related outbound shipment order line transactions are moved to a finalized transaction state for the Warehouse management module.

You can see all the *Background processes* running as part of the [**System administration > Setup > Process automations**](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) page.

> [!NOTE]
> In case of not having defined a language for the order the report will fall back to use the company specific language settings.

## Viewing and maintaining shipment order messages

It's possible to both view and update shipment order messages in Supply Chain Management Warehouse management only mode, which can be a quick way to test integrations as part of an implementation process.  When a message is in a *Failed* message state you can update all field values, except the order header and line numbers. The pages used to view and maintain the messages are:

- **Warehouse management > Inquiries and reports > Inbound shipment order messages**
- **Warehouse management > Inquiries and reports > Outbound shipment order messages**

The **Processing status** field can be used to monitor the progress of the shipment order messages. The following states are available:

- *Receiving* – The message is in the process of getting imported.
- *Received* – The message has been received and in a *Queued* [message processor](../supply-chain-dev/message-processor.md) state, ready to be picked up for processing.
- *Accepted* – The message processor state is *Processed* and thereby a shipment order has been created.  
- *Failed* – The [message processor](../supply-chain-dev/message-processor.md) has processed the message but one or more errors occurred. A copy of the message can get created as part of an edit saving.
- *Draft* – A copy of a message that can get updated. To reprocess the message, you can move the message into the *Queued* message state by using the **Queue** option.
- (*Canceled*) – New planned state in future version instead of using the *Failed* state for messages that have been canceled. You can resend a message (for the same order) from the external system.
<!-- Canceled -->
> [!TIP]
> By selecting the **Show old versions** option you can follow the manual message updates by using the *Replaced by message* field value.

> [!WARNING]
> Making manual message field updates in production environments might result in data inconsistency between the external source system and Supply Chain Management. As an example you will be able to change an *item number* to a value which will be unknown to the related external system. This type of update will most likely cause problems as part of the further progress information flows and might not be possible to get corrected as well in the back-end external system. Make sure to have the proper user role security privilege assigned for this process.

