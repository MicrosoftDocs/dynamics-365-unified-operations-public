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

A work policy controls whether warehouse work is created in response to reporting a manufactured item as finished, or when receiving goods with warehouse app. You set up each work policy by defining the conditions under which it applies (work order types and processes, inventory location, and (optionally) specific product(s)). For example, a purchase order of the product A0001 is to be received in warehouse 24, location RECV. The product is later consumed in another process at location RECV. In this case, you can set up a work policy to prevent putaway work from being created when a worker reports product A0001 as received in RECV.

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

For each line in the grid, set the **Work creation method** to one of the following:

- **Never** - the work policy will prevent warehouse work from being created for the selected work order type and related work process.
- **Cross docking** - the work policy will create cross-docking work using the policy you select in the **Cross docking policy name** column.

### The Inventory locations FastTab

On the **Inventory locations** FastTab, add all the locations where this work policy should be applied. If no location is associated with a work policy, the work policy won't be applied to any process.

You can't specify the same location for multiple work policies.

It's possible to use a warehouse location that is assigned to a location profile that doesn't have **Use license plate tracking** enabled. In this case, workers will directly register the on-hand inventory.

### The Products FastTab

Use the **Products** tab to control which products the policy should apply to:

- Set **Product selection** to **All** to apply this policy for all products.
- Set **Product selection** to **Selected** to apply the policy only to products listed in the grid. Use the toolbar here to add or remove products to/from the grid.

## Default and custom "To" locations

> [!NOTE]
> To make the functionality described in this section available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

Previously, the system supported receiving only at the default location defined for each warehouse. However, mobile device menu items that use the following processes now provide the **Use default data** option, which lets you assign a custom **To location** for one or more menu items (this option was already available for some other types of menu items):

- License plate receiving (and putaway)
- Load item receiving (and putaway)
- Purchase order line receiving (and putaway)
- Purchase order item receiving (and putaway)

The **To location** setting for a menu item will override the default receiving location of the warehouse for all the orders processed using that menu item.

To set up a mobile device menu item to support receiving at a custom location:

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select or create a menu item that uses one of the **Work creation process** settings listed at the start of this section.
1. On the **General** FastTab, set **Use default data** to **Yes**.
1. On the Action Pane, select **Default data**.
1. The **Default data** page opens. Make the following settings:
    - **Default data field** - Set to *To location*.
    - **Warehouse** - Select the destination warehouse to use with this menu item.
    - **Location** - This drop-down list displays all of the location IDs available for the selected warehouse, but this setting doesn't actually have any effect, so you can leave it blank. You could use this list to double check the ID you need to enter into the **Hardcoded value** field.
    - **Hardcoded value** - Enter the location ID for the receiving location that applies for this menu item.

> [!TIP]
> For a work policy to be applied, all the receiving locations (whether your using the default warehouse receiving location or a custom **To location**) must be listed in the relevant **Work policies** setup.

## Example scenario: Warehouse receiving

