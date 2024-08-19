---
title: Exchange data between systems
description: Learn how to exchange data and business events between systems in Warehouse management only mode with an outline on master and reference data.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 04/27/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage, WHSConsigner, WHSConsignerGroup, WHSConsignee, WHSConsignerGroup, WHSSourceSystemItem, EcoResStorageDimensionGroup, InventItemGroup, InventModelGroup, EcoResStorageDimensionGroup, EcoResTrackingDimensionGroup, WHSReservationHierarchy, UnitOfMeasure, WHSUOMSeqGroupTable, WHSSourceSystemProductMessage, WHSSourceSystemProductVariantMessage, WHSSourceSystemProductDocumentAttachmentMessage, WHSSourceSystemProductSpecificUnitOfMeasureConversionMessage, WHSSourceSystemProductBarcodeMessage, WHSSourceSystemProductGlobalTradeItemNumberMessage
---

# Exchange data between systems

[!include [banner](../includes/banner.md)]

Warehouse management only mode requires that you set up integration between external systems and the Microsoft Dynamics 365 Supply Chain Management system. The following categories of interactions are required:

- Master data (such as product information)
- Document data (such as purchase orders and sales orders)
- Progress data (such as receiving, dispatch, and on-hand inventory information)

Many different integration methodologies can be used for these three categories. This article describes the recommended integration process.

## <a name="master-data"></a>Master and reference data

For consistent communication, several types of master and reference data must be synced and available to both systems. One example is the product master data. This type of data can be imported into Supply Chain Management via the following messages that are related to product master data:

- `SourceSystemProductMessages` – Used to create products and released products, including product masters for variants.
- `SourceSystemProductVariantMessages` – Used to create variants for product masters where **ProductSubtype** = *ProductMaster*.
- `SourceSystemProductSpecificUnitOfMeasureConversionMessages` – Used to create product-specific unit-of-measure conversions.
- `SourceSystemProductBarcodeMessages` – Used to create the product bar code setup.
- `SourceSystemProductGlobalTradeItemNumberMessages` – Used to create the Global Trade Item Number (GTIN) for the products.
- `SourceSystemProductDocumentAttachmentMessages` – Used to attach product documents, product images, and so on.

> [!TIP]
> [Record templates](../../fin-ops-core/fin-ops/data-entities/use-record-template-new-record.md) are useful when you import products, because you can include the **TemplateName** value in your messages. In addition, you can make sure that the required reference fields for the released products are assigned.

Like shipment orders, these messages are validated during message processing and automatically link the product information to a [source system record](wms-only-mode-setup.md#source-systems) via the *Source system items* entity. The external system can use [business events](#business-events) to monitor how the status of messages changes during message processing.

Only one [source system record](wms-only-mode-setup.md#source-systems) can be marked as the external system that maintains the product master data that's related to the unique reference for a released product or item number. You can view and maintain this data by using the **Source system items** page.

> [!NOTE]
> The message processor processes each message related to creating product master data separately, according to its `MessageId`. Some messages have dependencies, such as the requirement to create the released product before giving it a barcode. If you use number sequences instead of external item numbers for products, then `SourceSystemProductMessages` processes will create new products when no released product or source system item data exists.

> [!TIP]
> The **Source system item number** field is used during communication between the systems. It's useful when, for example, an external system uses a European Article Number (EAN) bar code as the unique identification number that's linked to an **Item/variant number** field that has a different value. The *Source system item number* data is automatically created when the previously listed messages are used.
>
> When the Warehouse Management mobile app is used, the **Source system item number** value can also be used to look up the **Item/variant number** value that's used internally.

You can import the required master data into Supply Chain Management by using [data entities](../../fin-ops-core/dev-itpro/data-entities/data-entities.md). The following types of master and reference data are required to create the **Release product/Item number** value that's used in warehouse management processes:

- **Item model groups** – Each released product must be assigned to an item model group in Supply Chain Management. Therefore, at least one group must be available. The group can control business processes for batch-tracked items. The following settings are recommended for every item model group that's used with Warehouse management only mode. These settings eliminate the need to set up any costing data for the products.

    - **Inventory model** – Set this field to *Non-valuated*.
    - **Post physical inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).
    - **Post financial inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).

