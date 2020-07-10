---
# required metadata

title: Work policies
description: This topic explains how to set up work policies.
author: perlynne
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: WHSWorkPolicy
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Work policies

This topic explains how to set up the system and the warehouse app so that they support work policies. Use this functionality to quickly register inventory without creating putaway work when receiving purchase or transfer orders, or when completing manufacturing processes. (This is a general topic, for details relating to license plate receiving see [License plate receiving via the warehouse app](warehousing-mobile-device-app-license-plate-receiving.md).)

A work policy controls whether warehouse work is created<!-- KFM: In response to what? -->. You set up each work policy by defining the conditions under which it applies (work order types and processes, inventory location, and (optionally) specific product(s)). For example, a purchase order of the product A0001 is to be received in warehouse 24, location RECV. The product is later consumed in another process at location RECV. In this case, you can set up a work policy to prevent  putaway work from being created when a worker reports product A0001 as received in RECV. 

> [!NOTE]
> - For the work policy to be active, you must define at least one location for the work policy in the **Inventory locations** section. 
> - You can't specify the same location for multiple work policies.
> - The **Print label** option for mobile device menu items won't print a license plate label unless work was created.

## Activate these features for your system

To make all the functionalities described in this topic available on your system, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), and turn on the following two features:

- License plate receiving enhancements
- Work policy enhancements for inbound work

## The Work policies page

To set up work policies go to **Warehouse management \> Setup \> Work \> Work policies**. Then make the settings on each FastTab, as described in the following subsections.

### The Work order types FastTab

On the **Work order types** FastTab, add all of the work order types (and related processes) the policy will apply too. The following work order types and related work processes are supported for work policies: 

| **Work order type** | **Work process** |
|--|--|
| Raw material picking| All related processes |
| Co-product and by-product put away | All related processes |
| Finished goods putaway | All related processes |
| Transfer receipt | License plate receiving (and putaway) |
| Purchase orders | License plate receiving (and putaway) <br> Load item receiving (and putaway) <br> Purchase order line receiving (and putaway) <br> Purchase order item receiving (and putaway) |

To set a work policy to apply for several work processes of the same work order type, add multiple lines to the grid (one for each process).

For each line in the grid, set the **Work creation method**, do one of the following:

- **Never** - the work policy will prevent warehouse work from being created for the selected work order type and related work process.
- **Cross docking** - the work policy will create cross-docking work using the policy you select in the **Cross docking policy name** column. <!-- KFM: Please confirm this -->

### The Inventory locations FastTab

On the **Inventory locations** FastTab, add all the locations where this work policy should be applied. If no location is associated with a work policy, the work policy won't be applied to any process.

You can't specify the same location for multiple work policies.

It's possible to use a warehouse location that is assigned to a location profile that doesn't have **Use license plate tracking** enabled. In this case, workers will directly register the on-hand inventory.

### The Products FastTab

Use the **Products** tab to control which products the policy should apply to:

- Set **Product selection** to **All** to apply this policy for all products.
- Set **Product selection** to **Selected** to apply the policy only to products listed in the grid. Use the toolbar here to add or remove products to/from the grid.

## Default and custom "to" locations

> [!NOTE]
> To make the functionality described in this section available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

Previously, the system supported receiving only at the default location defined for each warehouse. However, mobile device menu items that use the following processes now provide the **Use default data** option, which lets you assign a custom "to" location for each menu item (this option was already available for some other types of menu items):

- License plate receiving
- License plate receiving and putaway
- Load item receiving
- Load item receiving and putaway
- Purchase order line receiving
- Purchase order line receiving and putaway
- Purchase order item receiving
- Purchase order item receiving and putaway

The **To location** will override the receiving location of the warehouse for all the orders processed with menu items set up to use this feature.

To set up a mobile device menu item to support receiving at a custom location:

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select or create a menu item that uses one of the **Work creation process** settings listed at the start of this section.
1. On the **General** FastTab, set **Use default data** to **Yes**.
1. On the Action Pane, select **Default data**.
1. The **Default data** page opens. Make the following settings:
    - **Default data field** - Set to *To location*.
    - **Warehouse** - Select the destination warehouse to use with this menu item.
    - **Location** - Select the destination location to use with this menu item.
    - **Hardcoded value** - Leave this blank. <!-- KFM: Correct? What is this for? -->


> [!TIP]
> For a work policy to be applied, all the receiving locations (whether your using the default warehouse receiving location or a custom **To location**) must be listed in the relevant **Work policies** setup.

## Example scenario: Warehouse receiving

Some products are to be registered in location **FLOOR-001** and be available in warehouse **24** whenever received by the *Purchase order item* process. Products received by any other process should be registered in location **RECV** and work should be created as usual.

To allow for this we will need a work policy for the **Purchase order item receiving (and putaway)** process, on location **FLOOR-001**, for all products, and a menu item with default data **To location** for **FLOOR-001.**

### Prerequisites

To make the functionality described in this scenario available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

This scenario uses the standard demo data, so if you'd like to work through it using the values provided here, you must work on a system with demo data installed and select the **USMF** legal entity.

### Set up a work policy

1. Go to **Warehouse management \> Setup \> Work \> Work policies**.
1. Select **New**.
1. In the **Work policy name** field, type "No purchase item putaway work".
1. Select **Save**.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the Work order type field, select **Purchase order**.
1. In the Work order type field, select **Purchase order item receiving (and putaway)**.
1. Expand the **Inventory locations** section.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Warehouse** list, enter **24**.
1. In the **Location** field, enter or select **FLOOR-001**.
1. Expand the **Products** section.
1. In the Product selection field, select **All**.
1. Select **Save**.

