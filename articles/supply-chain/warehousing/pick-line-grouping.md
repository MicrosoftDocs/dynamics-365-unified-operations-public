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

Before pick line grouping can be done, some eligible outbound work must be created.

Go to **Sales and Marketing > Sales orders > All sales orders**. Click New to create a new sales order. Pick any customer. In the _General_ section specify Warehouse 51.

1. Sales order 1:
  1. Line 1 – Item M9200, 3 ea
  2. Line 2 – Item M9201, 3 ea
  3. Line 3 – Item M9202, 2 ea
  4. Line 4 – Item M9200, 1 ea
  5. Line 5 – Item M9200, 3 ea
  6. Line 6 – Item M9202, 7 ea

Total quantities are therefore:

- --Item M9200, 7 ea
- --Item M9201, 3 ea
- --Item M9202, 9 ea

Before releasing the orders to warehouse, ensure there is enough inventory on the pick locations for all the items on the orders. Review the Location Directive setting to be sure what picking locations are used for sales order picking.

Reserve the inventory and Release it to warehouse. Work ID with 6 lines should have been created, sorted by Item number.

### Mobile device flow execution

Enter mobile device and select the menu where the new mobile device menu item is located.

Select the _Sales Pick – Group line_menu item and initiate the pick. After selecting the menu and entering the Work ID, the user will be presented with the Pick step where all Pick lines for Item M9200 will be grouped. The user is therefore instructed to pick 7ea of Item M9200. Confirm the Pick step. Navigate to the client screen of the Work in process and you can observe that all three Pick lines for Item M9200 have now been closed simultaneously.

Next, Work line 4 is presented for the user. Confirm the pick and continue further.

Last Pick step on the mobile device will aggregate the last two Pick lines from the Work order. Proceed with completing the Pick step in one go for 9 ea of Item M9202.

Confirm the Put step and any further Pick/Put pairs to complete the Work.

Appendix

- Work lines must be in sequence to be grouped
- Catch weight items are not supported

- If there are any catch weight items on the work, the user will receive an error before starting to pick

- Piece picking is not supported
- Work lines with unfinished replenishment work are not supported

- Over picking is not supported
