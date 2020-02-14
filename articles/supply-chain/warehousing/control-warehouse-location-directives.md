---
# required metadata

title: Control warehouse work by using work templates and location directives
description: This topic describes how to use work templates and location directives to determine how and where work is carried out in the warehouse.
author: perlynne
manager: AnnBe
ms.date: 02/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLocDirFailure, WHSLocDirHint, WHSLocDirTable, WHSLocDirTableUOM, WHSRFMenuItem, WHSWork, WHSWorkClass, WHSWorkPool, WHSWorkTemplateTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 72921
ms.assetid: 377ab8af-5b0c-4b5e-a387-06ac1e1820c0
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Control warehouse work by using work templates and location directives

[!include [banner](../includes/banner.md)]

This topic describes how to use work templates and location directives to determine how and where work is carried out in the warehouse.

The instructions that warehouse workers receive on a mobile device are determined by the Dynamics 365 Supply Chain Management work templates that you set up to define the various warehouse processes and tasks. Work templates determine how the work is performed for each warehouse process. By linking a location directive to work templates, you can help guarantee that work occurs in specific physical areas of the warehouses.

## Work templates
The **Work templates** page lets you define the work operations that must be performed in the warehouse. Typically, warehouse work operations consist of a pair of actions: a warehouse worker picks up on-hand inventory in one location and then puts the picked inventory down in another location. 

Work templates consists of a header and associated lines. Each work template is for a specific *work order type*. Many work order types are associated with source documents, such as purchase or sales orders. However, other work order types represent separate warehouse processes, such as cycle counting. The *work pool ID* lets you organize work into groups. 

The settings in the work header definition can be used to determine when a new piece of work should be created. For example, you can set a maximum number of pick lines and a maximum expected pick time. Then, if the work for a sales order picking process exceeds either of those values, that work is split into two pieces of work. 

The work lines represent the physical tasks that are required in order to process the work. For example, for an outbound warehouse process, there might be a work line for picking up the items within the warehouse and another line for putting those items into a staging area. There can then be an additional line for picking the items from staging, and another line for putting the items into a truck as part of the loading process. You can set a *directive code* on work template lines. A directive code is linked to a location directive and therefore helps guarantee that the warehouse work is processed in the correct location in the warehouse. 

You can set up a query to control when a particular work template is used. For example, you can set a limitation so that a particular template can be used for work only in a specific warehouse. Alternatively, you might have several templates that are used to create work for outbound sales order processing, depending on the sales origin. The system uses the **Sequence number** field to determine the order that the available work templates are assessed in. Therefore, if you have a very specific query for a particular work template, you should give it a low sequence number. That query will then be evaluated before other, more general queries. 

To stop or pause a work process, you can use the **Stop work** setting on the work line. In that case, the worker who is performing the work won't be asked to perform the next work line step. To move on to the next step, that worker or another worker must select the work again. You can also separate the tasks within a piece of work by using a different *work class ID* on the work template lines.

## Location directives
Location directives are rules that help identify pick and put locations for inventory movement. For example, in a sales order transaction, a location directive determines where the items will be picked, and where the picked items will be put. Location directives consist of a header and associated lines, and you create them on the **Location directives** page. 

On the header, each location directive must be associated with a *work order type* that specifies the type of inventory transaction that the directive will be used for, such as sales orders, replenishment, or raw material picking. The *work type* specifies whether the location directive will be used for picking or putting work, or for some other warehouse process, such as counting or inventory status changes. You must also specify a *site* and a *warehouse*. A *directive code* that you specify on the header can be used to link the location directive to one or more work templates. 

As for work templates, you can set up a query to determine when a particular location directive is used. For example, you can specify that when e-commerce is the origin of a sales order, the inventory must be picked up from a dedicated area in the warehouse. The system uses the **Sequence number** field to determine the order that the available location directives are assessed in. 

