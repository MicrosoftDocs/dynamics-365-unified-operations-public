---
# required metadata

title: Create location directives
description: This topic explains how to create location directives. Location directives are user-defined rules that help identify pick and put locations for inventory movement.
author: Mirzaab
manager: tfehr
ms.date: 07/28/2020
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
ms.search.validFrom: 2020-07-28
ms.dyn365.ops.version: Release 10.0.9
---

# Create location directives

[!include [banner](../includes/banner.md)]

This topic explains how to create location directives. Location directives are user-defined rules that help identify pick and put locations for inventory movement. For example, for a sales order transaction, a location directive determines where items will be picked and where the picked items will be put.

> [!NOTE]
> This topic applies to features in the **Warehouse management** module. It doesn't apply to features in the [Inventory management](../inventory/inventory-home-page.md) module.

You can use location directives to perform the following tasks:

- Put away incoming items.
- Pick and stage items for outbound transactions.
- Pick and put raw materials for production.
- Replenish locations.

## Prerequisites

Before you can create a location directive, you must follow these steps to make sure that the prerequisites are in place.

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. Create a warehouse.
1. On the **Warehouse** FastTab, set the **Use warehouse management processes** option to *Yes*.
1. Create locations, location types, location profiles, and location formats. For more information, see [Configure locations in a WMS-enabled warehouse](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/configure-locations-wms-enabled-warehouse).
1. Create sites, zones, and zone groups. For more information, see [Warehouse set up](https://docs.microsoft.com/dynamics365/commerce/channels-setup-warehouse) and [Configure locations in a WMS-enabled warehouse](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/configure-locations-wms-enabled-warehouse).

## Setup

### Create location directives

To create a location directive, follow these steps.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the list pane, set the **Work order type** field to the type of inventory transaction that you're creating a location directive for.
1. On the Action Pane, select **New** to create a location directive.
1. For the new location directive, set the fields as described in the following table.

    | Field | Description |
    |---|---|
    | Sequence number | Enter an integer that indicates the sequence position of the location directive. Sequence positions determine when each location directive is processed for the selected work order type. |
    | Name | Enter a name for the location directive. | 
    | Work type | Select the type of work that should be performed. The list of values depends on the type of inventory transaction that you selected in the **Work order type** field. The following values might be available:<ul><li>**Put** – The location directive will try to find the best location to place or locate inventory that comes into the system through receiving, production, or inventory adjustments. The location directive is also used to define the put-to-stage location or final bay door shipping location in the outbound flow.</li><li>**Pick** – The location directive will try to find the best locations to physically reserve inventory from (create work). The pick can be completed (that is, the pick work line can be closed), even if the work isn't completed. The user can complete physical picking. In the system, that action is a pick step. The user can then cancel from the mobile device and complete the work (for example, put) later. However, the work header is first closed when the final put is completed.</li><li>**Counting**, **Adjustments**, **Custom**, **Inventory status change**, **License plate building**, **Print**, **Status change**, and **Pack to nested license plates** – These values can't be used in any location directive setup.</li></ul> |
    | Site | Select the site where the work should be completed. |
    | Warehouse | Select the warehouse location where the work should be completed. |
    | Directive code | Select a directive code to guide the selection of location directives that are related to the work template put lines where this code is assigned. On the **Directive code** page, you can create new codes that can be used to connect a work template to a location directive. You can also use that page to establish the link between any work template line and a location directive (such as the bay door or stage location). For information about how to configure a directive code with a work template, see [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md).<p>If a directive code is set, when work must be generated, the system will search location directives by directive code instead of by sequence. In this way, you can be more precise about the location template that is used for a specific step in a work template, such as the step for staging the materials.</p> |
    | Disposition code | Select a disposition code to redirect the putaway of received items to a location. (For more information, see [Set up dispositions codes](tasks/set-up-dispositions-codes.md).) This field is available only when the **Work order type** field is set to *Purchase orders*, *Return orders*, or *Finished goods put away*. |
    | Multiple SKU | Set this option to *Yes* to use multiple stock keeping units (SKUs) on a location. For example, this option must be set to *Yes* for the bay door.<p>If the **Multiple SKU** option is set to *Yes*, the put location will be specified in work (as expected). However, the put location will be able to handle multiple-item put only if the work includes different SKUs that must be picked and put, not if the work includes just a single SKU that must be put.</p><p>If the **Multiple SKU** option is set to *No*, the put location will be specified only if the put has only one type of SKU.</p><p>To use both approaches, you must specify two lines that have the same structure and setup, but set the **Multiple SKU** option to *Yes* for one of the lines and *No* for the other. In other words, two identical location directives are required for put operations, even though you don't have to distinguish between single and multiple SKUs in the work ID. You must also set a location directive up for pick, if you have an order that has more than one item.</p><p>**Note:** If you set the **Multiple SKU** option to *Yes* for a location directive of the *Put* work type, the system will always select the first location directive line, regardless of other restrictions that are created on the lines.</p> |

1. Optional: On the Action Pane, select **Edit query** to select the locations, or to specify any restrictions that apply when you select a specific location directive.
1. On the **Lines** FastTab, create one or more lines to specify units, and to locate or reserve quantity in a warehouse.
1. On each new line, set the fields as described in the following table.

    | Field | Description |
    |---|---|
    | Sequence number | Enter an integer that indicates the sequence position of the location directive. Sequence positions determine when each location directive is processed for the selected work type. |
    | From quantity | Specify the beginning quantity range for when the middle-grid sequence should be selected. Specify the quantity in the unit of measure that is selected in the **Unit** field. |
    | To quantity | Specify the ending quantity range for when the middle-grid sequence should be selected. Specify the quantity in the unit of measure that is selected in the **Unit** field. |
    | Unit | Select the unit of measure for the items.<p>You can specify a minimum quantity and a maximum quantity that the directive should apply to. You can also specify that the directive should be used for a specific inventory unit. The **Unit** field is used only for quantity evaluation.</p><p>To determine whether a location directive line applies, the system evaluates quantities by using the **Unit** value that is specified on the line. Every time that a location directive line is accessed, the system will try to convert the demand unit to the unit that is specified on the line. If the unit conversion doesn't exist, the system will move on to the next line.</p> |
    | Locate quantity | This field is valid only when you try to put or locate quantity in the warehouse. In other words, it's valid only for *Put* work. Select the method that is used to evaluate whether the quantity is in the range that is set in the **From quantity** and **To quantity** fields. If the location directive is for an inbound transaction, select one of the following options:<ul><li>**License plate quantity** ─ To evaluate whether a quantity is in the target quantity range, use the quantity on the license plate that is being received.</li><li>**Unitized quantity** ─ To evaluate whether a quantity is in the target quantity range, use the quantity that is being unitized during the transaction. For example, in a warehouse, if you can receive a quantity of 1,000 and break it into 10 license plates, each of which has a quantity of 100, you can use a quantity of 1,000 items instead of the license plate quantity of 100.</li><li>**Remaining quantity** ─ To evaluate whether a quantity is in the target quantity range, use the quantity that remains to be received on the purchase order line that is currently being checked in.</li><li>**Expected quantity** ─ To evaluate whether a quantity is in the target quantity range, use the total quantity of the purchase order line, regardless of the quantity that has already been received.</li></ul> |

1. Optional: On the **Lines** FastTab, you can set the following additional fields.

    | Field | Description |
    |---|---|
    | Restrict by unit | Select this check box to restrict the units of measure that are considered valid selection criteria for the location directive lines. When units of measure have been specified, only items where the unit matches at least one unit that is defined for the unit sequence group will be considered valid for the line selection.<p>For example, the unit is restricted to pallets, and the item is associated with a unit sequence group that includes the *pallets* unit. In this case, the items will be considered a valid option for the location directive.</p><p>However, the **Restrict by unit** check box doesn't control the unit or units that are applied on work lines. The unit restriction applies only to the units that are made available via the unit sequence group.</p><p>For example, an item is associated with a unit sequence group that includes both the *pallets* and the *pcs* units. A unit of measure has been defined where 1 pallet = 100 pcs, and the location directive uses the **Restrict by unit** functionality only for pallets. Furthermore, a work template has been defined that limits the work header creation to 50 pcs. In this case, work lines of 50 pcs will be created.</p><p>To specify the unit of measure for restriction, follow these steps</p><ol><li>On the **Lines** FastTab, select **Restrict by unit**. This button becomes available only after you select the **Restrict by unit** check box on the line and then select **Save**.</li><li>In the **Unit** field, select the unit of measure to restrict by for the pick and putaway processes.</li></ol> |
    | Round up to unit | Select this option to indicate that raw material picking should be rounded up to a multiple of the handling unit that is specified in the **Restrict by unit** field. This field applies only to raw material picking and location directives of the *Pick* type. |
    | Locate packing quantity | Select this check box if a packing unit quantity is specified on the **Sales order** page. If you select this check box, only the locations that have this packing unit quantity are selected. |
    | Allow split | Select this check box to split the quantity across multiple locations. |
    | Immediate replenishment template | Create a connection to a replenishment template, so that replenishment is started immediately if items aren't allocated. If you leave this field blank, item replenishment won't be started until all lines of the location directive have been processed.<p>This field is available only on selected work order types where replenishment is permitted, such as *Sales orders* and *Raw material picking*.</p> |

1. On the **Location directive actions** FastTab, select **New** to select the location or range of locations.
1. The **Sequence number** field shows the sequence that the location directive will be processed in for the selected work type. You can modify the sequence. However, be cautious about sequence numbers for location directive actions, because location directive actions will always run in this sequence.
1. In the **Name** field, enter the name of the location directive action. Be specific, so that it's clear what the action is.
1. Optional: Select **Edit query** to modify the warehouse locations and other criteria.
1. Optional: You can set the following additional fields for a location directive.

    | Field | Description |
    |---|---|
    | Fixed location usage | Select which locations the location directive should consider:<ul><li>**Fixed and non-fixed locations** – The location directive will consider all locations.</li><li>**Only fixed locations for the product** – The location directive will consider only fixed locations for products.</li><li>**Only fixed locations for the product variant** – The location directive will consider only fixed locations for product variants.</li></ul> |
    | Allow negative inventory | Select this check box to allow negative inventory at the specified warehouse location. |
    | Batch enabled | Select this check box to use batch strategies for the items that are batch-enabled. If this check box is selected, and the **Strategy** field is set to *None*, the system will move on to the next action line. |
    | Strategy | Select the strategy that the location directive should use:<ul><li>**None** – No strategy will be used.</li><li>**Match packing quantity** – This strategy checks whether a pick location has the specified packing quantity. This strategy is valid only when the **Work type** field is set to *Pick*.</li><li>**Consolidate** – This strategy consolidates items in a specific location when similar items are already available. This strategy is valid only when the **Work type** field is set to *Put*. In a typical setup for put, the system tries to consolidate on the first action line, and then, on the second action line, it tries to put without consolidation. Consolidation of goods makes later picking more efficient.</li><li>**FEFO batch reservation** – This strategy is used when inventory is located by using a batch expiration date, and it's allocated for batch reservation. The first expiry, first out (FEFO) batch reservation strategy is also used when inventory is located by using a batch best-before date in addition to the expiration date. You can use this strategy only for batch-enabled items. This strategy is valid only when the **Work type** field is set to *Pick*. When you select this strategy, you override any query sorting for batch numbers that is applied.</li><li>**Round up to full LP** – This strategy rounds up the inventory quantity so that it matches the license plate quantity that is assigned to the items that must be picked. This strategy can only be used for replenishment type of location directives, and only when the **Work type** field is set to *Pick*.</li><li>**Empty location with no incoming work** – This strategy is used to locate empty locations. A location is considered empty if it has no physical inventory and no expected incoming work. This strategy is valid only when the **Work type** field is set to *Put*.</li></ul> |

## Example of the use of location directives

For this example, consider a purchase order process where the location directive must find free capacity within a warehouse for inventory items that have just been registered at the receiving dock. First, you need to find free capacity within the warehouse by consolidating with existing on-hand inventory. If consolidation isn't possible, then you need to find an empty location.

For this scenario, you must define two location directive actions. The first action in the sequence must use the **Consolidate** strategy, and the second should use the **Empty location with no incoming work** strategy. Unless you define a third action to handle an overflow scenario, two outcomes are possible when there is no more capacity in the warehouse: work can be created even though no locations are defined, or the work creation process can fail. The outcome is determined by the setup on the **Location directive failures** page, where you can decide whether to select the **Stop work on location directive failure** option for each work order type.

## Next step

After you create location directives, you can associate each directive code with a work template code for work creation. For more information, see [Control warehouse work by using work templates and location directives](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/control-warehouse-location-directives).

## Technical information for system admins

If you don't have access to the pages that are used to complete this task, contact your system admin, and provide the information that is shown in the following table.

| Category | Prerequisite |
|---|---|
| Configuration keys | Go to **System administration \> Setup \> License configuration**. Expand the **Trade** license key, and then select the **Warehouse and Transportation management** configuration key. |

### Additional resources

- Video: [Warehouse management configuration deep dive](https://community.dynamics.com/365/b/techtalks/posts/warehouse-management-configuration-deep-dive-october-14-2020)
- Help topic: [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md)
- Help topic: [Work with location directives](location-directives.md)
