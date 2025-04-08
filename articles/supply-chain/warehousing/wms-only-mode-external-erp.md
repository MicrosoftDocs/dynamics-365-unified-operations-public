---
title: Warehouse management only mode with external ERP systems
description: Learn how to perform day-to-day warehousing tasks when you use Warehouse only mode to integrate with an external ERP system.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 04/27/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage, WHSInventoryUpdateLog
---

# Warehouse management only mode with external ERP systems

[!include [banner](../includes/banner.md)]

This article explains how to perform day-to-day warehousing tasks when you use Warehouse only mode to integrate with an external enterprise resource planning (ERP) system.

There are numerous ways to use [Warehouse management only mode](wms-only-mode-overview.md). For example, you can enable Microsoft Dynamics 365 Supply Chain Management to handle logistics operations, and then connect warehouses to external ERP systems that do all the order and financial processing.

In addition, the warehouse management processes can use an owner inventory dimension to track the ownership of inventory for items that are shared across source systems.

## High-level implementation example

The following illustration shows an example where Warehouse management only mode is running in the *WOM* Supply Chain Management legal entity. This legal entity handles logistics warehouse operations for an external ERP system that manages order and financial processing.

:::image type="content" source="media/wms-only-erp-integration.svg" alt-text="Diagram that shows Warehouse management only mode with an external ERP system." lightbox="media/wms-only-erp-integration.svg":::

## Inbound process example (external ERP system integration)

The following illustration highlights the elements of the inbound process.

:::image type="content" source="media/wms-only-inbound-wom-process.svg" alt-text="Diagram that shows the inbound process for Warehouse management only mode." lightbox="media/wms-only-inbound-wom-process.svg":::

Here's a high-level description of the inbound process. Steps that start with *ERP* are done by the ERP system. Steps that start with *WOM* are done by Supply Chain Management in Warehouse management only mode.