The location directive lines set additional restrictions on the application of the location finding rules. You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit. For example, if the unit of measure is pallets, the items in pallets can be put in a specific location. You can also specify whether the quantity can be split across multiple locations. Like the location directive header, each location directive line has a sequence number that determines the order that the lines are assessed in. 

Location directives have one additional level of detail: *location directive actions*. You can define multiple location directive actions for each line. Once again, a sequence number is used to determine the order that the actions are assessed in. On this level, you can set up a query to define how to find the best location in the warehouse. You can also use predefined **Strategy** settings to find an optimal location.

## Location directives configuration details 

 ### Sequence number
 
This number indicates the sequence in which a location directive is processed for a selected order type. It can be changed using  **Move Up** and **Move Down** on the menu.
 
 ### Work type
 
This is the type of work to be performed. The type of work available is based on the type of inventory transaction that you have selected in the **Work order type** field.
-	**Put** - A work type equal to **Put** means that the location directive is going to find the most ideal location to place or locate inventory coming into the system, either from receiving, production, or inventory adjustments. It can also be used to define a put to a stage location or a final bay door shipping location.
-	**Pick** - A work type equal to **Pick** means that the warehouse is going to find the most ideal location to physically reserve inventory from (create work). The pick can be completed (pick work line can be closed), even if the work is not completed. The user can complete physical picking, which is a pick step. The user can then cancel from a mobile device and complete the work later. However, the work header is closed when final put is completed. 
-	**Counting, Adjustments, Custom, Inventory status change, License plate building, print, Status change, Pack to nested license plates** - These are not usable in any location directive setup. This is an enum so there is no filtering connected to the work order type. 

### Directive code

Select the directive code to associate to a work template or replenishment template. On the **Directive code** form, you can create new codes that can be used for connections between a work template replenishment template and location directive. This can also be used to establish the link between any work template line and location directive (such as baydoor or stage location).

Note that if code is set, when work is generated the system will not search the location directive by sequence, the search will be by directive code. This means that you can be more specific in what location template is used for a certain step in a work template, such as staging of materials. 

### Site

Site is a mandatory field because the location directive needs the site and warehouse that it is valid for. 

### Warehouse

Warehouse is a mandatory field because the location directive needs the site and warehouse that it is valid for.

### Multiple SKU

This allows multiple Stock Keeping Units (SKU) on a location, such as the baydoor. If you select **Multiple SKU**, the put location will be specified in work (which is expected), but it will only be able to handle multiple item put (if work includes different SKUs to be picked and put, not a single SKU put). If you do not select **Multiple SKU**, the put location will only be specified if the put has only one kind of SKU. To use both actions, you need to specify two lines, one with multiple SKU On, and one with multiple SKU Off. These need to have the same structure and setup. For put operations, you need to have location directives that are identical, even if you do not distinguish between single and multiple SKUs on the work ID. You also need to set up for pick, if you have an order with more than one item.

### Sequence number

Enter the sequence in which the location directive line are processed for the selected work type. You can also modify the sequence, if needed, using **Move up** and **Move down**.

### From/To quantity

This provides the ability to specify a quantity range for when the middle-grid sequence should be selected. You can specify the From/To range on Qty in the respective unit.

### Unit

You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit. The unit field on the line is used only for quantity evaluation.

When checking if the location directive line is applicable, this will be based on the quantity in the respective unit specified on the location directive line. Every time a location directive line is reached, the system will try to convert the demand unit to a unit specified on the line. If the UOM conversion does not exist, it will continue to the next line. 

### Locate quantity

This option is only used for put/locate quantity into the warehouse. It is only for the put work type. The valid values are:

-	**License Plate Qty** - When evaluating whether the quantity is within the “From” and “To” quantity ranges, use the quantity on the license plate being received.
-	**Unitized Qty** - When evaluating whether the quantity is within the “From” and “To” quantity ranges, use the quantity being unitized during the specific transaction.
-	**Remaining Qty** - When evaluating whether the quantity is within the “From” and “To” quantity ranges, use the quantity left to be received on the purchase order line currently being checked in.
-	**Expected Qty** - When evaluating whether the quantity is within the “From” and “To” quantity ranges, use the total quantity of the purchase order line, regardless of what has already been received.

