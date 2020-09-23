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

# ms.search.form:  [Operations AOT form name to tie this topic to]
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

<!--KFM: Describe briefly how to do this (nav path). Mention that the rest of the sections here describe the settings shown. Maybe add a screenshot (better than the ones in the Word file). I think one screen shot is probably enough. -->

## Location directives header

<!--KFM: Briefly tell what settings to in this area (if possible) and introduce the bullet list -->

- **Sequence number** - Sequence in which location directive is tried to be processed for selected order type. It can be changed using Move Up and Move Down on the menu.

- **Work type** - Select the type of work to be performed. The type of work available is based on the type of inventory transaction that you have selected in the Work order type field.

  - **Put** - A work type equal to "Put" means that the location directive is going to try and find the most ideal location to place or locate inventory coming into the system either from receiving, production, or inventory adjustments. It can be as well used to define put to stage location or final bay door shipping location.

  - **Pick** - A work type equal to "pick" means that WHS is going to try and find the most ideal location/s to physically reserve inventory from (Create work). The pick can be completed (pick work line can be closed), even if the work is not completed. The user can complete physically picking and in the system that is pick step, then user can cancel from the mobile device and complete the work (eg. Put) later. Work header however is first closed when final put is completed.

  - **Counting, Adjustments, Custom, Inventory status change, License plate building, print, Status change, Pack to nested license plates** - These are not usable in any location directive setup. It is a enum so there is no any filtering connected to Work order type.

- **Directive code** - Select the directive code to associate to a work template or replenishment template. On the form Directive code you can create new codes that can be used for connections between work template replenishment template and location directive. It can also be used to establish the link between any work template line and location directive (eg. Baydoor, stage location). Please note that if code is set, when work is to be generated system will not search location directive by sequence, but by Directive code. In this way you can be more specific what location template is used for certain step in work template like for staging of the materials.

- **Site** - Site is mandatory as Location directive needs to know what site and warehouse it is valid for.

- **Warehouse** - Warehouse is mandatory as Location directive needs to know what site and warehouse it is valid for.

- **Multiple SKU** - This will enable to use multiple Stock Keeping Units on a location. E.g. the Baydoor needs to have it enabled.  If we tick multiple SKU, our put location will be specified in work (this is expected), but it will only be able to handle multiple item put (if work includes different SKUs to be picked and put, not a single SKU put. If we un-tick multiple SKU, our put location will only be specified if our put has only one kind of SKU. For being able to do both we need to specify two lines one with multiple SKU on, and one with Multiple SKU off that have same structure and setup. So basically, for our put operations we need to have to location directives that are identical, even that we do not need to distinguish between single and multiple SKUs on work ID. Please note that you need to set it up for pick as well (if you have an order with more than one items).

## Location directive Lines
<!--KFM: Briefly tell what settings to in this area (if possible) and introduce the bullet list -->
- **Sequence number** - Enter the sequence in which the location directive line are processed for the selected work type. You can also modify the sequence, if needed using the move up and move down.

- **From / To quantity** - Unit – this gives the ability to specify a quantity range for when this middle-grid sequence should be selected. You can specify the From/To range on Qty in the respective unit.

- **Unit** - You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit. The unit field on line is used only for quantity evaluation. When checking if the location directive line is applicable at all, it will do that based on the quantity in the respective unit specified on the location directive line. Every time location directive line is reached system will try to convert demand unit to a unit specified on the line, if the UOM conversion does not exist it will continue to a next line.

- **Locate quantity** - this only comes into use when trying to "put"/locate quantity into the warehouse. So it is only for PUT work type. The valid values are described below:

  - **License Plate Qty** - When evaluating whether or not a quantity is within the "From" and "To" quantity ranges, use the quantity on the license plate being received.

  - **Unitized Qty** - When evaluating whether or not a quantity is within the "From" and "To" quantity ranges, use the quantity being unitized during the specific transaction.

  - **Remaining Qty** - When evaluating whether or not a quantity is within the "From" and "To" quantity ranges, what is the quantity left to be received on the Purchase Order Line currently being checked-in.

  - **Expected Qty** - When evaluating whether or not a quantity is within the "From" and "To" quantity ranges, use the total quantity of the Purchase Order Line, regardless of what has already been received

- **Restrict by unit:** - Restrict by unit, allows location directive line to be made specific to a unit of measure or multiple units of measure. When reserving quantity, if we only want to reserve pallets from a specific set of locations, then the middle-grid sequence would restrict that particular sequence to "PL" so that any quantity less than a pallet would not select the sequence. In order to setup the units, we need to select the checkbox. In addition to that, we can restrict the line to more than one units. This works only with the location directives of type pick.

- **Round up to unit** - This field works together with the field Restrict by unit. If the location directive line "restrict by unit" is set to e.g. box, and selecting Round up to unit indicates that the work generated out of the directive for raw material picking should be rounded up to a multiple of one handling unit specified in restrict by unit. Please note that this setup works only for raw material picking. This works only with the location directives of type pick.

- **Locate Packing Qty** – If you specify a packing quantity on a sales order, transfer order or a production order, this checkbox restricts the system to only select locations with at least that packing quantity in the location. This works only with the location directives of type pick.

- **Allow Split** – this specifies if location directive is allowed to split the quantity being received or the quantity being reserved across multiple warehouse locations or if the entire quantity must be located to a single location or reserved from a single location in order to create work.

## Location directive actions
<!--KFM: Briefly tell what settings to in this area (if possible) and introduce the bullet list -->
- **Sequence number** - The sequence in which the location directive is processed for the selected work type is displayed. You can modify the sequence, if needed. Be careful about sequence numbers as they will always run by these.

- **Name** - Enter the name for the location directive action. Be specific so it is clear from name

- **Fixed location usage** - Select one of the following values:

  - **Fixed and non-fixed locations** - The location directive will consider all locations.

  - **Only fixed locations for the product** - The location directive will consider only fixed locations for products.

  - **Only fixed locations for the product variant** - The location directive will consider only fixed locations for product variants.

- **Allow negative inventory:** -Select this check box to allow negative inventory at the specified warehouse location in location directives.

- **Batch Enabled** - Select this check box to use batch strategies for the items that are batch enabled. If you hit this line where Batch enabled is set with a none batch item it will just proceed to next action line.

- **Strategy** - Select one of the following values:

  - **Consolidate** - This strategy is used in Microsoft Dynamics AX to consolidate items in a particular location when similar items are already available. This works only for the PUT type of location directive. Common setup for put will be to try to consolidate on first action line and on second try to put without consolidation. Consolidating goods makes later picking more efficient.

  - **Match packing quantity** -  This strategy is used to verify whether a pick location has the specified packing quantity. This will only work for location directive of type Pick.

  - **FEFO batch reservation** -  This strategy is used when inventory is located using a batch expiration date and is allocated for batch reservation. You can only use this strategy for batch enabled items. See above. This strategy is only working for PICK work type of location directive.

  - **Round up to a full LP** - This strategy is used to round up the inventory quantity to match the license plate (LP) quantity that is assigned to the items to be picked. You can only use this strategy for replenishment type of Location directives for type Pick.

  - **Empty location with no incoming work** - This strategy is used to locate empty locations. The location is considered empty if it has no physical inventory and no expected incoming work. This strategy is used only for PUT type of location directive.

