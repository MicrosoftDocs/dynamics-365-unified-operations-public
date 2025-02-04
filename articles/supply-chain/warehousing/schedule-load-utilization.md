---
title: Schedule load utilization
description: Learn how to set up and schedule the load for a warehouse, including an outline on scheduling and viewing the load for a warehouse or site.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 05/26/2017
ms.reviewer: kamaybac
ms.search.form:  WMSSpaceUtilSetup
---

# Schedule load utilization

[!include[banner](../includes/banner.md)]

You can schedule load utilization for selected location types, and you can also project the current and future load utilization. You can project the load for one or more sites, for the load units (zone or warehouse), or for a combination of a zone and a warehouse.

## Schedule and view the load for a warehouse or site

To schedule the load for sites, warehouses, or zones, you create a space utilization setup and associate it with a master plan.

In the space utilization setup, you use location types, such as **Bulk location** and **Picking location**, to specify how space utilization should be projected. You also specify a storage load mode, such as **Zone**.

The projection of future space utilization is based on information that is calculated on the associated master plan. Master plans forecast the resource planning for incoming and outgoing orders for production and operations. The projection of available space is based on the relation between the space utilization setup and the selected master plan.

By using the storage load mode that you selected in the space utilization setup, you can specify whether the load should be projected for each warehouse or zone, or whether the projections should include information about both warehouses and zones. You also specify whether blocked locations should be excluded from the calculation of load utilization.

You can project the space utilization by generating the **Warehouse load utilization** report. When you generate this report, you can specify whether the load utilization should be projected for each site, across sites, or for the selected load unit, such as zone or warehouse.

### Create a space utilization setup for a warehouse

1. Select **Inventory management** \> **Setup** \> **Warehouse monitoring** \> **Space utilization**.
2. Select **New** to create a space utilization setup. Specify an ID and a name for the new setup.
3. In the **Storage load mode** field, select whether the overview of space utilization should show information by warehouse, zone, or warehouse and zone.
4. Set the **Exclude blocked locations** option to **Yes** to exclude blocked inventory locations from the calculation of available space. You can block an inventory location for input and output by specifying a blocking cause for the location in the **Input blocked** or **Output blocked** field on the **Other** FastTab on the **Inventory locations** page.
5. On the **Location type** FastTab, select the location types to include in the space utilization calculation. You must select at least one location type for the projection.

### Associate a space utilization setup with a master plan

1. Select **Inventory management** \> **Periodic tasks** \> **Schedule load utilization**.
2. In the **Master plan** field, select a master plan.
3. In the **Number of days** field, specify the number of days to include in the projection of current and future workloads.
4. In the **Space utilization** field, select the space utilization setup to use for the projection of current and future workloads.

### Specify the load utilization projection and view information

1. Select **Inventory management** \> **Inquiries and reports** \> **Physical inventory reports** \> **Warehouse load utilization**.
2. In the **Show by** field, select the level of the space utilization projection:

    - **Site** – Project the space utilization for each site. This projection is useful if, for example, you want to view all the warehouses for a site so that you can balance the space utilization between the warehouses.
    - **Load unit** – Project the space utilization for zones or warehouses. The available space is then projected according to the value that you selected in the **Storage load mode** field on the **Space utilization** page when you created the space utilization setup.

3. Follow one of these steps, depending on the value that you selected in the previous step:

    - If you selected **Site** in the **Show by** field, the **Site** field is available. Select one or more sites to include in the projection.
    - If you selected **Load unit** in the **Show by** field, the **Load unit** field is available. Select the load unit.

4. In the **Load type** field, select **Volume** or **Weight** to specify the warehouse operating unit to project space for.
5. In the **Space utilization setup** field, select the space utilization setup that the projection should be based on.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]