1. *ERP:* An external system submits an inbound shipment order message to Supply Chain Management.
1. *WOM:* Supply Chain Management processes the message in Warehouse management only mode and creates orders.
1. *WOM:* Inbound loads are created in one of four ways, as established by the [Source systems](wms-only-mode-setup.md#source-systems) settings in Supply Chain Management:

    - Manually, by using the [Inbound load planning workbench](create-or-modify-an-inbound-load.md#create-an-inbound-load-manually)
    - By importing [advanced shipping notices (ASNs)](import-asn-data-entity.md)
    - Automatically during [message processing](../supply-chain-dev/message-processor.md)
    - Automatically during the Warehouse Management mobile app receiving process

1. *WOM:* Warehouse workers use the Warehouse Management mobile app to *register* the inbound shipment transactions.
1. *WOM:* Supply Chain Management runs [receiving completed](wms-only-mode-shared-and-external-detail-use.md#receiving-completed) processes that are related to each relevant load. These processes update the load status to *Received*, generate [shipment receipts](wms-only-mode-shared-and-external-detail-use.md#shipment-receipts), and trigger *business events* for the external systems.
1. *ERP:* The external system reads and uses the [shipment receipt](wms-only-mode-shared-and-external-detail-use.md#shipment-receipts) data for further processing. For example, if purchase orders are associated with the inbound shipment orders in the external system, this processing involves purchase order invoicing.
1. *WOM:* Supply Chain Management finalizes the inbound shipment orders by running the *Post shipment receipts* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

For a more detailed description of this process and the related processes, see [Work with warehouse management only mode in Supply Chain Management](wms-only-mode-shared-and-external-detail-use.md).

## Outbound process example (external ERP system integration)

The following illustration highlights the elements of the outbound process.

:::image type="content" source="media/wms-only-outbound-wom-process.svg" alt-text="Diagram that shows the outbound process for Warehouse management only mode." lightbox="media/wms-only-outbound-wom-process.svg":::

Here's a high-level description of the outbound process. Steps that start with *ERP* are done by the ERP system. Steps that start with *WOM* are done by Supply Chain Management in Warehouse management only mode.

1. *ERP:* An external system submits an outbound shipment order message.
1. *WOM:* Supply Chain Management processes the message in Warehouse management only mode and creates orders.
1. *WOM:* Inventory reservations are created in one of two ways, as established by the [Source systems](wms-only-mode-setup.md#source-systems) settings in Supply Chain Management:

    - Automatically by the [message processor](../supply-chain-dev/message-processor.md)
    - Manually, as part of the release process

1. *WOM:* The orders are released for further warehouse processing, either manually or automatically (via the *Automatic release of outbound shipment orders* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md)).
1. *WOM:* Depending on the setup of your [wave template](wave-templates.md) definitions, warehouse work might be created and released immediately.
1. *WOM:* The outbound warehouse work is processed, and the status of the related outbound shipment order line transactions is updated to *Picked*.
1. *WOM:* The loads are outbound ship confirmed. As a result, *business events* and a [*shipment packing slip*](wms-only-mode-shared-and-external-detail-use.md#shipment-packing-slips) are created for the external system.
1. *ERP:* The external system reads the shipment packing slip and uses its data for further processing (such as sales order invoicing for sales orders that are associated with outbound shipment orders).
1. *WOM:* Supply Chain Management finalizes the outbound shipment order by running the *Post shipment packing slips* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

For a more detailed description of this process and the related processes, see [Work with warehouse management only mode in Supply Chain Management](wms-only-mode-shared-and-external-detail-use.md).

## <a name="on-hand-updates-between-systems"></a>On-hand inventory updates between systems

The following illustration shows the internal processes that are used for Warehouse management only mode.

:::image type="content" source="media/wms-only-internal-wom-process.svg" alt-text="Diagram that shows the internal processes for Warehouse management only mode." lightbox="media/wms-only-internal-wom-process.svg":::

The Warehouse management module uses the [counting journal](../inventory/inventory-journals.md#counting) to support multiple on-hand inventory update processes. For more information about the counting process, see [Cycle counting](cycle-counting.md).

As part of the journal posting process, Supply Chain Management triggers a business event. External systems can read about the updates through the [counting journal entities](/common-data-model/schema/core/operationscommon/entities/supplychain/inventoryandwarehousemanagement/inventinventorycountingjournallineentity). It's important to act only on the updated quantities. Otherwise, the systems can go out of sync because of the updates. The following scenario provides an example.

## Example scenario: Updating on-hand inventory between systems

At the start of this scenario, on-hand information about item number A0001 is in sync between the external ERP system (ERP) and the Supply Chain Management warehouse management system (WMS), as the following table shows.

| Item number | ERP on-hand | WMS on-hand |
|-------------|-------------|-------------|
| A0001       | 0 pcs       | 0 pcs       |

The following subsections show how different events cause these values to change.

### On-hand update 1

Supply Chain Management receives 10 pcs of item number A0001 against an inbound shipment order without running *receiving completed* processing. Therefore, the external system isn't yet informed about this update. As a result, the external system and Supply Chain Management are now out of sync, as the following table shows.

| Item number | ERP on-hand | WMS on-hand |
|-------------|-------------|-------------|
| A0001       | 0 pcs       | 10 pcs      |

### On-hand update 2

In Supply Chain Management, an on-hand adjustment (counting journal) that's posted for item A0001 adds 1 pcs of on-hand inventory. The following table shows the result.

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
> Make sure that each of your items is assigned to an item model group that's configured as described in [Master and reference data](wms-only-mode-exchange-data.md#master-data). In this way, you don't have to configure [inventory postings](../../finance/general-ledger/inventory-posting.md) and [fiscal calendars](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md) when you make adjustments by using the [counting journal](../inventory/tasks/define-inventory-counting-processes.md).

## On-hand inventory reconciliation

Warehouse management only mode can generate data for an on-hand inventory reconciliation process when you generate a **Create source system on-hand inventory** report (**Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Create source system on-hand inventory report**).

To create the header and line data, you must specify **Source system** and **As of date** values. You must also select the level of inventory dimensions that the report should be generated for.

When inventory that's related to inbound shipment orders is received, on-hand inventory is physically updated based on the status of the registered inventory transactions. When inventory is shipped via outbound shipment orders, the physical on-hand inventory is reduced based on the *Picked* inventory transactions. This physical inventory on-hand representation of the registered and picked items remains until the related *Shipment receipt* and *Shipment packing slip* journals are posted as part of the [background finalization processes](wms-only-mode-setup.md#background-processes). To include this part of the physical on-hand inventory in the export, be sure to enable the **Include Registered and Picked inventory quantities** parameter.

The external system is informed about the available data via the `WHSSourceSystemInventoryOnhandReportBusinessEvent` business event. It can read the data via the `WarehouseInventoryOnhandReports` and `WarehouseInventoryOnhandReportLines` data entities.

> [!NOTE]
> If you run the **Create source system on-hand inventory** report as a recurring batch job, the **As of date** value is ignored, and data is generated based on the current processing date. For example, you set up the recurrence so that it has a **Start date** value of yesterday, and you set the job to run once per day. In this case, every day, the batch job automatically generates on-hand inventory data for the previous day.

## <a name="warehouse-inventory-update-logs"></a>Warehouse inventory update logs

For integrations that require very quick on-hand inventory synchronization processes, you can use the Warehouse inventory update log (**Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Warehouse inventory update log**). This log can collect all the inventory transaction updates that lead to on-hand updates that are of interest for the external systems. For example, you might have an external system that handles information about inventory status changes.

To keep the external systems updated about inventory transaction updates that are related to inbound and outbound shipment orders, set the **Enable warehouse inventory update logs** option to *Yes* for the relevant [source systems](wms-only-mode-setup.md#source-systems), for both inbound and outbound shipment orders.

To view the update log, go to **Warehouse management** \> **Inquiries and reports** \> **Physical inventory reconciliation** \> **Warehouse inventory update log**.

> [!IMPORTANT]
> When the **Enable warehouse inventory update logs** option is enabled, be sure to uptake the updates in the external systems in such a way that they don't cause double updates in combination with the data that's used as part of the [*Shipment receipts*](wms-only-mode-shared-and-external-detail-use.md#shipment-receipts) and [*Shipment packing slips*](wms-only-mode-shared-and-external-detail-use.md#shipment-packing-slips) messages.

By default, the *Publish warehouse inventory update log updates* background process is set to run every 10 minutes. It creates data that external systems can consume by using the `WarehouseInventoryUpdateLogs` entity. The `WHSInventoryUpdateLogBusinessEvent` business event can be used as part of this process.
