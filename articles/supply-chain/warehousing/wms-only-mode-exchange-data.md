---
title: Exchange data between systems
description: This topic describes how to exchange data and business events between systems in Warehouse management only mode.
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

<!-- KFM: Preview until further notice -->

Warehouse management only mode requires integration to be set up between external systems and the Supply Chain Management system. The following categories of interactions are needed:

- Document data (such as purchase orders and sales orders)
- Master data (such as product information)
- Progress data (such as receiving, dispatch, and inventory on-hand information)

Many different integration methodologies can be used for these three categories. This article describes the recommended integration process.

## <a name="inbound-outbound-shipment-order-messages"></a>Inbound and outbound shipment order messages

You can use the inbound and outbound shipment order messages to inform Supply Chain Management about which physical inventory to receive and ship. These messages include both header and lines data.

Messages between systems are exchanged using lightweight *inbound shipment order* and *outbound shipment order* documents. These documents eliminate the need to use several other types of documents normally used by Supply Chain Management (such as sales orders, purchase orders, transfer orders, and so on). This will, for example, simplify integration with ERP and order management systems and make Supply Chain Management warehouse management functionality available to a wide variety of external ERP and order management systems.

Inbound shipment order and outbound shipment order messages can be exchanged using [Dataverse](/power-platform/admin/data-integrator.md) or through [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md) using shipment order message entities.

Incoming documents are queued and then processed by the Supply Chain Management [message processor](warehouse-message-processor-messages.md), which ensures consistent data between the systems, both when it comes to master data (like products) and order progress status. Supply Chain Management inbound and outbound shipment orders are therefore prevented from creating or updating invalid or unsupported order data. We recommend that you process the messages as part of a periodic batch job triggered by the [message processor](../supply-chain-dev/message-processor.md) using the *Shipment orders* message queue.

This following image shows how the message processor fits into an integrated system.

:::image type="content" source="media/wms-only-shipment-order-integrations.svg" alt-text="Message processing diagram." lightbox="media/wms-only-shipment-order-integrations.svg":::

## <a name="master-data"></a>Master and reference data

To enable consistent communication, several types of master and reference data must be synchronized and available to both systems. One way to import the required master data to Supply Chain Management is to use its [data entities](../../fin-ops-core/dev-itpro/data-entities/data-entities.md). The following types master and reference data are required:

- **Released products** – This data is required for creating inbound and outbound shipment orders. For more information about how to import product information, see [Product data entities](../pim/data-entities.md) and [Overview of ProductInformationManagement](/common-data-model/schema/core/operationscommon/entities/supplychain/productinformationmanagement/overview).

- **Item model groups** – Each released product must be assigned to an item model group in Supply Chain Management, so you must have at least one group available. Each group that you will use with Warehouse management only mode must have the following settings, which will eliminate the need to set up any costing data for these products:
    - **Inventory model** – Set to *Non-valuated*
    - **Post physical inventory** – Turned off. You you can ony choose this option provided you already set up at least one [source system record](wms-only-mode-setup.md).
    - **Post financial inventory** – Turned off. You you can ony choose this option provided you already set up at least one [source system record](wms-only-mode-setup.md).

- **Countries/regions** – Each [country/region](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) where you do business must be defined in Supply Chain Management. These records are used in outbound shipment orders to create addresses. You'll also need this data to [create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md) for the warehouses. Depending on your [address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md) and the way you use address fields in  order messages, you might need to create additional data before you'll be able to import order messages (for example, to support state and county combinations).

> [!NOTE]
> When you're using the  **Item - bar code** page to map items to [bar codes](../pim/tasks/create-bar-code-product.md), keep the following point in mind:
>
> - For product variants, only the **Item number** field is used from the order line messages when applying message value mappings for an items.
> - Be sure to set **Scanning** to *Yes* for each bar code (this setting is on the **General** tab of the **Item - bar code** page).

## Progress data and business events

External systems can have many different business process requests for the warehouse management system. One example is the progress of a sales order. Each external system could continuously poll for this information, but to honor the process, Supply Chain Management can be set up to deliver [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) when needed.

