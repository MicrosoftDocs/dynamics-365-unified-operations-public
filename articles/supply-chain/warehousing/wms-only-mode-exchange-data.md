---
title: Exchange data between systems
description: Learn how to exchange data and business events between systems in Warehouse management only mode with an outline on master and reference data.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 01/13/2026
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

You can use many different integration methodologies for these three categories. This article describes the recommended integration process.

## <a name="master-data"></a>Master and reference data

To keep communication consistent, both systems need to sync and have access to several types of master and reference data. One example is the product master data. You can import this type of data into Supply Chain Management by using the following messages that relate to product master data:

- `WHSSourceSystemProductMessageEntity` – Create products and released products, including product masters for variants.
- `WHSSourceSystemProductVariantMessageEntity` – Create variants for product masters where **ProductSubtype** = *ProductMaster*.
- `WHSSourceSystemProductSpecificUnitOfMeasureConversionMessageEntity` – Create product-specific unit-of-measure conversions.
- `WHSSourceSystemProductBarcodeMessageEntity` – Create the product bar code setup.
- `WHSSourceSystemProductGlobalTradeItemNumberMessageEntity` – Create the Global Trade Item Number (GTIN) for the products.
- `WHSSourceSystemProductDocumentAttachmentMessageEntity` – Attach product documents, product images, and so on.

> [!TIP]
> When you import products, use [record templates](../../fin-ops-core/fin-ops/data-entities/use-record-template-new-record.md) to include the **TemplateName** value in your messages. You can also make sure that the required reference fields for the released products are assigned.

Like shipment orders, the system validates these messages during message processing. The process automatically links the product information to a [source system record](wms-only-mode-setup.md#source-systems) through the *Source system items* entity. The external system can use [business events](#business-events) to monitor how the status of messages changes during message processing.

You can mark only one [source system record](wms-only-mode-setup.md#source-systems) as the external system that maintains the product master data related to the unique reference for a released product or item number. Use the **Source system items** page to view and maintain this data.

> [!NOTE]
> The message processor handles each message related to creating product master data separately, based on its `MessageId`. Some messages have dependencies, such as the requirement to create the released product before giving it a barcode. If you use number sequences instead of external item numbers for products, then `SourceSystemProductMessages` processes create new products when no released product or source system item data exists.

> [!TIP]
> Use the **Source system item number** field during communication between the systems. It's useful when, for example, an external system uses a European Article Number (EAN) bar code as the unique identification number that's linked to an **Item/variant number** field that has a different value. The *Source system item number* data is automatically created when you use the previously listed messages.
>
> When you use the Warehouse Management mobile app, you can use the **Source system item number** value to look up the **Item/variant number** value that's used internally.

You can import the required master data into Supply Chain Management by using [data entities](../../fin-ops-core/dev-itpro/data-entities/data-entities.md). The following types of master and reference data are required to create the **Release product/Item number** value that's used in warehouse management processes:

- **Item model groups** – Each released product must be assigned to an item model group in Supply Chain Management. Therefore, at least one group must be available. The group can control business processes for batch-tracked items. The following settings are recommended for every item model group that's used with Warehouse management only mode. These settings eliminate the need to set up any costing data for the products.

    - **Inventory model** – Set this field to *Non-valuated*.
    - **Post physical inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).
    - **Post financial inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).

