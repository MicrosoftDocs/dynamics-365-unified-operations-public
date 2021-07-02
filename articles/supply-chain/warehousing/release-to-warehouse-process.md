---
title: Release to warehouse process
description: This topic provides details about the release to warehouse process. It describes entities that are created when you release an order to the warehouse and options that are available for users to initiate release to warehouse process.
author: mirzaab
ms.date: 7/2/2021
ms.topic: article
ms.search.form: WHSReleaseToWarehouse, WHSReleaseToWarehouseSalesOrder, WHSReleaseToWarehouseTransferOrder, WHSLoadPlanningWorkbench, WHSWaveTemplateTable, WHSWorkTemplateTable, WHSLocDirTable 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-07-02
ms.dyn365.ops.version: 10.0.20
---

# Release to warehouse process

[!include [banner](../../includes/banner.md)]

This topic provides details about the release to warehouse process. It describes entities that are created when you release an order to the warehouse and options that are available for users to initiate release to warehouse process.

## Release to warehouse overview

Release to warehouse is a process of making an inventory ready for dispatch processing. 

When you release an order to a warehouse, the system creates load lines and shipments. And if automatic wave processing is set up, loads and required work are also created. The configuration of entities in question depends on the system setting. Let us review entities that are created during the release to warehouse process and system settings that define them.

 A *shipment* is a group of sales or transfer order lines for the same customer or for the same delivery address.

A *load* is a group of sales or transfer order lines grouped together and typically going out on a single truck, rail car, etc. A load can have one or many shipments. It is possible to create a load manually by adding order lines to a new load. In this case, order lines are assigned to the load before the release to warehouse process is initiated and can be released only from the **Load planning workbench** page.

Warehouse *work* is any warehouse operation performed by a warehouse worker. Typically, warehouse work operations consist of at least two consecutive actions: a warehouse worker picks up on-hand inventory in one location and then puts the picked inventory down in another location. 

When the orders are released to the warehouse, the system creates load lines and groups them into shipments. The shipment consolidation process allows for automated shipment consolidation during release to the warehouse process. For more information, see [Shipment consolidation policies](about-shipment-consolidation-policies.md).

The system uses *waves* to create picking work and load for shipment. A *wave template* must be available for the type of wave you want to create and for the warehouse of the order line. The wave template of *Shipping type* is used for shipping items for sales orders and transfer orders. The wave template contains the *wave methods* that will perform actions such as creating work for the wave or creating loads. For example, the wave template for shipping waves can contain methods for creating loads, allocating lines to waves, replenishment, and creating picking work for the wave. The wave template establishes settings for how the wave will be generated and processed, including which steps must be done manually and which are done automatically. For more information, see [Wave templates](wave-templates.md).

Therefore, depending on the wave template configuration, a wave can be automatically created, processed, and released at the time you release an order to warehouse or you can set up the wave template to perform some or all actions manually after release to warehouse is done.  

When a wave is processed, the system creates the picking work based on the suitable *work template* and *location directive* and makes the work available on mobile devices. Work templates determine how the work is performed for each warehouse process, and the location directive specifies the pick and put locations for inventory movement. For more information, see [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md). 

It is important to note, that waves are processed in batch by default.

During wave processing, the system usually creates a new load for each shipment that no load is assigned to.

> [!NOTE]
> If you want the system to assign unassigned shipments to existing loads instead, you could use Advanced wave load building functionality. For more information, see [Advanced load building during wave](advanced-load-building-during-wave.md).

You can review entities created for the order lines during release to warehouse process directly from the **Sales orders** page or **Transfer orders** page. 

- On the **Sales orders** page, under **Sales order lines** section, select **Warehouse > Shipment details**, **Warehouse > Load details** or **Warehouse > Work details** option to open related shipments, loads, or works respectively.

- On the **Sales orders** page, on the **Line details** FastTab, select **Load** tab to review related loads.

- On the **Transfer orders** page, select the **Shipment details** or the **Load details** button on the **Ship** tab to open related shipments or load. Or select the **Work details** button under the **Transfer order lines** section to open related works.

To conclude, the most automated flow when releasing the order to the warehouse would look like following: the system creates a shipment for the order and a wave, the wave is processed, the system creates a load and a work. Depending on wave templates, work templates and location directives settings, some steps inside the flow may become manual but the overall flow would remain the same.

There are several options how you can release an order to the warehouse. You can perform an operation manually or set up a batch job. Let us review in detail how you can perform release to warehouse operation.

## Manual release to warehouse from the Sales orders and Transfer order page

You can release an order to the warehouse directly from the **Sales orders** page or the **Transfer orders** page using the **Release to warehouse** button that is located on the **Warehouse** tab and the **Ship** tab accordingly. It is possible to release several sales orders simultaneously using the **Sales orders** page.

## Manual release to warehouse from the Release to warehouse page

Another option for manual release to warehouse operation is the **Release to warehouse** page that is located under **Warehouse management > Release to warehouse**. This page allows you to pick order lines or entire orders and then release them to the warehouse. 

The **Release to warehouse** page consists of the upper section where you can select order lines and the bottom section where you can initiate release to warehouse operation. The upper section displays both sales order lines (on the **Sales orders** tab) and transfer order lines (on the **Transfer orders** tab) that are available for release to warehouse. 

To select order lines for release to warehouse operation, use following buttons in the upper section: 

- **Add** button - To select specific order lines;

- **Add all** button - To select all lines from the tab;

- **Add order** button - To select all lines from the marked order. 

Selected lines are displayed in the bottom section of the page. You can then mark all lines or specific lines and use the **Release to warehouse** button to release order lines to the warehouse.

