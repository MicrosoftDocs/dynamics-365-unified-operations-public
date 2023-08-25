---
# required metadata

title: Warehouse slotting
description: This article provides information about warehouse slotting. Warehouse slotting lets you consolidate demand by item and unit of measure from orders that have a status of Ordered, Reserved, or Released. It helps warehouse managers intelligently plan picking locations before they release orders to the warehouse and create picking work.
author: Mirzaab
ms.date: 11/13/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form: WHSInventFixedLocation, WHSSlotDemandLocated, WHSSlotDemand, WHSSlotUOMTier, WHSSlotTemplate, WHSLocDirHint, WHSLocDirTable
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: 10.0.9
---

# Warehouse slotting

[!include [banner](../includes/banner.md)]
<!--In current version no "...slotting" features exists - suggest this and next section gets updated!-->
Several warehouse slotting features are available to help warehouse managers intelligently plan picking locations before they release orders to the warehouse and create picking work.

The *Warehouse slotting feature* lets you consolidate demand by item and unit of measure from orders that have a status of *Ordered*, *Reserved*, or *Released*. Generated demand can then be applied to locations that will be used for picking, based on quantity, unit, physical dimensions, fixed locations, and more. After the slotting plan has been established, replenishment work can be created to bring the appropriate amount of inventory to each location.

The *Warehouse slotting for transfer orders* feature lets warehouse managers replenish picking locations, based on demand from transfer orders that aren't yet released to the warehouse. It ensures that picking locations will include all the items that are required for the transfer orders after they are released to warehouse. This feature requires that you also turn on the *Warehouse slotting feature* feature.

The *Warehouse slotting allocation enhancements* feature adds an option for the template lines that are used by the *Warehouse slotting feature* feature. The option enables the system to consider existing on-hand inventory at a target location. Therefore, fewer replenishments might be generated for slotting. The *Warehouse slotting allocation enhancements* feature requires that you also turn on the *Warehouse slotting feature* feature. It can optionally be used together with the *Warehouse slotting for transfer orders* feature.

## Turn on the warehouse slotting features

Before you can use these features, they must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the features and turn them on if they are required. Turn on the following features as required:

- Warehouse slotting feature
- Warehouse slotting for transfer orders

    > [!IMPORTANT]
    > The *Warehouse slotting feature* feature must be turned on before this feature.

- Warehouse slotting allocation enhancements

    > [!IMPORTANT]
    > The *Warehouse slotting feature* feature must be turned on before this feature.

## Set up warehouse slotting

To use warehouse slotting, you must set up the following elements in your system:

- Slotting unit of measure tiers
- Directive codes
- Slotting templates
- Location directives

### <a name="unit-tiers"></a>Create unit-of-measure tiers for slotting

Unit-of-measure tiers enable multiple units of measure to be grouped together for the purposes of slotting. For example, if multiple sizes of boxes are all picked from the same box picking area, one tier can be created for all the sizes. **A line must be created for each unit of measure that should be part of the tier.**

1. Go to **Warehouse management \> Setup \> Replenishment \> Slotting unit of measure tiers**.
1. Select **New**.
1. In the header, set the following values:

    - **Unit of measure tier:** *EaBoxPl*
    - **Description:** *Each box pallet*

1. Select **Save**.
1. On the **Units of measure** FastTab, select **New** to add a line to the grid.
1. On the new line, set the following values:

    - **Unit:** *Box*
    - **Description:** Leave this field blank. It will be filled in automatically when you save your changes.
    - **Unit class:** *Quantity*

1. Select **New** to add a second line to the grid.
1. On the new line, set the following values:

    - **Unit:** *ea*
    - **Description:** Leave this field blank. It will be filled in automatically when you save your changes.
    - **Unit class:** *Quantity*

1. Select **New** to add a third line to the grid.
1. On the new line, set the following values:

    - **Unit:** *PL*
    - **Description:** Leave this field blank. It will be filled in automatically when you save your changes.
    - **Unit class:** *Quantity*

1. Select **Save** to save the tier.

### Create a directive code for slotting

You must select the directive code that should be associated with a template.

