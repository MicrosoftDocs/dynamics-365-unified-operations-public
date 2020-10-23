---
# required metadata

title: Work with location directives
description: This topic describes how to work with location directives
author: Mirzaab
manager: tfehr
ms.date: 10/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  WHSLocDirTable
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-10-20
ms.dyn365.ops.version: Release 10.0.15
---
# Work with location directives

[!include [banner](../includes/banner.md)]

Location directives are rules that help identify pick and put locations for inventory movement. For example, in a sales order transaction, a location directive determines where the items will be picked, and where the picked items will be put. Location directives consist of a header and associated lines. Location directives are created for specific *Work order types*.

> [!NOTE]
> This topic applies to features in the **Warehouse management** module. It doesn't apply to features in the [Inventory management](../inventory/inventory-home-page.md) module.

You can use location directives to perform the following tasks:

- Put away incoming items.
- Pick and stage items for outbound transactions.
- Pick and put raw materials for production.
- Replenish locations.

## Prerequisites

Before you can create a location directive, you must follow these steps to make sure that the prerequisites are in place:

1. Make sure the required license key is enabled (admin access required). To enable the license key, go to **System administration \> Setup \> License configuration**, expand the **Trade** license key, and then select the **Warehouse and Transportation management** configuration key.
1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. Create a warehouse.
1. On the **Warehouse** FastTab, set the **Use warehouse management processes** option to *Yes*.
1. Create locations, location types, location profiles, and location formats. For more information, see [Configure locations in a WMS-enabled warehouse](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/configure-locations-wms-enabled-warehouse).
1. Create sites, zones, and zone groups. For more information, see [Warehouse set up](https://docs.microsoft.com/dynamics365/commerce/channels-setup-warehouse) and [Configure locations in a WMS-enabled warehouse](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/configure-locations-wms-enabled-warehouse).

## Location Directive Work Order Types

Location directives have many common fields that are available for setup in each of the work order types. There are also fields specific to certain work order types. 

![Location directives work order types](media/Location_Directives_Work_Order_Types.png "Location directives work order types")

>[!NOTE]
>Two work order types, *Canceled work* and *Cycle counting*, are used only by the system and location directives cannot be created for these work order types.

The following subsections provide tables that list the common and specific fields available when setting up a location directive.

### Fields common to all work order types

The following table lists fields common to all work order types.

| FastTab | Field |
| --- | --- |
| Location directives | Work type |
| Location directives | Site |
| Location directives | Warehouse |
| Location directives | Directive code |
| Location directives | Multiple SKU |
| Lines | Sequence number |
| Lines | From quantity |
| Lines | To quantity |
| Lines | Unit |
| Lines | Locate quantity |
| Lines | Restrict by unit |
| Lines | Round up to unit |
| Lines |Locate packing quantity |
| Lines | Allow split |
| Location Directive Actions | Sequence number |
| Location Directive Actions | Name |
| Location Directive Actions | Fixed location usage |
| Location Directive Actions | Allow negative inventory |
| Location Directive Actions | Batch enabled |
| Location Directive Actions | Strategy |

### <a name="fields-specific-types"></a>Fields specific to work order types

The following table lists fields specific to the listed work order types.

| FastTab | Field | Work order type |
| --- | --- | --- |
| Location directives | Locate by | Purchase orders |
| Location directives | Applicable disposition code | Purchase orders |
| Location directives | Disposition code | Purchase orders |
| Location directives | Applicable disposition code |Finished goods put away |
| Location directives | Disposition code | Finished goods put away |
| Location directives | Applicable disposition code |Return orders |
| Location directives | Disposition code | Return orders |
| Location directives | Applicable disposition code |Kanban put away |
| Location directives | Applicable disposition code |Kanban picking |
| Lines | Immediate replenishment template | Sales orders |
| Lines | Immediate replenishment template | Raw material picking |
| Lines | Immediate replenishment template | Transfer issue |
| Lines | Immediate replenishment template | Kanban picking |

## Open the Location directives page

To open the page, go to **Warehouse management \> Setup \> Location directives**.

From here you can view, create, and edit your location directives using the commands on the Action Pane. See the remaining sections of this topic for details about how to use all of the available settings.

## The Location directives Action Pane

The **Location directives** page Action Pane contains options to create, edit, and delete directives (**Edit**, **New, and **Delete**); adjust the sequence in which the location directive is processed (**Move up** and **Move down**); and to configure a query (**Edit query**), which specifies what criteria the location directive is to be applied.

- **Move up** - Moves up the selected location directive in the sequence. For example, from sequence number 4 to sequence number 3.
- **Move down** - Moves the selected location directive down in the sequence. For example, from sequence number 4 to sequence number 5.
- **Edit query** - Opens a dialog box where you to define the conditions on which the selected location directive will be processed. For example, you may want to apply a given location directive only for a specific warehouse.

## Location directives header

The location directive header is where you set the sequence number for the location directive and where you establish the location directives descriptive name.

- **Sequence number** - Indicates the sequence in which the system tries to apply each location directive for selected order type. It can be changed using **Move Up** and **Move Down** on the Action Pane. Low numbers are applied first.

- **Name** - Descriptive name for the location directive. It should help identify the general purpose of the directive. For example, *Sales order picking in warehouse 24*.

## The Location directives FastTab

The fields displayed on the **Location directives** FastTab are specific to the **Work order type** selected in the list pane. Below is a list of fields that a user will see displayed in the FastTab.

- **Work type** - Select the type of work to be performed. The type of work available is based on the type of inventory transaction that you have selected in the **Work order type** field. Select one of the following:

  - **Put** - The location directive will try to find the most ideal location to place or locate inventory coming into the system either from receiving, production, or inventory adjustments. It can also be used to define put to stage location or final bay door shipping location.

  - **Pick** - The location directive will try to find the most ideal location(s) to physically reserve inventory from (create work). The pick can be completed (pick work line can be closed), even if the work is not completed. The user can complete physically picking and in the system that is pick step, then user can cancel from the mobile device and complete the work later. Work header however is first closed when final put is completed.

  >[!IMPORTANT]
  >The other values in the **Work type** drop-down list aren't relevant for location directives. They only appear because the drop-down list isn't filtered to match the **Work order type**.

- **Site** - Site is mandatory because the location directive needs to know what site and warehouse it is valid for.

- **Warehouse** - Warehouse is mandatory because the location directive needs to know what site and warehouse it is valid for.

- **Directive code** - Select the directive code to associate to a work template or replenishment template. On the **Directive code** page, you can create new codes that can be used to connect work template or replenishment templates to location directives. Directive codes can also be used to establish a link between any work template line and location directive (such as Baydoor or stage location).

    > [!TIP]
    > If a directive code is set, when work is to be generated, the system won't search location directives by sequence number, but by directive code. In this way, you can be more specific what location template is used for certain step in work template like for staging of the materials.

- **Multiple SKU** - Select *Yes* to enable the use of multiple stockkeeping units (SKUs) on a location. For example, the Baydoor must have it enabled.  If we enable multiple SKUs, our put location will be specified in work (this is expected), but it will only be able to handle a multi-item put (if work includes different SKUs to be picked and put) not a single SKU put. If we select *No* for **Multiple SKU**, our put location will only be specified if our put has only one kind of SKU.

    > [!IMPORTANT]
    > To be able to do both options, you must specify two lines (one with **Multiple SKU** set to *Yes*, and one with **Multiple SKU** set to *No*) that have same structure and setup. So, for put operations, you must have two location directives that are identical, even if you don't need to distinguish between single and multiple SKUs on a work ID. Not doing this often results in unexpected business process locations coming from the applied Location directive. You must set it up for pick to, if you have an order with more than one item.

    Use the **Multiple SKU** option for work lines that handle more than one item number (it is shown as blank in the work details and as **Multiple** on the warehouse app processing pages.

    A typical example scenario uses a work template setup with more than one pick/put pair. Here you might want to search for a specific put staging location type.

    >[!NOTE]
    >You can't use the **Edit query** option while **Multiple SKU** is enabled because the query can't evaluate at item level when having multiple items. To make sure the desired location directive gets selected, use the **Directive code** to guide the selection of the location directive related to the work template put lines that have this directive code assigned.

    Unless you always operate with either single-item or mixed-item operations, it is important to define two location directives for the put work type: one with the **Multiple SKU** enabled and another without.

- **Applicable disposition code** - Specify whether the disposition code of the location directive must match the disposition code that is applied at item receiving or if the location directive can be selected based on any disposition code. If you select Exact match and the Disposition code field is blank, only blank disposition codes will be considered for this location directive.

    >[!NOTE]
    >This field is available only on selected **Work order types** where replenishment is permitted. For a complete list, see [Fields specific to work order types](#fields-specific-types).

- **Locate by** - Determines if the putaway quantity will be the entire quantity on the license plate, or if it will be item by item. Use this setting to help guarantee that all the content on a license plate is put into one location, and that the system does not suggest that you split the contents into several locations for **ASN** (License plate receiving), **Mixed license plate** receiving, and **Cluster** receiving processes (requires that *Cluster Putaway Feature* is enabled). The behavior of the location directive query and the lines and Location directive actions will vary, depending on the value that you select. The lines restriction section will only be used when using **Item**.

    >[!NOTE]
    >This field is available only on selected **Work order types** where replenishment is permitted. For a complete list, see [Fields specific to work order types](#fields-specific-types).

- **Disposition code** - This field is used by location directives with a **Work order type** of *Purchase orders*, *Finished goods putaway*, or *Return orders* and a **Work type** of *Put*. Use it to guide the flow to use a specific location directive, depending on the disposition code selected by a worker using the warehouse app (for example, to direct returned goods to an inspection location before returning them to stock). A disposition code can be linked to an inventory status and thereby used to change the inventory status as part of a receiving process. So, let's say you have a disposition code *QA* that sets the inventory status to *QA*; then you can have a separate location directive to move that inventory to a quarantine location.

    >[!NOTE]
    >This field is available only on selected **Work order types** where replenishment is permitted. For a complete list, see [Fields specific to work order types](#fields-specific-types).

## The Lines FastTab

Use the **Lines** FastTab to establish conditions for applying the related actions specified in the **Location directive actions** FastTab. For each line, you can specify a minimum quantity and a maximum quantity that the actions should apply to, and you can specify that the actions should apply for a specific inventory unit.

- **Sequence number** - Enter the sequence in which each location directive line should be processed for the selected work type. You can modify the sequence, if needed, using the **Move up** and **Move down** buttons in the **Lines** toolbar.

- **From quantity** - Specify the beginning quantity range for which the line applies. Specify the quantity in the unit of measure that is selected in the **Unit** field.

- **To quantity** - Specify the ending quantity range for which the line applies. Specify the quantity in the unit of measure that is selected in the **Unit** field.

- **Unit** - Select the unit of measure for the items. You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit. The unit field is used *only* for quantity evaluation. When checking if the location directive line is applicable at all, it will do so based on the quantity in the respective unit specified on the location directive line. Every time a location directive line is reached, the system will try to convert the demand unit to a unit specified on the line, if the unit of measure conversion doesn't exist, the system will continue to a next line.

- **Locate quantity** - this only comes into use when trying to put or locate items into the warehouse (so it only applies when **Work type** is set to *Put*). Choose one of the following values:

  - **License plate quantity** - When evaluating whether or not a quantity is within the **From quantity** to **To quantity** range, use the quantity on the license plate being received.

  - **Unitized quantity** - When evaluating whether or not a quantity is within the **From quantity** to **To quantity** range, use the quantity used during the specific transaction. For example, in a warehouse, if you can receive a quantity of 1,000 and break it into 10 license plates, each of which has a quantity of 100, you can use a quantity of 1,000 items instead of the license plate quantity of 100.

  - **Remaining quantity** - When evaluating whether or not a quantity is within the **From quantity** to **To quantity** range, use the quantity left to be received on the purchase order line being processed.

  - **Expected quantity** - When evaluating whether or not a quantity is within the **From quantity** to **To quantity** range, use the total quantity of the purchase order line, regardless of what has already been received.

- **Restrict by unit** - Allows the location directive line to be made specific to a unit of measure or multiple units of measure. Select this check box to restrict the units of measure that are considered valid selection criteria for the location directive lines. This works only for location directives where **Work type** is set to *Pick*. Note the following:

  - For example, if we only want to reserve pallets from a specific set of locations when reserving quantity, then the lines would restrict that particular sequence to pallets such that any quantity less than a pallet would not be selected for this location directive.

  - The **Restrict by unit** check box doesn't control the unit or units that are applied on work lines. The unit restriction applies only to the units that are made available via the unit sequence group.

  - For example, an item is associated with a unit sequence group that includes both the *pallets* unit and the *pcs* units. A unit of measure has been defined where 1 pallet = 100 pcs, and the location directive uses the **Restrict by unit** functionality only for pallets. Furthermore, a work template has been defined that limits the work header creation to 50 pcs. In this case, work lines of 50 pcs will be created. To specify the unit of measure for restriction, do the following:

    1. Select **Restrict by unit** from the **Lines** FastTab toolbar. (This button becomes available only after you select the **Restrict by unit** check box on the line and then select **Save**.)

    1. The **Restrict by units** page opens. In the **Unit** field, select the unit of measure to restrict by for the pick and put processes.

- **Round up to unit** - This field works together with the field **Restrict by unit**. If the location directive line **Restrict by unit** is set, for example, to *box*, and **Round up to unit** is selected, this indicates that the work generated out of the directive for raw material picking should be rounded up to a multiple of one handling unit specified on the **Restrict by unit** page.

    >[!NOTE]
    >This **Round up to unit** setup works only for **Work order type** *Raw material picking*. This works only with the location directives of **Work type** *Pick*.

- **Locate Packing Qty** – If you specify a packing quantity on a sales order, transfer order, or a production order, this checkbox restricts the system to only select locations with at least that packing quantity in the location.

    >[!NOTE]
    >This works only with the location directives of type *pick*.

- **Allow Split** – This specifies if location directive is allowed to split the quantity being received or the quantity being reserved across multiple warehouse locations or if the entire quantity must be located to a single location or reserved from a single location in order to create work.

- **Immediate replenishment template** - Create a connection to a replenishment template, so that replenishment is started immediately if items aren't allocated. If you leave this field blank, item replenishment won't be started until all lines of the location directive have been processed.

    >[!NOTE]
    >This field is available only on selected **Work order types** where replenishment is permitted. For a complete list, see [Fields specific to work order types](#fields-specific-types).

## The Location directive actions FastTab

You can define multiple location directive actions for each line. Once again, a sequence number is used to determine the order that the actions are assessed in. On this level, you can set up a query to define how to find the best location in the warehouse. You can also use predefined **Strategy** settings to find an optimal location.

- **Sequence number** - Establishes sequence in which the actions are processed for the selected work type. You can modify the sequence, if needed, using the **Move up** and **Move down** buttons in the **Location directive actions** toolbar.

- **Name** - Enter the name for the location directive action. Be specific so it is clear from the name what action is performed.

- **Fixed location usage** - Establishes which locations the location directive considers. Select one of the following values:

  - **Fixed and non-fixed locations** - The location directive will consider all locations.

  - **Only fixed locations for the product** - The location directive will consider only fixed locations for products.

  - **Only fixed locations for the product variant** - The location directive will consider only fixed locations for product variants.

- **Allow negative inventory:** - Select this check box to allow negative inventory at the specified warehouse location in location directives.

- **Batch Enabled** - Select this check box to use batch strategies for items that are batch enabled. For processes using location directives to find locations from which to pick batch-number tracked items, it is important to select the **Batch enabled** check box to include the search for locations holding batch-number tracked items. If this check box is selected, and the **Strategy** field is set to *None*, the system will move on to the next action line.

- **Strategy** - To make it easier and quicker to define the actions that are associated with each location directive line, select one of the following predefined strategies.

  - **None** - No strategy will be used.

  - **Match packing quantity** -  This strategy verifies whether a pick location has the specified packing quantity. This strategy is valid only when the **Work type** is set to *Pick*.

  - **Consolidate** - This strategy consolidates items in a specific location when similar items are already available. This strategy is valid only when **Work type** is set to *Put*. A typical setup for put tries to consolidate on the first action line and then, on the second line, try to put without consolidation. Consolidating goods makes later picking more efficient.

  - **FEFO batch reservation** -  This strategy uses first expiry first out (FEFO) batch reservations. Use it when inventory is located using a batch expiration date and is allocated for batch reservation. You can only use this strategy for batch enabled items. This strategy only works when the **Work type** is set to *Pick*.
  
  - **Round up to the full LP and FEFO batch** - This strategy combines the elements of the *FEFO batch reservation* and *Round up to a full LP* strategies. It is only valid for batch-enabled items and *Pick* work type location directives. The line must be batch enabled to use the *FEFO batch reservation* strategy and rounding up to license plate (LP) strategies can only be used for replenishment. If this strategy is configured together with a location stocking limit, it can cause selected put-work location overload and ignore stocking limits.

  - **Round up to a full LP** - This strategy is used to round up the inventory quantity to match the license plate (LP) quantity that is assigned to the items to be picked. You can only use this strategy for replenishment location directives of type Pick. If this strategy is configured together with a location stocking limit, it can cause selected put-work location overload and ignore stocking limits.
  
  - **License plate guided** - When you release the order to the warehouse to create the pick-and-put work, use the *License plate guided* strategy. You can do this for multiple license plates. The *License plate guided* strategy will try to reserve and create picking work against the locations holding the requested license plates that have been associated with the transfer order lines. But if this isn't possible and you still would like to create picking work, you should fall back to another location directive action strategy, and perhaps also search for inventory in another area of the warehouse, depending on your business process needs.

  - **Empty location with no incoming work** - Use this strategy to locate empty locations. The location is considered empty if it has no physical inventory and no expected incoming work. You can only use this strategy for location directives with a **Work type** of *Pick*.
  
  - **Location aging FIFO** - Use the first in, first out (FIFO) strategy to ship both batch-tracked items and non-batch-tracked items, based on the date when the inventory entered the warehouse. This capability can be especially useful for non-batch-tracked inventory, where an expiration date isn't available to use for sorting. The FIFO strategy finds the location that contains the oldest aging date, and it allocates picking based on that aging date.
  
  - **Location aging LIFO** - Use the last in, last out (LIFO) strategy to ship both batch-tracked items and non-batch-tracked items, based on the date when the inventory entered the warehouse. This capability can be especially useful for non-batch-tracked inventory, where an expiration date isn't available to use for sorting. The LIFO strategy finds the location that contains the newest aging date, and it allocates picking based on that aging date.

## Example of using location directives

For this example, consider a purchase order process where the location directive must find free capacity within a warehouse for inventory items that have just been registered at the receiving dock. First, you need to find free capacity within the warehouse by consolidating with existing on-hand inventory. If consolidation isn't possible, then you need to find an empty location.

For this scenario, you must define two location directive actions. The first action in the sequence must use the *Consolidate* strategy, and the second should use the *Empty location with no incoming work* strategy. Unless you define a third action to handle an overflow scenario, two outcomes are possible when there is no more capacity in the warehouse: work can be created even though no locations are defined, or the work creation process can fail. The outcome is determined by the setup on the **Location directive failures** page, where you can decide whether to select the **Stop work on location directive failure** option for each work order type.

## Next step

After you create location directives, you can associate each directive code with a work template code for work creation. For more information, see [Control warehouse work by using work templates and location directives](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/control-warehouse-location-directives).

### Additional resources

- Video: [Warehouse management configuration deep dive](https://community.dynamics.com/365/b/techtalks/posts/warehouse-management-configuration-deep-dive-october-14-2020)
- Help topic: [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md)