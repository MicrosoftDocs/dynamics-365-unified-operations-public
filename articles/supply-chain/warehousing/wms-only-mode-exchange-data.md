---
title: Exchange data between systems
description: This article explains how to exchange data and business events between systems in Warehouse management only mode.
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

Warehouse management only mode requires that you set up integration between external systems and the Microsoft Dynamics 365 Supply Chain Management system. The following categories of interactions are required:

- Document data (such as purchase orders and sales orders)
- Master data (such as product information)
- Progress data (such as receiving, dispatch, and on-hand inventory information)

Many different integration methodologies can be used for these three categories. This article describes the recommended integration process.

## <a name="inbound-outbound-shipment-order-messages"></a>Inbound and outbound shipment order messages

You can use inbound and outbound shipment order messages to inform Supply Chain Management about which physical inventory to receive and ship. These messages include both header data and lines data.

Messages between systems are exchanged by using lightweight *inbound shipment order* and *outbound shipment order* documents. These documents eliminate the need to use several other types of documents that Supply Chain Management typically uses (such as sales orders, purchase orders, and transfer orders). Therefore, they have several benefits. For example, they simplify integration with enterprise resource planning (ERP) and order management systems. They also make Supply Chain Management warehouse management functionality available to a wide range of external ERP and order management systems.

Inbound and outbound shipment order messages can be exchanged by using [Dataverse](/power-platform/admin/data-integrator) or through [Open Data Protocol (OData)](../../fin-ops-core/dev-itpro/data-entities/odata.md) by using shipment order message entities.

Supply Chain Management queues the incoming documents and then processes them by using the [message processor](warehouse-message-processor-messages.md). This approach ensures consistent data between the systems: both master data (such as products) and order progress status. Supply Chain Management inbound and outbound shipment orders are therefore prevented from creating or updating invalid or unsupported order data. We recommend that you process the messages as part of a periodic batch job that the [message processor](../supply-chain-dev/message-processor.md) triggers by using the *Shipment orders* message queue.

This following illustration shows how the message processor fits into an integrated system.

:::image type="content" source="media/wms-only-shipment-order-integrations.svg" alt-text="Message processing diagram." lightbox="media/wms-only-shipment-order-integrations.svg":::

## <a name="master-data"></a>Master and reference data

For consistent communication, several types of master and reference data must be synced and available to both systems. One way to import the required master data into Supply Chain Management is to use its [data entities](../../fin-ops-core/dev-itpro/data-entities/data-entities.md). The following types of master and reference data are required:

- **Released products** – This data is required to create inbound and outbound shipment orders. For more information about how to import product information, see [Product data entities](../pim/data-entities.md) and [Overview of ProductInformationManagement](/common-data-model/schema/core/operationscommon/entities/supplychain/productinformationmanagement/overview).
- **Item model groups** – Each released product must be assigned to an item model group in Supply Chain Management. Therefore, at least one group must be available. Each group that you use with Warehouse management only mode must have the following settings. These settings eliminate the need to set up any costing data for the products:

    - **Inventory model** – Set this field to *Non-valuated*.
    - **Post physical inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).
    - **Post financial inventory** – Turn off this option. You can select this option only if you've already set up at least one [source system record](wms-only-mode-setup.md).

- **Countries/regions** – Each [country/region](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) where you do business must be defined in Supply Chain Management. The records are used in outbound shipment orders to create addresses. You also need this data to [create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md) for the warehouses. Depending on your [address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md) and the way that you use address fields in order messages, you might have to create additional data before you can import order messages (for example, to support state/province and county combinations).

> [!NOTE]
> When you're using the **Item - bar code** page to map items to [bar codes](../pim/tasks/create-bar-code-product.md), keep the following points in mind:
>
> - For product variants, only the **Item number** field from the order line messages is used when message value mappings are applied for an item.
> - Be sure to set the **Scanning** option on the **General** tab of the **Item - bar code** page to *Yes* for each bar code.

## Progress data and business events

External systems can have many different business process requests for the warehouse management system. For example, each external system can continuously poll for the progress of a sales order. To honor the process, Supply Chain Management can be set up to deliver [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) as required. Business events keep external systems informed about the progress and actions that are occurring in Supply Chain Management. When this setup is in place, the external systems don't have to continue to poll for information that might not have changed since the last request. Instead, they can react only when they're informed.

Several out-of-box business events are supported for warehouse integration. The following table lists some of them.

| Business event ID | Description |
|---|---|
| `InventCountingJournalPostedBusinessEvent` | Counting journal posted |
| `WHSOutboundNotificationCreatedBusinessEvent` | Outbound warehouse notification created |
| `WHSShipmentOrderMessageChangedStatusBusinessEvent` | Status update for shipment order message |
| `WHSShipmentPackingSlipJournalModifiedBusinessEvent` | Shipment packing slips updated |
| `WHSShipmentReceivingJournalModifiedBusinessEvent` | Shipment receipts updated |
| `SysMessageProcessorMessageProcessedBusinessEvent` | Message processor message failure |
| `WhsWaveExecutedBusinessEvent` | Wave executed |

At a minimum, we recommend that you use the following business events:

- `InventCountingJournalPostedBusinessEvent` – This event announces that an on-hand inventory adjustment has occurred and indicates where detailed information about the update can be found.
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
