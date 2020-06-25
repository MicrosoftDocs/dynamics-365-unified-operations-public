---
# required metadata

title: Warehouse work policies overview
description: Warehouse work policies control whether warehouse work is created by warehouse processes, based on work order type, inventory location, and product.
author: perlynne, clmontor, johanhoffmann
manager: tfehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSWorkPolicy
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 196561
ms.assetid: cbf48ec6-1836-48d5-ad66-a9b534af1786
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: perlynne, clmontor, johanhoffmann
ms.search.validFrom: 2020-06-25
ms.dyn365.ops.version: AX 7.0.1

---

# Warehouse work policies overview

[!include [banner](../includes/banner.md)]

# Work policies

This topic explains how to set up the warehousing app so that it supports work policies. This is a general article, for details relating to license plate receiving please refer to [License plate receiving via the warehousing app](warehousing-mobile-device-app-license-plate-receiving.md).

You can use this functionality to quickly register the inventory without creating put away work when receiving purchase or transfer orders, or when completing manufacturing processes.

A work policy controls whether warehouse work is created. You can set up the work policy by using a combination of: **work order types** (and **Work process**), an **inventory location**, and (optionally) a **product**. For example, a purchase order of the product A0001 is to be received in warehouse 24, location RECV. The product is later consumed in another process at location RECV. In this case, you can set up a work policy to prevent the put away work from being created when you report product A0001 as received in RECV. The work policy is an individual entity that can be described through the following information:

-   **Work policy name** (the unique identifier of the work policy)
-   **Work order types,**  **Work process,** and **Work creation method**
-   **Inventory locations**
-   **Products**

> [!NOTE]
> - For the work policy to be active you must define at least one location for the work policy in the **Inventory locations** section. 
>		- You can't specify the same location for multiple work policies.
> - The **Print label** option for Warehousing mobile device menu items won't print a license plate label without work creation.

To make all the functionalities available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Work policies form

To setup work policies go to **Warehouse management** &gt; **Setup** &gt; **Work** &gt; **Work policies**.

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

The **Work creation method** field can have the value **Never,** or **Cross docking**. If this value is set to **Never** the work policy will prevent warehouse work from being created for the selected work order type and related work process. If this value is set to **Cross docking** a cross docking policy must also be created.

### Inventory location

In the **Inventory locations** tab you can add to the grid all the locations where this work policy should be applied. If no location is associated with a work policy, the work policy won't be applied to any process. 

It's possible to use a warehouse location that is assigned to a location profile even when **Use license plate tracking** isn't turned on, and directly register the on-hand inventory.

### Products

In the **Products** tab you can select if this work policy will apply to all products or to the products listed on the grid.

## Warehousing mobile device app processing

Once the work policy is set up, the work policies will be checked whenever a worker uses a menu item associated with the respective **Work process.**

### Default locations

Previously, the system supported receiving only at the default location that is defined for each warehouse. However, when this feature is turned on, mobile device menu items for License plate receiving (and putaway), Load item receiving (and putaway), Purchase order line receiving (and putaway), and Purchase order item receiving (and putaway) now provide the **Use default data** option, which lets you select a custom "to" location for each menu item (this option was already available for some other types of menu items). The **To location** will override the receiving location of the warehouse for all the orders processed with this menu item.

For the work policy to be applied, all the receiving locations (wether default warehouse receiving location or default data **To location**) must be listed in the **Work policies** form. 

To make this functionality available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Example 

Some products are to be registered in location **FLOOR-001** and be available in warehouse **24** whenever received by the Purchase order item process. Products received by any other process should be registered in location **RECV** and work should be created as usual. 

To allow for this we will need a work policy for the **Purchase order item receiving (and putaway)** process, on location **FLOOR-001**, for all products, and a menu item with default data **To location** for **FLOOR-001.**

### Set up a work policy

To make this functionality available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The USMF demo data company was used to create this procedure.

 1.   Go to **Warehouse management** &gt; **Setup** &gt; **Work** &gt; **Work policies**. 
 2.   Click **New**.
 3.   In the Work policy name field, type 'No purchase item putaway work'.
 4.   Click **Save**.
 5.   Click **Add**.
 6.   In the list, mark the selected row.
 7.   In the Work order type field, select **Purchase order**.
 8.   In the Work order type field, select **Purchase order item receiving (and putaway)**.
 9.   Expand the **Inventory locations** section.
 10.  Click **Add**.
 11.  In the list, mark the selected row.
 14.  In the **Warehouse** list, enter **24**.
 15.  In the **Location** field, enter or select **FLOOR-001**.
 16.  Expand the **Products** section.
 17.  In the Product selection field, select **All**.
 18.  Click **Save**.