> [!NOTE]
> Due to performance issues, the **Release to warehouse** page will be substituted with following new pages:
> - **Release sales orders to warehouse** page;
>
> - **Release transfer orders to warehouse** page.
>
> New pages provide significantly improved performance in comparison with the **Release to warehouse** page. The **Release to warehouse** page will be deprecated in future.

## Manual release to warehouse from the Release sales orders to warehouse page

You can use the **Release sales orders to warehouse** page to manually release sales orders to the warehouse. This page was introduced as performance efficient substitution to the **Release to warehouse** form. The page is more source-document focused and allows users for better performance experience. 

The **Release sales orders to warehouse** page is located under **Warehouse management > Release to warehouse**. The page allows you to select sales orders and sales order lines and release them to the warehouse. 

The **Release sales orders to warehouse** page consists of the upper section where you can select sales order lines and the bottom section where you can initiate release to warehouse operation. You can use filters in the upper section of the page to search for the sales order lines that you want to release. 

To select sales order lines for release to warehouse operation, use following buttons in the upper section: 

- **Add** button - To select specific sales order lines;

- **Add all** button - To select all lines;

- **Add order** button - To select all lines from the marked sales order. 

Selected sales order lines are displayed in the bottom section of the page. You can then mark all lines or specific lines and use the **Release to warehouse** button to release sales order lines to the warehouse.

## Manual release to warehouse from the Release transfer orders to warehouse page

You can use the **Release transfer orders to warehouse** page to manually release transfer orders to the warehouse. This page was introduced as performance efficient substitution to the **Release to warehouse** form. The page is more source-document focused and allows users for better performance experience. 

The **Release transfer orders to warehouse** page is located under **Warehouse management > Release to warehouse**. The page allows you to select transfer orders and transfer order lines and release them to the warehouse. 

The **Release transfer orders to warehouse** page consists of the upper section where you can select transfer order lines and the bottom section where you can initiate release to warehouse operation. You can use filters in the upper section of the page to search for the transfer order lines that you want to release. 

To select transfer order lines for release to warehouse operation, use following buttons in the upper section: 

- **Add** button - To select specific transfer order lines;

- **Add all** button - To select all lines;

- **Add order** button - To select all lines from the marked transfer order. 

Selected transfer order lines are displayed in the bottom section of the page. You can then mark all lines or specific lines and use the **Release to warehouse** button to release transfer order lines to the warehouse.

## Manual release to warehouse from the Load planning workbench page

A further option to manually release orders to the warehouse is by using the **Load planning workbench** page. This page allows you to organize order lines into loads and then release loads to the warehouse.

The **Load planning workbench** page is located under **Warehouse management > Loads** and can also be accessed through the **Sales orders** and **Transfer orders** pages. In the upper section of the page, you can select sales order lines (on the **Sales lines** tab) and transfer order lines (on the **Transfer lines** tab) and add them to the new or existing load. 

To add order lines to the load, select one of the following buttons:

- **To new load** button - To add marked order lines to new load;

- **To existing load** button - To add marked order lines to existing load;

- **Entire order to new load** button - To add all lines from the marked order to new load;

- **Entire order to existing load** button - To add all lines from the marked order to existing load.

You can review created loads in the bottom section of the **Load planning workbench** page. To release loads to the warehouse, mark required loads and select the **Release > Release to warehouse** button. Since loads already assigned to order lines, as a result of release to warehouse operation, the system will create shipments and works, in case of automatic wave processing.

## Automatic release to warehouse

To automatically release orders to the warehouse, use **Automatic release of sales orders** or **Automatic release of transfer orders** procedures.  

To set up the batch job for releasing sales orders, follow the steps.
1. Go to **Warehouse management > Release to warehouse > Automatic release of sales orders**.
1. In the opened dialog box, on the **Parameters** FastTab, set the following fields.

    - **Quantity to release** - Select whether the whole quantity or the physically reserved quantity should be released.

	- **Allow release of partially released orders** - Specify whether remaining quantities for partially released orders should be released to warehouse.

	- **Keep reservations on release failure** - Specify whether quantities that were reserved automatically for a sales order should remain reserved when release to warehouse fails.

	- **Locked order handling** - Select how to handle sales orders that are currently locked because they are being edited by other users or processes. Following options are available:
	    - **Wait for orders to unlock** - The system would wait for the orders to become unlocked to release them to the warehouse. Release to warehouse process may take more time to complete in this case.

		- **Skip locked orders** - The system would skip locked orders.

	- **Valid order types** - Select what types of sales orders to be included into the batch.

	- **Credit limit type** - Select whether to perform credit limit checks during release to warehouse and what transaction information to include when the credit limit is checked.

1. On the **Records to include** FastTab, select **Filter** button and define a query for the sales orders that you want to release to the warehouse.
1. On the **Run in the background** FastTab, specify whether the job to be run in batch mode.
1. Select **OK** to apply your settings and initiate release to warehouse process.

To set up the batch job for releasing transfer orders, follow the steps.

1. Go to **Warehouse management > Release to warehouse > Automatic release of transfer orders**.
1. In the opened dialog box, on the **Parameters** FastTab, set the following fields.

    - **Quantity to release** - Select whether the whole quantity or the physically reserved quantity should be released.

	- **Allow release of partially released orders** - Specify whether remaining quantities for partially released orders should be released to warehouse.

	- **Group releases by destination warehouse** - Specify whether the system should release all transfer orders at once or first group transfer order lines by destination warehouse and then release each group to the warehouse separately.

1. On the **Records to include** FastTab, select **Filter** button and define query for the transfer orders that you want to release to the warehouse.
1. On the **Run in the background** FastTab, specify whether the job to be run in batch mode.
1. Select **OK** to apply your settings and initiate release to warehouse process.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]