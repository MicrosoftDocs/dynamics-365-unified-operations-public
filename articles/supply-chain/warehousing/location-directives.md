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

## Open the Location directives page

To open the page, go to **Warehouse management \> Setup \> Location directives**.

## Location Directive Work Order Types

Location directives have many common fields that are available for setup in each of the work order types. There are also fields specific to certain work order types. 

![Location directives work order types](media/Location_Directives_Work_Order_Types.png "Location directives work order types")

>[!NOTE]
>Two work order types, **Canceled work** and **Cycle counting**, are used only by the system and location directives cannot be created for these work order types.

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

### Fields specific to work order types

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

## The Location directives Action Pane

The **Location directives** page Action Pane contains options to create, edit, and delete directives (**Edit**, **New** and **Delete**); adjust the sequence in which the location directive is processed (**Move up** and **Move down**); and to configure a query (**Edit query**), which specifies what criteria the location directive is to be applied.

- **Move up** - Moves the selected location directive up in the sequence. For example, from sequence number 4 to sequence number 3.
- **Move down** - Moves the selected location directive down in the sequence. For example, from sequence number 4 to sequence number 5.
- **Edit query** - Opens a dialog box where you to define the conditions on which the selected location directive will be processed. For example, you may want to apply a given location directive only for a specific warehouse.

## Location directives header

The location directive header is where you set the sequence number for the location directive and where you establish the location directives descriptive name.

- **Sequence number** - Indicates the sequence in which the system tries to apply each location directive for selected order type. It can be changed using **Move Up** and **Move Down** on the Action Pane. Low numbers are applied first.

- **Name** - Descriptive name for the location directive. It should help identify the general purpose of the directive. For example, *Sales order picking in warehouse 24*.

## The Location directives FastTab

The fields displayed on the **Location directives** FastTab are specific to the **Work order type** selected in the list pane. Below is a list of fields that a user will see displayed in the FastTab.

- **Work type** - Select the type of work to be performed. The type of work available is based on the type of inventory transaction that you have selected in the **Work order type** field. Select one of the following:

  - **Put** - The location directive will try to find the most ideal location to place or locate inventory coming into the system either from receiving, production, or inventory adjustments. It can also used to define put to stage location or final bay door shipping location.

  - **Pick** - The location directive will try to find the most ideal location(s) to physically reserve inventory from (create work). The pick can be completed (pick work line can be closed), even if the work is not completed. The user can complete physically picking and in the system that is pick step, then user can cancel from the mobile device and complete the work (eg. Put) later. Work header however is first closed when final put is completed.

    >[!IMPORTANT]
    >**Counting, Adjustments, Custom, Inventory status change, License plate building, print, Status change, Pack to nested license plates** - These are not usable in any location directive setup. It is a enum so there is no any filtering connected to Work order type.

- **Site** - Site is mandatory as Location directive needs to know what site and warehouse it is valid for.

- **Warehouse** - Warehouse is mandatory as Location directive needs to know what site and warehouse it is valid for.

- **Directive code** - Select the directive code to associate to a work template or replenishment template. On the form Directive code you can create new codes that can be used for connections between work template replenishment template and location directive. It can also be used to establish the link between any work template line and location directive (eg. Baydoor, stage location).

    > [!TIP]
    > If a directive code is set, when work is to be generated the system will not search location directives by sequence number, but by Directive code. In this way you can be more specific what location template is used for certain step in work template like for staging of the materials.

