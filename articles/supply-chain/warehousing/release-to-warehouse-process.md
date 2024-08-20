---
title: Release to warehouse
description: Learn about the release to warehouse process, which is when you release an order to the warehouse and options that you can use to initiate the process.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 01/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSReleaseToWarehouse, WHSReleaseToWarehouseSalesOrder, WHSReleaseToWarehouseTransferOrder, WHSReleaseToWarehouseOutboundShipmentOrder, WHSLoadPlanningWorkbench, WHSWaveTemplateTable, WHSWorkTemplateTable, WHSLocDirTable, WHSOutboundLoadPlanningWorkbench 
---

# Release to warehouse

[!include [banner](../../includes/banner.md)]

This article provides details about the release to warehouse process. It describes entities that are created when you release an order to the warehouse and options that you can use to initiate the process.

## Release to warehouse overview

Release to warehouse is the process of making inventory ready for dispatch processing. When you release an order to the warehouse, the system creates load lines and shipments. If automatic wave processing is set up, loads and required work are also created. The configuration of the entities that are involved depends on the system settings. This section of the article reviews the entities that are created during the release to warehouse process and the system settings that define them.

A *shipment* is a group of order lines for the same customer/receiver or the same delivery address.

A *load* is a group of order lines that are grouped together, and that typically go out on a single truck, rail car, or other mode of transport. A load can have one or many shipments. You can manually create a load by adding order lines to a new load. In this case, order lines are assigned to the load before the release to warehouse process is initiated. Therefore, they can be released only from the **Outbound load planning workbench** page.

Warehouse *work* is any warehouse operation that is performed by a warehouse worker. Typically, warehouse work operations consist of at least two consecutive actions: a warehouse worker picks up on-hand inventory in one location and then puts it away in another location.

When orders are released to the warehouse, the system creates *load lines* and groups them into shipments. The shipment consolidation process allows for automated shipment consolidation during the release to warehouse process. Learn more in [Shipment consolidation policies overview](about-shipment-consolidation-policies.md).

The system uses *waves* to create picking work and loads for shipment. A *wave template* must be available for the type of wave that you want to create and for the warehouse of the order line. Wave templates of the *Shipping* type are used to ship items for sales orders and transfer orders.

Each wave template contains *wave methods*. Wave methods perform actions such as creating work for the wave or creating loads. For example, a wave template for shipping waves can contain methods for creating loads, allocating lines to waves, replenishment, and creating picking work for the wave. The wave template establishes settings that define how the wave will be generated and processed, which steps must be done manually, and which steps will be done automatically. Learn more in [Wave templates](wave-templates.md). Therefore, depending on the configuration of your wave template, either a wave is automatically created, processed, and released when you release an order to warehouse, or some or all of those actions are manually performed after the release to warehouse is done.

When a wave is processed, the system creates picking work, based on a suitable *work template* and *location directive*, and makes that work available on mobile devices. The work template determines how the work is performed for each warehouse process, and the location directive specifies the pick and put locations for inventory movement. Learn more in [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md).

> [!NOTE]
> By default, waves are processed in batch mode.

During wave processing, the system usually creates a new load for each shipment that no load is assigned to. If you want the system to assign unassigned shipments to existing loads instead, you can use the advanced wave load building functionality. Learn more in [Advanced load building during wave](advanced-load-building-during-wave.md).

On the **Sales orders**, **Transfer orders**, and **Outbound shipment orders** pages, you can review the entities created for order lines during the release to warehouse process.

- **All sales orders** page:

    - On the **Sales order lines** FastTab, select **Warehouse**, and then, on the menu, select **Shipment details** to open related shipments, **Load details** to open related loads, or **Work details** to open related work details.
    - On the **Line details** FastTab, select the **Load** tab to review related loads.

- **Transfer orders** page:

    - On the Action Pane, on the **Ship** tab, select **Shipment details** to open related shipments or **Load details** to open related loads.
    - On the **Transfer order lines** FastTab, select **Work details** to open related work details.

- **Outbound shipment orders** page:

    - On the **Outbound shipment order lines** FastTab, select **Warehouse**, and then, on the menu, select **Shipment details** to open related shipments, **Load details** to open related loads, or **Work details** to open related work details.

In conclusion, when an order is released to the warehouse, the most automated flow works in the following way:

1. The system creates a shipment for the order and a wave.
1. The wave is processed.
1. The system creates a load and a work ID.

Depending on wave templates, work templates, and location directives settings, some steps in this flow might become manual. However, the overall flow remains the same.

You have several options for how you release an order to the warehouse. You can perform the operation manually, or you can set up a batch job. The remaining sections of this article review, in detail, the various ways that you can perform a release to warehouse operation.

## Manual release to the warehouse from the Sales orders, Transfer orders, and Outbound shipment orders pages

You can release an order to the warehouse directly from the **Sales orders**, **Transfer  orders**, or **Outbound shipment orders** page, by selecting **Release to warehouse**.

- On the **Sales orders** page, the button is on the **Warehouse** tab of the Action Pane.
- On the **Transfer orders** page, the button is on the **Ship** tab of the Action Pane.
- On the **Outbound shipment orders** page, the button is on the **Warehouse** tab of the Action Pane.

While you're viewing the list pages, you can select multiple records. In this way, you can release several orders simultaneously.

## Manual release to the warehouse from the Release to warehouse pages

The system provides pages where you can review lines for multiple orders and release them to the warehouse:

- **Release sales orders to warehouse** (**Warehouse management \> Release to warehouse \> Release sales orders to warehouse**) – This page lets you work with sales orders only. However, it provides better performance than the **Release to warehouse** page.
- **Release transfer orders to warehouse** (**Warehouse management \> Release to warehouse \> Release transfer orders to warehouse**) – This page lets you work with transfer orders only. However, it provides better performance than the **Release to warehouse** page.
- **Release outbound shipment orders to warehouse** (**Warehouse management \> Release  outbound shipment orders to warehouse \> Release to warehouse**) – This page lets you work with outbound shipment orders only.
- **Release to warehouse** (**Warehouse management \> Release to warehouse \> Release to warehouse**) – This page lets you work with both sales orders and transfer orders. However, it provides slower performance than the pages that handle specific order types. This page will soon be deprecated.

All the pages provide similar functionality, as described in the rest of this section. All of them let you select order lines or whole orders, and then release them to the warehouse.

Each of the pages consists of an upper section, where you can select order lines, and a lower section, where you can initiate the release to warehouse process. You can use filters in the upper section to search for the order lines that you want to release. The **Release to warehouse** page provides a separate tab for sales orders and transfer orders in the upper section, whereas each of the specific pages shows just one type of order.

The toolbar in the upper section includes the following buttons that you can use to select order lines to release to the warehouse:

- **Add** – Select one or more order lines in the upper section, and then select this button to those lines to the lower section.
- **Add all** – Add all lines from the upper section to the lower section.
- **Add order** – Select an order, and then select this button to add all lines from that order to the lower section.

After you've finished adding lines to the lower section, mark each line that you want to release. Then select **Release to warehouse** on the toolbar to release those lines to the warehouse.

## Manual release to the warehouse from the Outbound load planning workbench page

You can also manually release orders to the warehouse by using the **Outbound load planning workbench** page. This page lets you organize order lines into loads and then release those loads to the warehouse.

To open the **Outbound load planning workbench** page, go to **Warehouse management \> Loads**. You can also open it from the **Sales orders**, **Transfer orders**, and **Outbound shipment orders** pages. In the upper section of the page, you can select to view the following information:

- Shipments
- Sales lines
- Transfer lines
- Outbound shipment order lines
- Transportation request lines (To view this information, you must enable [*In transit planning*](/dynamicsax-2012/appuser-itpro/set-up-transportation-parameters#set-up-general-transportation-parameters).)

On each tab, select lines, and then add them to a new or existing load.

The **Supply and demand** tab on the Action Pane includes the following buttons that you can use to add order lines in the upper section to a load:

- **To new load** – Select order lines in the upper section, and then select this button to create a new load and add those lines to it.
- **To existing load** – Select order lines in the upper section, and then select this button to add those lines to an existing load.
- **Entire order to new load** – Select orders, and then select this button to create a new load and add all lines from those orders to it.
- **Entire order to existing load** – Select an order, and then select this button to add all lines from that order to an existing load.

In the lower section, you can review the loads that are created. To release loads to the warehouse, select them, and then select **Release \> Release to warehouse** on the toolbar. If you're using automatic wave processing, because loads are already assigned to order lines, the system creates shipments and work IDs when the release to warehouse operation is performed.

## Automatic release to the warehouse

To automatically release orders to the warehouse, use the **Automatic release of sales orders**, **Automatic release of transfer orders**, and **Automatic release of outbound shipment orders** jobs.

To set up the batch job that releases sales orders, follow these steps.

1. Go to **Warehouse management \> Release to warehouse \> Automatic release of sales orders**.
1. In the **Automatic release of sales orders** dialog box, on the **Parameters** FastTab, set the following fields:

    - **Quantity to release** – Select whether the whole quantity (*All*), only the physically reserved quantity (*Physically reserved*), or only the physically reserved and cross dock quantity (*Reserved physically and cross dock*) should be released to the warehouse.
    - **Allow release of partially released orders** – Specify whether remaining quantities for partially released orders should be released to the warehouse.
    - **Keep reservations on release failure** – Specify whether quantities that were automatically reserved for a sales order should remain reserved if the release to warehouse process fails.
    - **Group releases by customer** – Specify whether the system should process release to warehouse operations separately for each customer or release all sales orders at the same time. When this option is set to *Yes*, the system will collect all the sales order lines for a selected customer, release those orders to the warehouse, and then process the next customer. When this option is set to *No*, the system will release all available sales order lines in a single release to warehouse operation. By enabling this option, you can help improve the performance and resilience of the release to warehouse process. However, you must be careful when you use this option together with wave templates that are configured to process waves at release to warehouse, because this combination might generate many single-customer waves, each of which has work that has been generated for that customer only. If you want to generate work that combines shipments for multiple customers, you should either turn off the *Group releases by customer* option or configure your wave templates to use postponed processing.
    - **Locked order handling** – Select how the system should handle sales orders that are currently locked because they are being edited by other users or processes:

        - *Wait for orders to unlock* – The system should wait for the orders to become unlocked before it releases them to the warehouse. In this case, the release to warehouse process might take more time.
        - *Skip locked orders* – The system should skip locked orders.

    - **Valid order types** – Select the types of sales orders to include in the batch.
    - **Credit limit type** – Select whether credit limits checks should be done during the release to warehouse process and, if the checks should be done, the transaction information to include in them.

1. To control which orders should be processed, on the **Records to include** FastTab, select **Filter**. A standard query dialog appears, where you can define selection criteria, sorting criteria, and joins. The fields work just as they work for other types of queries in Microsoft Dynamics 365 Supply Chain Management.
1. On the **Run in the background** FastTab, choose whether the job should run in batch mode, and/or set up a recurrent schedule. The fields work just as they work for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and initiate the release to warehouse process.

To set up the batch job that releases transfer orders, follow the steps.

1. Go to **Warehouse management \> Release to warehouse \> Automatic release of transfer orders**.
1. In the **Automatic release of transfer orders** dialog box, on the **Parameters** FastTab, set the following fields:

    - **Quantity to release** – Select whether the whole quantity (*All*), only the physically reserved quantity (*Physically reserved*), or only the physically reserved and cross dock quantity (*Reserved physically and cross dock*) should be released to the warehouse.
    - **Allow release of partially released orders** – Specify whether remaining quantities for partially released orders should be released to the warehouse.
    - **Group releases by destination warehouse** – Specify whether the system should release all transfer orders at the same time, or whether it should group transfer order lines by destination warehouse and then release each group to the warehouse separately.

To set up the batch job that releases outbound shipment orders, follow these steps.

1. Go to **Warehouse management \> Release to warehouse \> Automatic release of outbound shipment orders**.
1. In the **Automatic release of outbound shipment orders** dialog box, on the **Parameters** FastTab, set the following fields:

    - **Quantity to release** – elect whether the whole quantity (*All*), only the physically reserved quantity (*Physically reserved*), or only the physically reserved and cross dock quantity (*Reserved physically and cross dock*) should be released to the warehouse.
    - **Allow release of partially released orders** – Specify whether remaining quantities for partially released orders should be released to the warehouse.

1. To control which orders should be processed, on the **Records to include** FastTab, select **Filter**. A standard query dialog appears, where you can define selection criteria, sorting criteria, and joins. The fields work just as they work for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, choose whether the job should run in batch mode, and/or set up a schedule for recurrence. The fields work just as they work for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and initiate the release to warehouse process.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