### Restrict by unit

This allows a location directive line to be made specific to a unit of measure or multiple units of measure. When reserving quantity, if you only want to reserve pallets from a specific set of locations, then the middle-grid sequence would restrict that particular sequence to “PL” so that any quantity less than a pallet would not select the sequence. Select **Restrict by unit** to set up the units. You can also restrict the line to more than one unit. This works only with location directives of type pick. 

### Round up to unit

This field works together with the **Restrict by unit** field. If the location directive line **Restrict by unit** is set to "box," selecting **Round up to unit** indicates that the work generated out of the directive for raw material picking should be rounded up to a multiple of one handling unit (specified in **Restrict by unit**). Note that this works only for raw material picking and only with location directives of type pick.

### Locate packing Qty

If a packing quantity is specified on a sales order, transfer order, or production order, this restricts the system to only select locations with a packing quantity in the location. This works only with location directives of type pick.

### Allow split

This specifies if a location directive is allowed to split the quantity being received or the quantity being reserved across multiple warehouse locations, or if the entire quantity must be located to a single location or reserved from a single location in order to create work. 

### Sequence number

This number is the sequence in which the location directive is processed for the selected work type. You can modify the sequence, if needed. However, be cautious using sequence numbers, as processing will always run in sequence. 

### Name

Enter a name for the location directive action. Be sure to be specific when specifying a name.

### Fixed location usage 

-	**Fixed and non-fixed locations** - The location directive will consider all locations.
-	**Only fixed locations for the product** - The location directive will consider only fixed locations for products.
-	**Only fixed locations for the product variant** - The location directive will consider only fixed locations for product variants.

### Allow negative inventory

Select to allow negative inventory at the specified warehouse location in location directives. 

### Batch enabled 

Select to use batch strategies for the items that are batch enabled. If a line is reached where **Batch enabled** is set with a none batch item, the process will continue to the next action line. 

### Strategy

-	**Consolidate** - This strategy is used to consolidate items in a particular location when similar items are already available. This works only for the put type of location directive. Common setup for put will be to consolidate on the first action line, and then on second try to put without consolidation. Consolidating goods makes later picking more efficient.
-	**Match packing quantity** - This strategy will find a location that contains a license plate that has the exact quantity required. It cannot be used with locations that are not license plate controlled. This strategy only works for a Pick work type location directive.
-	**FEFO batch reservation** - This strategy is used when inventory is located using a batch expiration date and is allocated for batch reservation. You can only use this strategy for batch enabled items. This only works for a Pick work type location directive. 
-	**Round up to a full LP** - This strategy is used to round up the inventory quantity to match the license plate (LP) quantity that is assigned to the items to be picked. You can only use this strategy for the replenishment type of location directive of type Pick. 
-	**Empty location with no incoming work** - This strategy is used to locate empty locations. The location is considered empty if it has no physical inventory and no expected incoming work. This strategy is used only for a Put type of location directive. 

### Example of the use of location directives

For this example, consider a purchase order process where the location directive must find free capacity within a warehouse for inventory items that have just been registered at the receiving dock. First, you need to find free capacity within the warehouse by consolidating with existing on-hand inventory. If consolidation isn't possible, then you need to find an empty location. 

For this scenario, you must define two location directive actions. The first action in the sequence must use the **Consolidate** strategy, and the second should use the **Empty location with no incoming work** strategy. Unless you define a third action to handle an overflow scenario, two outcomes are possible when there is no more capacity in the warehouse: work can be created even though no locations are defined, or the work creation process can fail. The outcome is determined by the setup on the **Location directive failures** page, where you can decide whether to select the **Stop work on location directive failure** option for each work order type.
