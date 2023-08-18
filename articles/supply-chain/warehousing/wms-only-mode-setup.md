---
title: Enable and configure warehouse management only mode
description: Configure Warehouse Management only mode by setting up source systems, master data, and business events.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage
ms.topic: how-to
ms.date: 08/03/2023
audience: Application User
ms.search.region: Global
ms.custom:
  - bap-template
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:08/10/2023
---

# Enable and configure warehouse management only mode

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

## <a name="feature-management"></a>Turn on Warehouse management only mode

To use the **Warehouse management only mode** capability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The feature that's named *(Preview) Warehouse management only mode* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## <a name="source-systems"></a>Configure you source systems

Use the **Source systems** page to set up each external system that you want to integrate with using Warehouse management only mode. To use Warehouse management only mode, you must have at least one record here. To set up a source system, follow these steps:

1. Go to **Warehouse management > Setup > Warehouse management integration > Source systems**.
1. Do one of the following steps:
    - To create a new record, select **New** on the Action Pane.
    - To edit an existing record, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete an existing record, select it on the list pane and then select **Delete** on the Action Pane.
1. In the header of your new or selected record, enter a **Source system** name. The source system must include this name in each message that it sends to Supply Chain Management, and it must match exactly the value specified here.
1. Make other settings as needed to control the shipment order import processes. Tooltip help is provided for each field (hover your mouse pointer over a label to see it).
1. On the Action Pane, select **Save**.
1. On the Action pane, select **Message value mapping** to open a dialog where you can define how items and warehouses are uniquely identified in incoming documents. You can also choose whether loads for inbound shipment orders are automatically created as part of the setup on the **Inbound shipment order policies** FastTab. Tooltip help is provided for each field. Select **OK** when you're done making settings here.

## Set up automatic release of outbound shipment orders

Release to warehouse is the process of making inventory ready for dispatch processing. When you release an order to the warehouse, the system creates load lines and shipments. If automatic wave processing is set up, loads and required work are also created.

If you want to automatically release outbound shipment orders to the warehouse, you must set up a batch job to process the orders on a regular basis. Go to **Warehouse management > Release to warehouse > Automatic release of outbound shipment orders** to set up and schedule the job.

For more information about the release to warehouse process, see [Release to warehouse](release-to-warehouse-process.md).

## <a name="number-sequences"></a>Set up number sequences

If the external system provides order numbers that aren't the same as those used in Supply Chain Management, you must set up [number sequences](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) for *Outbound shipment orders* and *Inbound shipment orders*. Define all the number sequences associated with the **Warehouse management > Setup > Warehouse management parameters > Number sequences** page, which includes the following extra number sequences, which are added for Warehouse Management only mode:

- Outbound shipment order
- Inbound shipment order
- Shipment packing slip
- Shipment receipt
- Warehouse outbound notification ID
- Load line inventory pick

> [!TIP]
> You can quickly enable all number sequences by using the **Generate** option on the [**Number sequences**](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) page.

## Set up mobile device menu items

To enable warehouse workers to use the Warehouse Management mobile app to register inbound shipment transactions, you must set up one or more mobile device menu items that use one following [processes](configure-mobile-devices-warehouse.md#configure-menu-items-to-create-work-for-another-worker-or-process) (each of which requires an inbound load):

- *License plate receiving (and put away)*
- *Load item receiving (and put away)*
- *Mixed license plate receiving (and put away)* (for the source document line identification method *Load item receiving*)
- *Inbound shipment order line receiving* (when assigned to loads)
- *Inbound shipment item receiving* (when assigned to loads)
- *Inbound shipment order line receiving (and put away)* (when assigned to loads)
- *Inbound shipment order item receiving (and put away)* (when assigned to loads)

For more information, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

## Set up master data and business events

To enable Supply Chain Management to exchange meaningful information with an external system, some master and reference data must be synchronized between the two systems (such as released products, item model groups, and countries/regions). You must also set up business events to manage the exchange of information between the two systems. For details about this, see [Exchange data between systems](wms-only-mode-exchange-data.md).
