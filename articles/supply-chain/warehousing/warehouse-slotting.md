---
# required metadata

title: Warehouse slotting
description: Warehouse slotting lets you consolidate demand by item and unit of measure from orders that have a status of ordered, reserved, or released. It allows warehouse managers to plan picking locations intelligently before releasing orders to the warehouse and creating picking work.
author: mirzaab
manager: AnnBe
ms.date: 03/05/2020
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
ms.search.validFrom: 2020-03-05
ms.dyn365.ops.version: Release 10.0.8
---

# Warehouse slotting

Warehouse slotting lets you consolidate demand by item and unit of measure from orders that have a status of *ordered*, *reserved*, or *released*. Generated demand can then be applied to locations that will be used for picking based on quantity, unit, physical dimensions, fixed locations, and more. Once the slotting plan has been established, replenishment work can then be created to bring the appropriate amount of inventory to each location.

This functionality allows warehouse managers to plan picking locations intelligently before releasing orders to the warehouse and creating picking work.

## Enable the warehouse slotting feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - XXXX <!-- kfm: look  up this value -->

<a name="required-settings"></a>

## Set up warehouse slotting

To use warehouse slotting, you must set up the following elements in your system:

- **Unit-of-measure tiers for slotting**  
    Unit-of-measure tiers allow multiple units of measure to be grouped together for the purposes of slotting. For example, if there are multiple sizes of boxes that all get picked from the same box picking area, one tier could be created for all the sizes of boxes.
- **One or more directive codes for slotting**  
    <!-- KFM: what is this and why do we need it for this feature? -->
- **Slotting templates**  
    Each slotting template controls how inventory gets assigned to location for a specific warehouse. To set them up, go to **Warehouse management > Setup > Replenishment > Slotting templates**. Each template must include a line for each slotting specification.
- **Location directives**  
    You must have at least one location directive set up to support slotting picks. <!-- KFM: what is this and why do we need it for this feature? -->

