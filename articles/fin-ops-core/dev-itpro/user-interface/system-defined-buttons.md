---
title: System-defined buttons
description: This article describes the system-defined buttons.
author: jasongre
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 23b4dade-cb99-4c61-bd1e-cf2aeafddea4
---

# System-defined buttons

[!include [banner](../includes/banner.md)]

This article describes the system-defined buttons.

## Overview

Several system-defined buttons are automatically present on the Action Pane. In general, these system-defined buttons should be applicable and should kept available to the end user. However, in rare cases (for example, if a more specialized control is required, or if a system-defined button isn't useful or applicable for a particular form), developers might have to explicitly suppress or override a system-defined button. For example, in some situations, a MenuButton that lets the user select from multiple “New” options might be preferable to the system-defined **New** button.

## List of system-defined buttons
The following tables give the full list of system-defined buttons. The tables also provide information that will be useful if these buttons must be conditionally or completely suppressed or overridden.

### Common buttons

| Button       | Button name macro\*              | Comments                                                                                             |
|--------------|----------------------------------|------------------------------------------------------------------------------------------------------|
| Export       |                                  | Don't suppress this button.                                                                          |
| Attach       | \#SystemDefinedAttachButton      | Don't suppress this button, because we will suppress it on forms that aren't set up for attachments. |
| Show filters | \#SystemDefinedShowFiltersButton | By default, **Visible**=**No** on TOC forms.                                                         |

\* System-defined button name macros are found in the SysSystemDefinedButtons macro file.

### Buttons that are specific to Details forms

These buttons are an integral part of the Details form experience. Therefore, it's very unlikely that you'll have to suppress these buttons.

| Button              | Button name macro\*                    | Comments                                                |
|---------------------|----------------------------------------|---------------------------------------------------------|
| Change view         | \#SystemDefinedShowMenuButton          | This button exists under the **Options** Action Pane tab. |
| Grid view           | \#SystemDefinedGridViewButton          |                                                         |
| Details view        | \#SystemDefinedDetailsViewButton       |                                                         |
| Line details view   | \#SystemDefinedLineDetailsViewButton   |                                                         |
| Header details view | \#SystemDefinedHeaderDetailsViewButton |                                                         |
| Show list           | \#SystemDefinedShowListButton          |                                                         |

\* System-defined button name macros are found in the SysSystemDefinedButtons macro file.

## Form styles that have no system-defined buttons
For several form styles, it doesn't make sense to add system-defined buttons, primarily because these forms don't have standard Action Panes. The following form styles never receive system-defined buttons:

-   Dashboard
-   Dialog
-   DropDialog
-   FormPart
-   Lookup
-   Sitemap
-   Wizard

## Suppressing most or all of the system-defined buttons
If you find that you're suppressing most or all of the system-defined buttons on a form, you should reexamine your form style (**Form.Design.Style**) or pattern, and reconsider the purpose of the form. Should the form be a dialog instead? (By default, dialogs don't receive any system-defined buttons.) Often, forms that are in this situation have **Style**=**Auto** and would be more appropriate as dialogs. If your form should not technically be a dialog, there is no currently no metadata or code that can automatically suppress all the system-defined buttons at the same time. Unless you switch the form to a form style that doesn't receive any system-defined buttons, you must to suppress/override each button individually (see the other sections in this article). This scenario should be extremely rare.

## New and Delete system buttons
The **New** and **Delete** buttons are currently added by the kernel, and are controlled via special metadata properties. These buttons always work on the first master data source on the form.

### When are these buttons available by default?

Forms usually have system-defined **New** and **Delete** buttons. These buttons appear on a form under the following conditions:

-   The form has a style that allows for system-defined buttons.
-   There is at least one data source on the form.

### How do I affect the visibility of the New and Delete buttons on a form, but still allow the standard New and Delete tasks to fire via keyboard shortcuts?

Use the **ShowNewButton** and **ShowDeleteButton** properties on **Form.Design** to control the visibility of the **New** and **Delete** buttons on a form. Note that if the data sources still let the user create and delete records, the keyboard shortcuts will continue to work even if the system buttons aren't visible.

| Property                     | Value | Description                                                |
|------------------------------|-------|------------------------------------------------------------|
| Form.Design.ShowNewButton    | No    | Suppress the system-defined **New** button on the form.    |
| Form.Design.ShowDeleteButton | No    | Suppress the system-defined **Delete** button on the form. |

