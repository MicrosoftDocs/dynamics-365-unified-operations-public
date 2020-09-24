---
# required metadata

title: Work with location directives
description: This topic describes how to work with location directives
author: Mirzaab
manager: tfehr
ms.date: 09/23/2020
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
ms.search.validFrom: 2020-09-23
ms.dyn365.ops.version: Release 10.0.15
---
# Work with location directives

<!--KFM: We should have a general intro here. What is this feature, what does it do, why do I need it? -->

[!include [banner](../includes/banner.md)]

## Open the Location directives page

Location directives are rules that help identify pick and put locations for inventory movement. For example, in a sales order transaction, a location directive determines where the items will be picked, and where the picked items will be put. Location directives consist of a header and associated lines. Location directives are created for specific *Work order types*.

 - Go to **Warehouse management \> Setup \> Location directives**

## Location directives Action Pane

The Location directives Action pane contains, in addition to **Edit**, **New** and **Delete**; options to adjust the sequence in which the location directive is processed, **Move up** and **Move down**, as well as to configure a query, **Edit query**, which specifies what criteria the location directive is to be applied.

- **Move up** - Moves the selected location directive up in the sequence. For example, from Sequence number 4 to Sequence number 3.
- **Move down** - Moves the selected location directive down in the sequence. For example, from Sequence number 4 to Sequence number 5.
- **Edit query** - The Edit query option allows you to define the conditions on which the selected location directive will be processed. For example, you may want to only apply a specific location directive to work in one warehouse.

## Location directives header

The location directive header is where you set the sequence number for the location directive and where you establish the location directives descriptive name.

- **Sequence number** - Sequence in which location directive is tried to be processed for selected order type. It can be changed using Move Up and Move Down on the Action Pane.

- **Name** - Descriptive name for the location directive. It should help identify the general purpose of the directive. For example, Sales order Picking in Warehouse 24.

## Location directives

The fields displayed on the Location directives FastTab are specific to the **Work order type** selected in the Navigation list. Below is a list of fields that a user will see displayed in the FastTab.

- **Work type** - Select the type of work to be performed. The type of work available is based on the type of inventory transaction that you have selected in the Work order type field.

  - **Put** - A work type equal to "Put" means that the location directive is going to try and find the most ideal location to place or locate inventory coming into the system either from receiving, production, or inventory adjustments. It can be as well used to define put to stage location or final bay door shipping location.

  - **Pick** - A work type equal to "pick" means that WHS is going to try and find the most ideal location/s to physically reserve inventory from (Create work). The pick can be completed (pick work line can be closed), even if the work is not completed. The user can complete physically picking and in the system that is pick step, then user can cancel from the mobile device and complete the work (eg. Put) later. Work header however is first closed when final put is completed.

  - **Counting, Adjustments, Custom, Inventory status change, License plate building, print, Status change, Pack to nested license plates** - These are not usable in any location directive setup. It is a enum so there is no any filtering connected to Work order type.

- **Site** - Site is mandatory as Location directive needs to know what site and warehouse it is valid for.

- **Warehouse** - Warehouse is mandatory as Location directive needs to know what site and warehouse it is valid for.

- **Directive code** - Select the directive code to associate to a work template or replenishment template. On the form Directive code you can create new codes that can be used for connections between work template replenishment template and location directive. It can also be used to establish the link between any work template line and location directive (eg. Baydoor, stage location).

> [!NOTE]
> Please note that if a directive code is set, when work is to be generated the system will not search location directives by sequence number, but by Directive code. In this way you can be more specific what location template is used for certain step in work template like for staging of the materials.

- **Multiple SKU** - Selecting **Yes** will enable the use of multiple Stock Keeping Units on a location. E.g. the Baydoor needs to have it enabled.  If we tick multiple SKU, our put location will be specified in work (this is expected), but it will only be able to handle a multiple item put (if work includes different SKUs to be picked and put), not a single SKU put. If we select **No** for **Multiple SKU**, our put location will only be specified if our put has only one kind of SKU.

> [!TIP]
> To be able to do both options we need to specify two lines, one with multiple SKU **Yes**, and one with Multiple SKU **No** that have same structure and setup. So basically, for our put operations we need to have to location directives that are identical, even that we do not need to distinguish between single and multiple SKUs on work ID. Please note that you need to set it up for pick as well (if you have an order with more than one items).

