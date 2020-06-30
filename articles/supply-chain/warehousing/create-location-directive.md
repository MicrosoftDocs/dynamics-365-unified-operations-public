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
| **Sequence number** |Enter the sequence in which the location directive is processed for the selected work type. You can also modify the sequence, if needed. |
| **Name** | Enter a name for the location directive. This field is required. |
| **Work type** | Select the type of work to be performed. The type of work available is based on the type of inventory transaction that you have selected in the **Work order type** field. |
| **Site** | Select the site in which the work should be completed. This field is required. |
| **Warehouse** | Select the warehouse location in which the work should be completed. This field is required. |
| **Directive code** | Select a directive code to guide the selection of location directives related to the work template put lines having this code assigned. To configure a directive code with a work template, see <a href=" https://docs.microsoft.com/dynamics365/supply-chain/warehousing/control-warehouse-location-directives">Control warehouse work by using work templates and location directives</a>. |
| **Disposition code** | Optional: Select a disposition code to redirect the put away of the received items to a location. For more information, see <a href=" https://docs.microsoft.com/dynamics365/supply-chain/warehousing/tasks/set-up-dispositions-codes">Set up dispositions codes</a>. This field is available only if you select **Purchase orders**, **Return orders** or **Finished goods put away** in the **Work order type** field. |
| **Multiple SKU** | *Optional*: Select this check box to use multiple stock keeping units (SKUs). |

> [!NOTE]
> If you use this setting for a location directive of the work type Put, the first location directive line will always be selected by the system irrespective of other restrictions created in the lines.

4. *Optional*: Select **Edit query** to select the locations or to specify any restrictions that apply when you select a specific location directive.

1. On the **Lines** FastTab, create one or more lines to specify units and to locate or reserve quantity in a warehouse. Fill in the fields as described in the following table.

| Field | Description |
|---|---|
| **Sequence number** | Enter the sequence in which the location directive is processed for the selected work type. You can also modify the sequence, if needed. |
| **From quantity** | Enter the starting quantity of the items for which work should be performed. |
| **To quantity** | Enter the ending quantity of the items for which work should be performed. |
| **Unit** | Select the unit of measure for the items. |
| **Locate quantity** | Select the method that is used to check whether the quantity is in the range that is set in the **From quantity** and **To quantity** fields. If the location directive is for an inbound transaction, select one of the following options: |
|  | **License plate quantity** ─ The license plate quantity |
|  | **Unitized quantity** ─ The unitized quantity from the specified inventory transaction. |
|  | a. For example, in a warehouse if you can receive a quantity of 1000 and break it into 10 license plates of 100 each, you can use a quantity of 1000 items instead of the license plate quantity of 100. |
|  | **Remaining quantity** ─ The quantity yet to be received that is specified on the purchase order line. |
|  | **Expected quantity** ─ The total quantity that is specified on the purchase order line. |

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

1. In the **Sequence number** field, the sequence in which the location directive is processed for the selected work type is displayed. You can modify the sequence, if needed.

1. In the **Name** field, enter the name for the location directive action.

1. *Optional*: Select **Edit query** to modify the warehouse locations and other criteria.

1. *Optional*: You can select the following additional settings for a location directive.

| Field | Description |
|---|---|
| **Fixed location usage** | Determines which locations the location directive considers. If you select Fixed and non-fixed locations, all locations are considered. |
| **Allow negative inventory** | Select this check box to allow negative inventory at the specified warehouse location. |
| **Batch enabled** | Select this check box to use batch strategies for the items that are batch enabled. |

12. In the **Strategy** field, select one of the strategies for the specified location directive.

| Option | Description |
|---|---|
| **Strategy** | Determines the strategy used by the location directive. |
|  | **None**: No strategy will be used. |
|  | **Match packing quantity**: checks whether a pick location has the specified packing quantity.  |
|  | **Consolidate**: consolidates items in a particular location when similar items are already available. |
|  | **FEFO batch reservation**: used when inventory is located using a batch expiration date and is allocated for batch reservation. The FEFO batch reservation strategy is also used when inventory is located using a batch best before date in addition to the expiration date. |
|  | **Round up to full LP**: used to round up the inventory quantity to match the license plate (LP) quantity that is assigned to the items to be picked; this strategy can only be used for replenishment. |
|  | **Empty location with no incoming work**: used to locate empty locations. The location is considered empty if it has no physical inventory and no expected incoming work. |

## Next step

After you create location directives, you can associate each directive code with a work template code for work creation.

[Control warehouse work by using work templates and location directives](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/control-warehouse-location-directives)

## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system administrator and provide the information that is shown in the following table.

| Category | Prerequisite |
|---|---|
| **Configuration keys** | Select **System administration > Setup  > License configuration**. Expand the **Trade** license key, and select the **Warehouse and Transportation management** configuration key. |
