---
title: Enable and configure Warehouse management only mode
description: This article explains how to configure Warehouse management only mode by setting up source systems, master data, and business events.
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

# Enable and configure Warehouse management only mode

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

## <a name="feature-management"></a>Turn on Warehouse management only mode

To use the Warehouse management only mode capability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The feature that's named *(Preview) Warehouse management only mode* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## <a name="source-systems"></a>Configure your source systems

Use the **Source systems** page to set up each external system that you want to use Warehouse management only mode to integrate with. To use Warehouse management only mode, you must have at least one record on this page. To set up a source system, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**.
1. Follow one of these steps:

    - To create a new record, select **New** on the Action Pane.
    - To edit an existing record, select it in the list pane, and then select **Edit** on the Action Pane.
    - To delete an existing record, select it in the list pane, and then select **Delete** on the Action Pane.

1. On the header of the new or selected record, enter a name for the source system. The source system must include this name in each message that it sends to Supply Chain Management, and the name in the message must exactly match the value that you specify here.
1. Configure other settings as required to control the shipment order import processes. Tooltip help is provided for each field. Hover your mouse pointer over a field's label to view the tooltip.
1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Message value mapping** to open a dialog box where you can define how items and warehouses are uniquely identified in incoming documents. You can also specify whether loads for inbound shipment orders are automatically created as part of the setup on the **Inbound shipment order policies** FastTab. Tooltip help is provided for each field. When you've finished configuring settings in the dialog box, select **OK**.

### Background processes  
As part of the [Source system](#source-systems) creation process the following [automations background processes](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) will automatically get created:
- Post shipment packing slips - Used for the outbound shipment order finalization process (the repeat interval will default to 10 min. when setting the _Shipment packing slips posting delay_ to 1 day)
- Post shipment receipts - Used for the inbound shipment order finalization process (the repeat interval will default to 10 min. when setting the _Shipment receipts posting delay_ to 1 day)
- Process shipment order messages - Used for the message processing of the inbound and outbound shipment orders (the repeat interval defaults to 1 min.)

## Set up automatic release of outbound shipment orders

*Release to warehouse* is the process of making inventory ready for dispatch processing. When you release an order to the warehouse, the system creates load lines and shipments. If automatic wave processing is set up, loads and required work are also created.

If you want to automatically release outbound shipment orders to the warehouse, you must set up a batch job to process the orders on a regular basis. Go to **Warehouse management** \> **Release to warehouse** \> **Automatic release of outbound shipment orders** to set up and schedule the job.

For more information about the *release to warehouse* process, see [Release to warehouse](release-to-warehouse-process.md).

## <a name="number-sequences"></a>Set up number sequences

If the order numbers that the external system provides don't match the order numbers that are used in Supply Chain Management, you must set up [number sequences](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) for outbound shipment orders and inbound shipment orders. Define all the number sequences that are associated with the **Number sequences** page (**Warehouse management** \> **Setup** \> **Warehouse management parameters** \> **Number sequences**). These number sequences include the following extra number sequences that are added for Warehouse Management only mode:

- *Outbound shipment order*
- *Inbound shipment order*
- *Shipment packing slip*
- *Shipment receipt*
- *Warehouse outbound notification ID*
- *Load line inventory pick*

> [!TIP]
> You can quickly enable all number sequences by using the **Generate** option on the [**Number sequences**](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) page.

## Set up mobile device menu items

To enable warehouse workers to use the Warehouse Management mobile app to register inbound shipment transactions, you must set up one or more mobile device menu items that use one of the following [processes](configure-mobile-devices-warehouse.md#configure-menu-items-to-create-work-for-another-worker-or-process). (Each of these processes requires an inbound load.)

- *License plate receiving (and put away)*
- *Load item receiving (and put away)*
- *Mixed license plate receiving (and put away)*
- *Inbound shipment order line receiving*
- *Inbound shipment item receiving*
- *Inbound shipment order line receiving (and put away)*
- *Inbound shipment order item receiving (and put away)*

For more information, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

## Set up master data and business events

To enable Supply Chain Management to exchange meaningful information with an external system, some master and reference data must be synced between the two systems. This data includes released products, item model groups, and countries/regions. You must also set up business events to manage the exchange of information between the two systems. For more information, see [Exchange data between systems](wms-only-mode-exchange-data.md).
