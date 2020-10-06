---
# required metadata

title: Pick line grouping
description: This topic provides an overview of pick line grouping.
author: Mirzaab
manager: tfehr
ms.date: 12/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations, Supply Chain Management
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-12-31
ms.dyn365.ops.version: 10.0.1

---

# Pick line grouping

[!include [banner](../includes/banner.md)]

In pick line grouping, multiple work lines that have the same item and location can be combined into a single pick that is presented to the user on a mobile device. Therefore, warehouse workers can receive the most efficient instructions that are possible, but the required separation of work lines in the system is also maintained (for example, for different containers and orders).

## Set up pick line grouping

### Create a mobile device menu item

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**, and create a new menu item that is named **Sales group line picking – User directed**.
2. Under **Mobile device menu items**, set the following values:

    - In the **Menu item name** field, enter **Sales Pick - Group line**.
    - In the **Title** field, enter **Sales Pick - Group line**.
    - In the **Mode** field, select **Work**.
    - Set the **Use existing work** option to **Yes**.

3. On the **General** FastTab, you can set the following values:

    - In the **Directed by** field, select **User directed**.
    - Set the **Generate license plate** option to **Yes**.
    - Set the **Group pick** option to **Yes**.

4. On the **Work classes** FastTab, follow these steps to configure the valid work classes for the mobile device menu item:

    1. Select **New**.
    2. In the **Work class ID** field, select **Sales** or **SO Pick**, depending on the warehouse that you will use.
    3. In the **Work order type** field, select **Sales orders**.

### Set up a mobile device menu

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**. 
1. Add the menu item that you just created to the desired menu.

### Set up a work template

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. Find the work template that should be used with this function. For this example, select the standard **51 Pick to stage** Contoso work template.
1. On the menu, select **Edit query**.
1. On the **Sorting** tab, select **Add**, and then set the following values:

    - In the **Table** field, select **Temporary work transactions**.
    - In the **Derived table** field, select **Temporary work transactions**.
    - In the **Field** field, select **Item number**.
    - In the **Search direction** field, select **Ascending**.

> [!NOTE]
> For the pick line grouping functionality to work, the work lines must be sorted by item ID. If lines that have the same items aren't sequenced one after another, they won't be grouped.

## Example

### Create picking work

Before you can set up pick line grouping, you must create some eligible outbound work.

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
2. Select **New** to create a sales order. 
3. In the **Customer account** field, select any customer. 
4. On the **General** FastTab, in the **Warehouse** field, select **51**. Then select **OK**.
5. Under **Sales order lines**, add the following six lines:

    - **Line 1:** In the **Item number** field, select **M9200**. In the **Quantity** field, enter **3**.
    - **Line 2:** In the **Item number** field, select **M9201**. In the **Quantity** field, enter **3**. 
    - **Line 3:** In the **Item number** field, select **M9202**. In the **Quantity** field, enter **2**. 
    - **Line 4:** In the **Item number** field, select **M9200**. In the **Quantity** field, enter **1**. 
    - **Line 5:** In the **Item number** field, select **M9200**. In the **Quantity** field, enter **3**.
    - **Line 6:** In the **Item number** field, select **M9202**. In the **Quantity** field, enter **7**. 

    Here is a summary of the total quantities for each item:

    - **Item M9200:** 7 each
    - **Item M9201:** 3 each
    - **Item M9202:** 9 each

6. Before you release the orders to the warehouse, you must make sure that the pick locations have enough inventory for all the items on all the orders. Review the **Location directive** setting to determine which picking locations are used for sales order picking.
7. Reserve the inventory, and release it to the warehouse. A work ID that has six lines is created. The lines are sorted by item number.

### Run the mobile device flow

1. On the mobile device, select the menu that includes the new mobile device menu item.
1. Select the **Sales Pick – Group line** menu item, and initiate the pick.

    After you select the menu and enter the work ID, you see the pick step where all pick lines for item M9200 are grouped. You receive an instruction to pick 7 each of item M9200.

1. Confirm the pick step. 
1. Go to the client screen of the work in process, and notice that all three pick lines for item M9200 were closed simultaneously.

    Work line 4 is presented.

1. Confirm the pick step.

    The last pick step on the mobile device aggregates the last two pick lines from the work order.

1. Complete the pick step for 9 each of item M9202.
1. Confirm the put step and any additional pick/put pairs to complete the work.

> [!NOTE]
> - Work lines can be grouped only if they are in sequence.
> - The following functionality isn't supported:
>
>    - Catch-weight items. If there are any catch-weight items on the work, you receive an error message before you start to pick.
>    - Piece picking.
>    - Work lines that have unfinished replenishment work.
>    - Over-picking.
