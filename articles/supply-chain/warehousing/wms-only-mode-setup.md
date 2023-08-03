---
title: Enable and configure warehouse management only mode
description: XXXX
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

# Enable and configure warehouse management only mode

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

## <a name="feature-management"></a>Turn on warehouse only mode

To use the **Warehouse management only mode** capability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.

- The feature that's named **(Preview) Warehouse management only mode** must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## <a name="source-systems"></a>Configure you source systems

With the feature enabled you can open the **Warehouse management > Setup > Warehouse management integration > Source systems** used to define the integration systems. To enable all the functionalities, you must at least insert one record into this entity.

The **Warehouse management only mode** shipment order integration must be configured with information about the source systems going to provide inbound and outbound order messages. You can make this configuration on the **Warehouse management > Setup > Warehouse management integration > Source systems** page, and this configuration is required to make it possible to view the **Inbound shipment orders** and **Outbound shipment orders** and the related processes around the inbound shipment.

The **Source system** name must be identical with the name in the provided message before a message can be accepted getting imported into Supply Chain Management. Other settings can be used as part of the **Source systems** page to control the shipment order import processes, for example it's possible to define **Message value mapping** for item and warehouse identifications and define if loads for inbound shipment orders are automatically created as part of the **Inbound shipment order policies** definition.

> [!NOTE]
> When mapping the items to [**Bar codes**](../pim/tasks/create-bar-code-product.md) remember to enable the *Scanning* setting for the bar codes. For product variants it is only the "ItemNumber" field being used from the order line messages when using **Message value mapping** for the items.

## Set up automatic release of outbound shipment orders

To enable automatic release to warehouse, you can use the **Warehouse management > Release to warehouse > Automatic release of outbound shipment orders** batch job process. For more information, see [Release to warehouse](release-to-warehouse-process.md).

## Set up master data and business events

<!-- KFM: Add a short summary about setting up sync of master/product data. Refer to data topic. -->