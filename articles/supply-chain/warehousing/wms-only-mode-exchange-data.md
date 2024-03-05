---
title: Exchange data between systems (preview)
description: This article explains how to exchange data and business events between systems in Warehouse management only mode.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage, WHSConsigner, WHSConsignerGroup, WHSConsignee, WHSConsignerGroup, WHSSourceSystemItem, EcoResStorageDimensionGroup, InventItemGroup, InventModelGroup, EcoResStorageDimensionGroup, EcoResTrackingDimensionGroup, WHSReservationHierarchy, UnitOfMeasure, WHSUOMSeqGroupTable
ms.topic: how-to
ms.date: 01/29/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Exchange data between systems (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

Warehouse management only mode requires that you set up integration between external systems and the Microsoft Dynamics 365 Supply Chain Management system. The following categories of interactions are required:

- Master data (such as product information)
- Document data (such as purchase orders and sales orders)
- Progress data (such as receiving, dispatch, and on-hand inventory information)

Many different integration methodologies can be used for these three categories. This article describes the recommended integration process.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## <a name="master-data"></a>Master and reference data

For consistent communication, several types of master and reference data must be synced and available to both systems. One example is the product master data. This type of data can be imported into Supply Chain Management via the following messages that are related to product master data:

- `SourceSystemProductMessages` – Used to create products and released products, including product masters for variants.
- `SourceSystemProductVariantMessages` – Used to create variants for product masters where **ProductSubtype** = *ProductMaster*.
- `SourceSystemProductSpecificUnitOfMeasureConversionMessages` – Used to create product-specific unit-of-measure conversions.
- `SourceSystemProductBarcodeMessages` – Used to create the product bar code setup.

Like shipment orders, these messages are validated during message processing and automatically link the product information to a [source system record](wms-only-mode-setup.md#source-systems) via the *Source system items* entity. The external system can use [business events](#business-events) to monitor how the message state changes during message processing.

Only one [source system record](wms-only-mode-setup.md#source-systems) can be marked as the external system that maintains the product master data that's related to the unique reference for a released product or item number. You can view and maintain this data by using the **Source system items** page.

> [!NOTE]
> The message processor processes each message related to creating product master data separately, according to its `MessageId`. Some messages have dependencies, such as the requirement to create the released product before giving it a barcode. If you use number sequences instead of external item numbers for products, then `SourceSystemProductMessages` processes will create new products when no released product or source system item data exists.

> [!TIP]
> The **Source system item number** field is used during communication between the systems. It's useful when, for example, an external system uses a European Article Number (EAN) bar code as the unique identification number that's linked to an **Item/variant number** field that has a different value. The *Source system item number* data is automatically created when the previously listed messages are used.
>
> When the Warehouse Management mobile app is used, the **Source system item number** value can also be used to look up the **Item/variant number** value that's used internally.

You can import the required master data into Supply Chain Management by using [data entities](../../fin-ops-core/dev-itpro/data-entities/data-entities.md). The following types of master and reference data are required to create the **Release product/Item number** value that's used in warehouse management processes:

<!-- .40: Note that you can apply a [record template](../../fin-ops-core/fin-ops/data-entities/use-record-template-new-record.md) as part of the product import to for example get the mandatory reference fields assigned: -->

- **Item model groups** – Each released product must be assigned to an item model group in Supply Chain Management. Therefore, at least one group must be available. The group can control business processes for batch-tracked items. The following settings are recommended for every item model group that's used with Warehouse management only mode. These settings eliminate the need to set up any costing data for the products.

    - **Inventory model** – Set this field to *Non-valuated*.
    - **Post physical inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).
    - **Post financial inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).

- **Item groups** – Can be used to group business processes, especially when [product filter codes](filters-and-filter-codes.md) are used. No account setup is required when *Non-valuated* inventory model groups are used.
- **Storage dimension groups** – Enable the use of storage inventory dimensions values such as sites, warehouses, locations, and license plates. Be sure to enable the **Use warehouse management processes** parameter.
- **Tracking dimension groups** – Enable the use of tracking inventory dimensions such as owner, batch, and serial numbers. Note that the *Owner* dimension value must equal the company that a warehouse is associated with. For more information, see [Unsupported processes](wms-only-mode-overview.md#unsupported-processes).
- **Reservation hierarchy** – Defines which dimensions are reserved during the outbound shipment order reservation process. Dimensions that are put below the *Location* dimension are controlled by the warehouse management processes.
- **Units** – Each quantity that a warehouse process handles must be associated with a unit. When multiple units (such as each, box, and/or pallet) are used for an item, be sure to define the *inventory unit* as the smallest unit for the item.
- **Unit sequence groups** – Define the sequence of units that can be used in warehouse operations. For more information about the required setup, see [Unit of measure and stocking policies](unit-measure-stocking-policies.md).

> [!NOTE]
> The messages that create product master data use the [*product data entities*](../pim/data-entities.md). These entities can be used by themselves, or they can be used to maintain product master data.

### Test creating products by using messages

You can try to submit messages to create products by using [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test.md#query-odata-by-using-postman).

If you want, you can create a *fork* of the [Postman environment and collection examples](https://go.microsoft.com/fwlink/?linkid=2250135). Be sure to select the environment and fill in the correct environment variables before you run the `CREATE TOKEN VARIABLE` collection.

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

Several out-of-box business events are supported for warehouse integration. The following table lists some of them.

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

At a minimum, we recommend that you use the following business events:

- `InventCountingJournalPostedBusinessEvent` – This event announces that an on-hand inventory adjustment has occurred and indicates where detailed information about the update can be found.
- `WHSSourceSystemInventoryOnhandReportBusinessEvent` – This event announces that an on-hand inventory report has been generated and indicates where detailed information about the update can be found.
- `WHSShipmentPackingSlipJournalModifiedBusinessEvent` – This event announces that an outbound shipment confirmation process has occurred and indicates where the detailed dispatch advice data can be found. (This data can be used for a sales invoicing process, for example.)
- `WHSShipmentReceivingJournalModifiedBusinessEvent` – This event announces that an inbound receiving completion process has occurred and indicates where the detailed receiving advice data can be found. (This data can be used for a purchase order invoicing process, for example.)

## On-hand inventory updates between systems

The following illustration shows the internal processes that are used for Warehouse management only mode.

:::image type="content" source="media/wms-only-internal-wom-process.svg" alt-text="Internal process for Warehouse management only mode." lightbox="media/wms-only-internal-wom-process.svg":::

The **Warehouse management** module uses the [counting journal](../inventory/inventory-journals.md#counting) to support multiple on-hand inventory update processes. For more information about the counting process, see [Cycle counting](cycle-counting.md).

As part of the journal posting process, Supply Chain Management triggers a business event, and external systems can read about the updates through the [counting journal entities](/common-data-model/schema/core/operationscommon/entities/supplychain/inventoryandwarehousemanagement/inventinventorycountingjournallineentity). It's important to act only on the updated quantities, to avoid becoming out of sync because of the updates. The following scenario provides an example.

## Example scenario: Updating on-hand inventory between systems

At the start of this scenario, on-hand information about item number A0001 is in sync between the external ERP system and the Supply Chain Management warehouse management system (WMS), as shown in the following table.

| Item number | ERP on-hand | WMS on-hand |
|-------------|-------------|-------------|
| A0001       | 0 pcs       | 0 pcs       |

The following subsections show how different events cause these values to change.

### On-hand update 1

Supply Chain Management receives 10 pcs of item number A0001 against an inbound shipment order without *receiving completed* processing. Therefore, the external system isn't yet informed about this update. As a result, the external system and Supply Chain Management are now out of sync, as shown in the following table.

| Item number | ERP on-hand | WMS on-hand |
|-------------|-------------|-------------|
| A0001       | 0 pcs       | 10 pcs      |

### On-hand update 2

In Supply Chain Management, an on-hand adjustment (counting journal) is posted for item A0001 and adds 1 pcs of on-hand inventory. The following table shows the result.

| Item number | ERP on-hand | WMS on-hand |
|-------------|-------------|-------------|
| A0001       | 0 pcs       | 11 pcs      |

The external system is informed about the on-hand adjustment via a business event. As part of this process, the journal posting is changed from 10 pcs to 11 pcs in Supply Chain Management. The external system considers only the updated quantity of 1 pcs. The following table shows the result.

| Item number | ERP on-hand | WMS on-hand |
|-------------|-------------|-------------|
| A0001       | 1 pcs       | 11 pcs      |

### On-hand update 3

Supply Chain Management runs a *receiving completed* process that's related to the received 10 pcs of item number A0001. Therefore, the external system is informed via a business event. It then reads the shipment receipt information and updates its on-hand quantity with an additional 10 pcs. The following table shows the result.

| Item number | ERP on-hand | WMS on-hand |
|-------------|-------------|-------------|
| A0001       | 11 pcs      | 11 pcs      |

> [!NOTE]
> Make sure that each of your items is assigned to an item model group that's configured as described in the [Master data](#master-data) section. In this way, you don't have configure [inventory postings](../../finance/general-ledger/inventory-posting.md) and [fiscal calendars](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md) when you make adjustments via the [counting journal](../inventory/tasks/define-inventory-counting-processes.md).

## On-hand inventory reconciliation

Warehouse management only mode can generate data for an on-hand inventory reconciliation process when you generate a **Create source system on-hand inventory** report (at **Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Create source system on-hand inventory report**).

To create the header and line data, you must specify **Source system** and **As of date** values. You must also select the level of inventory dimensions that the report should be generated for.

When inventory that's related to *inbound shipment orders* is received, the on-hand inventory is physically updated based on the status of the registered inventory transactions. When inventory is shipped via *outbound shipment orders*, the physical on-hand inventory is reduced based on the `Picked` inventory transactions. This physical inventory on-hand representation of the registered and picked items remains until the related *Shipment receipt* and *Shipment packing slip* journals are posted as part of the [background finalization processes](wms-only-mode-setup.md#background-processes). To include this part of the physical on-hand inventory in the export, be sure to enable the **Include Registered and Picked inventory quantities** parameter.

The external system will be informed about the available data via the `WHSSourceSystemInventoryOnhandReportBusinessEvent` business event. It can read the data via the `WarehouseInventoryOnhandReports` and `WarehouseInventoryOnhandReportLines` data entities.

> [!TIP]
> If you run the **Create source system on-hand inventory** report as a recurring batch job, the **As of date** value is ignored, and data is generated based on the current processing date. For example, you set up the recurrence so that it has a **Start date** value of yesterday, and you set the job to run once per day. In this case, every day, the batch job automatically generates on-hand inventory data for the previous day.

## Warehouse inventory update logs

For integrations that require very quick on-hand inventory synchronization processes, you can use the Warehouse inventory update log (at **Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Warehouse inventory update log**). This log can collect all the inventory transaction updates that lead to on-hand updates that are of interest for the external systems. For example, you might have an external system that handles information about inventory status changes.

To keep the external systems updated about inventory transactions updates that are related to inbound and outbound shipment orders, enable the **Source systems** **Enable warehouse inventory update logs** parameter for both inbound and outbound shipment orders.

> [!IMPORTANT]
> Be sure to uptake the updates in the external systems in such a way that they don't cause double updates in combination with the data that's used as part of the [*Shipment receipts*](wms-only-mode-using.md#shipment-receipts) and [*Shipment packing slips*](wms-only-mode-using.md#shipment-packing-slips) messages when the **Enable warehouse inventory update logs** parameter is enabled.

By default, the *Publish warehouse inventory update log updates* background process is set to run every 10 minutes. It creates data that external systems can consume by using the `WarehouseInventoryUpdateLogs` entity. The `WHSInventoryUpdateLogBusinessEvent` business event can be used as part of this process.