- **Multiple SKU** - Selecting **Yes** will enable the use of multiple Stock Keeping Units (SKU) on a location. E.g. the Baydoor needs to have it enabled.  If we enable multiple SKU, our put location will be specified in work (this is expected), but it will only be able to handle a multiple item put (if work includes different SKUs to be picked and put), not a single SKU put. If we select **No** for **Multiple SKU**, our put location will only be specified if our put has only one kind of SKU.

    > [!IMPORTANT]
    > To be able to do both options we need to specify two lines, one with multiple SKU **Yes**, and one with Multiple SKU **No** that have same structure and setup. So basically, for our put operations we need to have to location directives that are identical, even that we do not need to distinguish between single and multiple SKUs on work ID. Not doing this often results in unexpected business process locations coming from the used **Location directive**. Please note that you need to set it up for pick as well (if you have an order with more than one items).

    The **Multiple SKU** option on the **Location directives** is used for work lines handling more than one item number (it shows up as blank in the work details and as "Multiple" on the **Warehouse app** processing pages.

    An typical example scenario would be when using a **Work template** setup with more than one *Pick/Put* pair. Here you might want to search for a specific put ***Staging location type***.

    >[!Note]
    >You will not be able to use the **Edit query** option when having the **Multiple SKU** enabled because the query cannot evaluate on item level, when having multiple items. To make sure the desired **Location directive** gets selected you can use the **Directive code** to guide the selection of the **Location directive** related to the work template put lines having this **Directive code** assigned.

    Unless you always only operate with single item or mixed item operations, it is important to define two **Location directives** for the **_Put_** **Work type**. One with the **Multiple SKU** enabled and another without.

- **Applicable disposition code** - Specify if the disposition code of the location directive must match the disposition code that is applied at item receiving or if the location directive can be selected based on any disposition code. If you select Exact match and the Disposition code field is blank, only blank disposition codes will be considered for this location directive.

    >[!IMPORTANT]
    >This field is available only on selected **Work order types** where replenishment is permitted, see the table **Fields specific to work order types** at the beginning of this topic for the complete list.

- **Locate by** - Determines if the put away quantity will be the entire quantity on the license plate, or if it will be item by item. Use this setting to help guarantee that all the content on a license plate is put into one location, and that the system does not suggest that you split the contents into several locations for **ASN** (License plate receiving), **Mixed license plate** receiving, and **Cluster** receiving processes (requires that *Cluster Putaway Feature* is enabled). Note that the behavior of the location directive query and the lines and Location directive actions will vary, depending on the value that you select. The lines restriction section will only be used when using **Item**.

    >[!IMPORTANT]
    >This field is available only on selected **Work order types** where replenishment is permitted, see the table **Fields specific to work order types** at the beginning of this topic for the complete list.

- **Disposition code** - Disposition code is used on *Purchase orders*, *Finished goods putaway*, and *Return orders* type **Put** location directives. It is used to guide the flow to use a specific location directive, depending on disposition code selected by the user on the warehouse mobile application. For example, to direct returned goods to an Inspection location before being returned to stock. Note that a disposition code can be linked to an inventory status and thereby used to change the inventory status as part of a receiving process. So, let's say you set disposition code “QA” that sets an inventory status “QA” and then you can have a separate location directive to move that inventory to a quarantine location.

    >[!IMPORTANT]
    >This field is available only on selected **Work order types** where replenishment is permitted, see the table **Fields specific to work order types** at the beginning of this topic for the complete list.

## Location directive Lines FastTab

The location directive lines set additional restrictions on the application of the location finding rules. You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit.

- **Sequence number** - Enter the sequence in which the location directive line are processed for the selected work type. You can also modify the sequence, if needed using the move up and move down buttons in the **Lines** toolbar.

- **From quantity** - Specify the beginning quantity range for when the middle-grid sequence should be selected. Specify the quantity in the unit of measure that is selected in the **Unit** field.

- **To quantity** - Specify the ending quantity range for when the middle-grid sequence should be selected. Specify the quantity in the unit of measure that is selected in the **Unit** field.

- **Unit** - Select the unit of measure for the items. You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit. The unit field on line is used *only* for quantity evaluation. When checking if the location directive line is applicable at all, it will do that based on the quantity in the respective unit specified on the location directive line. Every time location directive line is reached system will try to convert demand unit to a unit specified on the line, if the UOM conversion does not exist it will continue to a next line.

- **Locate quantity** - this only comes into use when trying to put or locate quantity into the warehouse. So it is only for the *Put* work type. The valid values are described below:

  - **License plate quantity** - When evaluating whether or not a quantity is within the *From quantity* and *To quantity* ranges, use the quantity on the license plate being received.

  - **Unitized quantity** - When evaluating whether or not a quantity is within the *From quantity* and *To quantity* ranges, use the quantity being unitized during the specific transaction. For example, in a warehouse, if you can receive a quantity of 1,000 and break it into 10 license plates, each of which has a quantity of 100, you can use a quantity of 1,000 items instead of the license plate quantity of 100.

  - **Remaining quantity** - When evaluating whether or not a quantity is within the "From" and "To" quantity ranges, what is the quantity left to be received on the Purchase Order Line currently being checked-in.

  - **Expected quantity** - When evaluating whether or not a quantity is within the "From" and "To" quantity ranges, use the total quantity of the Purchase Order Line, regardless of what has already been received.

- **Restrict by unit** - Restrict by unit, allows location directive line to be made specific to a unit of measure or multiple units of measure. Select this check box to restrict the units of measure that are considered valid selection criteria for the location directive lines. This works only with the location directives of **Work type** *Pick*.

  - For example, when reserving quantity, if we only want to reserve pallets from a specific set of locations, then the middle-grid sequence would restrict that particular sequence to pallets so that any quantity less than a pallet would not be selected in the sequence.

  - However, the **Restrict by unit** check box doesn't control the unit or units that are applied on work lines. The unit restriction applies only to the units that are made available via the unit sequence group.

  - For example, an item is associated with a unit sequence group that includes both the pallets and the pcs units. A unit of measure has been defined where 1 pallet = 100 pcs, and the location directive uses the Restrict by unit functionality only for pallets. Furthermore, a work template has been defined that limits the work header creation to 50 pcs. In this case, work lines of 50 pcs will be created.

  - To specify the unit of measure for restriction, follow these steps:

    - On the **Lines** FastTab, select **Restrict by unit**. This button becomes available only after you select the **Restrict by unit** check box on the line and then select **Save**.

    - In the **Unit** field, select the unit of measure to restrict by for the pick and putaway processes.

- **Round up to unit** - This field works together with the field Restrict by unit. If the location directive line **Restrict by unit** is set to e.g. *box*, and selecting **Round up to unit** indicates that the work generated out of the directive for raw material picking should be rounded up to a multiple of one handling unit specified in restrict by unit.

    >[!IMPORTANT]
    >Please note that this **Round up to unit** setup works only for **Work order type** *Raw material picking*. This works only with the location directives of **Work type** *Pick*.

- **Locate Packing Qty** – If you specify a packing quantity on a sales order, transfer order or a production order, this checkbox restricts the system to only select locations with at least that packing quantity in the location.

    >[!IMPORTANT]
    >This works only with the location directives of type pick.

- **Allow Split** – This specifies if location directive is allowed to split the quantity being received or the quantity being reserved across multiple warehouse locations or if the entire quantity must be located to a single location or reserved from a single location in order to create work.

- **Immediate replenishment template** - Create a connection to a replenishment template, so that replenishment is started immediately if items aren't allocated. If you leave this field blank, item replenishment won't be started until all lines of the location directive have been processed.

    >[!IMPORTANT]
    >This field is available only on selected **Work order types** where replenishment is permitted, see the table **Fields specific to work order types** at the beginning of this topic for the complete list.

## Location directive actions

You can define multiple location directive actions for each line. Once again, a sequence number is used to determine the order that the actions are assessed in. On this level, you can set up a query to define how to find the best location in the warehouse. You can also use predefined **Strategy** settings to find an optimal location.

- **Sequence number** - The sequence in which the location directive is processed for the selected work type is displayed. You can modify the sequence, if needed.

    >[!IMPORTANT]
    >Be careful about sequence numbers as they will always run by these.

- **Name** - Enter the name for the location directive action. Be specific so it is clear from the name what action is performed.

- **Fixed location usage** - Determines which locations the location directive considers. If you select Fixed and non-fixed locations, all locations are considered. Select one of the following values:

  - **Fixed and non-fixed locations** - The location directive will consider all locations.

  - **Only fixed locations for the product** - The location directive will consider only fixed locations for products.

  - **Only fixed locations for the product variant** - The location directive will consider only fixed locations for product variants.

- **Allow negative inventory:** -Select this check box to allow negative inventory at the specified warehouse location in location directives.

- **Batch Enabled** - Select this check box to use batch strategies for the items that are batch enabled. For processes using the **Location directives** to find locations to pick  batch number tracked items from, it is important to select the **Batch enabled** setting to include the search for locations holding batch number tracked items. If this check box is selected, and the **Strategy** field is set to *None*, the system will move on to the next action line.

- **Strategy** - To make it easier and quicker to define the actions that are associated with each location directive line, use one of the predefined strategies.

  - **None** - No strategy will be used.

  - **Match packing quantity** -  This strategy is used to verify whether a pick location has the specified packing quantity. This strategy is valid only when the **Work type** field is set to *Pick*.

  - **Consolidate** - This strategy consolidates items in a specific location when similar items are already available. This strategy is valid only when the **Work type** field is set to *Put*. Common setup for put will be to try to consolidate on first action line and on second try to put without consolidation. Consolidating goods makes later picking more efficient.

  - **FEFO batch reservation** -  This strategy is used when inventory is located using a batch expiration date and is allocated for batch reservation. You can only use this strategy for batch enabled items. See above. This strategy is only working for *Pick* work type of location directive.
  
  - **Round up to the full LP and FEFO batch** - This strategy combines the elements of **FEFO batch reservation** and **Round up to a full LP**. It is only valid for batch enabled items and *Pick* work type location directives. The line must be batch enabled to use FEFO Batch Reservation strategy and rounding up to LP strategies can only be used for replenishment. Please note, if this strategy is configured together with location stocking limit, it can cause selected Put work location overload and ignore stocking limits.

  - **Round up to a full LP** - This strategy is used to round up the inventory quantity to match the license plate (LP) quantity that is assigned to the items to be picked. You can only use this strategy for replenishment type of Location directives for type Pick. Please note, if this strategy is configured together with location stocking limit, it can cause selected Put work location overload and ignore stocking limits.
  
  - **License plate guided** - When you release the order to the warehouse to create the pick-and-put work, the **License plate guided** strategy on the location directive is used. You can do this for multiple license plates. The License plate guided strategy will try to reserve and create picking work against the locations holding the requested license plates that have been associated with the transfer order lines. But if this isn't possible and you still would like to create picking work, you should fall back to another location directive action strategy, and perhaps also search for inventory in another area of the warehouse, depending on your business process needs.

  - **Empty location with no incoming work** - This strategy is used to locate empty locations. The location is considered empty if it has no physical inventory and no expected incoming work. This strategy is used only for PUT type of location directive.
  
  - **Location aging FIFO** - You can use the FIFO strategy to ship both batch-tracked items and non-batch-tracked items, based on the date when the inventory entered the warehouse. This capability can be especially useful for non-batch-tracked inventory, where an expiration date isn't available to use for sorting. The FIFO strategy finds the location that contains the oldest aging date, and it allocates picking based on that aging date.
  
  - **Location aging LIFO** - You can use the LIFO strategy to ship both batch-tracked items and non-batch-tracked items, based on the date when the inventory entered the warehouse. This capability can be especially useful for non-batch-tracked inventory, where an expiration date isn't available to use for sorting. The LIFO strategy finds the location that contains the newest aging date, and it allocates picking based on that aging date.

## Example of the use of location directives

For this example, consider a purchase order process where the location directive must find free capacity within a warehouse for inventory items that have just been registered at the receiving dock. First, you need to find free capacity within the warehouse by consolidating with existing on-hand inventory. If consolidation isn't possible, then you need to find an empty location.

For this scenario, you must define two location directive actions. The first action in the sequence must use the **Consolidate** strategy, and the second should use the **Empty location with no incoming work** strategy. Unless you define a third action to handle an overflow scenario, two outcomes are possible when there is no more capacity in the warehouse: work can be created even though no locations are defined, or the work creation process can fail. The outcome is determined by the setup on the **Location directive failures** page, where you can decide whether to select the **Stop work on location directive failure** option for each work order type.

### Additional resources

- Video: [Warehouse management configuration deep dive](https://community.dynamics.com/365/b/techtalks/posts/warehouse-management-configuration-deep-dive-october-14-2020)
- Help topic: [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md)
- Help topic: [Create location directives](create-location-directive.md)
