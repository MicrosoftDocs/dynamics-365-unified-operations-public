---
# required metadata

title: Create a location directive
description: This topic explains how to create location directives. Location directives are user-defined rules that help identify pick and put locations for inventory movement.
author: Mirzaab
manager: tfehr
ms.date: 06/23/2020
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
ms.search.validFrom: 2020-06-23
ms.dyn365.ops.version: Release 10.0.9
---

# Create a location directive

> [!NOTE]
> This topic applies to features in the *Warehouse management* module. It does not apply to features in the [Inventory management](../inventory/inventory-home-page.md) module.

This topic explains how to create location directives. Location directives are user-defined rules that help identify pick and put locations for inventory movement. For example, in a sales order transaction, a location directive determines where the items will be picked and where the picked items will be put.

You can use location directives to do the following:

- Put away incoming items.
- Pick and stage items for outbound transactions.
- Pick and put raw materials for production.
- Replenish locations.

## Prerequisites

The following prerequisites must be in place before you create a location directive:

1. Go to **Warehouse management > Setup > Warehouse setup > Warehouses**.
    - Create a warehouse.
    - On the **Warehouse management** FastTab, select the **Use warehouse management processes** check box.
1. Create locations, location types, location profiles, and location formats.
    - For more information, see [Configure locations in a WMS-enabled warehouse](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/configure-locations-wms-enabled-warehouse).
