---
title: Exchange data between systems (preview)
description: This article explains how to exchange data and business events between systems in Warehouse management only mode.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage, WHSConsigner, WHSConsignerGroup, WHSConsignee, WHSConsignerGroup, WHSSourceSystemItem, EcoResStorageDimensionGroup, InventItemGroup, InventModelGroup, EcoResStorageDimensionGroup, EcoResTrackingDimensionGroup, WHSReservationHierarchy, UnitOfMeasure, WHSUOMSeqGroupTable
ms.topic: how-to
ms.date: 08/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Exchange data between systems (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

Warehouse management only mode requires that you set up integration between external systems and the Microsoft Dynamics 365 Supply Chain Management system. The following categories of interactions are required:

- Document data (such as purchase orders and sales orders)
- Master data (such as product information)
- Progress data (such as receiving, dispatch, and on-hand inventory information)

Many different integration methodologies can be used for these three categories. This article describes the recommended integration process.

## <a name="inbound-outbound-shipment-order-messages"></a>Inbound and outbound shipment order messages

You can use inbound and outbound shipment order messages to inform Supply Chain Management about which physical inventory to receive and ship. These messages include both header data and lines data.

Messages between systems are exchanged by using lightweight *inbound shipment order* and *outbound shipment order* documents. These documents eliminate the need to use several other types of documents that Supply Chain Management typically uses (such as sales orders, purchase orders, and transfer orders). Therefore, they have several benefits. For example, they simplify integration with enterprise resource planning (ERP) and order management systems. They also make Supply Chain Management warehouse management functionality available to a wide range of external ERP and order management systems.

Inbound and outbound shipment order messages can be exchanged by using [Dataverse](/power-platform/admin/data-integrator). Alternatively, they can be exchanged through [Open Data Protocol (OData)](../../fin-ops-core/dev-itpro/data-entities/odata.md) by using shipment order message entities and/or by using the [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md) import process (for example, by using `Inbound shipment order messages composite entity` and `Outbound shipment order messages composite entity`).

Supply Chain Management queues the incoming documents and then processes them by using the [message processor](warehouse-message-processor-messages.md). This approach ensures consistent data between the systems: both master data (such as products) and order progress status. Supply Chain Management inbound and outbound shipment orders are therefore prevented from creating or updating invalid or unsupported order data. We recommend that you process the messages as part of a periodic batch job that the [message processor](../supply-chain-dev/message-processor.md) triggers by using the *Shipment orders* message queue.

This following illustration shows how the message processor fits into an integrated system.

:::image type="content" source="media/wms-only-shipment-order-integrations.svg" alt-text="Message processing diagram." lightbox="media/wms-only-shipment-order-integrations.svg":::

## <a name="master-data"></a>Master and reference data

For consistent communication, several types of master and reference data must be synced and available to both systems. One being the product master data, which can easily get imported into Microsoft Dynamics 365 Supply Chain Management via the `Product message`. This message will similar to the shipment orders be validated as part of the message processing and automatically enable the product information linking to a [source system record](wms-only-mode-setup.md#source-systems).

Only one [source system record](wms-only-mode-setup.md#source-systems) can be recorded as the external system maintaining the product master data related to the unique reference for a **Release product/Item number**, this data can be viewed and manually maintained in the **Source system items** page.

> [!TIP]
> The *Source system item number* will be used for the communication between the systems which is useful when for example an external system uses an EAN barcode as the unique identification number linked to a *item/variant number* having a different value.

Additionally you can import the required master data into Supply Chain Management by using [data entities](../../fin-ops-core/dev-itpro/data-entities/data-entities.md). The following types of master and reference data are required to create a **Release product/Item number** going to be used in warehouse management processes. Note that you can apply a [record template](../../fin-ops-core/fin-ops/data-entities/use-record-template-new-record.md) as part of the product import to get the mandatory reference fields assigned:

- **Item model groups** – Each released product must be assigned to an item model group in Supply Chain Management. Therefore, at least one group must be available. The group can control business processes for batch tracked item and it is recommended that each group that you use with Warehouse management only mode have the following settings. These settings eliminate the need to set up any costing data for the products:

    - **Inventory model** – Set this field to *Non-valuated*.

    - **Post physical inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).

    - **Post financial inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).

-  **Item groups** - Can be used to group business processes, especially when using [product filter codes](filters-and-filter-codes). No account setup is needed when using *Non-valuated* inventory model group.

- **Storage dimension groups** - Used to enable the use of storage inventory dimensions values like sites, warehouses, locations, and license plates. Make sure to enable the *Use warehouse management processes* parameter.

- **Tracking dimension groups** - Used to enable the use of tracking inventory dimensions like owner, batch, and serial numbers. Note that the *Owner* dimension support must equal the company a warehouse is associated with, see more [here](wms-only-mode-overview.md#unsupported-processes).

- **Reservation hierarchy** - Used to define which dimensions are getting reserved as part of an outbound shipment order reservation process. Dimensions placed below the *Location* dimension gets controlled by the warehouse management processes.

- **Units** - Every quantity getting handled as part of the warehouse processes must get associated with a *Unit*. When using multiple units like Each, Box, Pallet for an item, make sure to define the *Inventory unit* as the smallest unit for an item.

- **Unit sequence groups** - Used to define the sequence of units that can be used in warehouse operations. You can read more about the needed setup [here](unit-measure-stocking-policies.md).

> [!NOTE]
> The `Product message` uses the [*Product data entities*](../pim/data-entities.md) which of cause can be used isolated as well to maintain the product master data. You can read more about the entities as part of the [Overview of Product Information Management](/common-data-model/schema/core/operationscommon/entities/supplychain/productinformationmanagement/overview).

To [create a new legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md) for the warehouses and import *Outbound shipment orders* you must as well have [**country/region**](../../fin-ops-core/dev-itpro/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) defined in Supply Chain Management. The records are used in outbound shipment orders to create addresses. Depending on your [address setup](../../fin-ops-core/dev-itpro/organization-administration/global-address-book-address-setup.md) and the way that you use address fields in order messages, you might have to create additional data before you can import order messages (for example, to support state/province and county combinations).

### Consigner and consignee information

To easy the warehouse operation setup you can create and use the data for *consigners* and *consignees* and their related group definitions. This could for example be for a setup process related to a [quality order creation process](../inventory/quality-associations.md) for a specific consigner og consigner group.
Note that the *Inbound shipment order policies* as part of the *Source systems* setup nor the inbound shipment order message processing requires the fields for the *Consigner's account number* to exist in the entity for the **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Consigners**. The same "free text" concept exists for the outbound shipment order process related to the *Consigneer's account number*.

## Progress data and business events

External systems can have many different business process requests for the warehouse management system. For example, each external system can continuously poll for the progress of a sales order. To honor the process, Supply Chain Management can be set up to deliver [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) as required. Business events keep external systems informed about the progress and actions that are occurring in Supply Chain Management. When this setup is in place, the external systems don't have to continue to poll for information that might not have changed since the last request. Instead, they can react only when they're informed.

Several out-of-box business events are supported for warehouse integration. The following table lists some of them.

| Business event ID | Description |
|---|---|
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

When inventory related to *Inbound shipment orders* gets received the inventory on-hand gets physically updated based on the status of the `Registered` inventory transactions and when inventory gets shipped via *Outbound shipment orders* the physical inventory on-hand gets reduced base on the `Picked` inventory transactions. This physical inventory on-hand representation of the `Registered` and `Picked` items will remain until the related `Shipment receipt` and `Shipment packing slip` journals gets posted as part of the [background finalization processes](wms-only-mode-setup.md#background-processes). To include this part of the physical inventory on-hand for the export, make sure to enable the setting *Include Registered and Picked inventory quantities*.

The external system will be informed about the available data via the `WHSSourceSystemInventoryOnhandReportBusinessEvent` business event. It can read the data via the `WarehouseInventoryOnhandReports` and `WarehouseInventoryOnhandReportLines` data entities.

> [!TIP]
> If you run the **Create source system on-hand inventory** report as a recurring batch job, the **As of date** value is ignored, and data is generated based on the current processing date. For example, you set up the recurrence so that it has a **Start date** value of yesterday, and you set the job to run once per day. In this case, every day, the batch job automatically generates on-hand inventory data for the previous day.

## Warehouse inventory update logs

For integrations that require very quick on-hand inventory synchronization processes, you can use the **Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Warehouse inventory update log**. This log can collect all the inventory transaction updates that lead to on-hand updates that are of interest for the external systems. For example, you might have an external system that handles information about inventory status changes.

To keep the external systems updated about inventory transactions updates related the inbound and outbound shipment orders, make sure to enable the *Source systems* parameter *Enable warehouse inventory update logs* for both inbound and outbound shipment orders.

> [!NOTE]
> Make sure uptake the updates in the external systems in a way not resulting in double updates in combination with the data used as part of the [*Shipment receipts*](wms-only-mode-using.md#shipment-receipts) and [*Shipment packing slips*](wms-only-mode-using.md#shipment-packing-slips) messages when have *Enable warehouse inventory update logs* activated.

By default, the *Publish warehouse inventory update log updates* background process is set to run every 10 minutes. It creates data that external systems can consume by using the `WarehouseInventoryUpdateLogs` entity. The `WHSInventoryUpdateLogBusinessEvent` business event can be used as part of this process.