- **Applicable disposition code** - Specify if the disposition code of the location directive must match the disposition code that is applied at item receiving or if the location directive can be selected based on any disposition code. If you select Exact match and the Disposition code field is blank, only blank disposition codes will be considered for this location directive.

- **Locate by** -

- **Disposition code** -

## Location directive Lines

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

>[!NOTE]
>Please note that this **Round up to unit** setup works only for **Work order type** *Raw material picking*. This works only with the location directives of **Work type** *Pick*.

- **Locate Packing Qty** – If you specify a packing quantity on a sales order, transfer order or a production order, this checkbox restricts the system to only select locations with at least that packing quantity in the location. This works only with the location directives of type pick.

- **Allow Split** – This specifies if location directive is allowed to split the quantity being received or the quantity being reserved across multiple warehouse locations or if the entire quantity must be located to a single location or reserved from a single location in order to create work.

- **Immediate replenishment template** - Create a connection to a replenishment template, so that replenishment is started immediately if items aren't allocated. If you leave this field blank, item replenishment won't be started until all lines of the location directive have been processed.

  - This field is available only on selected **Work order types** where replenishment is permitted, such as *Sales orders* and *Raw material picking*.

## Location directive actions

You can define multiple location directive actions for each line. Once again, a sequence number is used to determine the order that the actions are assessed in. On this level, you can set up a query to define how to find the best location in the warehouse. You can also use predefined **Strategy** settings to find an optimal location.

- **Sequence number** - The sequence in which the location directive is processed for the selected work type is displayed. You can modify the sequence, if needed. Be careful about sequence numbers as they will always run by these.

- **Name** - Enter the name for the location directive action. Be specific so it is clear from the name what action is performed.

- **Fixed location usage** - Determines which locations the location directive considers. If you select Fixed and non-fixed locations, all locations are considered. Select one of the following values:

  - **Fixed and non-fixed locations** - The location directive will consider all locations.

  - **Only fixed locations for the product** - The location directive will consider only fixed locations for products.

  - **Only fixed locations for the product variant** - The location directive will consider only fixed locations for product variants.

- **Allow negative inventory:** -Select this check box to allow negative inventory at the specified warehouse location in location directives.

- **Batch Enabled** - Select this check box to use batch strategies for the items that are batch enabled. If this check box is selected, and the **Strategy** field is set to *None*, the system will move on to the next action line.

- **Strategy** - Select one of the following values:

  - **None** - No strategy will be used.

  - **Consolidate** - This strategy consolidates items in a specific location when similar items are already available. This strategy is valid only when the **Work type** field is set to *Put*. Common setup for put will be to try to consolidate on first action line and on second try to put without consolidation. Consolidating goods makes later picking more efficient.

  - **Match packing quantity** -  This strategy is used to verify whether a pick location has the specified packing quantity. This strategy is valid only when the **Work type** field is set to *Pick*.

  - **FEFO batch reservation** -  This strategy is used when inventory is located using a batch expiration date and is allocated for batch reservation. You can only use this strategy for batch enabled items. See above. This strategy is only working for PICK work type of location directive.

  - **Round up to a full LP** - This strategy is used to round up the inventory quantity to match the license plate (LP) quantity that is assigned to the items to be picked. You can only use this strategy for replenishment type of Location directives for type Pick.

  - **Empty location with no incoming work** - This strategy is used to locate empty locations. The location is considered empty if it has no physical inventory and no expected incoming work. This strategy is used only for PUT type of location directive.

## Example of the use of location directives

For this example, consider a purchase order process where the location directive must find free capacity within a warehouse for inventory items that have just been registered at the receiving dock. First, you need to find free capacity within the warehouse by consolidating with existing on-hand inventory. If consolidation isn't possible, then you need to find an empty location.

For this scenario, you must define two location directive actions. The first action in the sequence must use the **Consolidate** strategy, and the second should use the **Empty location with no incoming work** strategy. Unless you define a third action to handle an overflow scenario, two outcomes are possible when there is no more capacity in the warehouse: work can be created even though no locations are defined, or the work creation process can fail. The outcome is determined by the setup on the **Location directive failures** page, where you can decide whether to select the **Stop work on location directive failure** option for each work order type.
