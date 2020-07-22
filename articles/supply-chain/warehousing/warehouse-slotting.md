---
# required metadata

title: Warehouse slotting
description: This topic provides information about warehouse slotting. Warehouse slotting lets you consolidate demand by item and unit of measure from orders that have a status of Ordered, Reserved, or Released. It helps warehouse managers intelligently plan picking locations before they release orders to the warehouse and create picking work.
author: mirzaab
manager: tfehr
ms.date: 07/01/2020
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
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: Release 10.0.9
---

# Warehouse slotting

[!include [banner](../includes/banner.md)]

Warehouse slotting lets you consolidate demand by item and unit of measure from orders that have a status of *Ordered*, *Reserved*, or *Released*. Generated demand can then be applied to locations that will be used for picking, based on quantity, unit, physical dimensions, fixed locations, and more. After the slotting plan has been established, replenishment work can be created to bring the appropriate amount of inventory to each location.

This functionality helps warehouse managers intelligently plan picking locations before they release orders to the warehouse and create picking work.

## Turn on the warehouse slotting feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Warehouse slotting feature*

## Set up warehouse slotting

To use warehouse slotting, you must set up the following elements in your system.

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

Next, you must set up the template header, slotting specifications, and location directives, as explained in the following subsections.

#### Set up a slotting template header

1. In the header for the template, set the following values:

    - **Slotting template:** _61_
    - **Description:** _61_
    - **Demand type:** *Sales order*

        Currently, *Sales order* is the only demand type that is supported.

    - **Demand strategy:** _Ordered_

        The following values are available in this field:

        - **Ordered** – The full ordered quantity on the sales order should be considered demand.
        - **Reserved** – Only the sales order line quantities that are reserved (physical and ordered) should be considered demand.

    - **Warehouse:** _61_
    - **Allow wave demand to use unreserved quantities:** _Yes_

You can also specify a query to narrow the scope of the demand that is evaluated.

#### Set up slotting specifications for each template

For each template that you create, follow these steps to add a line for each slotting specification.

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

        This field defines the units of measure of demand that are valid for the line. (For more information, see the [Set up unit-of-measure tiers for slotting](#unit-tiers) section earlier in this topic.)

    - **Assign slot criteria:** _Consider qty_

        The following values are available in this field:

        - **Assume empty** – This system should assume that all locations in the picking area are empty and should not check those locations for inventory.
        - **Consider qty** – The system should check the locations in the picking area for inventory and should skip any locations that aren't empty.

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

##### Configure the Location directives FastTab

1. On the **Location directives** FastTab, set the following values. Accept the default values for all other fields.

    - **Work type:** _Pick_
    - **Site:** _6_
    - **Warehouse:** _61_
    - **Directive code:** _Slotting_

1. Select **Save** to make the **Lines** FastTab available.

##### Configure the Lines FastTab

1. On the **Lines** FastTab, select **New** to create a line.
1. On the new line, set the following values. Accept the default values for all other fields.

    - **From quantity:** _0_
    - **To quantity:** _1000000_

1. Select **Save** to make the **Location Directive Actions** FastTab available.

##### Configure the Location Directive Actions FastTab

1. On the **Location Directive Actions** FastTab, select **New** to create a line.
1. On the new line, set the following values. Accept the default values for all other fields.

    - **Name:** _Bulk_
    - **Strategy:** _None_

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

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

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

The slotting plan shows the location that each item/quantity was assigned to, whether overflow was used, whether let-up work was created, and the template line that was used. **Any demand that could not be slotted is highlighted in red.**

- On the Action Pane, select **Slotting plan** to view the results.

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
