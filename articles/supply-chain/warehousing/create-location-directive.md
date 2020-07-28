---
# required metadata

title: Create a location directive
description: This topic explains how to create location directives. Location directives are user-defined rules that help identify pick and put locations for inventory movement.
author: Mirzaab
manager: tfehr
ms.date: 07/28/2020
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
ms.search.validFrom: 2020-07-28
ms.dyn365.ops.version: Release 10.0.9
---

# Create a location directive

[!include [banner](../includes/banner.md)]

This topic explains how to create location directives. Location directives are user-defined rules that help identify pick and put locations for inventory movement. For example, in a sales order transaction, a location directive determines where the items will be picked and where the picked items will be put.

> [!NOTE]
> This topic applies to features in the *Warehouse management* module. It does not apply to features in the [Inventory management](../inventory/inventory-home-page.md) module.

You can use location directives to do the following:

- Put away incoming items.
- Pick and stage items for outbound transactions.
- Pick and put raw materials for production.
- Replenish locations.

## Prerequisites

The following prerequisites must be in place before you create a location directive:

1. Go to **Warehouse management > Setup > Warehouse > Warehouses**.
1. Create a warehouse.
1. On the **Warehouse** FastTab, set **Use warehouse management processes** to *Yes*.
1. Create locations, location types, location profiles, and location formats (see also [Configure locations in a WMS-enabled warehouse](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/configure-locations-wms-enabled-warehouse)).
1. Create sites, zones, and zone groups (see also [Warehouse set up](https://docs.microsoft.com/dynamics365/commerce/channels-setup-warehouse) and [Configure locations in a WMS-enabled warehouse](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/configure-locations-wms-enabled-warehouse)).

## Setup

### Create location directives

To create a location directive, follow these steps:

1. Select **Warehouse management > Setup > Location directives**.

1. On the list pane, set **Work order type** to the type of inventory transaction for which you want to create a location directive.

1. On the Action Pane, select **New** to create a new location directive and make the settings described in the following table.

    | Field | Description |
    |---|---|
    | **Sequence number** | This sets the sequence in which location directives will be processed for the selected order type. Enter an integer to indicate the position at which this location directive should be processed for the selected work type. You can modify the sequence if needed. |
    | **Name** |Enter a name for the location directive.  | 
    | **Work type** | Select the type of work to be performed. The types of work available depend on the type of inventory transaction that you have selected in the **Work order type** field on the list pane. The following values may be available: <ul><li>**Put** - The location directive will try to find the most ideal location to place or locate inventory coming into the system from receiving, production, or inventory adjustments. It  is also used to define the put-to-stage location or final bay door shipping location in the outbound flow.</li><li>**Pick** - The location directive will try to find the most ideal location(s) to physically reserve inventory from (create work). The pick can be completed (pick work line can be closed), even if the work is not completed. The user can complete physically picking and in the system that is pick step, then user can cancel from the mobile device and complete the work (eg. Put) later. Work header however is first closed when final put is completed.</li><li>**Counting, Adjustments, Custom, Inventory status change, License plate building, print, Status change, Pack to nested license plates**: These are not usable in any location directive setup. </li></ul> |
    | **Site** | Select the site where the work should be completed.  |
    | **Warehouse** | Select the warehouse location where the work should be completed.  |
    | **Directive code** | Select a directive code to guide the selection of location directives related to the work template put lines that have this code assigned. On the **Directive code** page, you can create new codes for connecting a work template to a location directive. It can also be used to establish the link between any work template line and location directive (such as bay door or stage location). For details about how to configure a directive code with a work template, see [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md). <br><br>If a directive code is set, then when work is to be generated, the system won't search location directives by sequence, but by **Directive code**. In this way you can be more specific about which location template is used for a certain step in a work template, such as for staging of the materials. |
    | **Disposition code** | Select a disposition code to redirect the put away of the received items to a location (see also [Set up dispositions codes](tasks/set-up-dispositions-codes.md)). This field is only available when the **Work order type** field is set to *Purchase orders*, *Return orders* or *Finished goods put away*. |
    | **Multiple SKU** | Set this to *Yes* to use multiple stock keeping units (SKUs) on a location. For example, the bay door needs to have it enabled.<br><br>If **Multiple SKU** is set to *Yes*, the put location will be specified in work (this is expected), but it will only be able to handle multiple-item put if work includes different SKUs to be picked and put (not a single SKU put).<br><br>If **Multiple SKU** is set to *No*, the put location will only be specified if the put has only one kind of SKU.<br><br>To be able to do both, you must specify two lines that have same structure and setup, except one has **Multiple SKU** set to *Yes*, and the other one has **Multiple SKU** set to *No*. This means that for put operations, it is required to have two location directives that are identical, even though we don't need to distinguish between single and multiple SKUs on work ID. Note that you must also set it up for pick (if you have an order with more than one item).<br><br>**Note:** If you enable **Multiple SKU** for a location directive of the work type put, the first location directive line will always be selected by the system, regardless of other restrictions created in the lines.
     |

1. *Optional*: Select **Edit query** in the Action Pane to select the locations or to specify any restrictions that apply when you select a specific location directive.

1. On the **Lines** FastTab, create one or more lines to specify units and to locate or reserve quantity in a warehouse. Fill in the fields as described in the following table.

    | Field | Description |
    |---|---|
    | **Sequence number** | This sets the sequence in which location directive lines will be processed. Enter an integer to indicate the position at which each location directive line should be processed for the selected work type. You can modify the sequence if needed. |
    | **From quantity** | Enter the starting range of the quantity of the items for which work should be performed. Specify the quantity using the unit specified in the **Unit** column. |
    | **To quantity** | Enter the ending range of the quantity of the items for which work should be performed.  Specify the quantity using the unit specified in the **Unit** column. |
    | **Unit** | Select the unit of measure for the items.<br><br>You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit. The **Unit** field is used only for quantity evaluation.<br><br>When deciding whether a location directive line applies, the system evaluates quantities using the **Unit** specified on the line. Every time a location directive line is accessed, the system will try to convert demand unit to the unit specified on the line, if the unit conversion does not exist, it will continue to the next line. |
    | **Locate quantity** | This is only valid when trying to put/locate quantity at the warehouse. It is therefore only valid for **Put** work. Select the method used to check whether the quantity is in the range that is set in the **From quantity** and **To quantity** fields. If the location directive is for an inbound transaction, select one of the following options:<ul><li>**License plate quantity** ─ When evaluating whether or not a quantity is within the “From” and “To” quantity ranges, use the quantity on the license plate being received.</li><li>**Unitized quantity** ─ When evaluating whether or not a quantity is within the “From” and “To” quantity ranges, use the quantity being unitized during the specific transaction. For example, in a warehouse if you can receive a quantity of 1000 and break it into 10 license plates of 100 each, you can use a quantity of 1000 items instead of the license plate quantity of 100.</li><li>**Remaining quantity** ─ When evaluating whether or not a quantity is within the “From” and “To” quantity ranges, what is the quantity left to be received on the Purchase Order Line currently being checked-in.</li><li>**Expected quantity** ─ When evaluating whether or not a quantity is within the “From” and “To” quantity ranges, use the total quantity of the Purchase Order Line, regardless of what has already been received. |

1. *Optional*: You can select the following additional settings on the **Lines** FastTab.

    | Field | Description |
    |---|---|
    | **Restrict by unit** | Select this check box to restrict the units of measure that are to be considered as valid selection criteria for the location directive lines. When units of measure have been specified, only those items with a unit that matches at least one unit defined for the unit sequence group will be considered as valid for the line selection.
    |  | For example, say that the unit is restricted to pallets and the item is associated with a unit of measures sequence group that includes pallets. In this case the items will be considered a valid choice for the location directive. |
    |  | However, the **Restrict by unit** check box does not control the unit or units that are applied on work lines. The unit restriction only restricts the units that are made available via the unit sequence group. |
    |  | For example, say that an item is associated with a sequence group that includes both the Pallets and the Pcs units. A unit of measure has been defined with 1 pallet = 100 pcs and the location directive uses Restrict by unit for pallets only. Furthermore a work template has been defined that breaks the work header creation by 50 pcs. In this case work lines of 50 pcs will be created. |
    |  | To specify the unit of measure for restriction: |
    |  | a. Select **Restrict by unit**. This button is available only when you press **Ctrl+S** after you have selected the **Restrict by unit** check box. |
    |  | b. In the **Unit** field, select the unit of measure to restrict for the pick and put away process. |
    | **Round up to unit** | Select this option to indicate if the raw material picking should be rounded up to a multiple of the handling unit specified in the Restrict by unit field. This applies only to raw material picking and location directives of the type Pick. |
    | **Locate packing quantity**| Select this check box if a packing unit quantity is specified in the **Sales order** form. If you select this check box, only the locations with this packing unit quantity are selected. |
    | **Allow split**| Select this check box to split the quantity across multiple locations. |
    | **Immediate replenishment template** | Create a connection to a replenishment template to start replenishment immediately if items are not allocated. If the field is left blank, item replenishment will not start until all lines of the location directive have been processed. |
    |  | a. This field is only available on selected work order types where replenishment is permitted, such as Sales orders and Raw material picking. |

1. On the **Location Directive Actions** FastTab, select **New** in the Action Pane to select the location or range of locations.

1. In the **Sequence number** field, the sequence in which the location directive is processed for the selected work type is displayed. You can modify the sequence, if needed. Use caution with location directive action sequence numbers, as they will always run in this sequence.

1. In the **Name** field, enter the name for the location directive action. Be specific so it is clear what the action is from the name.

1. *Optional*: Select **Edit query** to modify the warehouse locations and other criteria.

1. *Optional*: You can select the following additional settings for a location directive.

    | Field | Description |
    |---|---|
    | **Fixed location usage** | Determines which locations the location directive considers. |
    |  |**Fixed and non-fixed locations** - The location directive will consider all locations. |
    |  | **Only fixed locations for the product** - The location directive will consider only fixed locations for products. |
    |  |**Only fixed locations for the product variant** - The location directive will consider only fixed locations for product variants.  |
    | **Allow negative inventory** | Select this check box to allow negative inventory at the specified warehouse location. |
    | **Batch enabled** | Select this check box to use batch strategies for the items that are batch enabled. If this is enabled and the Strategy is set to None, the system will proceed to the next action line. |

1. In the **Strategy** field, select one of the strategies for the specified location directive.

    | Option | Description |
    |---|---|
    | **Strategy** | Determines the strategy used by the location directive. |
    |  | **None**: No strategy will be used. |
    |  | **Match packing quantity**: checks whether a pick location has the specified packing quantity. This will only work for location directive of type **Pick**.  |
    |  | **Consolidate**: consolidates items in a particular location when similar items are already available. This works only for the **Put** type of location directive. Common setup for Put will be to try to consolidate on first action line and on second try to Put without consolidation. Consolidating goods makes later picking more efficient. |
    |  | **FEFO batch reservation**: used when inventory is located using a batch expiration date and is allocated for batch reservation. The FEFO batch reservation strategy is also used when inventory is located using a batch best before date in addition to the expiration date. You can only use this strategy for batch enabled items. This strategy is only valid for a **Pick** work type of location directive. When you select this strategy it will override any query sorting for batch numbers that may be applied. |
    |  | **Round up to full LP**: used to round up the inventory quantity to match the license plate (LP) quantity that is assigned to the items to be picked; this strategy can only be used for replenishment type of location directives, for the type of **Pick**. |
    |  | **Empty location with no incoming work**: used to locate empty locations. The location is considered empty if it has no physical inventory and no expected incoming work. This strategy is used only for **Put** type of location directive. |

## Next step

After you create location directives, you can associate each directive code with a work template code for work creation.

[Control warehouse work by using work templates and location directives](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/control-warehouse-location-directives)

## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system administrator and provide the information that is shown in the following table.

| Category | Prerequisite |
|---|---|
| **Configuration keys** | Select **System administration > Setup  > License configuration**. Expand the **Trade** license key, and select the **Warehouse and Transportation management** configuration key. |
