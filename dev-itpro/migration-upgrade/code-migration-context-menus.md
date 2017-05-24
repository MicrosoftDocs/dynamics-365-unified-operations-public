---
# required metadata

title: Code migration - Context menus
description: A new programming model is required for context menus (shortcut menus). This article outlines the process for migrating context menu code from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 for Operations. It also includes UX guidelines for context menus.
author: jasongre
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 16301
ms.assetid: 8f3b62f2-4de6-4ea3-b3e6-1101d0fe308e
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Code migration - Context menus

[!include[banner](../includes/banner.md)]


A new programming model is required for context menus (shortcut menus). This article outlines the process for migrating context menu code from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 for Operations. It also includes UX guidelines for context menus.

In Microsoft Dynamics AX 2012 and earlier versions, developers modified right-click context menus (shortcut menus) by using the **PopupMenu** class. This class relied on Microsoft Windows application programming interfaces (APIs) that aren't available on the web. In Dynamics 365 for Operations, the **ContextMenu** APIs have been created as replacements to provide similar functionality. Previously, the **context()** and **showContextMenu()** method overrides were the entry points for modifying context menus for specific controls. These overrides typically contained code to add options to the context menu, and also to process the user’s selection. The code for processing the user's selection used a wait model. In Dynamics 365 for Operations, these overrides are being removed, and the wait model is being eliminated. Instead, developers must create two overrides: **getContextMenuOptions()** to add options to the context menu and **selectedMenuOption()** to process the user’s selection.

## Migrate context menu code in Dynamics 365 for Operations
Migration from the **PopupMenu** APIs to the **ContextMenu** APIs can be broken down into three main steps.

### Step 1. Add a constant for each menu option that must be added

The old **insertItem()** method in the **PopupMenu** class returned an identifier for the menu option that was being added. This identifier was saved into a variable for future reference. Because developers will define the menu identifier for themselves in Dynamics 365 for Operations, it's a good idea to define constants for each option to help with code readability.

-   At the form level, add a constant for each menu option that is being added to the context menu. The value must be unique within each context menu. Note that you must modify the old variable name if it conflicts with another variable on the form or control.

#### Before

    public void context()
    {
        ...
        int listCreateRoot = listMenu.insertItem("@SYS5480");
        ...

#### After

    [Form]
    public class MainAccount extends FormRun
    {
        ...
        public const int listCreateRoot = 1;
        ...

### Step 2. Build the context menu

Construct the list of submenus and menu options, and add it to the control’s context menu.

1.  Add the **getContextMenuOptions()** method override on the control.
2.  Create a new context menu and a list to hold the options that you will add to the menu:
    -   ContextMenu menu = new ContextMenu();
    -   List menuOptions = new List(Types::Class);

3.  Add menu options to the list:
    -   ContextMenuOption option = ContextMenuOption::Create(label,identifier);
    -   menuOptions.addEnd(option);

4.  Add the list of options to the menu.
    -   menu.ContextMenuOptions(menuOptions);

5.  Modify the **return** statement.
    -   return menu.Serialize();

### Step 3. Process the user selection from the context menu

1.  Add the **selectedMenuOption()** method override on the control.
2.  Move the **switch()** statement for processing options into this override.

## Code example
This section illustrates the migration of a context menu from Dynamics AX 2012 to Dynamics 365 for Operations. The **MainAccount** form is used as an example.

### Original code

    public void context()
    {       
        PopupMenu  listMenu        = new PopupMenu(element.hWnd());
        int        listCreateRoot  = listMenu.insertItem("@SYS5480");
        int        selectedMenu;
        selectedMenu = listMenu.draw();
        switch (selectedMenu)
        {
            case -1:
                break;
            case listCreateRoot:
                mainAccount_ds.create();
                break;
            default:
                break;
        }
    }

### Migrated code

    // Define new form-level constant for each context menu option
    public const int listCreateRoot = 1;
    // Define new override on the control for building the context menu
    public str getContextMenuOptions()
    {
        str ret;
        ContextMenu menu = new ContextMenu(); 
        ContextMenuOption option = ContextMenuOption::Create("@SYS5480", listCreateRoot);
        List menuOptions = new List(Types::Class); 
        // Add label and ID of menu option
        menuOptions.addEnd(option); 
        menu.ContextMenuOptions(menuOptions);
        return menu.Serialize();
    }
    // Define new override on the control for processing the user selection
    public void selectedMenuOption(int selectedOption)
    {
        switch (selectedOption)
        {
            case -1:
                break;
            case listCreateRoot:
                mainAccount_ds.create();
                break;
            default:
                break;
        }
    }

## UX guidelines for context menus
As you migrate context menus, consider the following guidelines:

-   The most important commands should be at the top of the menu.
-   Remove commands that don't apply to the current state of the element that is the target of the right-click.
-   Right-click is a shortcut. Therefore, the commands on the context menu should **always** be available in other places on the page.
-   Don't create submenus of context menus. Submenus are hard to use and aren't touch-friendly.
-   Limit the number of menu items to five.