1. Create sites, zones, and zone groups.
    - For more information, see [Warehouse set up](https://docs.microsoft.com/dynamics365/commerce/channels-setup-warehouse) and [Configure locations in a WMS-enabled warehouse](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/configure-locations-wms-enabled-warehouse).

## Set up

### Location directives

To create a location directive, follow these steps:

1. Select **Warehouse management > Setup > Location directives**.

1. In the list **Work order type** field, select the type of inventory transaction for which you want to create a location directive.

1. On the **Location directives** FastTab, select **New** to create a new location directive and specify the details as described in the following table.

| Field | Description |
|---|---|
| **Sequence number** |This is the sequence in which the location directive will be processed for the selected order type. Enter the sequence in which the location directive is processed for the selected work type. You can also modify the sequence, if needed. |
| **Name** |Enter a name for the location directive. This field is required. |
| **Work type** |Select the type of work to be performed. The type of work available is based on the type of inventory transaction that you have selected in the **Work order type** field. |
|  |**Put**: A work type equal to “Put” means that the location directive is going to try and find the most ideal location to place or locate inventory coming into the system either from receiving, production, or inventory adjustments. It it is also used to define put to stage location or final bay door shipping location in the outbound flow. |
|  |**Pick**: A work type equal to “Pick” means that the location directive is going to try and find the most ideal location/s to physically reserve inventory from (Create work). The pick can be completed (pick work line can be closed), even if the work is not completed. The user can complete physically picking and in the system that is pick step, then user can cancel from the mobile device and complete the work (eg. Put) later. Work header however is first closed when final put is completed. |
|  |**Counting, Adjustments, Custom, Inventory status change, License plate building, print, Status change, Pack to nested license plates**: These are not usable in any location directive setup. It is a enum field so there is no any filtering connected to Work order type. |
| **Site** | Select the site in which the work should be completed. This field is required. |
| **Warehouse** | Select the warehouse location in which the work should be completed. This field is required. |
| **Directive code** | Select a directive code to guide the selection of location directives related to the work template put lines having this code assigned. On the *Directive code* page you can create new codes that can be used for connections between a work template and a location directive. It can also be used to establish the link between any work template line and location directive (eg. Baydoor, stage location). To configure a directive code with a work template, see <a href=" https://docs.microsoft.com/dynamics365/supply-chain/warehousing/control-warehouse-location-directives">Control warehouse work by using work templates and location directives</a>. |
|  |Please note that if a directive code is set, when work is to be generated the system will not search location directive by sequence, but by *Directive code*. In this way you can be more specific what location template is used for certain step in work template like for staging of the materials. |
| **Disposition code** | Optional: Select a disposition code to redirect the put away of the received items to a location. For more information, see <a href=" https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/set-up-dispositions-codes">Set up dispositions codes</a>. This field is available only if you select **Purchase orders**, **Return orders** or **Finished goods put away** in the **Work order type** field. |
| **Multiple SKU** | *Optional*: Select this check box to use multiple stock keeping units (SKUs). This will enable to use multiple Stock Keeping Units on a location. E.g. the Baydoor needs to have it enabled.  If **Multiple SKU** is selected, the put location will be specified in work (this is expected), but it will only be able to handle multiple item put if work includes different SKUs to be picked and put (not a single SKU put). If **Multiple SKU** is not selected, the put location will only be specified if the put has only one kind of SKU. To be able do both, we need to specify two lines, one with **Multiple SKU** set to **Yes** (on), and one with **Multiple SKU** set to **No** (off) that have same structure and setup. So basically, for the put operations it is required to have to location directives that are identical, even though we do not need to distinguish between single and multiple SKUs on work ID. Please note that you need to set it up for pick as well (if you have an order with more than one items).
 |

> [!NOTE]
> If you use this setting for a location directive of the work type Put, the first location directive line will always be selected by the system irrespective of other restrictions created in the lines.

4. *Optional*: Select **Edit query** in the Action Pane to select the locations or to specify any restrictions that apply when you select a specific location directive.

1. On the **Lines** FastTab, create one or more lines to specify units and to locate or reserve quantity in a warehouse. Fill in the fields as described in the following table.

| Field | Description |
|---|---|
| **Sequence number** | Enter the sequence in which the location directive line is processed for the selected work type. You can also modify the sequence, if needed. |
| **From quantity** | Enter the starting range of the quantity of the items for which work should be performed. You can specify the From quantity on Unit in the respective unit for the range. |
| **To quantity** | Enter the ending range of the quantity of the items for which work should be performed. You can specify the To quantity on the Unit in the respective unit for the range. |
| **Unit** | Select the unit of measure for the items. |
|  | You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit.  The unit field on line is used only for quantity evaluation. |
|  |When checking if the location directive line is applicable at all, it be based on the quantity in the respective Unit field specified on the location directive line. Every time a location directive line is accessed, the system will try to convert demand unit to a unit specified on the line, if the Unit conversion does not exist it will continue to a next line. |
| **Locate quantity** | This is only valid when trying to Put/Locate quantity into the warehouse. It is therefore only valid for **Put** work. Select the method that is used to check whether the quantity is in the range that is set in the **From quantity** and **To quantity** fields. If the location directive is for an inbound transaction, select one of the following options: |
|  | **License plate quantity** ─ When evaluating whether or not a quantity is within the “From” and “To” quantity ranges, use the quantity on the license plate being received. |
|  | **Unitized quantity** ─ When evaluating whether or not a quantity is within the “From” and “To” quantity ranges, use the quantity being unitized during the specific transaction. |
|  | a. For example, in a warehouse if you can receive a quantity of 1000 and break it into 10 license plates of 100 each, you can use a quantity of 1000 items instead of the license plate quantity of 100. |
|  | **Remaining quantity** ─ When evaluating whether or not a quantity is within the “From” and “To” quantity ranges, what is the quantity left to be received on the Purchase Order Line currently being checked-in. |
|  | **Expected quantity** ─ When evaluating whether or not a quantity is within the “From” and “To” quantity ranges, use the total quantity of the Purchase Order Line, regardless of what has already been received. |

6. *Optional*: You can select the following additional settings on the **Lines** FastTab.

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

7. On the **Location Directive Actions** FastTab, select **New** in the Action Pane to select the location or range of locations.

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

12. In the **Strategy** field, select one of the strategies for the specified location directive.

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