Business events keep external systems informed about the progress and actions going on in Supply Chain Management. With this setup, the external systems don't need to keep polling for information that might not have changed since the last request, but instead only need to react when informed.

Several out-of-the-box business events are supported for warehouse integration. The following table lists several (but not all) of them.

| Business event ID | Description |
|---|---|
| `InventCountingJournalPostedBusinessEvent` | Counting journal posted |
| `WHSOutboundNotificationCreatedBusinessEvent` | Outbound warehouse notification created |
| `WHSShipmentOrderMessageChangedStatusBusinessEvent` | Status update for shipment order message |
| `WHSShipmentPackingSlipJournalModifiedBusinessEvent` | Shipment packing slips updated |
| `WHSShipmentReceivingJournalModifiedBusinessEvent` | Shipment receipts updated |
| `SysMessageProcessorMessageProcessedBusinessEvent` | Message processor message failure |
| `WhsWaveExecutedBusinessEvent` | Wave executed |

At minimum, we recommend that you use the following business events:

- `InventCountingJournalPostedBusinessEvent` – Announces that an inventory on-hand adjustment has occurred and tells and where to find the detailed information about the update.
- `WHSShipmentPackingSlipJournalModifiedBusinessEvent` – Announces that an outbound shipment confirmation process has occurred and tells and where to find the detailed dispatch advice data (which, for example, can be used for a sales invoicing process).
- `WHSShipmentReceivingJournalModifiedBusinessEvent` – Announces that an inbound receiving completion process has occurred and tells and where to find the detailed receiving advice data (which, for example, can be used for a purchase order invoicing process).

## Inventory on-hand updates between systems

The following illustration shows the internal processes used for warehouse management only mode.

:::image type="content" source="media/wms-only-internal-wom-process.svg" alt-text="Warehouse management only mode internal process." lightbox="media/wms-only-internal-wom-process.svg":::

The Warehouse management module supports multiple inventory on-hand update processes using the [counting journal](../inventory/inventory-journals.md#counting). For more information about the counting process, see [Cycle counting](cycle-counting.md).

As part of the journal posting process, Supply Chain Management triggers a business event and external systems can read about the updates through the [counting journal entities](/common-data-model/schema/core/operationscommon/entities/supplychain/inventoryandwarehousemanagement/inventinventorycountingjournallineentity). It's important to act only on the updated quantities to prevent getting out of sync as a result of the updates. The following scenario provides an example.

## Example scenario of updating on-hand inventory between systems

At the start of this scenario, on-hand information about item number A0001 is in-sync between the external ERP system and the Supply Chain Management warehouse management system (WMS), as shown in the following table.

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |0 pcs       |

The following subsections show how these values change as a result of different events.

### On-hand update #1

Supply Chain Management receives 10 pcs of item number A0001 against an inbound shipment order without *receiving completed* processing. Therefore, the external system isn't yet informed about this. As a result, the external system and Supply Chain Management are now out of sync, as shown in the following table.

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |10 pcs      |

### On-hand update #2

In Supply Chain Management, an on-hand adjustment (counting journal) is posted for item A0001, adding 1 pcs on-hand, which produces the following result.

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |11 pcs      |

The external system is informed via a business event about the on-hand adjustment. As part of this process, the journal posting changes from 10 pcs. to 11 pcs. in Supply Chain Management. The external system only considers the updated quantity of 1 pcs, which produces the following result.

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |1 pcs       |11 pcs      |

### On-hand update #3

Supply Chain Management runs a *receiving completed* process related to the received 10 pcs of item number A0001. As a result, the external system is informed via a business event, so it reads the shipment receipt information and updates its on-hand quantity with an additional 10 pcs, which produces the following result.

|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |11 pcs      |11 pcs      |

> [!NOTE]
> To avoid the need to configure [inventory postings](../../finance/general-ledger/inventory-posting.md) and [fiscal calendars](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md) when making adjustments via the [counting journal](../inventory/tasks/define-inventory-counting-processes.md), make sure that each of your items is assigned to an item model group that is configured as described previously under [Master data](#master-data).
