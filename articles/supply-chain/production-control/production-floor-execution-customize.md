---
title: Customize the production floor execution interface
description: This topic explains how to extend current forms or create their own form and buttons for the production floor execution interface
author: johanhoffmann
ms.date: 11/08/2021
ms.topic: article
ms.search.form:
ms.technology:
audience: Application User, Developer, IT Pro
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2021-11-08
ms.dyn365.ops.version: 10.0.24
---

# Customize the production floor execution interface

[!include [banner](../includes/banner.md)]

Developers can extend current forms or create their own forms and buttons for the production floor execution interface. Once you have added the code for these new elements, admins or shop floor managers can easily add them to the interface using the standard configuration controls.

For example, if new columns are needed on a main form, the possible solutions include:

- Extend the `JmgProductionFloorExecutionMainGrid` form and add desired fields.
- Create a new form and add it as a new main view (tab).

## Add a new button (action)

To add a new button (action), create a class to implement your custom action by doing the following steps:

1. Create a new class named `<ExtensionPrefix>_JmgProductionFloorExecution<ActionName>Action`, where:
    - `<ExtensionPrefix>` - Uniquely identifies your solution (typically using your company name)
    - `<ActionName>` - A unique name for this class (typically identifies the kind of action)
1. The new class must extend the `JmgProductionFloorExecutionAction` class.
1. Override all necessary methods.

For examples, take a look at the code for the following classes:

- `JmgProductionFloorExecutionBreakAction` class for simple action that doesn't need any records
- `JmgProductionFloorExecutionReportFeedbackAction` class for providing more complex functionality

When you're done, the new button (action) will be automatically listed on the **Design tabs** page, where you (or an admin or floor manager) can easily add it to the primary or secondary toolbar, just as with the standard buttons. For instructions, see [Design the production floor execution interface](production-floor-execution-tabs.md)..

## Add a new main view

1. Create a new form with the desired elements and functionality (this is  a new form, not extension). Name the form `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>`, where:
    - `<ExtensionPrefix>` - Uniquely identifies your solution (typically using your company name).
    - `<FormName>` - A unique name for this form.
1. Create a menu item named `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>`.
1. Create an extension named `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>_Extension` where the `getMainMenuItemsList` method is extended by adding the new menu item to the list.

After this setup, the new Main view can be selected from Main view combobox on the **Configure production floor execution** page.

```xpp
[ExtensionOf(classStr(JmgProductionFloorExecutionForm))]
public final class <ExtensionPrefix>_JmgProductionFloorExecutionForm<FormName>_Extension{
    static public List getMainMenuItemsList()
    {
        List menuItemList = next getMainMenuItemsList();
        menuItemList.addEnd(menuItemDisplayStr(<ExtensionPrefix>_JmgProductionFloorExecutionForm<FormName>));
        return menuItemList;
    }
```

## Add a details view

1. Create a new form with the desired elements and functionality (this is  a new form, not extension). Name the form `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>Detail`, where:
    - `<ExtensionPrefix>` - Uniquely identifies your solution (typically using your company name).
    - `<FormName>` - A unique name for this form.
1. Create a menu item named `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>Detail`.
1. Create an extension named `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>_Extension` where the `getDetailsMenuItemList` method is extended by adding the new menu item to the list.

## Add a numeric keypad to a form or dialog

Here is the short instruction how to set up a couple of numeric keypads on a form:

1. A form must contain the number of numeric keypad controllers equal to the number of numeric keypads on the form.

    ![Text Description automatically generated](media/image1.png)

1. Set up the behavior of each numeric keypad controller and connect it to a numeric keypad form part.

    ![Text Description automatically generated](media/image2.png)

## Use a numeric keypad as a pop-up dialog

The following code example shows one way to set up a numeric keypad controller for a pop-up dialog.

```xpp
    private void setupNumpadController()
    {
        numpadController = new JmgProductionFloorExecutionNumpadController();
        numpadController.parmShouldNumpadShowOkCancelButtons(true);
        numpadController.setNumpadValueToParentFormDelegate += eventhandler(this.setQtyValueFromNumpad);
    }
```