### Set up a mobile device menu item to change the receiving location

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select the existing **Purchase receive** menu item.
1. Set **Use default data** to **Yes**.
1. Select **Save**.
1. On the Action Pane, select **Default data**.
1. Select **New**.
1. In **Default data field**, select **To location**.
1. In the **Warehouse** field, select **24**.
1. In the **Hardcoded value** field, write **FLOOR-001**.
1. Select **Save**.

### Receive a purchase order without creating work

This procedure shows an example of receiving a purchase order item without creating work at a location different than the default receiving location set up for the warehouse. An applicable work policy and mobile device menu item is a prerequisite for this task. The previous procedures show these setups.

#### Create a purchase order

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. Select vendor account **US-101**.
1. Expand the **General** section.
1. Select site **2**.
1. Select warehouse **24**.
1. Select **OK**.
1. Select the purchase order line.
1. In the **Item number** field, select **A0001**.
1. Select **Save**.

#### Receive a purchase order

1. Sign in to the mobile device on warehouse **24**
1. Select **Inbound**.
1. Select **Purchase receive**.
   The current page should display location **FLOOR-001**.
1. Write the purchase order number from the previous sub-taks.
1. Write item number **A0001**.
1. Select **OK**.
1. Write quantity **1**.
1. Select **OK**
1. Work completed.

The purchase order is now received and there's no work associated to it. The on-hand inventory has been updated and a quantity of 1 **A0001** is available in **FLOOR-001**.

## Example scenario: Manufacturing

In the following example, there are two production orders, PRD-001 and PRD-002. Production order PRD-001 has an operation that is named **Assembly**, where product SC1 is being reported as finished to location 001. Production order PRD-002 has an operation that is named **Painting** and consumes product SC1 from location 001. Production order PRD-002 also consumes raw material RM1 from location 001. RM1 is stored in warehouse location BULK-001 and will be picked to location 001 by warehouse work for raw material picking. The picking work is generated when production PRD-002 is released.

[![Warehouse work policies](./media/warehouse-work-policies.png)](./media/warehouse-work-policies.png)

When you plan to configure a warehouse work policy for this scenario, you should consider the following:

- Warehouse work for finished goods putaway isn’t required when you report product SC1 as finished from production order PRD-001 to location 001. This is because the **Painting** operation for production order PRD-002 consumes SC1 at the same location.
- Warehouse work for raw material picking is required in order to move raw material RM1 from warehouse location BULK-001 to location 001.

Here is an example of a work policy that you could set up, based on these considerations:

- **Work policy name**: No putaway work.
- **Work order type**: _Finished goods put away_, and _Co-product and by-product put away_.
- **Inventory locations**: warehouse 51, location 001
- **Products**: SC1

The following procedures provide step-by-step instructions about how to set up the warehouse work policy for this scenario. A sample setup showing how to report a production order as finished to a location that isn’t license-plate controlled is also described.

## Example scenario: Report as finished to a location that isn’t license-plate controlled

This scenario shows an example of reporting a production order as finished to a location that isn't license-plate controlled. This scenario assumes that you already have an appropriate work policy available.

This scenario uses the standard demo data, so if you'd like to work through it using the values provided here, you must work on a system with demo data installed and select the **USMF** legal entity.

### Set up a warehouse work policy

Warehouse processes don’t always include warehouse work. By defining a work policy, you can prevent the creation of work for raw material picking and put-away of finished goods for a set of products at specific locations.

1. Go to **Warehouse management \> Setup \> Work \> Work policies**.
1. Select **New**.
1. In the Work policy name field, type **No put-away work**.
1. Select **Save**.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Work order type** field, select **Finished goods put away**.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Work order type field**, select **Co-product and by-product put away**.
1. Expand the **Inventory locations** section.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Warehouse** list, enter **51**.
1. In the **Location** field, enter or select **001**.
1. Expand the **Products** section.
1. In the **Product selection** field, select **Selected**.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select **L0101**.
1. Select **Save**.

### Set up an output location

1. Go to **Organization administration \> Resources \> Resource groups**.
1. In the list, select resource group **5102**.
1. Select **Edit**.
1. In the **Output warehouse** field, enter **51**.
1. In the **Output location** field, enter **001**.

> [!NOTE]
> Location 001 isn't a license-plate controlled location. You can set up a non–license plate output location only if an applicable work policy exists for the location.

### Create a production order and report it as finished

1. Close the page.
1. Go to **Production control \> Production orders \> All production orders**.
1. Select **New production order**.
1. In the Item number field, enter **L0101**.
1. Select **Create**.
1. On the Action Pane, select **Production order**.
1. Select **Estimate**.
1. Select **OK**.
1. Select **Start**.
1. Select the **General** tab.
1. In the **Automatic BOM consumption** field, select **Never**.
1. Select **OK**.
1. Select **Report as finished**.
1. Select the **General** tab.
1. Select **Yes** in the **Accept error** field.
1. Select **OK**.
1. On the Action Pane, select **Warehouse**.
1. Select **Work details**.

When the production order was reported as finished, no work was generated for put-away. This occurs because a work policy is defined that prevents work from being generated when product L0101 is reported as finished to location 001.

## More information

For more information about mobile device menu items, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

For more information about license plate receiving and work policies, see [License plate receiving via the warehouse app](warehousing-mobile-device-app-license-plate-receiving.md).

For more information about inbound load management, see [Warehouse handling of inbound loads for purchase orders](inbound-load-handling.md).