- **Item groups** – Use these groups to organize business processes, especially when you use [product filter codes](filters-and-filter-codes.md). No account setup is required when you use *Non-valuated* inventory model groups.
- **Storage dimension groups** – Enable the use of storage inventory dimensions such as sites, warehouses, locations, and license plates. Be sure to enable the **Use warehouse management processes** parameter.
- **Tracking dimension groups** – Enable the use of tracking inventory dimensions such as owner, batch, and serial numbers. Note that the *Owner* dimension value must equal the company that a warehouse is associated with. Learn more in [Unsupported processes](wms-only-mode-overview.md#unsupported-processes).
- **Reservation hierarchy** – Defines which dimensions are reserved during the outbound shipment order reservation process. Dimensions that are put below the *Location* dimension are controlled by the warehouse management processes.
- **Units** – Each quantity that a warehouse process handles must be associated with a unit. When multiple units (such as each, box, and pallet) are used for an item, define the *inventory unit* as the smallest unit for the item.
- **Unit sequence groups** – Define the sequence of units that can be used in warehouse operations. For more information about the required setup, see [Unit of measure and stocking policies](unit-measure-stocking-policies.md).

> [!NOTE]
> The messages that create product master data use the [*product data entities*](../pim/data-entities.md). You can use these entities by themselves, or you can use them to maintain product master data.

### View and maintain source system product messages

In Warehouse management only mode, you can view, update, and create product messages. Therefore, you can quickly test integrations during the implementation process. When an externally created message is in a *Failed* message state, you can update field values and assign the updated message back into the message queue. The original message is versioned and non-editable. Go to one of the following pages to view and maintain the messages:

- **Warehouse management** \> **Source system products** \> **Source system product messages**
- **Warehouse management** \> **Source system products** \> **Source system product variant messages**
- **Warehouse management** \> **Source system products** \> **Source system product barcode messages**
- **Warehouse management** \> **Source system products** \> **Source system product document attachment messages**
- **Warehouse management** \> **Source system products** \> **Source system product global trade item number messages**
- **Warehouse management** \> **Source system products** \> **Source system product specific unit of measure conversion messages**

The **Warehouse integration monitoring** workspace lets you track the number of source system product messages that are *Queued* and *Failed*.

> [!NOTE]
> You can set each source system to either allow or prevent users from manually creating messages on the listed pages. Open the relevant [source system](wms-only-mode-setup.md#source-systems) record, and set the **Enable manual source system product message creation** option to *Yes* to allow manual messages or *No* to prevent them. Be aware that, unlike messages that are imported via integration, manually created messages aren't versioned.

### Consigner and consignee information

To make it easier to set up your warehouse operation, you can create and use data for *consigners* and *consignees* and their related group definitions. For example, you can use this approach for a process that's related to setting up a [quality order creation process](../inventory/quality-associations.md) for a specific consigner or consigner group.

Neither the *Inbound shipment order policies* (which are part of the **Source systems** setup) nor inbound shipment order message processing requires that the fields for the **Consigner's account number** value exist in the entity for the **Consigners** page (**Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Consigners**). The same "free text" concept exists for the outbound shipment order process that's related to the **Consigner's account number** value.

### Country/region

To [create a new legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md) for your warehouses and import outbound shipment orders, you must have [**country/region**](../../fin-ops-core/dev-itpro/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) values defined in Supply Chain Management. These records are used in outbound shipment orders to create addresses. Depending on your [address setup](../../fin-ops-core/dev-itpro/organization-administration/global-address-book-address-setup.md) and the way that you use address fields in order messages, you might have to create additional data before you can import order messages (for example, to support state/province and county combinations).

## <a name="inbound-outbound-shipment-order-messages"></a>Inbound and outbound shipment order messages

Use inbound and outbound shipment order messages to inform Supply Chain Management about which physical inventory to receive and ship. These messages include both header data and lines data.

- `WHSInboundShipmentOrderMessageEntity` – Create inbound shipment order header.
- `WHSInboundShipmentOrderLineMessageEntity` – Create inbound shipment order lines.
- `WHSOutboundShipmentOrderMessageEntity` – Create outbound shipment order header.
- `WHSOutboundShipmentOrderLineMessageEntity` – Create outbound shipment order lines.

> [!NOTE]
>
> - You can update an inbound or outbound shipment order by submitting a message that includes a matching order number and source system in the header data.
> - You can delete an inbound or outbound shipment order by submitting a message that includes a matching order number and source system in the header data and omits all line data.

Messages between systems are exchanged by using lightweight *inbound shipment order* and *outbound shipment order* documents. These documents eliminate the need to use several other types of documents that Supply Chain Management typically uses (such as sales orders, purchase orders, and transfer orders). Therefore, they have several benefits. For example, they simplify integration with enterprise resource planning (ERP) and order management systems. They also make Supply Chain Management warehouse management functionality available to a wide range of external ERP and order management systems.

You can exchange inbound and outbound shipment order messages by using [Dataverse](/power-platform/admin/data-integrator). Alternatively, you can exchange these messages through [Open Data Protocol (OData)](../../fin-ops-core/dev-itpro/data-entities/odata.md) by using shipment order message entities. You can also use the [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md) import process. For example, you can use the *Inbound shipment order messages composite entity* ()`WHSInboundShipmentOrderMessageCompositeEntity`) and *Outbound shipment order messages composite entity* (`WHSOutboundShipmentOrderMessageCompositeEntity`).

You can attach documents to inbound and outbound shipment order messages by using the *Inbound shipment order message document attachment entity* (`WHSInboundShipmentOrderMessageDocumentAttachmentEntity`) and *Outbound shipment order message document attachment entity* (`WHSOutboundShipmentOrderMessageDocumentAttachmentEntity`).

Supply Chain Management queues the incoming documents and then processes them by using the [message processor](warehouse-message-processor-messages.md). This approach ensures consistent data between the systems, both for master data (such as products) and order progress status. Therefore, Supply Chain Management inbound and outbound shipment orders are prevented from creating or updating nonvalid or unsupported order data. Process the messages as part of a periodic batch job that the [message processor](../message-processor/message-processor.md) triggers by using the *Shipment orders* message queue.

The following illustration shows how the message processor fits into an integrated system.

:::image type="content" source="media/wms-only-shipment-order-integrations.svg" alt-text="Message processing diagram." lightbox="media/wms-only-shipment-order-integrations.svg":::

## <a name="business-events"></a>Progress data and business events

External systems can send many different business process requests to the warehouse management system. For example, each external system can continuously check for the progress of a sales order. To support this process, you can set up Supply Chain Management to deliver [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) as required. Business events keep external systems informed about the progress and actions that are occurring in Supply Chain Management. When you set up this process, the external systems don't have to continue to check for information that might not have changed since the last request. Instead, they can react only when they're informed.

Warehouse integrations support several out-of-the-box business events. The following table lists some of them.

Some business events don't include all journal details directly. In these cases, the event contains only the journal ID. You can use this ID to retrieve the full information through related data entities listed in the following table.

| Business event ID | Description | Data entities |
| --- | --- | --- |
| `WHSSourceSystemProductMessageChangedStatusBusinessEvent` | Source system product message changed status | |
| `InventCountingJournalPostedBusinessEvent` | Counting journal posted | `InventInventoryCountingJournalHeaderEntity`<br>`InventInventoryCountingJournalHeaderLineEntity`<br>`InventInventoryCountingJournalNameEntity` |
| `WHSSourceSystemInventoryOnhandReportBusinessEvent` | Source system on-hand inventory report created | `WHSInventoryOnhandReportEntity`<br>`WHSSourceSystemInventoryOnhandReportLineEntity` |
| `WHSInventoryUpdateLogBusinessEvent` | Warehouse inventory update log updated | `WHSSourceSystemItemInventoryUpdateLogEntity` |
| `WHSOutboundNotificationCreatedBusinessEvent` | Outbound warehouse notification created | `WHSOutboundNotificationEntity`<br>`WHSOutboundShipmentNotificationEntity`<br>`WHSOutboundShipmentLineNotificationEntity` |
| `WHSShipmentOrderMessageChangedStatusBusinessEvent` | Shipment order message status updated | |
| `WHSShipmentPackingSlipJournalModifiedBusinessEvent` | Shipment packing slip updated | `WHSShipmentPackingSlipJournalHeaderEntity`<br>`WHSShipmentPackingSlipJournalLineEntity`<br>`WHSShipmentPackingSlipTransactionInventoryDimensionEntity` |
| `WHSShipmentPackingSlipJournalFailedBusinessEvent` | Shipment packing slips update failed | |
| `WHSShipmentReceivingJournalModifiedBusinessEvent` | Shipment receipts updated | `WHSShipmentReceiptJournalHeaderEntity`<br>`WHSShipmentReceiptJournalLineEntity`<br>`WHSShipmentReceiptTransactionInventoryDimensionEntity` (Supply Chain Management version 10.0.45 and earlier)<br>`WHSShipmentReceiptTransactionInventoryDimensionV2Entity` (Supply Chain Management version 10.0.46 and later) |
| `WHSShipmentReceivingJournalFailedBusinessEvent` | Shipment receipts update failed | |
| `SysMessageProcessorMessageProcessedBusinessEvent` | Message processor message failed | |
| `WhsWaveExecutedBusinessEvent` | Wave executed | |
| `WHSQualityOrderValidatedBusinessEvent` | Quality order validated | |
| `WHSEWInboundShipmentOrderRequestCreatedBusinessEvent` | Inbound shipment order request created (can be used to integrate Supply Chain Management with another warehouse management system) | `WHSEWInboundShipmentOrderRequestEntity`, `WHSEWInboundShipmentOrderLineRequestEntity`<br>`WHSEWInboundShipmentOrderRequestStatusEntity` |
| `WHSEWOutboundShipmentOrderRequestCreatedBusinessEvent` | Outbound shipment order request created (can be used to integrate Supply Chain Management with another warehouse management system) | `WHSEWOutboundShipmentOrderRequestEntity`<br>`WHSEWOutboundShipmentOrderLineRequestEntity`<br>`WHSEWOutboundShipmentOrderRequestStatusEntity` |
| `WHSEWInboundShipmentOrderUpdateChangedStatusBusinessEvent` | Inbound shipment order update is being processed and has therefore changed status (can be used to integrate Supply Chain Management with another warehouse management system) | |
| `WHSEWOutboundShipmentOrderUpdateChangedStatusBusinessEvent` | Outbound shipment order update is being processed and has therefore changed status (can be used to integrate Supply Chain Management with another warehouse management system) | |

At a minimum, use the following business events for integration with an external ERP system:

- `InventCountingJournalPostedBusinessEvent` – Announces that an on-hand inventory adjustment occurred and indicates where detailed information about the update can be found.
- `WHSSourceSystemInventoryOnhandReportBusinessEvent` – Announces that an on-hand inventory report was generated and indicates where detailed information about the update can be found.
- `WHSShipmentPackingSlipJournalModifiedBusinessEvent` – Announces that an outbound shipment confirmation process occurred and indicates where the detailed dispatch advice data can be found. This data can be used for a sales invoicing process, for example.
- `WHSShipmentReceivingJournalModifiedBusinessEvent` – Announces that an inbound receiving completion process occurred and indicates where the detailed receiving advice data can be found. This data can be used for a purchase order invoicing process, for example.

## On-hand adjustments

When you integrate an ERP system and a warehouse management system, it's essential that you keep on-hand inventory data aligned. Several processes can help maintain this alignment as part of the Warehouse management only mode implementation approach. For more information about how the inventory on-hand update process works, see [On-hand inventory updates between systems](wms-only-mode-external-erp.md#on-hand-updates-between-systems).

## Warehouse management only mode with external shared warehouses

You can set up an integration between Supply Chain Management and an external warehouse management system. To enable this integration, use external warehouse shipment order requests and updates for communication between the systems. Learn more in [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).

### Inbound and outbound shipment order requests

Use external warehouse inbound and outbound shipment order requests to import orders from Supply Chain Management into your warehouse management system. When you release an order to the warehouse, the system creates a business event with a request ID. You can use this ID to retrieve full details through related data entities.

| Business event ID | Description | Data entities |
| --- | --- | --- |
| `WHSEWInboundShipmentOrderRequestCreatedBusinessEvent` | Inbound shipment order request created | `WHSEWInboundShipmentOrderRequestEntity`<br>`WHSEWInboundShipmentOrderLineRequestEntity`<br>`WHSEWInboundShipmentOrderRequestStatusEntity` |
| `WHSEWOutboundShipmentOrderRequestCreatedBusinessEvent` | Outbound shipment order request created | `WHSEWOutboundShipmentOrderRequestEntity`<br>`WHSEWOutboundShipmentOrderLineRequestEntity`<br>`WHSEWOutboundShipmentOrderRequestStatusEntity` |

### Inbound and outbound shipment order updates

Use external warehouse inbound and outbound shipment order updates to send shipment updates from your warehouse management system to Supply Chain Management. The message processor processes these updates in the same way as [inbound and outbound shipment order messages](#inbound-outbound-shipment-order-messages).

- `WHSEWInboundShipmentOrderUpdateEntity`
- `WHSEWInboundShipmentOrderLineUpdateEntity`
- `WHSEWInboundShipmentOrderLineInventDimUpdateEntity`
- `WHSEWOutboundShipmentOrderUpdateEntity`
- `WHSEWOutboundShipmentOrderLineUpdateEntity`
- `WHSEWOutboundShipmentOrderLineInventDimUpdateEntity`

## Unannounced sales returns from another warehouse management system

If your warehouse management system receives an unannounced sales return, it must update the Supply Chain Management system accordingly. To achieve this goal, send an external warehouse inbound shipment order update message to the Supply Chain Management system. Ensure that you include all required details and entities so the return update can be processed correctly.

- `WHSEWInboundShipmentOrderUpdateEntity`
    - Set the value of the `InboundShipmentOrderOriginLinkType` field to *1*, which represents the `ExternalOrigin` enum value of the `WHSInboundShipmentOrderOriginLinkType` enum.
- `WHSEWInboundShipmentOrderLineUpdateEntity`
- `WHSEWInboundShipmentOrderLineInventDimUpdateEntity`
- `WHSEWInboundShipmentOrderExternalOriginEntity`
    - This entity provides additional required information.
    - The value of the `InboundShipmentOrderExternalOriginId` field must match the `InboundShipmentOrderOriginId` field on the `WHSEWInboundShipmentOrderUpdateEntity` entity. You can choose and maintain this ID.
    - Set the `ExternalWarehouseManagementSystemId` field to the external warehouse management system ID configured in your Supply Chain Management system.