- **Item groups** – Can be used to group business processes, especially when [product filter codes](filters-and-filter-codes.md) are used. No account setup is required when *Non-valuated* inventory model groups are used.
- **Storage dimension groups** – Enable the use of storage inventory dimensions values such as sites, warehouses, locations, and license plates. Be sure to enable the **Use warehouse management processes** parameter.
- **Tracking dimension groups** – Enable the use of tracking inventory dimensions such as owner, batch, and serial numbers. Note that the *Owner* dimension value must equal the company that a warehouse is associated with. Learn more in [Unsupported processes](wms-only-mode-overview.md#unsupported-processes).
- **Reservation hierarchy** – Defines which dimensions are reserved during the outbound shipment order reservation process. Dimensions that are put below the *Location* dimension are controlled by the warehouse management processes.
- **Units** – Each quantity that a warehouse process handles must be associated with a unit. When multiple units (such as each, box, and/or pallet) are used for an item, be sure to define the *inventory unit* as the smallest unit for the item.
- **Unit sequence groups** – Define the sequence of units that can be used in warehouse operations. For more information about the required setup, see [Unit of measure and stocking policies](unit-measure-stocking-policies.md).

> [!NOTE]
> The messages that create product master data use the [*product data entities*](../pim/data-entities.md). These entities can be used by themselves, or they can be used to maintain product master data.

### View and maintain source system product messages

In Warehouse management only mode, you can view, update, and create product messages. Therefore, you can quickly test integrations during the implementation process. When an externally created message is in a *Failed* message state, you can update field values and assign the updated message back into the message queue. The original message will be versioned and non-editable. Go to one of the following pages to view and maintain the messages:

- **Warehouse management** \> **Source system products** \> **Source system product messages**
- **Warehouse management** \> **Source system products** \> **Source system product variant messages**
- **Warehouse management** \> **Source system products** \> **Source system product barcode messages**
- **Warehouse management** \> **Source system products** \> **Source system product document attachment messages**
- **Warehouse management** \> **Source system products** \> **Source system product global trade item number messages**
- **Warehouse management** \> **Source system products** \> **Source system product specific unit of measure conversion messages**

The **Warehouse integration monitoring** workspace lets you track the number of source system product messages that are *Queued* and *Failed*.

> [!NOTE]
> You can set each source system to either allow or prevent users from manually creating messages on the listed pages. Open the relevant [source system](wms-only-mode-setup.md#source-systems) record, and set the **Enable manual source system product message creation** option to *Yes* allow manual messages or *No* to prevent them. Be aware that, unlike messages that are imported via integration, manually created messages aren't versioned.

### Consigner and consignee information

To make it easier to set up your warehouse operation, you can create and use data for *consigners* and *consignees* and their related group definitions. For example, you can use this approach for a process that's related to setting up a [quality order creation process](../inventory/quality-associations.md) for a specific consigner or consigner group.

Neither the *Inbound shipment order policies* (which are part of the **Source systems** setup) nor inbound shipment order message processing requires that the fields for the **Consigner's account number** value exist in the entity for the **Consigners** page (**Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Consigners**). The same "free text" concept exists for the outbound shipment order process that's related to the **Consigner's account number** value.

### Country/region

To [create a new legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md) for your warehouses and import outbound shipment orders, you must have [**country/region**](../../fin-ops-core/dev-itpro/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) values defined in Supply Chain Management. These records are used in outbound shipment orders to create addresses. Depending on your [address setup](../../fin-ops-core/dev-itpro/organization-administration/global-address-book-address-setup.md) and the way that you use address fields in order messages, you might have to create additional data before you can import order messages (for example, to support state/province and county combinations).

## <a name="inbound-outbound-shipment-order-messages"></a>Inbound and outbound shipment order messages

You can use inbound and outbound shipment order messages to inform Supply Chain Management about which physical inventory to receive and ship. These messages include both header data and lines data.

Messages between systems are exchanged by using lightweight *inbound shipment order* and *outbound shipment order* documents. These documents eliminate the need to use several other types of documents that Supply Chain Management typically uses (such as sales orders, purchase orders, and transfer orders). Therefore, they have several benefits. For example, they simplify integration with enterprise resource planning (ERP) and order management systems. They also make Supply Chain Management warehouse management functionality available to a wide range of external ERP and order management systems.

Inbound and outbound shipment order messages can be exchanged by using [Dataverse](/power-platform/admin/data-integrator). Alternatively, they can be exchanged through [Open Data Protocol (OData)](../../fin-ops-core/dev-itpro/data-entities/odata.md) by using shipment order message entities and/or by using the [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md) import process (for example, by using the *Inbound shipment order messages composite entity* and *Outbound shipment order messages composite entity*).

Supply Chain Management queues the incoming documents and then processes them by using the [message processor](warehouse-message-processor-messages.md). This approach ensures consistent data between the systems, both for master data (such as products) and order progress status. Therefore, Supply Chain Management inbound and outbound shipment orders are prevented from creating or updating nonvalid or unsupported order data. We recommend that you process the messages as part of a periodic batch job that the [message processor](../supply-chain-dev/message-processor.md) triggers by using the *Shipment orders* message queue.

This following illustration shows how the message processor fits into an integrated system.

:::image type="content" source="media/wms-only-shipment-order-integrations.svg" alt-text="Message processing diagram." lightbox="media/wms-only-shipment-order-integrations.svg":::

## <a name="business-events"></a>Progress data and business events

External systems can have many different business process requests for the warehouse management system. For example, each external system can continuously poll for the progress of a sales order. To honor the process, Supply Chain Management can be set up to deliver [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) as required. Business events keep external systems informed about the progress and actions that are occurring in Supply Chain Management. When this setup is in place, the external systems don't have to continue to poll for information that might not have changed since the last request. Instead, they can react only when they're informed.

Several out-of-box business events are supported for warehouse integrations. The following table lists some of them.

| Business event ID | Description |
|---|---|
| `WHSSourceSystemProductMessageChangedStatusBusinessEvent` | Source system product message changed status |
| `InventCountingJournalPostedBusinessEvent` | Counting journal posted |
| `WHSSourceSystemInventoryOnhandReportBusinessEvent` | Source system on-hand inventory report created |
| `WHSInventoryUpdateLogBusinessEvent` | Warehouse inventory update log updated |
| `WHSOutboundNotificationCreatedBusinessEvent` | Outbound warehouse notification created |
| `WHSShipmentOrderMessageChangedStatusBusinessEvent` | Shipment order message status updated |
| `WHSShipmentPackingSlipJournalModifiedBusinessEvent` | Shipment packing slip updated |
| `WHSShipmentPackingSlipJournalFailedBusinessEvent` | Shipment packing slips update failed |
| `WHSShipmentReceivingJournalModifiedBusinessEvent` | Shipment receipts updated |
| `WHSShipmentReceivingJournalFailedBusinessEvent` | Shipment receipts update failed |
| `SysMessageProcessorMessageProcessedBusinessEvent` | Message processor message failed |
| `WhsWaveExecutedBusinessEvent` | Wave executed |
| `WHSQualityOrderValidatedBusinessEvent` | Quality order validated |
| `WHSEWInboundShipmentOrderRequestCreatedBusinessEvent` | Inbound shipment order request created (can be used to integrate Supply Chain Management with another WMS) |
| `WHSEWOutboundShipmentOrderRequestCreatedBusinessEvent` | Outbound shipment order request created (can be used to integrate Supply Chain Management with another WMS) |
| `WHSEWInboundShipmentOrderUpdateChangedStatusBusinessEvent` | Inbound shipment order update is being processed and has therefore changed status (can be used to integrate Supply Chain Management with another warehouse management system (WMS)) |
| `WHSEWOutboundShipmentOrderUpdateChangedStatusBusinessEvent` | Outbound shipment order update is being processed and has therefore changed status (can be used to integrate Supply Chain Management with another WMS) |

At a minimum, we recommend that you use the following business events for integration with an external ERP system:

- `InventCountingJournalPostedBusinessEvent` – This event announces that an on-hand inventory adjustment has occurred and indicates where detailed information about the update can be found.
- `WHSSourceSystemInventoryOnhandReportBusinessEvent` – This event announces that an on-hand inventory report has been generated and indicates where detailed information about the update can be found.
- `WHSShipmentPackingSlipJournalModifiedBusinessEvent` – This event announces that an outbound shipment confirmation process has occurred and indicates where the detailed dispatch advice data can be found. (This data can be used for a sales invoicing process, for example.)
- `WHSShipmentReceivingJournalModifiedBusinessEvent` – This event announces that an inbound receiving completion process has occurred and indicates where the detailed receiving advice data can be found. (This data can be used for a purchase order invoicing process, for example.)

## On-hand adjustments

When you integrate an ERP system and a warehouse management system, it's essential that you keep on-hand inventory data aligned. Several processes can help maintain this alignment as part of the Warehouse management only mode implementation approach. For more information about how the inventory on-hand update process works, see [On-hand inventory updates between systems](wms-only-mode-external-erp.md#on-hand-updates-between-systems).
