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

Pick line grouping allows multiple work lines that have the same item and location to be combined into a single pick presented to the user on the mobile device. This allows for warehouse workers to be given the most efficient instructions possible, while still maintaining required work line separation within the system (for different containers, orders, etc).

## Set up pick line grouping

### Mobile device menu item

Navigate to Warehouse management _-_Setup _-_  Mobile device _-_ Mobile device menu items and create a new menu item for Sales group line picking – User directed.

In **Header** , specify the following:

- --Menu item name – _Sales Pick - Group line_
- --Title – _Sales Pick - Group line_
- --Mode – _Work_
- --Use existing work – _Yes_

In **General** fast tab, the following setting can be specified:

- --Directed by – _User directed_
- --Generate license plate – _Yes_
- --Group pick – _Yes_

In **Work classes** fast tab, set up the valid work classes for this mobile device menu item:

- --Work class ID – _Sales and SO Pick – depending on which warehouse you will be using for demo_
- --Work order type – _Sales orders_

### Mobile device menu

Navigate to _Warehouse management_ __ _Setup_ __ _Mobile device_ __ _Mobile device_ menu and add the newly created menu item to the desired menu.

### Work template

Navigate to _Warehouse management - Setup - Work - Work templates_ and find the Work template that will be used with this function. For this demo, standard Contoso Work template **51 Pick to stage** was used.

Select the correct Work template, click on _Edit query_ and navigate to _Sorting_tab. Add a new line with the following criteria:

- --Table – _Temporary work transactions_
- --Derived table – _Temporary work transactions_
- --Field – _Item number_
- --Search direction – _Ascending_

Current limitation of this functionality is that the work lines must be sorted by Item ID in order for this to work. If lines with the same items are not sequenced one after another, then they will not be grouped together.

## Demo

### Create picking work

Before Pick line grouping can be done, some eligible outbound work must be created.

Navigate to _Sales and Marketing - Sales orders - All sales order_. Click New to create a new sales order. Pick any customer. In the _General_ section specify Warehouse 51.

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
