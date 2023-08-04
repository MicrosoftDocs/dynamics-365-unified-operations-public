---
title: Exchange data between systems
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

# Exchange data between systems

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Running **Warehouse management only mode** requires integration to be defined between the ERP/Order systems and the Microsoft Dynamics 365 Supply Chain Management system.
Integration between systems is a widespread challenge, but nevertheless of huge importance getting to work seamlessly.
In general, three categories of interactions are needed for the **Warehouse management only mode**:

- Document data (like purchase and sales orders)
- Master data (like products)
- Progress data (like receiving, dispatch, and inventory on-hand information)

Many different integration methodologies can be used for these three categories, but the following subsections describe the recommended integration process.

## Document data

To inform the warehouse management system about what physical inventory to receive and ship, you can easily use the inbound and outbound shipment order messages. These messages are designed with header and lines data.

With the introduction of these two new, lightweight inbound and outbound warehouse interface documents, you no longer need to set up multiple documents for inbound and outbound operations (sales orders, purchase orders, transfer orders, and so on) that essentially serve the same purpose from a pure warehouse management perspective. This will, for example, simplify integration with ERP and order management systems and enable the use of the Dynamics 365 warehouse management functionality in an ERP agnostic manner.

The **inbound shipment order messages** and the **outbound shipment order messages** can be imported via a [**Dataverse integration**](/power-platform/admin/data-integrator.md) or directly integrated with the [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md) shipment order message entities in an optimal manner.

A following [**message processing**](warehouse-message-processor-messages.md) will validate the import process by ensuing consistent data between the systems, both when it comes to the master data like products, but also the order progress status alignments, making the Supply Chain Management inbound/outbound shipment orders actionable for the warehouse management processes, by not allowing creation or updating of invalid/unsupported order data. We recommend that you process the messages as part of a periodic batch job triggered by the [**Message processor**](../supply-chain-dev/message-processor.md) page where you must use the **Shipment Orders** *Message queue*.

This following image shows how the message processor fits into an integrated system.

:::image type="content" source="media/wms-only-shipment-order-integrations.svg" alt-text="Message processing diagram." lightbox="media/wms-only-shipment-order-integrations.svg":::

> [!NOTE]
> Having the shipment order line field data related to the released products in the [**Supply Chain Management product information management module**](../pim/product-information.md) requires the products to be created before the system can accept the shipment order messages.

## Master data

A few master data entities will need to be recorded to be able to run your warehouse management system, here the [**data entities**](../../fin-ops-core/dev-itpro/data-entities/data-entities.md) can be used to easily import the data.

To create the *shipment orders*, **Released products** must exist. You can read more about the support of importing product master data via the [**product data entities**](../pim/data-entities.md) and get an overview of the [**Product information management entities**](/common-data-model/schema/core/operationscommon/entities/supplychain/productinformationmanagement/overview.md).

As part of the creation of a *Released product* you must assign an **Item model group**. Make sure this model group gets enabled with an *Inventory model* as **Non-valuated** with *Post physical inventory* and *Post financial inventory* cleared which will eliminate the need for setting up any costing data for this product.

Besides the product master data, you must at least have defined the [**Countries/regions**](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) which will be used for the outbound shipment order import process to create addresses. You'll also need this data to [create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md) for the warehouses.

> [!NOTE]
> Depending on the [address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md) and the use of the address fields in the order messages you might need to create additional data before the order messages can get imported. Example could be the state and county combinations.

## Progress data and business events

External systems have many different business process requests for the warehouse management system. One example being the progress of a sales order. The external systems can keep polling for this kind of information, but to honor this process the Supply Chain Management warehouse management system can be set up to provide [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md).

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

## Inventory on-hand updates between the systems

The following illustration shows the internal processes used for warehouse management only mode.

:::image type="content" source="media/wms-only-internal-wom-process.svg" alt-text="Warehouse management only mode internal process." lightbox="media/wms-only-internal-wom-process.svg":::

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



