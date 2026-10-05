---
title: Set up unit sequence groups
description: Learn how to create unit sequence groups, which define the units that warehouse processes can use for a product, and the policies that apply to each unit.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetails, EcoResProductDetailsExtended, EcoResStorageDimensionGroup, InventItemOrderSetup, UnitOfMeasureConversion, WHSRFMenuItem, WHSUOMSeqGroupTable
ms.topic: how-to
ms.date: 10/05/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Set up unit sequence groups

[!INCLUDE [banner](../includes/banner.md)]

A *unit sequence group* lists the units that warehouse processes can use for a product, from the smallest unit to the largest, and defines the policies that apply to each of those units. The sequence shows the relationship among the units. For example, you store pallets that contain boxes that contain individual pieces. In that case, the unit sequence group contains three units, in that order.

Warehouse processes use unit sequence groups to determine the unit that work is created in, how license plates are grouped during receiving, which units a worker can count during cycle counting, and which unit is suggested by default in several mobile device flows. This article applies both to the warehouse management processes (WMS) that are available in the **Warehouse management** module and to the more basic warehousing solution that is available in the **Inventory management** module.

## Create a unit sequence group

A unit sequence group consists of a header, which identifies the group, and one line for each unit in the sequence. Follow these steps to create a group and add its units.

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Unit sequence groups**.
1. On the Action Pane, select **New** to add a group.
1. In the header, set the following fields:

    - **Unit sequence group ID** – Enter a unique identifier for the group. Because you assign the group to released products by using this value, choose a name that indicates which packaging hierarchy it describes. (In the USMF demo data, the groups are named after their units, such as *Each-Box-PL*.)
    - **Name** – Enter a short description of the group.

1. In the lines grid, select **New** to add a line for each unit that the group must contain. Add the units in order, from the smallest unit to the largest. The **Line number** value determines the position of the unit in the sequence. The first line must hold the smallest unit, and that unit must match the inventory unit of every product that you assign the group to.
1. For each line, set the fields that are described in the next section. You can't change the **Unit** value after you save the line.
1. On the Action Pane, select **Save**.

## Line settings

Each line represents one unit in the sequence. Set the following fields on it:

- **Unit** – Select the unit of measure. Set up a unit conversion between this unit and every other unit in the group. Otherwise, the system can't translate quantities between the levels of the sequence. Define conversions on the **Unit conversions** page. For example, for a group that contains *Pcs*, *Box*, and *PL*, you might define *10 Pcs = 1 Box* and *100 Pcs = 1 PL*. Learn more in [Manage units of measure](../pim/tasks/manage-unit-measure.md).
- **License plate packing type** – Enter an identifier for a license plate packing type. The system adds this identifier to the license plate numbers that it creates for this unit.
- **License plate grouping** – Select this checkbox if a receipt of more than one of this unit should group onto a single license plate. If you leave it cleared, the system requests a separate license plate for each unit that it receives. Because grouping always applies from the smallest unit upward, the system keeps your settings consistent. When you select the checkbox on a line, it's also selected on every smaller unit in the group. When you clear it, it's also cleared on every larger unit.

    For example, a group contains *Pcs* and *PL*, where one pallet holds 100 pieces. If you select the checkbox for *Pcs* but not for *PL*, a receipt of 250 pieces produces one license plate for each full pallet and one license plate that holds the remaining 50 pieces as a group.

    To use license plate grouping on a mobile device, you must also select the **License plate grouping** option on the mobile device menu item that's used for the receipt.

- **Use unit for cycle counting** – Select this checkbox to let workers count the product in this unit. Select at most four units per group. If you select more, mobile devices don't show the extra units. If no unit in the group is selected, cycle counting fails for the products that use the group.
- **Default unit for purchase and transfer** – Select this checkbox to suggest this unit by default when workers receive purchase orders and transfer orders on a mobile device. Only one line per group can be selected. If you select the checkbox on a second line, the system automatically clears it on the first line. For example, you can select *PL* so that pallet quantities are suggested during purchase order receiving, even though the inventory unit is *Pcs*.
- **Default unit for production** – Select this checkbox to suggest this unit by default when workers report production quantities. Only one line per group can be selected.
- **Default container type** – Select the container type to use by default on license plates that hold this unit. Container types describe the physical characteristics of a carrying unit, such as its dimensions and tare weight.
- **Default unit for material consumption** – Select this checkbox to suggest this unit by default when workers register material consumption for production. Only one line per group can be selected.
- **Wave label type** – Select a wave label type to generate wave label records for this unit. If a wave label template refers to the same type, the system creates one wave label record for each unit on the work line. For example, if you set the type on the *Box* unit, and a work line is for five boxes, the system creates five wave label records. If you set the type on the *Pcs* unit, and one box holds 10 pieces, a work line for one box produces 10 wave label records. You can use each wave label type on only one line per group.