For examples of how to set up each of these elements, see [Set up the scenario](#set-up-demo) later in this topic.

## Set up automatic slotting

Once all of the required elements are in place, you can set slotting to run automatically by doing the following:

1. Go to **Warehouse management > Replenishment > Run slotting**
1. Specify which slotting steps you want to run by selecting one or more of the following:
    - **Generate demand**
    - **Locate demand**
    - **Create replenishment work**
1. Specify which slotting template to use.
1. Set the recurrence to run automatically if desired.

## Try out this feature

<a name="set-up-demo"></a>

### Set up the scenario

Before you can see how the feature works, you must set up the prerequisite items listed in [Set up warehouse slotting](#required-settings). For this scenario, use the built-in sample data and create the records described in this section.

#### Use the USMF sample data

To work through this scenario using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

<a name="unit-tiers"></a>

#### Set up unit-of-measure tiers for slotting

Enter the following values in the header: <!-- kfm: what header? Where are we? -->

- **Slotting unit of measure tier id** – _EaBoxPl_
- **Description** – _Each box pallet_

Create a line for each unit of measure that should be part of the tier. Each line requires:

- **Unit** – _Box_
- **Description** – _Box_
- **Unit class** – _Quantity_

#### Create a directive code for slotting

Go to **Warehouse management > Setup > Directive code** and create a new directive code called "Slotting".

#### Set up your slotting templates

1. Go to **Warehouse management > Setup > Replenishment > Slotting templates**.
1. In the header of the template, enter the following:

    - **Slotting template Id** – _61_
    - **Description** – _61_
    - **Slot template demand** – Currently only *Sales order demand* is supported
    - **Slot demand strategy** – _Ordered_.  
        The following values are available:
      - **Ordered** – The full ordered quantity on the sales order will be considered as demand.
      - **Reserved** – Only the sales order line quantities that are reserved (physical and ordered) will be considered as demand.
    - **Warehouse** – _61_
    - **Allow wave demand to use unreserved quantities** - _Yes_

You can also specify a query to narrow the scope of what demand is evaluated.

#### Set up slotting specifications for each template

For each templates that you create, add a line for each slotting specification. Make the following settings for each line:

- **Line** – _1_
- **Description** – _Fixed location_
- **Minimum quantity** – _1_  
    Sets the minimum quantity of demand that is required for the line.
- **Maximum quantity** – _1000000_  
    Sets the maximum quantity of demand that is valid for this line.
- **Unit** – _(empty)_   
    Sets the unit of measure the minimum and maximum quantities refer to.
- **Slotting Unit of Measure Tier Id** – _EaBoxPl_  
    Sets the unit(s) of measure of demand that are valid to be used on this line (See also [Set up unit-of-measure tiers for slotting](#unit-tiers))
- **Assign slot criteria** – _Consider qty_.  
    The following values are available:
  - **Assume empty** – Assumes that all locations in the picking area are empty, does not check the locations for inventory.
  - **Consider qty** – Checks if the locations in the picking area already contain inventory. Skips any locations that are not empty
- **Directive code** – _Slotting_  
    Sets the location directive to use when finding the picking location of the replenishment work.
- **Overflow location** – _(empty)_  
    Sets the location inventory that will be put to if the quantity fails to find a location during processing of the line.
- **Allow let up** – _Yes_  
    When enabled, if any demand couldn't be slotted, movement work will be created to take inventory out of locations that have inventory, but where nothing was slotted. The template is then run again, ignoring the inventory in the locations. Works best when **Assign slot criteria** = _Consider qty_. 
- **Use fixed locations** – _Only fixed locations for the product_.  
    The following values are available:
  - **Fixed and non-fixed locations** – Will not restrict to only using fixed locations
  - **Only fixed locations for the product** – Will only slot to locations that are fixed locations for the product
  - **Only fixed locations for the product variant** – Will only slot to locations that are fixed locations for the product variant

Create a second template line with the following values:

- **Line** – _2_
- **Description** – _Other_
- **Minimum Qty** – _1_
- **Maximum Qty** – _1000000_
- **Unit** – _(empty)_
- **Slotting unit of measure tier ID** – _EaBoxPl_
- **Assign slot criteria** – _Consider qty_
- **Directive code** – _Slotting_
- **Allow let up** – _Yes_
- **Use fixed locations** – _Fixed and non-fixed locations_

In the query for the second line, specify the criteria for what location(s) the demand this line can be slotted to. Set _Location profile ID = PICK-06_.

#### Set up your location directives

Create a new replenishment location directive for slotting picks. Make the following settings

- **Name** – _Slotting pick_
- **Work type** – _Pick_
- **Site** – _6_
- **Warehouse** – _61_
- **Directive code** – _Slotting_

Create a new line with the following settings:

- **From quantity** – _0_
- **To quantity** – _1000000_

Create an action with the following settings:

- **Name** – _Bulk_
- **Strategy** – _None_
- **Query** – *Specify Zone ID = BULK*

#### Create demand

Do the following to create the demand for which you will apply slotting: 

1. Go to **Sales and Marketing > Sales orders >  All sales order**.
1. Select **New** to create a new sales order and enter the following settings for it:
    - **Customer** - _US-007_
    - **Warehouse** - _61_
1. Add a line to the sales order with the following values:
    - **Item** - _L0101_
    - **Quantity** - _20_
    - **Unit** - _ea._
1. Add a second line with the following values:
    - **Item** - _T0100_
    - **Quantity** - _8_
    - **Unit** - _ea_
1. Select **New** to create a second sales order with the following settings:
    - **Customer** - _US-008_
    - **Warehouse** - _61_
1. Add a line to the second sales order with the following values:
    - **Item** - _T0100_
    - **Quantity** - _1_
    - **Unit** - _pl_

### Walk through a typical slotting scenario

Once you have all of the prerequisite elements in place, as described in the previous section, you are ready to try out the feature by working through each of the exercises in this section.

#### Generate demand

Go to **Warehouse management > Setup > Replenishment > Slotting templates** and select the slotting template created earlier. Select **Generate demand** on the action bar. This will evaluate all demand that is in the system and matches the slotting template query. The total demand across all order will be consolidated into one line per Qty/UOM.

> [!NOTE]
> You could instead edit demand manually, or import in from an external system using data management. Whatever is in the slotting demand will be used in the next step, regardless of where it came from.

#### Locate demand

Once demand has been generated, select **Locate demand** on the action pane.

The slotting process now runs. Select **Slotting Plan** on the action pane to see the results.

The slotting plan shows the location that each item/qty was assigned, whether overflow was used, whether let-up work was created, and which template line was used. Any demand that couldn't be slotted will be highlighted in red.

#### Create replenishment

After the slotting plan has been created, select **Run Replenishment** in the action pane to create replenishment based on the plan.

Location directives to use will be identified based on the directive code specified on each template line.