1. Go to **Warehouse management \> Setup \> Directive codes**.
1. On the Action Pane, select **New**.
1. In the **Directive code** field, enter *Slotting*.
1. In the **Directive description** field, enter *Slotting*.

### Set up slotting templates

Each slotting template controls how inventory is assigned to locations for a specific warehouse. Each template must include a line for each slotting specification. Use the procedures in this section to set up slotting templates.

1. Go to **Warehouse management \> Setup \> Replenishment \> Slotting templates**.
1. Select **New** to create a template.

Next, you must set up the template header, slotting specifications, and location directives, as explained in the following subsections. The setup for slotting for transfer orders resembles the setup for slotting for sales orders, but the **Demand type** field is set *Transfer orders* instead of *Sales order*.

#### Set up the header for a sales order slotting template

1. In the header for the template, set the following values:

    - **Slotting template:** _61_
    - **Description:** _61_
    - **Demand type:** *Sales order*

        > [!NOTE]
        > Currently, *Sales orders*, *Transfer orders*, and *Outbound shipment orders* are the only demand types that are supported. You can select *Transfer orders* only if the *Warehouse Slotting for transfer orders* feature is turned on. <!-- in current version TO-feature does no longer exists... suggest we remove this and DON'T add WOM-feature comment --->

    - **Demand strategy:** _Ordered_

        The following values are available in this field:

        - **Ordered** – The full ordered quantity on the sales order should be considered demand.
        - **Reserved** – Only the sales order line quantities that are reserved (physical and ordered) should be considered demand.
        - **Released** – The released quantity should be considered demand.

    - **Allow wave demand to use unreserved quantities:** _Yes_

1. Use the **Warehouse selection** fast tab to specify the warehouse where the slotting template will apply.

    - **Warehouse selection** – Select one of the following values:

        - *All* – Use the slotting template for all warehouses.
        - *Warehouse group* – Use the slotting template for all warehouses in the warehouse group that's selected in the **Warehouse group** field.
        - *Warehouse* – Use the slotting template only for the specific warehouse that's selected in the **Warehouse** field.

    - **Warehouse** – If the **Warehouse selection** field is set to *Warehouse*, select the warehouse where the slotting template applies. 
    - **Warehouse group** – If the **Warehouse selection** field is set to *Warehouse group*, select the warehouse group where the slotting template applies. For more information about how to set up warehouse groups, see [Warehouse groups](warehouse-groups.md).

    For this scenario, set the following values:
    - **Warehouse selection:** *Warehouse*
    - **Warehouse:** *61*

You can also specify a query to narrow the scope of the demand that is evaluated.

#### Set up slotting specifications for each template

For each sales order template that you create, follow these steps to add a line for each slotting specification.

