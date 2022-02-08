---
title: Customize the production floor execution interface
description: This topic explains how to extend current forms or create new forms and buttons for the production floor execution interface.
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

Developers can extend current forms or create their own forms and buttons for the production floor execution interface. After you've added the code for these new elements, admins or shop floor managers can easily add them to the interface by using the standard configuration controls.

For example, here are some of the possible solutions if new columns are needed in a main form:

- Extend the `JmgProductionFloorExecutionMainGrid` form, and add the desired fields.
- Create a new form, and add it as a new main view (tab).

## Add a new button (action)

To add a new button (action), follow these steps to create a class that implements your custom action.

1. Create a new class that is named `<ExtensionPrefix>_JmgProductionFloorExecution<ActionName>Action`, where:

    - `<ExtensionPrefix>` uniquely identifies your solution, typically by using your company name.
    - `<ActionName>` is a unique name for the class. It typically identifies the kind of action.

1. The new class must extend the `JmgProductionFloorExecutionAction` class.
1. Override all necessary methods.

For examples, look at the code for the following classes:

- `JmgProductionFloorExecutionBreakAction` – A class for a simple action that doesn't need any records.
- `JmgProductionFloorExecutionReportFeedbackAction` – A class that provides more complex functionality.

When you've finished, the new button (action) will automatically be listed on the **Design tabs** page in Microsoft Dynamics 365 Supply Chain Management. There, you (or an admin or floor manager) can easily add it to the primary or secondary toolbar, just as you can add the standard buttons. For instructions, see [Design the production floor execution interface](production-floor-execution-tabs.md).

## Add a new main view

1. Create a new form that has the desired elements and functionality. Note that this form is a new form, not an extension. Name the form `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>`, where:

    - `<ExtensionPrefix>` uniquely identifies your solution, typically by using your company name.
    - `<FormName>` is a unique name for the form.

1. Create a menu item that is named `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>`.
1. Create an extension that is named `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>_Extension`, where the `getMainMenuItemsList` method is extended by adding the new menu item to the list. The following code shows an example.

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

When you've finished, the new main view will automatically be listed in the **Main view** combo box on the **Design tabs** page in Supply Chain Management. There, you (or an admin or floor manager) can easily add it to new or existing tabs, just as you can add the standard main views. For instructions, see [Design the production floor execution interface](production-floor-execution-tabs.md).

## Add a details view

1. Create a new form that has the desired elements and functionality. Note that this form is new, not an extension. Name the form `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>Detail`, where: 

    - `<ExtensionPrefix>` uniquely identifies your solution, typically by using your company name.
    - `<FormName>` is a unique name for the form.

1. Create a menu item that is named `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>Detail`.
1. Create an extension that is named `<ExtensionPrefix>_JmgProductionFloorExecution<FormName>_Extension`, where the `getDetailsMenuItemList` method is extended by adding the new menu item to the list.

When you've finished, the new details view will automatically be listed in the **Details view** combo box on the **Design tabs** page in Supply Chain Management. There, you (or an admin or floor manager) can easily add it to new or existing tabs, just as you can add the standard details views. For instructions, see [Design the production floor execution interface](production-floor-execution-tabs.md).

## Add a numeric keypad to a form or dialog

The following example shows how to add numeric keypads to a form.

1. The number of numeric keypad controllers that each form contains must equal the number of numeric keypads in that form.

    ```xpp
    private JmgProductionFloorExecutionNumpadController   numpadController1;
    private JmgProductionFloorExecutionNumpadController   numpadController2;
    private JmgProductionFloorExecutionNumpadController   numpadController3;
    ```

1. Set up the behavior of each numeric keypad controller, and connect each numeric keypad controller to a numeric keypad form part.

    ```xpp
    /// <summary>
    /// Initializes all numpad controllers, defines their behavior and connects them with numpad form parts.
    /// </summary>
    public void initializeNumpadController()
    {
        numpadController1 = new JmgProductionFloorExecutionNumpadController();
        numpadController1.getValueFromNumpadDelegate += eventhandler(this.setQuanityValueFromNumpad_1);
        QuantityNumpad1.getPartFormRun().setNumpadController(numpadController1);
    
        numpadController2 = new JmgProductionFloorExecutionNumpadController();
        numpadController2.parmNumpadEnabled(false);
        numpadController2.parmNumpadValue(333.56);
        numpadController2.getValueFromNumpadDelegate += eventhandler(this.setQuanityValueFromNumpad_2);
        QuantityNumpad2.getPartFormRun().setNumpadController(numpadController2);
    }
    ```

## Use a numeric keypad as a pop-up dialog

The following example shows one way to set up a numeric keypad controller for a pop-up dialog.

```xpp
private void setupNumpadController()
{
    numpadController = new JmgProductionFloorExecutionNumpadController();
    numpadController.parmShouldNumpadShowOkCancelButtons(true);
    numpadController.setNumpadValueToParentFormDelegate += eventhandler(this.setQtyValueFromNumpad);
}
```

The following example shows one way to call the numeric keypad pop-up dialog.

```xpp
Args args = new Args();
args.name(formstr(JmgProductionFloorExecutionNumpad));
args.menuItemName(menuItemDisplayStr(JmgProductionFloorExecutionNumpad));
args.caller(element);
Object formRun = classfactory.formRunClass(args);
formRun.init();
formRun.setNumpadController(numpadController);
numpadController.setValueToNumpad(333.56);
formRun.run();
```

## Additional resources

- [Style the production floor execution interface](production-floor-execution-styles.md)
- [Design the production floor execution interface](production-floor-execution-tabs.md)
