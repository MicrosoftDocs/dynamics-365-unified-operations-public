---
# required metadata

title: Schedule load utilization
description: This topic describes how to set up and schedule the load for a warehouse.
author: MarkusFogelberg
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  WMSSpaceUtilSetup
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mafoge
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

[!include[banner](../includes/banner.md)]

# Schedule load utilization

You can schedule load utilization for selected location types, and also project
the current and future load utilization. You can project the load for one or
more sites, for the load units of warehouse or zone, or for a combination of
zone and warehouse.

Schedule and view the load for a warehouse or site

To schedule the load for sites, warehouses, or zones, you create a space
utilization setup and associate it with a master plan.

In the space utilization setup, you specify how to project space utilization by
using location types, such as **Bulk location** and **Picking location**. You
also specify a storage load mode, such as **Zone**.

The projection of future space utilization is based on information that is
calculated on the associated master plan. Master plans forecast the resource
planning for incoming and outgoing orders for production and operations. The
projection of available space is based on the relation between the space
utilization setup and the selected master plan.

By using the unit load mode that you selected in the space utilization setup,
you specify whether the load should be projected for each warehouse or zone, or
if the projections should include information about both warehouse and zone. You
also specify if blocked locations should be excluded from the calculation of the
load utilization.

The space utilization can be projected by using the **Warehouse load
utilization** report. When you generate the report, you can specify whether the
load utilization should be projected for each site or across sites or for the
selected load unit, such as zone or warehouse.

Create a space utilization setup for a warehouse

1.  Click **Inventory management** \> **Setup** \> **Warehouse monitoring** \>
    **Space utilization**.

2.  Click **New** to create a space utilization setup. Specify an ID and a name
    for the setup.

3.  In the **Storage load mode** field, select whether the overview of space
    utilization should be by warehouse, zone, or warehouse and zone.

4.  Set the **Exclude blocked locations** slider to **Yes** if blocked inventory
    locations should not be included in the calculation of available space. You
    can block an inventory location for input and output by specifying a
    blocking cause for the location in the **Input blocked** or the **Output
    blocked** fields on the **Other** tab on the **Inventory locations** page.

5.  On the **Location type** tab, select the location types to include in the
    space utilization calculation. You must select at least one location type
    for the projection.

Associate a space utilization setup with a master plan

1.  Click **Inventory management** \> **Periodic tasks** \> **Schedule load
    utilization**.

2.  In the **Master plan** field, select a master plan.

3.  In the **Number of days** field, specify the number of days to include in
    the projection of current and future workloads.

4.  In the **Space utilization** field, select the space utilization setup to
    use for the projection of current and future workloads.

Specify the load utilization projection and view information

1.  Click **Inventory management** \> **Inquiries and reports** \> **Physical
    inventory reports** \> **Warehouse load utilization**.

2.  In the **Show by** field, select **Site** or **Load unit** to identify the
    level of space utilization projection.

    -   Select **Site** to project the space utilization for each site. This
        projection is useful if, for example, you want to view all the
        warehouses for a site so that you can balance the space utilization
        between the warehouses.

    -   Select **Load unit** to project the space utilization for zones or
        warehouses. The available space is then projected according to the
        selected option in the **Storage load mode** field on the **Space
        utilization** page.

3.  In the **Site** field, select one or more sites to include in the
    projection. This option is available only if you selected **Site** in the
    **Show by** field.

4.  In the **Load unit** field, select the load unit. This option is available
    only if you selected **Load unit** in the **Show by** field.

5.  In the **Load type** field, specify **Volume** or **Weight** to indicate the
    warehouse operating unit to project space for.

6.  In the **Space utilization setup** field, select the space utilization setup
    that the projection will be based on.
