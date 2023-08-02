---
title: Warehouse management only mode
description: Run all supply chain warehouse operations in Microsoft Dynamics 365 Supply Chain Management as part of a dedicated ecosystem that easily integrates with other ERP and order management systems via inbound and outbound shipment orders.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage
ms.topic: how-to
ms.date: 08/02/2023
audience: Application User
ms.search.region: Global
---

<!--
How does this documentation gets generated?

https://learn.microsoft.com/en-us/common-data-model/schema/core/operationscommon/entities/supplychain/wms/overview 

Will it be OK to ref. to WHSInboundShipmentOrders and WHSOutboundShipmentOrders ????
-->

# Warehouse management only mode

*Warehouse management only mode* provides several deployment options to support the actual business needs of running your [warehouse management](warehouse-management-overview.md) processes.

![High level integrations](./media/high-level-integrations.png)

One example being a dedicated LCS Supply Chain Management cloud deployment only handling the warehouse operations and all integrations related to orders and financial processing handled outside this deployment. With this implementation concept, you must configure the processes around warehouse management as part of the Supply Chain Management cloud deployment.  

![Warehouse management only mode to ERP/Order system, example 1](./media/scm-wom-2-erp.png)

Another example is a more Supply Chain Management integrated implementation methodology, having the warehouses enabled for Supply Chain Management processes like sales, purchase, production orders, etc. and at the same time handling warehouse operations for other ERP/order processing systems. With this type of implementation, the same warehouse instance can handle all the logistic warehouse processes for both internal and external integrations.

![Warehouse management only mode to ERP/Order system, example 2](./media/scm-wms-scm-2-erp.png)

And then everything between the two previous example deployment options, which for example could be running a dedicated legal entity within an existing Supply Chain Management deployment that only handles the warehouse management processes for external systems. All-in-all you can use the **Warehouse management only mode** exactly as needed.

## <a name="feature-management"></a>Feature management

To use the **Warehouse management only mode** capability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.

- The feature that's named **(Preview) Warehouse management only mode** must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- With the feature enabled you can open the **Warehouse management > Setup > Warehouse management integration > Source systems** used to define the integration systems. To enable all the functionalities, you must at least insert one record into this entity.

## Data exchange

Running **Warehouse management only mode** requires integration to be defined between the ERP/Order systems and the Microsoft Dynamics 365 Supply Chain Management system.
Integration between systems is a widespread challenge, but nevertheless of huge importance getting to work seamlessly.
In general, three categories of interactions are needed for the **Warehouse management only mode**:

- Document data (like purchase and sales orders)
- Master data (like products)
- Progress data (like receiving, dispatch, and inventory on-hand information)

Many different integration methodologies can be used for these three categories, but the following subsections describe the recommended integration process.

### Document data

To inform the warehouse management system about what physical inventory to receive and ship, you can easily use the inbound and outbound shipment order messages. These messages are designed with header and lines data.

With the introduction of these two new, lightweight inbound and outbound warehouse interface documents, you no longer need to set up multiple documents for inbound and outbound operations (sales orders, purchase orders, transfer orders, and so on) that essentially serve the same purpose from a pure warehouse management perspective. This will, for example, simplify integration with ERP and order management systems and enable the use of the Dynamics 365 warehouse management functionality in an ERP agnostic manner.

#### <a name="inbound-outbound-shipment-order-messages"></a>Inbound and outbound shipment order messages

The **inbound shipment order messages** and the **outbound shipment order messages** can be imported via a [**Dataverse integration**](/power-platform/admin/data-integrator.md) or directly integrated with the [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md) shipment order message entities in an optimal manner.

A following [**message processing**](warehouse-message-processor-messages.md) will validate the import process by ensuing consistent data between the systems, both when it comes to the master data like products, but also the order progress status alignments, making the Supply Chain Management inbound/outbound shipment orders actionable for the warehouse management processes, by not allowing creation or updating of invalid/unsupported order data. We recommend that you process the messages as part of a periodic batch job triggered by the [**Message processor**](../supply-chain-dev/message-processor.md) page where you must use the **Shipment Orders** *Message queue*.

![Message processing diagram](./media/shipment-order-integrations.png)

> [!NOTE]
> Having the shipment order line field data related to the released products in the [**Supply Chain Management product information management module**](../pim/product-information.md) requires the products to be created before the system can accept the shipment order messages.

##### Viewing and maintaining shipment order messages

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

### Master data

A few master data entities will need to be recorded to be able to run your warehouse management system, here the [**data entities**](../../fin-ops-core/dev-itpro/data-entities/data-entities.md) can be used to easily import the data.