> [!NOTE]
> If you add units that belong to different unit of measure classes to the same group (for example, a weight unit and a quantity unit), the system shows a warning when you save. Such a group can produce work in an unexpected unit of measure, and it can cause unexpected rounding of load quantities and work line quantities. Set it up only after careful consideration.

## Assign a unit sequence group to a released product

Before you can use a released product in warehouse work processes, you must assign a unit sequence group to it. If the product uses a storage dimension group where the **Use warehouse management processes** option is set to *Yes*, validation of the product fails until you assign a unit sequence group.

When you assign a group, the system verifies that the smallest unit in the group matches the inventory unit of the product. The inventory unit is the unit that's used for base calculations of on-hand inventory. Therefore, you typically need one unit sequence group for each combination of inventory unit and packaging hierarchy that you work with. For a catch weight product, the smallest unit must match the catch weight unit, and every unit in the group must belong to the same unit of measure class as that unit.

You can also set up unit of measure conversions for the variants of a product master by using the **Enable unit of measure conversions** option. Learn more in [Unit of measure conversion per product variant](../pim/uom-conversion-per-product-variant.md).

## How the system chooses the unit for warehouse work

When the system creates warehouse work, it uses the unit sequence group to determine the unit for each work quantity. It evaluates the units from the largest unit in the sequence to the smallest, and it selects the first unit that represents the quantity as a whole number. If a larger unit would produce a fractional quantity, the system evaluates the next smaller unit.

For example, a unit sequence group contains *Pcs*, *Box*, and *PL*, and one pallet equals 100 pieces. A work quantity of 100 Pcs is represented as 1 PL, because the conversion produces a whole number. A work quantity of 20 Pcs can't be represented as a whole pallet. The system therefore uses *Box* or *Pcs*, depending on the unit conversions in the sequence group.

Therefore, work lines for the same product can use different units, depending on their quantities. The inventory unit remains the base unit for on-hand inventory calculations. The **Default unit for purchase and transfer** option controls only the unit that's suggested during mobile device receiving. It doesn't force warehouse work to use that unit.

## Default order settings

Unit sequence groups control the units that warehouse processes use. They don't control the units and quantities that are suggested when orders are created. Those values come from the default order settings of each released product, which you maintain separately.

Default order settings are divided into three FastTabs: **Purchase order**, **Inventory**, and **Sales order**. On each FastTab, you can specify the following kinds of values:

- The default site and warehouse where the product is sourced from or stored.
- The standard order quantity, together with the minimum quantity, the maximum quantity, and the multiple that quantities are rounded to.
- The lead time, and whether the product is stopped.

Each product has one set of general default order settings. You can add more rules that apply only to specific dimensions, such as a site, a product variant, or a configuration. Rules have a rank, and the system applies the rule that has the highest rank among the rules that match. The general settings always have rank zero and serve as the fallback. Site-specific order settings are modeled as rules that specify a site.

To view or change these settings, go to **Product information management** > **Products** > **Released products**, select a product, and then, on the Action Pane, open the **Plan** tab and, from the **Order settings** group, select **Default order settings**.

Because the two features are independent, ensure that the units you select in the default order settings work with the unit sequence group that's assigned to the product. If you create an order in a unit that has no conversion to the units in the group, warehouse processes can't represent the quantity correctly.

## Related information

- [Default order settings for dimensions and product variants](../production-control/default-order-settings.md)
- [Cycle counting](cycle-counting.md)
- [Wave label printing](configure-wave-label-printing.md)
