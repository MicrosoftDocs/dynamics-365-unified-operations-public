---
# required metadata

title: Code migration -  Mouse double-click
description: In Microsoft Dynamics 365 for Operations, the mouseDblClick() override has been deprecated, and you will have to move this logic to new controls.
author: jasongre
manager: AnnBe
ms.date: 2015-12-18 23 - 21 - 21
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 28331
ms.assetid: e4da2127-ae8d-4eb0-8412-95e23f50e9c8
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Code migration -  Mouse double-click

In Microsoft Dynamics 365 for Operations, the mouseDblClick() override has been deprecated, and you will have to move this logic to new controls.

In Microsoft Dynamics AX 2012, the mouse double-click event was used for various reasons. For example, it helped provide a better user experience and provided an alternative way to run certain scenarios. Here are some examples of common usage patterns:

-   Moving elements between two lists or tree controls
-   Opening a new form to get more details about the selected field
-   Running complex business logic
-   Selecting a field in a lookup

In Dynamics 365 for Operations, the **mouseDblClick()** override has been deprecated, and developers will have to move this logic to new controls, depending on the logic that was implemented.

## Strategy overview
Before you begin to use the form, it's a good idea to fix all best practice warning messages that state, “The mouseDblClick control method has been deprecated and should not be used.” Otherwise, the form might be useless, or it might work only in limited ways.

## Migrate code from mouseDblClick() methods
As we mentioned earlier, there were various reasons for using the **mouseDblClick()** method in Dynamics AX 2012. This section explains how to migrate some of the most common scenarios.

### Moving items between two lists controls

In Dynamics AX 2012, a mouse double-click was often used in List Panel scenarios, where two list controls appeared side by side. Often, when a user double-clicked an item in one list control, that item was moved to the second list control. Migration of this **mouseDblClick()** scenario in Dynamics 365 for Operations involves alignment to the List Panel pattern. You have two options for migrating this usage pattern:

-   Use the **SysListPanel** class itself, which provides the logic and the buttons for moving items between the two list controls.
-   If you can't use the **SysListPanel** class (because the lists aren't ListViews, or the class isn't appropriate for the given situation), you can manually model the controls by following the List Panel sub-pattern. This pattern includes buttons for moving items between lists, but the developer will have to add the correct logic to make these buttons work.

### Opening a new form

In another common usage pattern in Dynamics AX 2012, the user double-clicked a field to open a new form that showed more detailed information about that field. You have several options for migrating this usage pattern:

-   Use a single-click to open a backing form that shows more details about a field. This functionality is automatically implemented for many fields that are based on table relations, and you can implement it manually by overriding the **jumpRef()** method on a control. The preferred migration route is to move the code from **mouseDblClick()** into a **jumpRef()** override, so that the navigation will be aligned with other fields in the system.
-   Model a new button on the form, and move the logic from the **mouseDblClick()** method into the button's **clicked()** method. You should use this approach only for non-input field controls (for example, a Tree control) in which a **jumpRef()** override doesn't exist.
-   Add a right-click context menu (shortcut menu) option. However, note that UX guidelines specify that the commands on context menus should **always** be available in other locations on the page. A **View details** command is automatically added to the right-click context menu for controls that have an overridden **jumpRef()** method. Therefore, this approach should be used only as an optional addition to the previous migration route (modeling a new button). For more information about how to add context menu options in Dynamics 365 for Operations, see [Code migration: Context menus](code-migration-context-menus.md).

### Moving logic to a button control

In another common usage pattern in Dynamics AX 2012, the double-click caused complex business logic to run. For this scenario, the preferred migration route is to model a new button on the form, and then move the logic from **mouseDblClick()** into the new button's **clicked()** method.

### Selecting a field in a lookup

In some custom lookups in Dynamics AX 2012, code was added so that the user could double-click a row in a grid (or an element in a tree) to select the value and close the lookup. For this scenario, the recommended migration route is to add a **Select** button at the bottom of the lookup form to enable record selection.

## UX guidelines
As you migrate mouse double-click methods, you should consider the following guidelines:

-   To move items between controls, use the **SysListPanel** class or the ListPanel pattern whenever possible.
-   When you add buttons to replace mouse double-click logic, put the button as close as possible (contextually) to the control.
-   In some cases, you might have to redesign the form to accommodate the logic that was present in the **mouseDblClick()** method.