All products received by the *Purchase order item* process are to be registered in location FL-001 and be available in warehouse 24 (without creating work). Products received by any other process (using other mobile device menu items) should be registered at the default warehouse receiving location (RECV) and work should be created as usual. (In this scenario, we won't show the second (default) receiving setup.)

To allow for this, we will need:

- A work policy for the *Purchase order item receiving (and putaway)* process on location FL-001 for all products
- A mobile device menu item with default data that sets the **To location** to *FL-001*.

### Prerequisites

To make the functionality described in this scenario available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

This scenario uses the standard demo data, so if you'd like to work through it using the values provided here, you must work on a system with demo data installed and select the **USMF** legal entity.

### Set up a work policy

1. Go to **Warehouse management \> Setup \> Work \> Work policies**.
1. Select **New**.
1. In the **Work policy name** field, enter *No purchase item putaway work*.
1. Select **Save**.
1. On the **Work order types** FastTab toolbar, select **Add** to add a row to the grid and then make the following settings for the new row:
    - **Work order type** - *Purchase orders*
    - **Work process** - *Purchase order item receiving (and putaway)*
    - **Work creation method** - *Never*
    - **Cross docking policy name** - Leave this blank

1. Expand the **Inventory locations** FastTab.
1. Select **Add** to add a row to the grid and then make the following settings for the new row:
    - **Warehouse** - *24*
    - **Location** - *FL-001*
1. Expand the **Products** FastTab and set **Product selection** to *All*.
1. Select **Save**.

### Set up a mobile device menu item to change the receiving location

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select the existing **Purchase receive** menu item from the list pane.
1. On the **General** FastTab, set **Use default data** to *Yes*.
1. Select **Save**.
1. On the Action Pane, select **Default data**.
1. The **Default data** page opens. On the Action pane, select **New** to add a row to the grid and then make the following settings for the new row:
    - **Default data field** - *To location*
    - **Warehouse** - *24*
    - **Location** - (Leave blank)
    - **Hardcoded value** - *FL-001*
1. Select **Save**.

### Receive a purchase order without creating work

This procedure shows an example of how to receive a purchase order item without creating work at a location different than the default receiving location set up for the warehouse. It uses the work policy and mobile device item created earlier in this scenario.

#### Create a purchase order

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. The **Create purchase order** dialog box opens. Make the following settings here:
    - **Vendor account** - *US-101*
    - **Site** - *2*
    - **Warehouse** - *24*
1. Select **OK** to close the dialog box and open the new purchase order
1. Make the following settings for the empty row in the **Purchase order lines** FastTab:
    - **Item number** - *A0001*
    - **Quantity** - *1*
1. Select **Save**.
1. Take note of the purchase order number.

#### Receive a purchase order

1. Sign in to the mobile device on warehouse 24 (**User ID**: *24*, **Password**: *1*)
1. Select **Inbound**.
1. Select **Purchase receive**. The current page should display **Location** *FL-001*.
1. Enter the purchase order number for the purchase order you created during the previous procedure.
1. For **Item number**, enter *A0001*.
1. Select **OK**.
1. For **Quantity**, enter *1*.
1. Select **OK**.

The purchase order is now received and there's no work associated with it. The on-hand inventory has been updated and a quantity of one A0001 is now available at location FL-001.

## Example scenario: Manufacturing

In the following example, there are two production orders, PRD-001 and PRD-002. Production order PRD-001 has an operation that is named *Assembly*, where product SC1 is being reported as finished to location 001. Production order PRD-002 has an operation that is named *Painting* and consumes product SC1 from location 001. Production order PRD-002 also consumes raw material RM1 from location 001. RM1 is stored in warehouse location BULK-001 and will be picked to location 001 by warehouse work for raw material picking. The picking work is generated when production PRD-002 is released.

[![Warehouse work policies](./media/warehouse-work-policies.png)](./media/warehouse-work-policies.png)

When you plan to configure a warehouse work policy for this scenario, you should consider the following:

- Warehouse work for finished goods putaway isn't required when you report product SC1 as finished from production order PRD-001 to location 001. This is because the *Painting* operation for production order PRD-002 consumes SC1 at the same location.
- Warehouse work for raw material picking is required to move raw material RM1 from warehouse location BULK-001 to location 001.

Here is an example of a work policy that you could set up, based on these considerations:

- **Work policy name** - *No putaway work*
- **Work order types** - *Finished goods put away* and *Co-product and by-product put away*.
- **Inventory locations** - **Warehouse** *51*, **Location** *001*
- **Products**: SC1

The following example scenario provides step-by-step instructions for how to set up the warehouse work policy for this scenario.

## Example scenario: Report as finished to a location that isn't license-plate controlled

This scenario shows an example of reporting a production order as finished to a location that isn't license-plate controlled.

This scenario uses the standard demo data, so if you'd like to work through it using the values provided here, you must work on a system with demo data installed and select the **USMF** legal entity.

### Set up a warehouse work policy

Warehouse processes don't always include warehouse work. By defining a work policy, you can prevent the creation of work for raw material picking and putaway of finished goods for a set of products at specific locations.

1. Go to **Warehouse management \> Setup \> Work \> Work policies**.
1. Select **New**.
1. In the **Work policy name** field, enter *No putaway work*.
1. On the Action Pane, select **Save**.
1. On the **Work order types** FastTab toolbar, select **Add** to add a row to the grid and then make the following settings for the new row:
    - **Work order type** - *Finished goods put away*
    - **Work process** - *All related work processes*
    - **Work creation method** - *Never*
    - **Cross docking policy name** - Leave this blank

1. Select **Add** from the toolbar again to add a second row to the grid and then make the following settings for the new row:
    - **Work order type** - *Co-product and by-product put away*
    - **Work process** - *All related work processes*
    - **Work creation method** - *Never*
    - **Cross docking policy name** - Leave this blank
1. On the **Inventory locations** FastTab toolbar, select **Add** to add a row to the grid and then make the following settings for the new row:
    - **Warehouse** - *51*
    - **Location** - *001*
1. On the **Products** FastTab, set **Product selection** to *Selected*.
1. On the **Products** FastTab toolbar, select **Add** to add a row to the grid and then make the following settings for the new row:
    - **Item number** - *L0101*
1. On the Action Pane, select **Save**.

### Set up an output location

1. Go to **Organization administration \> Resources \> Resource groups**.
1. On the list pane, select resource group **5102**.
1. Make the following settings on the **General** FastTab:
    - **Output warehouse** - *51*
    - **Output location** - *001*
1. On the Action Pane, select **Save**.

> [!NOTE]
> Location 001 isn't a license-plate controlled location. You can set up a non–license plate output location only if an applicable work policy exists for the location.

### Create a production order and report it as finished

1. Go to **Production control \> Production orders \> All production orders**.
1. On the Action Pane, select **New production order**.
1. The **Create production order** dialog box opens. Set the **Item number** to  *L0101* and then select **Create** to create the order and close the dialog box.
1. Select **Create**.
1. A new production order is added to the **All production orders** grid. Keep this new production order selected.
1. On the Action Pane, open the **Production order** tab and then, from the **Process** group, select **Estimate**.
1. The **Estimate** dialog box opens. Read the estimate and then select **OK**.
1. On the Action Pane, open the **Production order** tab and then, from the **Process** group, select **Start**.
1. The **Start** dialog box opens. Open the **General** tab.
1. Set **Automatic BOM consumption** to *Never*.
1. Select **OK** to save you setting and close the dialog box.
1. On the Action Pane, open the **Production order** tab and then, from the **Process** group, select **Report as finished**.
1. The **Report as finished** dialog box opens. Open the **General** tab.
1. Set **Accept error** to *Yes*.
1. Select **OK** to save you setting and close the dialog box.
1. On the Action Pane, select **Warehouse**.
1. On the Action Pane, open the **Warehouse** tab and then, from the **General** group, select **Work details**.

When the production order was reported as finished, no work was generated for putaway. This occurs because a work policy is defined that prevents work from being generated when product L0101 is reported as finished to location 001.

## More information

For more information about mobile device menu items, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

For more information about license plate receiving and work policies, see [License plate receiving via the warehouse app](warehousing-mobile-device-app-license-plate-receiving.md).

For more information about inbound load management, see [Warehouse handling of inbound loads for purchase orders](inbound-load-handling.md).