1. On the **Slotting template details** FastTab, select **New** to create a template line.
1. On the new line, set the following values:

    - **Sequence:** _1_
    - **Description:** _Fixed location_
    - **Minimum quantity:** _1_

        This field defines the minimum quantity of demand that is required for the line.

    - **Maximum quantity:** _1000000_

        This field defines the maximum quantity of demand that is valid for the line.

    - **Unit:** Leave this field blank.

        This field defines the unit of measure that the minimum and maximum quantities refer to.

    - **Unit of Measure Tier:** _EaBoxPl_

        This field defines the units of measure of demand that are valid for the line. (For more information, see the [Set up unit-of-measure tiers for slotting](#unit-tiers) section earlier in this article.)

    - **Assign slot criteria:** _Consider qty_

        The following values are available in this field:

        - **Assume empty** – This system should assume that all locations in the picking area are empty and should not check those locations for inventory.
        - **Consider qty** – The system should check the locations in the picking area for inventory and should skip any locations that aren't empty.
        - **Consider on-hand** – The system should check whether any target location contains unreserved quantities for the item on the demand line. If the quantity is large enough to satisfy at least one unit of the demand line, the generated slotting plan record is reduced by the available amount. For example, if the demand is 10 cases, and one case is on hand, the located demand will be nine cases. If the demand is 10 cases, and one each is on hand, the located demand will be 10 cases. This value is available only when the *Warehouse slotting allocation enhancements* feature is turned on.

    - **Directive code:** _Slotting_

        This field defines the location directive that is used to find the picking location of the replenishment work.

    - **Overflow location:** Leave this field blank.

        This field defines the location that inventory that is put to if a location can't be found for the quantity when the line is processed.

    - **Allow let up:** _Yes_

        When this option is set to *Yes*, if any demand can't be slotted, movement work will be created to take inventory out of locations where there is inventory, but where nothing was slotted. The template is then run again. This time, it ignores the inventory in the locations. This functionality works best when the **Assign slot criteria** field is set to _Consider qty_.

    - **Fixed location usage:** _Only fixed locations for the product_

        The following values are available in this field:

        - **Fixed and non-fixed locations** – The system should not be limited to using only fixed locations.
        - **Only fixed locations for the product** – The system should slot only to locations that are fixed locations for the product.
        - **Only fixed locations for the product variant** – The system should slot only to locations that are fixed locations for the product variant.

> [!NOTE]
> If the slotting template contains at least one line where the **Assign slot criteria** field is set to *Consider on-hand*, let-ups are no longer allowed for any line in the template.

1. Select **Save**.
1. Select **New** to create a second template line.
1. On the new line, set the following values:

    - **Sequence:** _2_
    - **Description:** _Other_
    - **Minimum Qty:** _1_
    - **Maximum Qty:** _1000000_
    - **Unit:** Leave this field blank.
    - **Unit of measure tier:** _EaBoxPl_
    - **Assign slot criteria:** _Consider qty_
    - **Directive code:** _Slotting_
    - **Overflow location:** Leave this field blank.
    - **Allow let up:** _Yes_
    - **Use fixed locations:** _Fixed and non-fixed locations_

    In the query for the second line, you will now specify the criteria that are used to determine what locations the demand for that line can be slotted to.

1. Select the line where the **Sequence** field is set to *2*.
1. Select **Edit query**.
1. On the **Range** tab, select **Add** to add a line to the grid.
1. On the new line, set the following values:

    - **Table:** *Locations*
    - **Derived table:** *Locations*
    - **Field:** *Location profile ID*
    - **Criteria:** *Pick-06* (Select the double plus sign \[**++**\] in the field to expand the list, and then select *Pick-06* - *Picking Site 6*.)

1. Select **OK**.

#### Set up location directives

At least one location directive must be set up to support slotting picks. Use the procedures in this section to set up a new *replenishment location directive* for slotting picks.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the left pane, in the **Work order type** field, select *Replenishment*.
1. On the Action Pane, select **New**.
1. In the header for the new location directive, in the **Name** field, enter *61 Slotting pick*.
1. In the **Sequence number** field, accept the default value.

##### Configure the Location directives FastTab

1. On the **Location directives** FastTab, set the following values. Accept the default values for all other fields.

    - **Work type:** _Pick_
    - **Site:** _6_
    - **Warehouse:** _61_
    - **Directive code:** _Slotting_

1. Select **Save** to make the **Lines** FastTab available.

##### Configure the Lines FastTab

1. On the **Lines** FastTab, select **New** to create a line.
1. On the new line, set the following values.

    - **From quantity:** _0_
    - **To quantity:** _1000000_

1. Accept the default values for the remaining fields.
1. Select **Save** to make the **Location Directive Actions** FastTab available.

##### Configure the Location Directive Actions FastTab

1. On the **Location Directive Actions** FastTab, select **New** to create a line.
1. On the new line, set the following values. Accept the default values for all other fields.

    - **Sequence number:** Accept the default value.
    - **Name:** _Bulk_
    - **Strategy:** _None_

1. Accept the default values for the remaining fields.
1. Select **Save** to make the **Edit query** button available.

##### Edit the query

1. On the **Location Directive Actions** FastTab, select **Edit query**.
1. On the **Range** tab, select **Add** to add a line to the grid.
1. On the new line, set the following values:

    - **Table:** *Locations*
    - **Derived table:** *Locations*
    - **Field:** *Zone ID*
    - **Criteria:** *Bulk* (Select the double plus sign \[**++**\] in the field to expand the list, and then select *Bulk*.)

1. Select **OK**.

## Scenario

### Set up the scenario

For this scenario, use the built-in sample data, and create the records that are described in this section.

#### Use the USMF sample data

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

#### Create demand

Follow these steps to create the demand that you will apply slotting to.

1. Go to **Sales and marketing \> Sales orders \> All sales order**.
1. Select **New** to create a sales order.
1. In the **Create sales order** dialog box, in the **Customer account** field, select _US-007_.
1. In the **Warehouse** field, select _61_.
1. Select **OK**.
1. The new sales order is opened. It includes an empty line on the **Sales order lines** FastTab. On this line, set the following values:

    - **Item:** _L0101_
    - **Quantity:** _20_

1. Select **Add line** to add a new line, and set the following values:

    - **Item:** _T0100_
    - **Quantity:** _8_

1. Select **Save**.
1. Select **New** to create a second sales order.
1. In the **Create sales order** dialog box, in the **Customer account** field, select _US-008_.
1. In the **Warehouse** field, select _61_.
1. The new sales order is opened. It includes an empty line on the **Sales order lines** FastTab. On this line, set the following values:

    - **Item:** _T0100_
    - **Quantity:** _1_

1. Select **Save**.

### Walk through a typical slotting scenario

After all the prerequisite elements are in place, as described in the previous section, you're ready to try out the feature by working through each exercise in this section.

#### Generate demand

1. Go to **Warehouse management \> Setup \> Replenishment \> Slotting templates**, and select the slotting template that you created earlier.
1. On the Action Pane, select **Generate demand**. This command evaluates all demand that is in the system, and that matches the slotting template query. The total demand across all orders is then consolidated onto one line per quantity/unit of measure. An informational message appears when the process is completed.

#### Slotting demand

The *slotting demand* shows the results of demand generation, based on the setup of the slotting template.

- On the Action Pane, select **Slotting demand** to view the results from the **Generate demand** command. The lines in the slotting demand can be edited. You can delete a line, add a new line, or edit the line details.

> [!NOTE]
> You can edit demand manually, or you can import it from an external system by using data management. Whatever is in the slotting demand will be used in the next step, regardless of where it came from.

#### Locate demand

After demand has been generated, you must use the **Locate demand** command to generate the *slotting plan*.

- On the Action Pane, select **Locate demand**. The slotting process runs. An informational message appears when the process is completed.

#### Slotting plan

The slotting plan shows the location that each item/quantity was assigned to, whether overflow was used, whether let-up work was created, and the template line that was used. *Any demand that could not be slotted is highlighted in red.*

- On the Action Pane, select **Slotting plan** to view the results.

> [!NOTE]
> - The **Generate demand**, **Locate demand**, and **Run replenishment** processes are now run in a sandbox. (These processes are available from the Action Pane on the **Slotting templates** page.)
> - The **Generate demand**, **Locate demand**, and **Run replenishment** processes have a lock to ensure that they can't be triggered at the same time. Otherwise, the data that is used could be deleted.
> - The **Generate demand** and **Locate demand** processes show a warning if the run didn't generate records, or if the records are missing information.
> - When you select **Slotting plan**, the page doesn't have **New**, **Edit**, or **Delete** buttons on the Action Pane, because the data source can't be edited.
> - When you select **Run replenishment**, the system validates the selected slot template and processes.

#### Create replenishment

After the slotting plan has been created, you must create *replenishment work*, based on the plan.

- On the Action Pane, select **Run replenishment**. An informational message appears when the process is completed. This message indicates the number of headers that were created for the work build ID.

Location directives that will be used are identified based on the directive code that is specified on each template line.

## Tips

### Set up automatic slotting

After all the required elements are in place, you can set up slotting to run automatically by following these steps.

1. Go to **Warehouse management \> Replenishment \> Run slotting**.
1. Specify the slotting steps to run. Select one or more of the following slotting steps:

    - Generate demand
    - Locate demand
    - Create replenishment work

    > [!NOTE]
    > The slotting steps are progressive. If you want to select *Locate demand*, you must first select *Generate demand*.

1. Specify the slotting template to use.
1. Set the recurrence to run automatically, if you want.

For the exercises in the scenario, do **not** set up automatic slotting.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
