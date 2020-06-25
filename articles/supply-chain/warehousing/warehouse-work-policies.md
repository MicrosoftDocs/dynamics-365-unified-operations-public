---
# required metadata

title: Work policies
description: This topic explains how to set up work policies.
author: perlynne
manager: tfehr
ms.date: 06/25/2020
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
ms.search.validFrom: 2020-06-25
ms.dyn365.ops.version: Release 10.0.13
---

# Work policies

This topic explains how to set up the warehousing app so that it supports work policies. This is a general article, for details relating to license plate receiving see [License plate receiving via the warehousing app](warehousing-mobile-device-app-license-plate-receiving.md).

Use this functionality to quickly register the inventory without creating put away work when receiving purchase or transfer orders, or when completing manufacturing processes.

A work policy controls whether warehouse work is created. You can set up the work policy by using a combination of: **work order types** (and **Work process**), an **inventory location**, and (optionally) a **product**. For example, a purchase order of the product A0001 is to be received in warehouse 24, location RECV. The product is later consumed in another process at location RECV. In this case, you can set up a work policy to prevent the put away work from being created when you report product A0001 as received in RECV. The work policy is an individual entity that can be described through the following information:

- **Work policy name** (the unique identifier of the work policy)
- **Work order types**,  **Work process,** and **Work creation method**
- **Inventory locations**
- **Products**

> [!NOTE]
> - For the work policy to be active you must define at least one location for the work policy in the **Inventory locations** section. 
> - You can't specify the same location for multiple work policies.
> - The **Print label** option for Warehousing mobile device menu items won't print a license plate label without work creation.

To make all the functionalities available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Work policies form

To setup work policies go to **Warehouse management \> Setup \> Work \> Work policies**.

### Work order types

In the **Work policies** form, on the **Work order types** tab you can select from the following work order types and related work processes: 

| **Work order type** | **Work process** |
|--|--|
| Raw material picking| All related processes |
| Co-product and by-product put away | All related processes | 
| Finished goods putaway | All related processes |
| Transfer receipt | License plate receiving (and putaway) |
| Purchase orders | License plate receiving (and putaway) <br> Load item receiving (and putaway) <br> Purchase order line receiving (and putaway) <br> Purchase order item receiving (and putaway) |

In order for the work policy to apply for several work processes of the same work order type multiple lines must be added to this grid.

The **Work creation method** field can have the value **Never** or **Cross docking**. If this value is set to **Never**, the work policy will prevent warehouse work from being created for the selected work order type and related work process. If this value is set to **Cross docking**, a cross docking policy must also be created.

### Inventory location

On the **Inventory locations** tab, you can add to the grid all the locations where this work policy should be applied. If no location is associated with a work policy, the work policy won't be applied to any process.

It's possible to use a warehouse location that is assigned to a location profile even when **Use license plate tracking** isn't turned on, and directly register the on-hand inventory.

### Products

On the **Products** tab, you can select if this work policy will apply to all products or to the products listed on the grid.

## Warehousing mobile device app processing

Once the work policy is set up, the work policies will be checked whenever a worker uses a menu item associated with the respective **Work process.**

### Default locations

Previously, the system supported receiving only at the default location that is defined for each warehouse. However, when this feature is turned on, mobile device menu items for License plate receiving (and putaway), Load item receiving (and putaway), Purchase order line receiving (and putaway), and Purchase order item receiving (and putaway) now provide the **Use default data** option, which lets you select a custom "to" location for each menu item (this option was already available for some other types of menu items). The **To location** will override the receiving location of the warehouse for all the orders processed with this menu item.

For the work policy to be applied, all the receiving locations (whether default warehouse receiving location or default data **To location**) must be listed in the **Work policies** form.

To make this functionality available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Example scenario

Some products are to be registered in location **FLOOR-001** and be available in warehouse **24** whenever received by the Purchase order item process. Products received by any other process should be registered in location **RECV** and work should be created as usual.

To allow for this we will need a work policy for the **Purchase order item receiving (and putaway)** process, on location **FLOOR-001**, for all products, and a menu item with default data **To location** for **FLOOR-001.**

### Set up a work policy

To make this functionality available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The USMF demo data company was used to create this procedure.

1. Go to **Warehouse management \> Setup \> Work \> Work policies**.
1. Select **New**.
1. In the Work policy name field, type "No purchase item putaway work".
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

The USMF demo data company was used to create this procedure.

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

To make this functionality available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

This procedure shows an example of receiving a purchase order item without creating work at a location different than the default receiving location set up for the warehouse. An applicable work policy and mobile device menu item is a prerequisite for this task. The previous procedures show these setups.

#### Subtask: create a purchase order

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

#### Subtask: receive a purchase order

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

## Manufacturing Example

In the following example, there are two production orders, PRD-001 and PRD-002. Production order PRD-001 has an operation that is named **Assembly**, where product SC1 is being reported as finished to location 001. Production order PRD-002 has an operation that is named **Painting** and consumes product SC1 from location 001. Production order PRD-002 also consumes raw material RM1 from location 001. RM1 is stored in warehouse location BULK-001 and will be picked to location 001 by warehouse work for raw material picking. The picking work is generated when production PRD-002 is released.

[![Warehouse work policies](./media/warehouse-work-policies.png)](./media/warehouse-work-policies.png)

When you plan to configure a warehouse work policy for this scenario, you should consider the following information:

- Warehouse work for finished goods put-away isn’t required when you report product SC1 as finished from production order PRD-001 to location 001. This is because the **Painting** operation for production order PRD-002 consumes SC1 at the same location.
- Warehouse work for raw material picking is required in order to move raw material RM1 from warehouse location BULK-001 to location 001.

Here is an example of the work policy that you can set up, based on these considerations:

- **Work policy name**: No put-away work.
- **Work order type**: _Finished goods put away_, and _Co-product and by-product put away_.
- **Inventory locations**: warehouse 51, location 001
- **Products**: SC1

The following procedures provide step-by-step instructions about how to set up the warehouse work policy for this scenario. A sample setup showing how to report a production order as finished to a location that isn’t license plate–controlled is also described.

## Set up a warehouse work policy

Warehouse processes don’t always include warehouse work. By defining a work policy, you can prevent the creation of work for raw material picking and put-away of finished goods for a set of products at specific locations. The USMF demo data company was used to create this procedure.

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

## Report a production order as finished to a location that isn’t license plate–controlled

This procedure shows an example of reporting as finished to a location that isn't license plate–controlled. An applicable work policy is the prerequisite for this task. The previous procedure shows the setup of the work policy.

### Subtask: Set up an output location

1. Go to **Organization administration \> Resources \> Resource groups**.
1. In the list, select resource group **5102**.
1. Select **Edit**.
1. In the **Output warehouse** field, enter **51**.
1. In the **Output location** field, enter **001**.

> [!NOTE]
> Location 001 isn't a license plate–controlled location. You can set up a non–license plate output location only if an applicable work policy exists for the location.

### Subtask: Create a production order and report it as finished

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

For more information about license plate receiving and work policies, see [License plate receiving via the warehousing app](warehousing-mobile-device-app-license-plate-receiving.md).

For more information about inbound load management, see [Warehouse handling of inbound loads for purchase orders](inbound-load-handling.md).