To create the *shipment orders*, **Released products** must exist. You can read more about the support of importing product master data via the [**product data entities**](../pim/data-entities.md) and get an overview of the [**Product information management entities**](/common-data-model/schema/core/operationscommon/entities/supplychain/productinformationmanagement/overview.md).

As part of the creation of a *Released product* you must assign an **Item model group**. Make sure this model group gets enabled with an *Inventory model* as **Non-valuated** with *Post physical inventory* and *Post financial inventory* cleared which will eliminate the need for setting up any costing data for this product.

Besides the product master data, you must at least have defined the [**Countries/regions**](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) which will be used for the outbound shipment order import process to create addresses. You'll also need this data to [create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md) for the warehouses.

> [!NOTE]
> Depending on the [address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md) and the use of the address fields in the order messages you might need to create additional data before the order messages can get imported. Example could be the state and county combinations.

### Progress data

External systems have many different business process requests for the warehouse management system. One example being the progress of a sales order. The external systems can keep polling for this kind of information, but to honor this process the Supply Chain Management warehouse management system can be set up to provide [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md).

#### <a name="business-events"></a>Business events

The Supply Chain Management warehouse management system can be set up to provide [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md) to keep the external systems informed about the progress and actions going on. With this setup, the external systems don't need to keep polling for information that might not have changed since the last request of information, but instead only need to act when getting informed.

Several out-of-the-box [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md) are supported for warehouse integration. The following table lists several (but not all) of these business events.

| Business event ID | Description |
|---|---|
| `InventCountingJournalPostedBusinessEvent` | Counting journal posted |
| `WHSOutboundNotificationCreatedBusinessEvent` | Outbound warehouse notification created |
| `WHSShipmentOrderMessageChangedStatusBusinessEvent` | Status update for shipment order message |
| `WHSShipmentPackingSlipJournalModifiedBusinessEvent` | Shipment packing slips updated |
| `WHSShipmentReceivingJournalModifiedBusinessEvent` | Shipment receipts updated |
| `SysMessageProcessorMessageProcessedBusinessEvent` | Message processor message failure |
| `WhsWaveExecutedBusinessEvent` | Wave executed |

As a minimum, we recommend that you use the following  [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md):

- `InventCountingJournalPostedBusinessEvent` – To be informed about an inventory on-hand adjustment has happened and where to look up the detailed information about the update.

- `WHSShipmentPackingSlipJournalModifiedBusinessEvent` – To be informed about an outbound shipment confirmation process has happened and where to look up the detailed dispatch advice data, which, for example,  can be used for a sales invoicing process.

- `WHSShipmentReceivingJournalModifiedBusinessEvent` – To be informed about an inbound receiving completion process has happened and where to look up the detailed receiving advice data, which, for example,  can be used for a purchase order invoicing process.

## <a name="source-systems"></a> Source systems

The **Warehouse management only mode** shipment order integration must be configured with information about the source systems going to provide inbound and outbound order messages. You can make this configuration on the **Warehouse management > Setup > Warehouse management integration > Source systems** page, and this configuration is required to make it possible to view the **Inbound shipment orders** and **Outbound shipment orders** and the related processes around the inbound shipment.

The **Source system** name must be identical with the name in the provided message before a message can be accepted getting imported into Supply Chain Management. Other settings can be used as part of the **Source systems** page to control the shipment order import processes, for example it's possible to define **Message value mapping** for item and warehouse identifications and define if loads for inbound shipment orders are automatically created as part of the **Inbound shipment order policies** definition.

> [!NOTE]
> When mapping the items to [**Bar codes**](../pim/tasks/create-bar-code-product.md) remember to enable the *Scanning* setting for the bar codes. For product variants it is only the "ItemNumber" field being used from the order line messages when using **Message value mapping** for the items.

## Warehouse integration monitoring

The **Warehouse management > Workspaces > Warehouse integration monitoring** page provides an overview of the warehouse integration messages and an easy way to navigate to the related areas, for example to the [**System administration > Message processor > Message processor messages**](warehouse-message-processor-messages.md) page.

## Inbound shipment orders

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

## Outbound shipment orders

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

## Automatic release of outbound shipment orders

To enable automatic release to warehouse, you can use the **Warehouse management > Release to warehouse > Automatic release of outbound shipment orders** batch job process. For more information, see [Release to warehouse](release-to-warehouse-process.md).

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

## <a name="shipment-packing-slips"></a>Shipment packing slips