### Set up a mobile device menu item to change the receiving location

The USMF demo data company was used to create this procedure.


 1.   Go to **Warehouse management** &gt; **Setup** &gt; **Mobile device** &gt; **Mobile device menu items**.
 2.   Select the existing **Purchase receive** menu item.
 3.   Click on the **Use default data** toggle to activate it.
 4.   Click **Save**.
 5.   Click **Default data**.
 6.   Click **New**.
 7.   In **Default data field**, select **To location**.
 8.   In the **Warehouse** field, select **24**.
 9.   In the **Hardcoded value** field, write **FLOOR-001**.
 10.  Click **Save**.

### Receive a purchase order without creating work

To make this functionality available on your system, you must turn on the *License plate receiving enhancements,* and *Work policy enhancements for inbound work* features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

This procedure shows an example of receiving a purchase order item without creating work at a location different than the default receiving location set up for the warehouse. An applicable work policy and mobile device menu item is a prerequisite for this task. The previous procedures show these setups. 

**Sub-task: create a purchase order**
 1.   Go to **Procurement and sourcing** &gt; **Purchase orders** &gt; **All purchase orders**.
 2.   Select **New**.
 3.   Select vendor account **US-101**.
 4.   Expand the **General** section.
 5.   Select site **2**.
 6.   Select warehouse **24**.
 7.   Select **OK**.
 8.   Select the purchase order line.
 9.   In the **Item number** field, select **A0001**.
 10.  Click **Save**.

**Sub-task: receive a purchase order**

 1.   Log on to the mobile device on warehouse **24**
 2.   Select **Inbound**.
 3.   Select **Purchase receive**.
   The current page should display location **FLOOR-001**.
 5.   Write the purchase order number from the previous sub-taks.
 6.   Write item number **A0001**.
 7.   Select **OK**.
 8.   Write quantity **1**.
 7.   Select **OK**
 8.   Work completed.

The purchase order is now received and there's no work associated to it. The on-hand inventory has been updated and a quantity of 1 **A0001** is available in **FLOOR-001**.

## Manufacturing Example

In the following example, there are two production orders, PRD-001 and PRD-00*2*. Production order PRD-001 has an operation that is named **Assembly**, where product SC1 is being reported as finished to location O1. Production order PRD-002 has an operation that is named **Painting** and consumes product SC1 from location O1. Production order PRD-002 also consumes raw material RM1 from location O1. RM1 is stored in warehouse location BULK-001 and will be picked to location O1 by warehouse work for raw material picking. The picking work is generated when production PRD-002 is released. 

[![Warehouse work policies](./media/warehouse-work-policies.png)](./media/warehouse-work-policies.png) 

When you plan to configure a warehouse work policy for this scenario, you should consider the following information:

-   Warehouse work for finished goods put-away isn’t required when you report product SC1 as finished from production order PRD-001 to location O1. This is because the **Painting** operation for production order PRD-002 consumes SC1 at the same location.
-   Warehouse work for raw material picking is required in order to move raw material RM1 from warehouse location BULK-001 to location O1.

Here is an example of the work policy that you can set up, based on these considerations.


