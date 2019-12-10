---
# required metadata

title: Pick line grouping
description: This topic provides an overview of pick line grouping.
author: Mirzaab
manager: AnnBe
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
ms.reviewer: josaw
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

Pick line grouping allows multiple work lines that have the same item and location to be combined into a single pick presented to the user on a mobile device. This functionality allows for warehouse workers to be given the most efficient instructions possible, while still maintaining required work line separation within the system (for different containers, orders, etc.).

## Set up pick line grouping

### Create a mobile device menu item

1. Go to **Warehouse management > Setup >  Mobile device > Mobile device menu items** and create a new menu item for "Sales group line picking – User directed".

1. Under **Mobile device menu items**, specify the following:

- In the **Menu item name** field, enter "Sales Pick - Group line".
- In the **Title** field, enter "Sales Pick - Group line".
- In the **Mode** field, select **Work**.
- Set the **Use existing work** toggle to **Yes**.

1. On the **General** FastTab, the following setting can be specified:

- In the **Directed by** field, select **User directed**.
- Set the  **Generate license plate** toggle to **Yes**.
- Set the **Group pick** toggle to **Yes**.

1. On the **Work classes** FastTab, configure the valid work classes for this mobile device menu item:

- Click **New**.
- In the **Work class ID** field, select **Sales** or **SO Pick**, depending on which warehouse you will be using.
- In the **Work order type** field, select **Sales orders**.

### Set up mobile device menu

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**. 

1. Add the newly created menu item to the desired menu.

### Set up work template

1. Go to **Warehouse management > Setup > Work > Work templates**.

1. Find the work template that will be used with this function. For this example, select the standard Contoso work template **51 Pick to stage**.

1. In the menu, click **Edit query**.

1. Click the **Sorting** tab.

1. Click **Add** and select the following:

- In the **Table** field, select **Temporary work transactions**.
- In the **Derived table** field, select **Temporary work transactions**.
- In the **Field** field, select **Item number**.
- In the **Search direction** field, select **Ascending**.

> [!NOTE]
> The work lines must be sorted by **Item ID** for this funcitonality to work. If lines with the same items are not sequenced one after another, then they will not be grouped together.

## Example

### Create picking work

Before pick line grouping can be set up, some eligible outbound work must be created.

1. Go to **Sales and Marketing > Sales orders > All sales orders**.

1. Click **New** to create a new sales order. 

1. In the **Customer account** field, select any customer. 

1. On the **General** FastTab, in the **Warehouse** field, select **51** and then click **Ok**.

1. Under **Sales order lines**, add six lines with the selections:
  1. Line 1: in the **Item number** field, select **M9200**. In the **Quantity** field, enter **3**.
  2. Line 2: in the **Item number** field, select **M9201**. In the **Quantity** field, enter **3**. 
  3. Line 3: in the **Item number** field, select **M9202**. In the **Quantity** field, enter **2**. 
  4. Line 4: in the **Item number** field, select **M9200**. In the **Quantity** field, enter **1**. 
  5. Line 5: in the **Item number** field, select **M9200**. In the **Quantity** field, enter **3**.
  6. Line 6: in the **Item number** field, select **M9202**. In the **Quantity** field, enter **7*. 

  The total quantities are:
  - Item M9200, 7 each
  - Item M9201, 3 each
  - Item M9202, 9 each

1. Before releasing the orders to the warehouse, you need to ensure there is enough inventory on the pick locations for all the items on the orders. Review the **Location directive** setting to see which picking locations are used for sales order picking.

1. Reserve the inventory and release it to the warehouse. A Work ID with six lines is created, sorted by **Item number**.

### Mobile device flow execution

1. On the mobile device, select the menu where the new mobile device menu item is located.

1. Select the **Sales Pick – Group line** menu item and initiate the pick.

1. After selecting the menu and entering the work ID, you will see the pick step where all pick lines for item M9200 are grouped. You will receive an instruction to pick 7 each of item M9200.

1. Confirm the pick step. 

1. Go to the client screen of the work in process and you can observe that all three pick lines for item M9200 have now been closed simultaneously.

1. Work line 4 is then presented.

1. Confirm the pick.

1. The last pick step on the mobile device will aggregate the last two pick lines from the work order. Complete the pick step for 9 each of item M9202.

1. Confirm the put step and any further pick/put pairs to complete the work.

> [!NOTES]
> - Work lines must be in sequence to be grouped.
> - The following functionality is not supported:
>   - Catch weight items. If there are any catch weight items on the work, you will receive an error before starting to pick.
>   - Piece picking.
>   - Work lines with unfinished replenishment work.
>   - Over picking is not supported.
