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

## <a name="feature-management"></a>Turn on warehouse only mode

To use the **Warehouse management only mode** capability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The feature that's named *(Preview) Warehouse management only mode* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## <a name="source-systems"></a>Configure you source systems

Use the **Source systems** page to set up each external system that you want to integrate with using Warehouse management only mode. To use Warehouse only mode, you must have at least one record here. To set up a source system, follow these steps:

1. Go to **Warehouse management > Setup > Warehouse management integration > Source systems**.
1. Do one of the following steps:
    - To create a new record, select **New** on the Action Pane.
    - To edit an existing record, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete an existing record, select it on the list pane and then select **Delete** on the Action Pane.
1. In the header of your new or selected record, enter a **Source system** name. The source system must include a this name in each message that it sends to Supply Chain Management, and it must match exactly the value specified here. <!-- KFM: This is pretty light documentation. Maybe we could give a bit more guidance? For example, a short summary of the kinds of settings each FastTab provides. -->
1. Make other settings as needed to control the shipment order import processes. Tooltip help is provided for each field (hover your mouse pointer over a label to see it).
1. On the Action Pane, select **Save**.
1. On the Action pane, select **Message value mapping** to open a dialog where you can set up item and warehouse identifications and define whether loads for inbound shipment orders are automatically created as part of the setup on the **Inbound shipment order policies** FastTab <!-- KFM: I don't really understand this, especially the second part. -->. Tooltip help is provided for each field. Select **OK** when you are done making settings here.

> [!NOTE] <!-- KFM: This note seems out of place. Maybe this belongs in the data topic somewhere? -->
> When you're using the  **Item - bar code** page to map items to [Bar codes](../pim/tasks/create-bar-code-product.md), keep the following point in mind:
>
> - For product variants, only the **Item number** field is used from the order line messages when applying message value mappings for an items. <!-- KFM: I don't understand this. What is an "order line message"? -->
> - Be sure to set **Scanning** to *Yes* for each bar code (this setting is on the **General** tab of the **Item - bar code** page).

## Set up automatic release of outbound shipment orders

Release to warehouse is the process of making inventory ready for dispatch processing. When you release an order to the warehouse, the system creates load lines and shipments. If automatic wave processing is set up, loads and required work are also created. <!-- KFM: I copied this here. Please confirm. -->

If you want to automatically release outbound shipment orders to the warehouse, you must set up a batch job to process the orders on a regular basis. Go to **Warehouse management > Release to warehouse > Automatic release of outbound shipment orders** to set up and schedule the job.

For more information about the release to warehouse process, see [Release to warehouse](release-to-warehouse-process.md).

## Set up master data and business events

<!-- KFM: Add a short summary about setting up sync of master/product data. Refer to data topic. -->

## Set up mobile device menu items

<!-- KFM: Explain what is needed to set up the required mobile device menu items for receiving inventory (list processes) -->