|                                       |                                       |
|---------------------------------------|---------------------------------------|
| <strong>Work policy name</strong><br> | <strong>Work order types</strong><br> |
|         No put away 01     `          |     - Finished good put away<br>      |
|                                       |    <strong>Locations</strong><br>     |
|                                       |                 - O1                  |
|                                       |    <strong>Products</strong> <br>     |
|                                       |                 - SC1                 |

The following procedures provide step-by-step instructions about how to set up the warehouse work policy for this scenario. A sample setup showing how to report a production order as finished to a location that isn’t license plate–controlled is also described.

## Set up a warehouse work policy
Warehouse processes don’t always include warehouse work. By defining a work policy, you can prevent the creation of work for raw material picking and put-away of finished goods for a set of products at specific locations. The USMF demo data company was used to create this procedure. 

STEPS (21)

|     |                                                                            |
|-----|----------------------------------------------------------------------------|
| 1.  | Go to Warehouse management &gt; Setup &gt; Work &gt; Work policies.        |
| 2.  | Click New.                                                                 |
| 3.  | In the Work policy name field, type 'No put-away work'.                    |
| 4.  | Click Save.                                                                |
| 5.  | Click Add.                                                                 |
| 6.  | In the list, mark the selected row.                                        |
| 7.  | In the Work order type field, select 'Finished goods put away'.            |
| 8.  | Click Add.                                                                 |
| 9.  | In the list, mark the selected row.                                        |
| 10. | In the Work order type field, select 'Co-product and by-product put away'. |
| 11. | Expand the Inventory locations section.                                    |
| 12. | Click Add.                                                                 |
| 13. | In the list, mark the selected row.                                        |
| 14. | In the Warehouse list, enter '51'.                                         |
| 15. | In the Location field, enter or select '001'.                              |
| 16. | Expand the Products section.                                               |
| 17. | In the Product selection field, select 'Selected'.                         |
| 18. | Click Add.                                                                 |
| 19. | In the list, mark the selected row.                                        |
| 20. | In the Item number field, enter or select 'L0101'.                         |
| 21. | Click Save.                                                                |

## Report a production order as finished to a location that isn’t license plate–controlled
This procedure shows an example of reporting as finished to a location that isn't license plate–controlled. An applicable work policy is the prerequisite for this task. The previous procedure shows the setup of the work policy. 

STEPS (25)

<table>
<tbody>
<tr>
<td colspan="3"><strong>Sub-task: Set up an output location.</strong></td>
</tr>
<tr>
<td></td>
<td>1.</td>
<td>Go to Organization administration &gt; Resources &gt; Resource groups.</td>
</tr>
<tr>
<td></td>
<td>2.</td>
<td>In the list, select resource group &#39;5102&#39;.</td>
</tr>
<tr>
<td></td>
<td>3.</td>
<td>Click Edit.</td>
</tr>
<tr>
<td></td>
<td>4.</td>
<td>In the Output warehouse field, enter &#39;51&#39;.</td>
</tr>
<tr>
<td></td>
<td>5.</td>
<td>In the Output location field, enter &#39;001&#39;.</td>
</tr>
<tr>
<td></td>
<td>6.</td>
<td>Location 001 isn&#39;t a license plate–controlled location. You can set up a non–license plate output location only if an applicable work policy exists for the location.</td>
</tr>
<tr>
<td colspan="3"><strong>Sub-task: Create a production order and report it as finished.</strong></td>
</tr>
<tr>
<td></td>
<td>1.</td>
<td>Close the page.</td>
</tr>
<tr>
<td></td>
<td>2.</td>
<td>Go to Production control &gt; Production orders &gt; All production orders.</td>
</tr>
<tr>
<td></td>
<td>3.</td>
<td>Click New production order.</td>
</tr>
<tr>
<td></td>
<td>4.</td>
<td>In the Item number field, enter &#39;L0101&#39;.</td>
</tr>
<tr>
<td></td>
<td>5.</td>
<td>Click Create.</td>
</tr>
<tr>
<td></td>
<td>6.</td>
<td>On the Action Pane, click Production order.</td>
</tr>
<tr>
<td></td>
<td>7.</td>
<td>Click Estimate.</td>
</tr>
<tr>
<td></td>
<td>8.</td>
<td>Click OK.</td>
</tr>
<tr>
<td></td>
<td>9.</td>
<td>Click Start.</td>
</tr>
<tr>
<td></td>
<td>10.</td>
<td>Click the General tab.</td>
</tr>
<tr>
<td></td>
<td>11.</td>
<td>In the Automatic BOM consumption field, select &#39;Never&#39;.</td>
</tr>
<tr>
<td></td>
<td>12.</td>
<td>Click OK.</td>
</tr>
<tr>
<td></td>
<td>13.</td>
<td>Click Report as finished.</td>
</tr>
<tr>
<td></td>
<td>14.</td>
<td>Click the General tab.</td>
</tr>
<tr>
<td></td>
<td>15.</td>
<td>Select Yes in the Accept error field.</td>
</tr>
<tr>
<td></td>
<td>16.</td>
<td>Click OK.</td>
</tr>
<tr>
<td></td>
<td>17.</td>
<td>On the Action Pane, click Warehouse.</td>
</tr>
<tr>
<td></td>
<td>18.</td>
<td>Click Work details.</td>
</tr>
<tr>
<td></td>
<td>19.</td>
<td>When the production order was reported as finished, no work was generated for put-away. This occurs because a work policy is defined that prevents work from being generated when product L0101 is reported as finished to location 001.</td>
</tr>
</tbody>
</table>



