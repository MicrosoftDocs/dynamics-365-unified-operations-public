---
title: Release to warehouse
description: This topic provides details about the release to warehouse process. It describes entities that are created when you release an order to the warehouse and options that are available for users to initiate release to warehouse process.
author: mirzaab
ms.date: 8/13/2021
ms.topic: article
ms.search.form: WHSReleaseToWarehouse, WHSReleaseToWarehouseSalesOrder, WHSReleaseToWarehouseTransferOrder, WHSLoadPlanningWorkbench, WHSWaveTemplateTable, WHSWorkTemplateTable, WHSLocDirTable 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-08-13
ms.dyn365.ops.version: 10.0.20
---

# Release to warehouse

[!include [banner](../../includes/banner.md)]

This topic provides details about the release to warehouse process. It describes entities that are created when you release an order to the warehouse and options that are available for users to initiate release to warehouse process.

## Release to warehouse overview

Release to warehouse is a process of making an inventory ready for dispatch processing.

When you release an order to a warehouse, the system creates load lines and shipments. If automatic wave processing is set up, loads and required work are also created. The configuration of entities in question depends on the system settings. Let us review entities that are created during the release to warehouse process and system settings that define them.

A *shipment* is a group of sales or transfer order lines for the same customer or for the same delivery address.

A *load* is a group of sales or transfer order lines grouped together and typically going out on a single truck, rail car, or other mode of transport. A load can have one or many shipments. It is possible to create a load manually by adding order lines to a new load. In this case, order lines are assigned to the load before the release to warehouse process is initiated and can be released only from the **Load planning workbench** page.

Warehouse *work* is any warehouse operation performed by a warehouse worker. Typically, warehouse work operations consist of at least two consecutive actions: a warehouse worker picks up on-hand inventory in one location and then puts the picked inventory away in another location.

When orders are released to the warehouse, the system creates load lines and groups them into shipments. The shipment consolidation process allows for automated shipment consolidation during the release to warehouse process. For more information, see [Shipment consolidation policies](about-shipment-consolidation-policies.md).

The system uses *waves* to create picking work and loads for shipment. A *wave template* must be available for the type of wave you want to create and for the warehouse of the order line. Wave templates of type *Shipping* are used for shipping items for sales orders and transfer orders. Each wave template contains *wave methods*, which perform actions such as creating work for the wave or creating loads. For example, a wave template for shipping waves can contain methods for creating loads, allocating lines to waves, replenishment, and creating picking work for the wave. The wave template establishes settings for how the wave will be generated and processed, including which steps must be done manually and which are done automatically. For more information, see [Wave templates](wave-templates.md).

Therefore, depending on your wave template configuration, a wave can be automatically created, processed, and released at the time you release an order to warehouse, or you can set up the wave template to perform some or all actions manually after release to warehouse is done.  

When a wave is processed, the system creates picking work based on the suitable *work template* and *location directive* and makes the work available on mobile devices. Work templates determine how the work is performed for each warehouse process, and the location directive specifies the pick and put locations for inventory movement. For more information, see [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md).

It is important to note that waves are processed in batch by default.

During wave processing, the system usually creates a new load for each shipment that no load is assigned to.

> [!NOTE]
> If you want the system to assign unassigned shipments to existing loads instead of creating a new loads, you could use the advanced wave load building functionality. For more information, see [Advanced load building during wave](advanced-load-building-during-wave.md).

You can review entities created for the order lines during release to warehouse process directly from the **Sales orders** or **Transfer orders** page.

- On the **Sales orders** page, in the **Sales order lines** FastTab, select **Warehouse > Shipment details**, **Warehouse > Load details** or **Warehouse > Work details** on the toolbar to open related shipments, loads, or work details respectively.
- On the **Sales orders** page, on the **Line details** FastTab, select the **Load** tab to review related loads.
- On the **Transfer orders** page, open the **Ship** tab on the Action Pane and then select **Shipment details** or **Load details** to open related shipments or loads. Or select the **Work details** button on the **Transfer order lines** FastTab toolbar to open related works.

To conclude, the most automated flow when releasing an order to the warehouse works as follows:

1. The system creates a shipment for the order and a wave.
1. The wave is processed.
1. The system creates a load and a work ID.

Depending on wave templates, work templates, and location directives settings, some steps inside the flow may become manual but the overall flow would remain the same.

There are several options how you can release an order to the warehouse. You can perform the operation manually or set up a batch job. Let us review in detail how you can perform release to warehouse operation.

## Manually release to warehouse from the Sales orders and Transfer order pages

You can release an order to the warehouse directly from the **Sales orders** page or the **Transfer orders** page using the **Release to warehouse** button that is located on the **Warehouse** tab and the **Ship** Action Pane tab, respectively. It is possible to release several sales orders simultaneously from the **Sales orders** page.

## Manually release to warehouse from the release to warehouse pages

The system currently provides three pages that let you review and release lines for multiple orders to the warehouse:

- **Warehouse management \> Release to warehouse \> Release to warehouse** – Allows you work with both sales orders and transfer orders, but provides slower performance compared to the other two pages. This page will soon be deprecated
- **Warehouse management \> Release to warehouse \> Release sales orders to warehouse** – Allows you work with sales orders only, but provides better performance than the **Release to warehouse** page.
- **Warehouse management \> Release to warehouse \> Release transfer orders to warehouse** – Allows you work with transfer orders only, but provides better performance than the **Release to warehouse** page.

Each of these pages provides similar functionality, as described in the remainder of this section. Each allows you to pick order lines or entire orders and then release them to the warehouse.

Each of these pages consists of an upper section, where you can select order lines, and a lower section, where you can initiate the release to warehouse operation. You can use filters in the upper section of the page to search for the sales order lines that you want to release.The upper section of the **Release to warehouse** page provides tabs for viewing **Sales orders** and **Transfer orders**, respectively, while each of the other pages shows just one of these two types of orders.

To select order lines for release to warehouse operation, select one or more order lines in the upper section and then select one of the following buttons in the upper section toolbar:

- **Add** – To add the selected order lines to the lower section.
- **Add all** – To add all lines from the upper tab to the lower section.
- **Add order** – To add all lines from a selected order to the lower section.

After adding lines to the lower section of the page, mark each of these lines you want to release and then select **Release to warehouse** on the lower section toolbar to release those lines to the warehouse.

## Manual release to warehouse from the Load planning workbench page

A further option to manually release orders to the warehouse is by using the **Load planning workbench** page. This page allows you to organize order lines into loads and then release loads to the warehouse.

The **Load planning workbench** page is located under **Warehouse management > Loads** in the navigation pane and can also be accessed through the **Sales orders** and **Transfer orders** pages. In the upper section of the page, you can select sales order lines (on the **Sales lines** tab) and transfer order lines (on the **Transfer lines** tab) and add them to a new or existing load.

To add order lines to a load, select the relevant lines in the upper grid. Then open the **Supply and demand** tab on the Action Pane and select one of the following buttons:

- **To new load** – To create a new load and add the marked order lines to it.
- **To existing load** – To add the marked order lines to an existing load.
- **Entire order to new load** – To create a new load and add all lines from the marked orders to it.
- **Entire order to existing load** – To add all lines from the marked order to an existing load.

You can review created loads in the lower section of the **Load planning workbench** page. To release loads to the warehouse, mark the required loads and select **Release > Release to warehouse** from the lower section toolbar. Since loads are already assigned to order lines, as a result of release to warehouse operation, the system will create shipments and work IDs provided you are using automatic wave processing.

## Automatic release to warehouse

To automatically release orders to the warehouse, use the **Automatic release of sales orders** and **Automatic release of transfer orders** procedures.  

To set up the batch job for releasing sales orders, follow these steps.

1. Go to **Warehouse management > Release to warehouse > Automatic release of sales orders**.
1. The **Automatic release of sales orders** dialog opens. On the **Parameters** FastTab, make the following settings:

    - **Quantity to release** – Select whether the whole quantity or the physically reserved quantity should be released.
    - **Allow release of partially released orders** – Specify whether remaining quantities for partially released orders should be released to warehouse.
    - **Keep reservations on release failure** – Specify whether quantities that were reserved automatically for a sales order should remain reserved when release to warehouse fails.
    - **Locked order handling** – Select how to handle sales orders that are currently locked because they are being edited by other users or processes. The following options are available:
        - *Wait for orders to unlock* – The system will wait for the orders to become unlocked before releasing them to the warehouse. The release to warehouse process may take more time to complete in this case.
        - *Skip locked orders* – The system will skip locked orders.
    - **Valid order types** – Select which types of sales orders to be included into the batch.
    - **Credit limit type** – Choose whether to perform credit limit checks during release to warehouse and which transaction information to include when the credit limit is checked.

1. To control which orders should be processed, select the **Filter** button on the **Records to include** FastTab. A standard query dialog appears, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, choose whether to run the job in batch mode and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and initiate the release to warehouse process.

To set up the batch job for releasing transfer orders, follow the steps.

1. Go to **Warehouse management > Release to warehouse > Automatic release of transfer orders**.
1. The **Automatic release of sales orders** dialog opens. On the **Parameters** FastTab, set the following fields.

    - **Quantity to release** – Select whether the whole quantity or the physically reserved quantity should be released.
    - **Allow release of partially released orders** – Specify whether remaining quantities for partially released orders should be released to warehouse.
    - **Group releases by destination warehouse** – Specify whether the system should release all transfer orders at once or first group transfer order lines by destination warehouse and then release each group to the warehouse separately.

1. To control which orders should be processed, select the **Filter** button on the **Records to include** FastTab. A standard query dialog appears, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, choose whether to run the job in batch mode and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and initiate the release to warehouse process.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