In the **Warehouse management > Inquiries and reports > Shipment packing slips** page you can view the detailed line transactions related to the shipped inventory and print a report of the data via the **Preview/Print** option. You can control the printed inventory dimension values as part of the **Warehouse management > Setup > Warehouse management parameters - Reports - Shipment packing slip**.

The **Shipment packing slip** data is version controlled and you can follow the **Posting status** on the header data.

The header is changed from *Ready for posting* to *Posted* as part of the [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) *Post shipment packing slips* job, which is automatically initialized as part of the [source system](#source-systems) setup. The source system setup also lets you schedule the batch job, which ensures that the related outbound shipment order line transactions are moved to a finalized transaction state for the Warehouse management module.

You can see all the *Background processes* running as part of the [**System administration > Setup > Process automations**](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) page.

> [!NOTE]
> In case of not having defined a language for the order the report will fall back to use the company specific language settings.

## Inventory on-hand updates between the systems

![Warehouse management only mode - internal process](./media/internal-wom-process.png)

The Warehouse management module supports multiple inventory on-hand update processes using the [Counting journal](../inventory/inventory-journals.md#counting). For more information about the counting process, see [Cycle counting](cycle-counting.md).

As part of a journal posting process a [business event](#business-events) gets triggered and the integrated systems can read about the updates as part of the [counting journal entities](/common-data-model/schema/core/operationscommon/entities/supplychain/inventoryandwarehousemanagement/inventinventorycountingjournallineentity). It's important only to act on the updated quantities not to get out of sync as part of the updates. The following scenario provides an example.

**Prerequisite:**

The external system and the Supply Chain Management WMS on-hand is in sync:

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |0 pcs       |

**When 1:**

Supply Chain Management WMS receives 10 pcs of item number A0001 against an inbound shipment order without *Receiving completed* processing, so the external system is not yet informed about this.

**Then 1:**

The external system and Supply Chain Management WMS is out of sync:

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |10 pcs      |

**When 2:**

In Supply Chain Management WMS, an on-hand adjustment (counting journal) us posted for A0001, adding 1 pcs more on-hand:

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |11 pcs      |

**Then 2:**

The external system is informed via a business event that an adjustment has occurred, and as part of this process, the reading of the journal posting changes from 10 pcs. to 11 pcs. in the WMS. It's important that the external system only consider the updated quantity of 1 pcs:

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |1 pcs       |11 pcs      |

**When 3:**

Supply Chain Management WMS runs a **Receiving completed** process related to the received 10 pcs. of item number A0001.

**Then 3:**

The external system is informed via a business event, and can read the shipment receipts information and update on-hand quantity with an additional 10 pcs.

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |11 pcs      |11 pcs      |

> [!NOTE]
> To avoid configuration for the [*inventory postings*](../../finance/general-ledger/inventory-posting.md) and [*fiscal calendars*](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md) when making adjustments via the [**counting journal**](../inventory/tasks/define-inventory-counting-processes.md), make sure your items are assigned to an **Item model group** using the *Inventory model* **Non-valuated** with *Post physical inventory* and *Post financial inventory* cleared.

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

## Example of using inbound and outbound shipment orders

This section provides an example scenario that shows how to create inbound and outbound shipment orders. To ease a tryout, the examples are running on the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) for the **USMF** legal entity.

To create inbound and outbound shipment orders, a message entity needs to be posted using [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md) requests. That message then needs to be processed by the [**Message processor**](../supply-chain-dev/message-processor.md) in Supply Chain Management, which will create the orders in the warehouse system.

The same message structure logic applies for both the inbound and outbound shipment order messages, which are:

``` Message structure:
- Order header
   - Order line 1
   - Order line 2
   - Order line … 
- Complete
```

To showcase basic examples, [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) is used in the following to create simple orders with minimal payload.
The provided example data uses the process of not being depending on the default company for the authorization user and the messages are therefore containing a *dataAreaId* value.

> [!NOTE]
> To ease the messages processing [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) supports collections and environment variables that can be reused for all the requests, including the *Authorization*. You will in the following see the used variables within "{{" "}}" indications.

### Prerequisites

#### Feature enablement

Make sure having the **Warehouse management only mode** enabled as described in the [Feature management](#feature-management) section.

#### Microsoft Entra ID applications

In the **Microsoft Entra ID applications** page, assign the *Admin* user, or a user having authentication access to the integration messages, like the default ***Warehouse System Integration Operator*** role to the client that is used for authentication while interacting with the Supply Chain Management environment from an external source. In case you use the same user as part of the product master data import you must add more privileges related to product master data entities to the ***Warehouse System Integration Operator*** role.

When posting entities via [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md), it's important to ensure that either the user's default company matches the company in which the entity will be posted or to specify the company (dataAreaId), in the request payload messages. In any case, the company (dataAreId) must get specified to complete the messages for the shipment orders.

#### Source systems example

Make sure a record is created in the **Source systems** page, this enables the full use of the capability.

For this example, define *Source system* as ***ERP***.

#### <a name=”number-sequences”></a>Number sequences

For the order import process, the [number sequences](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview) for *Outbound shipment orders* and *Inbound shipment orders* must be defined when not using the same order numbers as the external system provides in Supply Chain Management WMS. In general, make sure to define all the number sequences associated with the **Warehouse management > Setup > Warehouse management parameters > Number sequences** which includes the following extra number sequences:

- Outbound shipment order
- Inbound shipment order
- Shipment packing slip
- Shipment receipt
- Warehouse outbound notification ID
- Load line inventory pick

> [!TIP]
> You can quickly enable all number sequences by using the ***Generate*** option on the [**Number sequences**](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview) page.

### Create shipment order messages

#### <a name="simple-inbound-shipment-order-example"></a>Simple inbound shipment order message example

For the inbound shipment order header message **InboundShipmentOrderMessages**, you must provide the following data as a minimum:

- MessageId = M1
- dataAreaId = USMF (optional depending on default authorization user company)
- SourceSystemId = ERP
- OrderNumber = IO1
- ReceivingWarehouseId = 51

Using the [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) with variables, the message will look like:

``` JSON InboundShipmentOrderMessages example
POST {{EnvironmentUrl}}/data/InboundShipmentOrderMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"ReceivingWarehouseId": "{{Warehouse}}"
}
```

and post **Inbound shipment order line** message:

``` JSON InboundShipmentOrderLineMessages example
POST {{EnvironmentUrl}}/data/InboundShipmentOrderLineMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"OrderLineNumber": 1,
"ItemNumber": "A0001",
"ExpectedQuantity": 10,
"ExpectedUnitSymbol": "Pcs"
}
```

Post **Complete** message for the header and lines to commit the messages

``` JSON InboundShipmentOrderMessages Complete example
POST {{EnvironmentUrl}}/data/InboundShipmentOrderMessages(MessageId='{{MessageId}}', dataAreaId='{{dataAreaId}}',SourceSystemId='{{SourceSystem}}', OrderNumber='{{OrderNumber}}')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The dataAreaId is used as part of the key to match up against the released header and line messages and must be specified. The suffix *?cross-company=true* is only needed when having messages for a different company than the used **Microsoft Entra ID applications** user default company.

#### Simple outbound shipment order message example

For the outbound shipment order header message **OutboundShipmentOrderMessages**, you must provide the following data as a minimum:

- MessageId = M2
- dataAreaId = USMF  (optional depending on default authorization user company)
- SourceSystemId = ERP
- OrderNumber = OO1
- ShipFromWarehouseId = 51
- ConsigneeName or ReceiverName = Microsoft  
- ConsigneeCountryRegionId or ReceiverCountryRegionId = USA

Using the [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) with variables the message will look like:

``` JSON OutboundShipmentOrderMessages example
POST {{EnvironmentUrl}}/data/OutboundShipmentOrderMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"ShipFromWarehouseId": "{{Warehouse}}",
"ConsigneeName": "{{ConsigneeName}}",
"ConsigneeCountryRegionId": "{{ConsigneeCountryRegionId}}"
}
```

and post **Outbound shipment order line** message:

``` JSON OutboundShipmentOrderLineMessages example
POST {{EnvironmentUrl}}/data/OutboundShipmentOrderLineMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"OrderLineNumber": 1,
"ItemNumber": "A0001",
"OrderedQuantity": 10,
"OrderedUnitSymbol": "Pcs"
}
```

Post *Complete* message for the header and lines to commit the messages

``` JSON OutboundShipmentOrderMessages Complete example
POST {{EnvironmentUrl}}/data/OutboundShipmentOrderMessages(MessageId='{{MessageId}}', dataAreaId='{{dataAreaId}}',SourceSystemId='{{SourceSystem}}', OrderNumber='{{OrderNumber}}')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The dataAreaId is used as part of the key to match up against the released header and line messages and must be specified. The suffix *?cross-company=true* is only needed when having messages for a different company than the used **Microsoft Entra ID applications** user default company.

### Message processor messages for shipment orders

Having the two documents imported into the [message queue](#inbound-outbound-shipment-order-messages) you now need to get them [processed](warehouse-message-processor-messages.md) and thereby getting the actual **Inbound and outbound shipment orders** created in the **Warehouse management only mode** system.

## Frequently asked questions

### What to do when a message processing is **Failed**?

The [message processing](../supply-chain-dev/message-processor.md) will retry three times before failing. You can use [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md) to be notified about this. Follow the [view log](../supply-chain-dev/message-processor.md#view-message-log) information for the **Message processor messages** page and use the information to take the next appropriate action of either moving the message back into reprocessing (**Queue** option), **Cancel** the message, or manually [update the message](#viewing-and-maintaining-shipment-order-messages).
> [!NOTE]
> Typically, data updated must happen before it make sense trying to reprocess the *Failed* message.

### Why does my message not get processed, but stays in the *Queued* state?

If you have multiple messages with dependencies (for example, for same order number) in the *Failed* state, you must either correct the data and move the message back into *Queued* state for reprocessing or *Cancel* the dependent messages beforehand.

### Why do I need to provide a **Country/Region** field value for my outbound shipment order?

The *Outbound shipment order* requires to create an address. For this to happen you must specify at least two field values the [countries/regions](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup#set-up-countryregion-information) and a *Name*. The *Country/Region* value must match existing data in the [**Address setup**](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup#set-up-countryregion-information). You can use the following message fields to provide the data:

- ConsigneeName
- ConsigneeCountryRegionId
- ReceiverName
- ReceiverCountryRegionId

### Why do I see all the modules and not only the ones that are needed for warehouse management processes?

The **Warehouse management only mode** is part of the larger Microsoft Dynamics Supply Chain Management deployment and thereby enabling you to use all the integration points being part of this. To limit the access to processes you must assign [**roles**](../../fin-ops-core/dev-itpro/sysadmin/role-based-security) only related to warehouse management processes, which will limit the access to other areas of the product.

- *Warehouse manager* – Enables and reviews processes, maintains master data, and responds to inquiries
- *Warehouse mobile device user* – Used to access the Warehouse Mobile Devices Portal service
- *Warehouse planner* – Setup and planning processes
- *Warehouse system integration operator* – Setup integration processes related to inbound and outbound shipment orders
- *Receiving clerk* – Working with inbound processes
- *Shipping clerk* – Working with outbound processes
- *Warehouse worker* – Working with daily warehouse processes

### Why do I get the error "No fiscal calendar has been defined for the ledger. In general ledger setup, select a fiscal calendar for the ledger." when posting a counting journal?

Unless you set up the *Released products* with an **Item model group** enabled with an *Inventory model* as **Non-valuated** with cleared *Post physical inventory* and *Post financial inventory* you'll need to set up all the costing and general ledger setup data like the [*fiscal calendars*](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md).

### Why do I get the error "The accounting currency hasn't been defined for the ledger. You must define the currency in the Ledger form." when processing warehouse operations?

Unless you set up the *Released products* with an **Item model group** enabled with an *Inventory model* as **Non-valuated** with cleared *Post physical inventory* and *Post financial inventory* you'll need to set up all the costing and general ledger setup data like the [*the currency in the ledger*](../../finance/general-ledger/configure-ledger.md).

### Why do I get the error "The accounting currency has not been defined for the ledger. You must define the currency in the Ledger form." when processing different order types?

Even though using *Released products* with an **Item model group** enabled with an *Inventory model* as **Non-valuated** with cleared *Post physical inventory* and *Post financial inventory* you'll need to setup costing data for orders currently not supported by the *Warehouse management only mode*.

### Why can't I just **Receive complete** what I have partly inbound registered

Depending on your setup an inbound load will either automatically get created as part of the *Inbound shipment order* import, via *ASN* import or via a manual process. In the current version the load line quantities must be fulfilled according to over-/under-delivery settings and the **Receiving completed** must be triggered manually.
<!-- Delivery policy -->

### Why do I see the error "Unable to update product receipt for a load with inbound shipment order lines" for my existing **Update product receipts** process?

In case of enabling the *Warehouse management only mode* capability and already running a periodic **Update product receipts** batch job for loads associated with purchase orders, you'll need to update the query for the batch job to exclude the inventory transaction updates for the *inbound shipment orders*. This can easily be done by adding the *Load details* entity with a *NotExist* join to the *Loads* entity followed by a range definition for the *Reference* field with *Criteria* = Inbound shipment order.