### How do I affect the state (enabled/disabled) of the New and Delete buttons, and the associated task behavior on a form?

To affect both the state of the **New** and **Delete** buttons and the associated task behavior on a form, use the **AllowCreate** and **AllowDelete** properties on the first master data source. Additionally, the associated keyboard shortcuts will have no effect if you use this approach to disable the **New** and **Delete** buttons.

| Property                                                   | Value | Description                                                                                                  |
|------------------------------------------------------------|-------|--------------------------------------------------------------------------------------------------------------|
| Form.Datasources.&lt;FirstMasterDatasource&gt;.AllowCreate | No    | The form doesn't allow record creation. The form has a disabled system-defined **New** button.               |
| Form.Datasources.&lt;FirstMasterDatasource&gt;.AllowCreate | Yes   | The form allows record creation. The form has an enabled system-defined **New** button (if it's visible).    |
| Form.Datasources.&lt;FirstMasterDatasource&gt;.AllowDelete | No    | The form doesn't allow record deletion. The form has a disabled system-defined **Delete** button.            |
| Form.Datasources.&lt;FirstMasterDatasource&gt;.AllowDelete | Yes   | The form allows record deletion. The form has an enabled system-defined **Delete** button (if it's visible). |

> [!NOTE]
> If the form has a New record action, that button control overrides the enabled state of the system-defined **New** button.

### How do I change the behavior of the New task (either by clicking the button or by using the keyboard shortcut)?

There are three mechanisms for changing the behavior of the New task:

- Use the **New Record Action** property. This property is currently available only on **Form.Design**, and the referenced action will be triggered for **all** CommandButtons that call the **New** command on the form, even CommandButtons that are bound to secondary collections. In the future, the **New Record Action** property will be placed on all container controls to provide better control over the property's scope. Note that, currently, the **New Record Action** property also can't be defined as a Menu Button or Drop Dialog Button.

  |          Property           |             Value              |                              Description                              |
  |-----------------------------|--------------------------------|-----------------------------------------------------------------------|
  | Form.Design.NewRecordAction | The control name from the form | This property overrides the New task to perform the specified action. |


- (Recommended) Use eventing. In particular, there are pre-events and post-events for record creation and deletion, where you can put code that is meant to run before and after these actions. See the following code example.

    ```xpp
    [Form]
    public class Form1 extends FormRun
    {
        public void init()
        {
            super();
            element.dataHelper().RecordCreating += eventhandler(this.PreRecordCreate);
            element.dataHelper().RecordCreated  += eventhandler(this.PostRecordCreate);
            // similar methods exist for deletion:
            // element.dataHelper().RecordDeleting, element.dataHelper().RecordDeleted
            //
            // explicit actions can be triggered via:
            // element.dataHelper().RecordCreate(), element.dataHelper().RecordDelete()        
        }
        public void PreRecordCreate(FormRunServiceArgs _cancellableArgs)
        {
            //  I can add my logic here that gets invoked before the global creation task
            // if I need to, I can cancel the "super" of the task by doing:
            // _cancellableArgs.cancel()
        }
        public void PostRecordCreate()
        {
            //  I can add my logic here that gets invoked after the global creation task
        }
    }
    ```

- Create an override on the **create()** or **delete()** method on the corresponding data source.

### How do I change the behavior of the New button (but not the task)?

Imagine that you want to replace the system-defined **New** button with a menu button that lets the user select among several "New" options. Therefore, you complete the following tasks:

1.  Hide the system-defined **New** button.
2.  Model your own button for the New action.

However, at this point, the system-behavior for New still fires when the keyboard shortcut is invoked. If you want to make this modeled **New** button fire when the keyboard shortcut is pressed, you must set this button as the NewRecordAction on **Form.Design**. As we noted in the previous section, the action will currently be fired for all CommandButtons that call the New task on the form. Therefore, you should not use this approach on forms that have multiple data sources.

## Edit, Done, Save, and Restore system buttons

The **Edit**, **Done**, **Save**, and **Restore** buttons let users switch the edit mode of the form as they require. Because this capability is critical, these buttons can't currently be suppressed. However, if a form should always be in **Edit** mode or should always be in **View** mode, you can use the **ViewEditMode** property to achieve that effect, and the buttons won't appear on the form. Note that most forms should be left as **ViewEditMode**=**Auto**. Don't set **ViewEditMode**=**View** or **ViewEditMode=Edit** for purely cosmetic reasons, but only if the form will always be read-only or will always be editable.

| Form.Design.ViewEditMode | Form behavior                                                     | System-defined button behavior                                                                                                                                                                                                        |
|--------------------------|-------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| View                     | The form is always in **View** mode.                              | None of these buttons (**Edit**, **Done**, **Save**, and **Restore**) are shown, because the framework assumes that they aren't needed.                                                                                               |
| Edit                     | The form is always in **Edit** mode.                              | Only the **Save** and **Revert** buttons are shown, because the user can't exit **Edit** mode. The **Revert** button is on the framework-provided **Options** tab.                                                                    |
| Auto                     | The form can be switched between **View** mode and **Edit** mode. | In **View** mode, the **Edit** button is shown on the Action Pane. In **Edit** mode, the **Save** button is shown on the Action Pane, and the **Read mode** and **Revert** buttons are shown on the framework-provided **Options** tab. |

### Can I conditionally suppress or show the Edit button?

If a form is editable at some points and read-only at other points, the logic that is used to determine whether the user can edit the form can be used to set the **ViewEditMode** property at run time. When the form should be read-only, set **ViewEditMode**=**View**. When the form can be either edited or viewed, set **ViewEditMode**=**Auto**.

### How do I run additional code when the Edit button is clicked?

To have additional code run when the user clicks the **Edit** button, use eventing (see the example in the "How do I change the behavior of the New task (either by clicking the button or by using the keyboard shortcut)?" section earlier in this article). Specifically, use the following events:

-   To subscribe to view/edit mode switching, use these events:
    -   element.viewEditModeHelper().EditModeSwitching
    -   element.viewEditModeHelper().EditModeSwitche
-   To query the current view/edit mode, use these events:
    -   element.viewEditModeHelper().isInEditMode()
    -   element.viewEditModeHelper().IsInViewMode()
-   To trigger view/edit mode switching, use these events:
    -   element.viewEditModeHelper().setViewEditMode(ViewEditMode::Edit)

## Refresh, Popout, and Close system buttons
The **Refresh**, **Popout**, and **Close** buttons are system buttons that are located on the right side of the Action Pane. The **Refresh** button is used to refresh all data on the form. The **Popout** button is used to move the current form into a separate window. The **Close** button closes the form (essentially, this button clicks the browser's **Back** button). These system buttons are integral components and can't currently be suppressed.

## Other system-defined buttons
The remaining system-defined buttons are added during **Form.Init**. They are added only if a control of the same name doesn't already exist.

### How do I run additional code together with a system-defined button or change the behavior of the button?

-   For view switching buttons (for example, buttons that switch to the grid view, details view, header view, or lines view), you should override the **pageActivated()** method on the individual TabPage.
-   For system-defined buttons that have pre-eventing/post-eventing (for example, **New**, **Delete**, and **Edit**), you can subscribe to the appropriate events. See the corresponding sections for **New**/**Delete** and **Edit** buttons for information about specific events for those buttons.
-   For system-defined buttons that don't call a task directly (for example, **SystemDefinedShowMenuButton** and **SystemDefinedShowListButton**), you can register an override on the button through a **registerOverrideMethod()** call to have additional code run when the system-defined button is clicked.

    ```xpp
    public void overrideFunction(FormCommandButtonControl _command)
        {
            // Put any pre-super code here 
            // This serves as the call to super()
            _command.clicked(); 
            // Put any post-super code here
        }
    ```

### How do I suppress any of these system-defined buttons on a form, but without suppressing any corresponding task?

In general, we don't recommend that you suppress any of the system buttons. Their presence provides consistency to actions on forms. However, the buttons currently appear in some situations where they aren't as useful. We have future work items to address many of these situations. For example, have work items for the following tasks:

-   Suppress the **Attach** button on forms that aren't configured to allow attachments.
-   Suppress the **Export** button on forms that have no grids.
-   Suppress the **Show filters** button on forms that don't have a main grid.

However, if you must suppress one of these buttons (strongly discouraged), you can find the control via code and set its visibility to **false**, as shown in the following code example. Use SysSystemDefinedButtons macros, where they are available, to reference the button names.

```xpp
FormCommandButtonControl attachButton;

    public void init()
    {
        #SysSystemDefinedButtons

        super();

        attachButton= this.control(this.controlId(#SystemDefinedAttachButton)) as FormCommandButtonControl; 
        attachButton.visible(false); 
    }
```




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
