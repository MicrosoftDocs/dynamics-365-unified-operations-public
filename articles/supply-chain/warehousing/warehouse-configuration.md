---
title: Warehouse configuration overview
description: Learn how to configure a warehouse, including information about how to enable a warehouse layout and warehouse processes.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: InventLocation, WHSLocation, WHSLocationBuild, WHSLocationProfile, WHSLocationType, WHSLocDirTable, WHSParameters, WHSWaveTemplateTable, WHSWorkPool, WHSWorkTemplateTable, WHSZone, WHSZoneGroup
ms.topic: how-to
ms.date: 11/20/2025
ms.custom:
  - bap-template
---

# Warehouse configuration overview

[!include [banner](../includes/banner.md)]

This article explains how to configure a warehouse. It includes information about how to enable a warehouse layout and warehouse processes.

> [!NOTE]
> This article applies to features in the Warehouse management module. It doesn't apply to warehouse features in the Inventory management module.

## Warehouse layout

Warehouse management processes (WMS) in Supply Chain Management give you flexible ways to define your warehouse layout to meet changing needs, so that you can achieve optimal warehouse efficiency.

- You can establish high-priority and low-priority storage areas for optimum placement of goods.
- You can divide your warehouse into zones to accommodate various storage needs, such as temperature requirements, or various turnover rates for items.
- You can specify warehouse locations on any level (for example, site, warehouse, aisle, rack, shelf, and bin position).
- You can group locations by using physical capacity constraint settings.
- You can control how items are stored and picked, based on query-defined rules.

To use WMS in Supply Chain Management, you must create a warehouse and enable it for WMS. On the **Warehouses** page, select the **Use warehouse management processes** option.

### Zone groups, zones, location types, and locations

As part of the process for enabling a warehouse layout, you must define warehouse zone groups, and zones, location profiles, location types, and locations.

- **Zone groups** – A logical or physical grouping of zones within a warehouse.
- **Zones** – A logical or physical grouping of locations within a warehouse.
- **Location profiles** – A logical or physical grouping of locations that have the same warehouse location process policies (for example, a mix of different item numbers can be stored there, and the same physical capacity constraints apply).
- **Locations types** – A logical or physical grouping of the warehouse locations. For example, you can create a location type for all staging locations. Mandatory settings on the **Warehouse management parameters** page drive the process of defining staging location types and the final shipping location type.
- **Locations** – The lowest level of location information. Use locations to track where the on-hand inventory is stored and picked in a warehouse.

The entities that you create to define your warehouse layout are used in the queries that you set up in work templates to drive work orders in the warehouse. Therefore, when you define the zones, location types, and so on, consider how different areas in the warehouse are used for different processes. Additionally, consider factors such as the physical characteristics of a particular area. For example, there might be areas where you can use only a certain type of forklift truck. Or, if your company has both production and finished goods within the same facility, you might want to create a single warehouse in Supply Chain Management but then separate the two operations by creating two zone groups. Give your entities descriptive names, so that it's easy to identify them when you use them in template queries.

### Location stocking limits, location profiles, and fixed picking locations

You must consider the physical layout of the warehouse, both to determine storage capacities (location stocking limits and location profiles) and as part of your attempts to achieve optimal warehouse processes.

Location stocking limits help guarantee that work isn't created to request inventory to be put in a location that doesn't have the physical capacity to carry the inventory. For example, if some locations within a warehouse can hold only one pallet per location, enable location stocking limits. Set the **Quantity** value to *1*, and set the **Unit** value to *PL* within a specific location profile grouping.

If you need more advanced calculations to control the location capacity constraints, use location profiles. In this case, the weight and volume are considered when capacity calculations are done.

To achieve optimal outbound processes, evaluate whether to use fixed picking locations and fixed packing locations. Often, minimum/maximum replenishment is used for replenishment processes from a bulk area to the fixed picking locations, and multiple fixed picking locations can be enabled within the same warehouse and for product variants. Consider the flexibility that you can achieve by enabling dedicated demand replenishment overflow locations that are used only for wave/load replenishment processing.

### Location setup wizard

To quickly create the locations within a warehouse, use the **Location setup** wizard. As part of this process, you can easily maintain the format of the location names.

## Warehouse processes

As part of the configuration of a warehouse, enable warehouse processes according to your business requirements. The most important components to configure are wave templates, work templates, work pools, and location directives.

### Wave templates

Wave templates help enable the outbound "Release to warehouse" process. Use the wave template functionality as soon as you release order lines (either directly from source documents, via batch job processes, or via loads that you already created).

You can create three types of wave templates:

- **Shipping**
- **Production order**
- **Kanban**

Use parameters to define how far the system should automatically go in the outbound work processing. The system selects a wave template based on the wave template sequence and criteria that you specify in the template. The system checks the criteria in the template listed at the top of the sequence first. If the criteria are met, the system processes the wave template. Otherwise, the system checks the criteria in the next template, and so on. Therefore, put the template that has the most specific criteria at the top of the wave template sequence list, so that it's processed first. For example, you want to process all the work for a specific carrier today and temporarily delay processing of the work for other carriers. In this case, list the wave template that selects work for that carrier higher in the sequence than other templates. Otherwise, the work for other carriers might be processed before the work for that carrier is completed.

You must specify the wave process methods in each wave template. The available methods vary, depending on the wave template type.

### Work templates

Work template definitions play an important role in the definition of warehouse management work processes. They define what work is performed, and how the work is done. Templates can also contain a directive code that links to a location directive to determine where work is performed. Work templates include a query that specifies the criteria for the work. Each template must include at least one Pick operation and one Put operation to drive the basic work operation of transferring on-hand inventory from one location to another.

If multiple workers must be able to process work for some of your warehouse operations, consider using the concept of *staging* for the inventory and separating the work execution into different work classes.

### <a name="warehouse-management-parameters-work"></a>General warehouse work policies

General warehouse work policies let you influence how warehouse work is created and handled. Set up policies to control options such as default work priority values, deferred work processing, work transaction dates, and more. To view and set these policies, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. Open the **General** tab.
1. Expand the **Work** FastTab.
1. Select policies and set other work options available on this FastTab. Each field has tooltip help. To see the tooltip for a field, hover your mouse pointer over the relevant field label.

### Work pools

Use work pools to organize work into groups. For example, create a work pool to classify work that occurs in a particular warehouse location. For all work types except counting, assign a work pool to a work template. For cycle counting, assign a work pool on the following pages:

- Cycle count plans
- Cycle count thresholds
- Cycle count work by location
- Cycle count work by item

When you use work templates to create work, the work pool is automatically assigned to the work.

You can also use work pool IDs to limit the type of work that is directed to a particular warehouse worker, provided that you configure this functionality on the relevant mobile device menu item.

### Location directives

As the name suggests, use location directives to direct the work transactions to the appropriate locations in the warehouse. In other words, they define where to pick and put.

To make it easier and quicker to define the actions that are associated with each location directive line, use one of the predefined strategies. For example, you can use the *Empty location with no incoming work* strategy to search for free locations in a warehouse, or you can use *FEFO batch reservation* strategy for outbound sales picking.

## Next steps

- [Configure locations in a WMS-enabled warehouse](tasks/configure-locations-wms-enabled-warehouse.md)
- [Get started with setting up the Warehouse management module](get-started-with-setting-up-module.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
