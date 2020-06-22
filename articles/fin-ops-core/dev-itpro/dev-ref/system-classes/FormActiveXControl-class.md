---
title: FormActiveXControl class
description: This topic describes the FormActiveXControl class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class FormActiveXControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormActiveXControl extends FormControl
```

## Remarks

## Examples

## Methods

| Method                                                                                                      | Description                                                                                                                                          |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                             |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                  |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                  |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                   |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                               |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                   |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                              |
| public str className(\[str value\])                                                                         |                                                                                                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                  |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                     |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                       |
| public str custom(\[str value\])                                                                            |                                                                                                                                                      |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                        |
| public AnyType dispatch(VarArg )                                                                            |                                                                                                                                                      |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the client, or in Enterprise Portal, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                    |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                       |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                     |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                               |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                  |
| public COMError error()                                                                                     |                                                                                                                                                      |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                             |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                              |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                              |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                       |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                              |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                             |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                             |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                      |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                        |
| public ComInterface interface()                                                                             |                                                                                                                                                      |
| public boolean isContainer()                                                                                |                                                                                                                                                      |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                   |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                  |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                  |
| public boolean leave()                                                                                      |                                                                                                                                                      |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                     |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                        |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                     |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                            |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                    |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                    |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                             |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.              |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                      |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                      |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                        |
| public boolean rTLCapable(\[boolean value\])                                                                |                                                                                                                                                      |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                          |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                             |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                      |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                          |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                       |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                          |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                       |
| public int type(\[int value\])                                                                              |                                                                                                                                                      |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                      |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                          |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                     |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                          |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                  |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                 |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                   |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                             |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                               |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                    |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls on the form. |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                  |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                        |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                          |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                        |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                               |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                               |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                       |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                               |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                              |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                 |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                     |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                   |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                               |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                      |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                            |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                             |
| public void enter()                                                                                         |                                                                                                                                                      |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                      |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                |
| public void updateSize()                                                                                    |                                                                                                                                                      |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                       |
| public void mouseLeave()                                                                                    | Is called when the user moves the mouse pointer out of the control area.                                                                             |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                 |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                        |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                    |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                               |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                      |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                      |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                      |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                       |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                           |

## Method alignControl

Determines whether to align the control.

```xpp
public boolean alignControl([boolean value])
```

### Parameters - alignControl

value  
The new value for the property; optional.

### Return Value - alignControl

true if the control should be aligned; otherwise, false.

### Remarks - alignControl

The upper-left corner of the control is aligned according to the longest label.

## Method allowEdit

Determines whether the user can change the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  
The value to be assigned to the allowEdit property.

### Return Value - allowEdit

true if the control can be edited; otherwise, false.

### Remarks - allowEdit

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

## Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

```xpp
public boolean allowSysSetup()
```

### Return Value - allowSysSetup

true if the control is shown in the SysSetup form; otherwise, false.

## Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  
The property is set to this value, if supplied.

### Return Value - autoDeclaration

true if the member variable can be declared for this control; otherwise, false.

### Remarks - autoDeclaration

Controls cannot have identical names.

## Method beginDrag

Is called when the user starts to drag a form control.

```xpp
public int beginDrag(int x, int y)
```

### Parameters - beginDrag

x  
An integer value that indicates the y-coordinate of the mouse pointer.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer.

### Return Value - beginDrag

0 (zero) if the event has been handled.

### Remarks - beginDrag

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

## Method calcControlSize

Retrieves the size of the control.

```xpp
public container calcControlSize(int chars, int lines)
```

### Parameters - calcControlSize

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

### Return Value - calcControlSize

The container that has the width and height.

## Method caption

Gets or set the caption of the control.

```xpp
public str caption([str value])
```

### Parameters - caption

value  

### Return Value - caption

The string that is used as the caption of the control.

## Method className

```xpp
public str className([str value])
```

### Parameters - className

value  

### Return Value - className

## Method configurationKey

Gets or sets the configuration key that is assigned to the control.

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  
The ID of the configuration key that is being assigned to the control; optional.

### Return Value - configurationKey

The identifier of the configuration key that is assigned to the control.

### Remarks - configurationKey

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

## Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are in effect for the control.

```xpp
public List configurationKeyEx()
```

### Return Value - configurationKeyEx

A list that contains the IDs of configuration keys that are in effect for the control.

### Remarks - configurationKeyEx

The returned list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. The returned list also contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

## Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

```xpp
public str countryRegionCodes([str value])
```

### Parameters - countryRegionCodes

value  
The string that contains the country/region codes to set; optional.

### Return Value - countryRegionCodes

The comma-separated list of country/region codes for the control.

## Method custom

```xpp
public str custom([str value])
```

### Parameters - custom

value  

### Return Value - custom

## Method dataRelationPath

Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.

```xpp
public str dataRelationPath([str value])
```

### Parameters - dataRelationPath

value  
The string that contains the period-delimited list of relations; optional.

### Return Value - dataRelationPath

The period-delimited list of relations that links the field binding of the DataField object to a relative table.

### Remarks - dataRelationPath

This method is used by the reference group control to track exactly which relations produce the replacement field that is used. It enables the reference group control to bind consistently to the controls that it contains.

## Method dispatch

```xpp
public AnyType dispatch(VarArg )
```

### Parameters - dispatch


### Return Value - dispatch

## Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the client, or in Enterprise Portal, or in both.

```xpp
public int displayTarget([int value])
```

### Parameters - displayTarget

value  
The integer value that indicates where the control is displayed; optional.

### Return Value - displayTarget

The value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both.

## Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

```xpp
public int dragDrop([int value])
```

### Parameters - dragDrop

value  
An Integer data type that indicates whether the drag-and-drop behavior is enabled; optional.

### Return Value - dragDrop

1 if drag-and-drop operations are enabled; otherwise, false.

### Remarks - dragDrop

Use the FormControl::dragLeave, FormControl::dragOver, and FormControl::dragOverEx methods to specify the behavior.

## Method dragOver

Raises the dragOver event to indicate that a mouse drag operation is over the current control.

```xpp
public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - dragOver

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

### Return Value - dragOver

A FormDrag enumeration value that indicates the mode of dragging.

## Method dragOverEx

Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.

```xpp
public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - dragOverEx

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

### Return Value - dragOverEx

A FormDrag enumeration value that indicates the mode of dragging.

## Method dragText

Retrieves the text that is displayed when the form control is dragged.

```xpp
public str dragText()
```

### Return Value - dragText

The text that is displayed when the control is dragged; an empty string if there is no text to display when the control is dragged.

## Method enabled

Determines whether to enable or disable the object.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  
A Boolean value that specifies whether the control is enabled; optional.

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

## Method error

```xpp
public COMError error()
```

### Return Value - error

## Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

```xpp
public boolean hasChanged([boolean val])
```

### Parameters - hasChanged

val  
The value to assign as the hasChanged value for the control; optional.

### Return Value - hasChanged

true if the contents of the control have changed; otherwise, false.

## Method hasUserSetting

Indicates whether the control has custom user settings.

```xpp
public boolean hasUserSetting()
```

### Return Value - hasUserSetting

true if the control has custom user settings; otherwise, false.

## Method height

Gets or sets the height of the control.

```xpp
public int height(int value, [int mode])
```

### Parameters - height

value  
An Integer data type that indicates how the height is calculated; optional.

<!-- -->

mode  
An Integer data type that indicates how the height is calculated; optional.

### Return Value - height

The height of the control in pixels.

### Remarks - height

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

## Method heightMode

Gets or sets a calculation mode for the height of the control.

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  
An Integer data type value that indicates how the control height is calculated; optional.

### Return Value - heightMode

The calculation mode.

### Remarks - heightMode

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

## Method heightValue

Gets or sets the height of the control.

```xpp
public int heightValue([int value])
```

### Parameters - heightValue

value  
An Integer data type that specifies the height in pixels; optional.

### Return Value - heightValue

The height in pixels.

### Remarks - heightValue

The height of the control is not changed unless the exact height calculation mode is used.

## Method helpField

Retrieves the Help text for the control.

```xpp
public str helpField()
```

### Return Value - helpField

The Help text for the control; an empty string if there is no Help text for the control.

### Remarks - helpField

The helpField method cannot be used to set the value of the Help text.

## Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  
The value that is assigned as the help text for the control.

### Return Value - helpText

The string to be displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

## Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

```xpp
public str hierarchyParent([str value])
```

### Parameters - hierarchyParent

value  
The value to assign as the HierarchyParent value of the control.

### Return Value - hierarchyParent

The HierarchyParent property value of the control.

## Method hWnd

Retrieves the Windows handle for the control.

```xpp
public int hWnd()
```

### Return Value - hWnd

The handle for the control.

### Remarks - hWnd

The handle can be used with the Windows API.

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method isContainer

```xpp
public boolean isContainer()
```

### Return Value - isContainer

## Method isDisplayed

Retrieves a value that indicates whether the control is displayed.

```xpp
public boolean isDisplayed()
```

### Return Value - isDisplayed

true if the control is displayed; otherwise, false.

### Remarks - isDisplayed

To modify the visible state of the control, call the visible method.

## Method isRestricted

Retrieves a value that indicates whether the control is restricted.

```xpp
public boolean isRestricted()
```

### Return Value - isRestricted

true if the control is restricted; otherwise, false.

## Method isUserSetupEnabled

Returns a value that indicates whether the control allows for the specified level of customization.

```xpp
public boolean isUserSetupEnabled(int neededSetupRights)
```

### Parameters - isUserSetupEnabled

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control. For more information, see the �Remarks� section.

### Return Value - isUserSetupEnabled

true if the control, design, and parent container allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

### Remarks - isUserSetupEnabled

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                 |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. Using this value for neededSetupRights always returns true.                              |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label and width properties of the control. The user can also move the control. |

This method returns true only if the AllowUserSetup property for the design and all parent containers is at least as high as the level that is specified by the neededSetupRights parameter.

## Method leave

```xpp
public boolean leave()
```

### Return Value - leave

## Method left

Gets or sets the horizontal position of the control in the form.

```xpp
public int left(int value, [int mode])
```

### Parameters - left

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the horizontal arrange mode for the control; optional.

### Return Value - left

The horizontal position of the control in the form.

## Method leftMode

Sets the horizontal arrange mode for the control in the form.

```xpp
public int leftMode([int value])
```

### Parameters - leftMode

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

### Return Value - leftMode

The horizontal arrange mode for the control in the form.

## Method leftValue

Gets or sets the horizontal position of the control in the form.

```xpp
public int leftValue([int value])
```

### Parameters - leftValue

value  
An integer value that indicates the horizontal position of the control; optional.

### Return Value - leftValue

The horizontal position of the control in the form.

## Method markAsUserAdd

Marks or unmarks the control as a user-added control.

```xpp
public boolean markAsUserAdd([boolean value])
```

### Parameters - markAsUserAdd

value  
A Boolean value that indicates whether the control should be marked as a user-added control.

### Return Value - markAsUserAdd

true if the control was marked as a user-added control; otherwise, false.

## Method mouseDblClick

Is called when the control is double-clicked by the user.

```xpp
public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseDblClick

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

### Return Value - mouseDblClick

0 (zero) if the event has been handled.

### Remarks - mouseDblClick

Typically, when this method is overridden, the return value from a call to the super method is returned.

## Method mouseDown

Is called when the user clicks the mouse button over the control.

```xpp
public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseDown

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

### Return Value - mouseDown

0 (zero) if the event has been handled.

### Remarks - mouseDown

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

## Method mouseMove

Is called when the user moves the mouse pointer over the control.

```xpp
public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseMove

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

### Return Value - mouseMove

0 (zero) if the event has been handled.

### Remarks - mouseMove

Typically, when this method is overridden, the return value from a call to the super method is returned.

## Method mouseUp

Is called when the user releases the mouse button over the control area.

```xpp
public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseUp

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

### Return Value - mouseUp

0 (zero) if the event has been handled.

### Remarks - mouseUp

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  
The name to assign to the control; optional.

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must begin with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

## Method neededPermission

```xpp
public int neededPermission([int value])
```

### Parameters - neededPermission

value  

### Return Value - neededPermission

## Method SysObsoleteAttribute

```xpp
public container SysObsoleteAttribute()
```

### Return Value - SysObsoleteAttribute

## Method parentControl

Retrieves the parent control for the control.

```xpp
public FormControl parentControl()
```

### Return Value - parentControl

The parent control for the control.

## Method rTLCapable

```xpp
public boolean rTLCapable([boolean value])
```

### Parameters - rTLCapable

value  

### Return Value - rTLCapable

## Method securityKey

Sets or returns the ID of the security key for the control.

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  
The ID of the security key to assign to the control; optional.

### Return Value - securityKey

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

## Method showContextMenu

Shows the shortcut menu for the control.

```xpp
public int showContextMenu(int menuHandle)
```

### Parameters - showContextMenu

menuHandle  
The ID of the menu to show.

### Return Value - showContextMenu

An integer value that indicates whether the call succeeded.

## Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  
The value to assign to the skip property of the control.

### Return Value - skip

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

## Method toolTip

Retrieves the tooltip text for the control.

```xpp
public str toolTip()
```

### Return Value - toolTip

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

### Remarks - toolTip

The method might be overridden to provide a value to the toolTip method.

## Method top

Gets or sets the vertical position of the control in the form.

```xpp
public int top(int value, [int mode])
```

### Parameters - top

value  
An integer value that indicates the vertical arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the vertical arrange mode for the control; optional.

### Return Value - top

The vertical position of the control in the form.

## Method topMode

Sets the vertical arrange mode for the control in the form.

```xpp
public int topMode([int value])
```

### Parameters - topMode

value  
An integer value that indicates the vertical arrange mode for the control; optional.

### Return Value - topMode

The vertical arrange mode for the control in the form.

## Method topValue

Gets or sets the vertical position of the control in the form.

```xpp
public int topValue([int value])
```

### Parameters - topValue

value  
An integer value that indicates the vertical position of the control; optional.

### Return Value - topValue

The vertical position of the control in the form.

## Method type

```xpp
public int type([int value])
```

### Parameters - type

value  

### Return Value - type

## Method SysObsoleteAttribute

```xpp
public boolean SysObsoleteAttribute(container data)
```

### Parameters - SysObsoleteAttribute

data  

### Return Value - SysObsoleteAttribute

## Method userData

Gets or sets the user data for the control.

```xpp
public int userData([int value])
```

### Parameters - userData

value  
An integer value that indicates the user data for the control; optional.

### Return Value - userData

The user data for the control.

## Method userDataItem

Gets or sets the user data item for the control.

```xpp
public int userDataItem([int value])
```

### Parameters - userDataItem

value  
An integer value that indicates the user data item for the control; optional.

### Return Value - userDataItem

The user data item for the control.

## Method userDataItems

Gets or sets the number of user data items for the control.

```xpp
public int userDataItems([int value])
```

### Parameters - userDataItems

value  
An integer value that indicates the number of user data items for the control; optional.

### Return Value - userDataItems

The number of user data items for the control.

## Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

```xpp
public int userDisable([int value])
```

### Parameters - userDisable

value  
The value that indicates whether the control is disabled for the user; optional.

### Return Value - userDisable

1 if the control is disabled for the user; otherwise, 0.

## Method userHeight

Gets or sets the custom user height for the control.

```xpp
public int userHeight([int value])
```

### Parameters - userHeight

value  
The user height for the control; optional.

### Return Value - userHeight

The custom user height for the control.

## Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

```xpp
public int userHide([int value])
```

### Parameters - userHide

value  
The value that indicates whether the control is hidden from the user; optional.

### Return Value - userHide

1 if the control is hidden from the user; otherwise, 0.

### Remarks - userHide

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. Right-clicking invokes a menu that enables the control to be hidden or displayed. This method lets you programmatically determine and set the value.

## Method userOrgContainer

Gets or sets the organization container for the control.

```xpp
public int userOrgContainer([int value])
```

### Parameters - userOrgContainer

value  
The organization container to set for the control; optional.

### Return Value - userOrgContainer

The organization container for the control.

## Method userOrgSibling

Gets or sets the organization sibling for the control.

```xpp
public int userOrgSibling([int value])
```

### Parameters - userOrgSibling

value  
The organization sibling to set for the control; optional.

### Return Value - userOrgSibling

The organization sibling for the control.

## Method userPromptText

Gets or sets the user label text for the control.

```xpp
public str userPromptText([str value])
```

### Parameters - userPromptText

value  
The user label text to set for the control; optional.

### Return Value - userPromptText

The user label text for the control.

## Method userSecurityLevel

Gets or sets the user security level for the control.

```xpp
public int userSecurityLevel([int value])
```

### Parameters - userSecurityLevel

value  
The user security level to set for the control; optional.

### Return Value - userSecurityLevel

The user security level for the control.

## Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls on the form.

```xpp
public int userSkip([int value])
```

### Parameters - userSkip

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

### Return Value - userSkip

1 if the user setting to skip the control is in effect; otherwise, 0.

## Method userWidth

Sets or returns the width of the control in pixels.

```xpp
public int userWidth([int value])
```

### Parameters - userWidth

value  
The number of pixels to use as the width of the control; optional.

### Return Value - userWidth

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

### Remarks - userWidth

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to invoke the setup form in which the character specification is made.

## Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

```xpp
public int verticalSpacing([int value], [AutoMode mode])
```

### Parameters - verticalSpacing

value  
An integer value that indicates the AutoMode for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode for the control; optional.

### Return Value - verticalSpacing

The vertical spacing of the control in the form.

## Method verticalSpacingMode

Sets the vertical spacing mode for the control in the form.

```xpp
public AutoMode verticalSpacingMode([AutoMode mode])
```

### Parameters - verticalSpacingMode

mode  

### Return Value - verticalSpacingMode

The vertical spacing mode for the control in the form.

## Method verticalSpacingValue

Gets or sets the vertical spacing of the control in the form.

```xpp
public int verticalSpacingValue([int value])
```

### Parameters - verticalSpacingValue

value  
An integer value that indicates the vertical spacing of the control; optional.

### Return Value - verticalSpacingValue

The vertical spacing of the control in the form.

## Method visible

Sets or returns a value that indicates whether the control is visible.

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  
The value to assign to the visibility setting for the control; optional.

### Return Value - visible

true if the control is visible; otherwise, false.

## Method width

Gets or sets the width of the control.

```xpp
public int width(int value, [int mode])
```

### Parameters - width

value  
An Integer data type that indicates how the width is calculated; optional.

<!-- -->

mode  
An Integer data type that indicates how the width is calculated; optional.

### Return Value - width

The width of the control in pixels.

### Remarks - width

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

## Method widthMode

Gets or sets the calculation mode of the width of the control.

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  
An Integer data type value that indicates how control width is calculated; optional.

### Return Value - widthMode

An integer value that indicates the current calculation mode.

### Remarks - widthMode

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

## Method widthValue

Gets or sets the width of the control.

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  
An Integer data type that specifies the width in pixels; optional.

### Return Value - widthValue

The width in pixels of the control.

### Remarks - widthValue

To change the width of the control, use the exact width calculation mode.

## Method inputSearch

Performs data filtering for the control, based on the specified string.

```xpp
public void inputSearch(str searchStr)
```

### Parameters - inputSearch

searchStr  
The string value to use to filter data; optional.

## Method copy

Copies the contents of the control to the clipboard.

```xpp
public void copy()
```

## Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

```xpp
public void dragLeave()
```

## Method drop

Raises the drop event to indicate that a drop operation is being performed on the current control.

```xpp
public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - drop

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

## Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

```xpp
public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseEnter

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

## Method registerOverrideMethod

```xpp
public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])
```

### Parameters - registerOverrideMethod

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Method resetUserSetting

Resets the user settings for the control.

```xpp
public void resetUserSetting()
```

## Method context

Shows the shortcut menu for the control.

```xpp
public void context()
```

## Method enter

```xpp
public void enter()
```

## Method OnGotFocus

```xpp
private void OnGotFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnGotFocus

sender  

<!-- -->

e  

## Method displayControl

Displays the control.

```xpp
public void displayControl()
```

## Method updateSize

```xpp
public void updateSize()
```

## Method gotFocus

Indicates that the control has received focus.

```xpp
public void gotFocus()
```

## Method mouseLeave

Is called when the user moves the mouse pointer out of the control area.

```xpp
public void mouseLeave()
```

### Examples - mouseLeave

The following example writes to the information log when the mouse pointer leaves the control.

```xpp
public void mouseLeave() 
{ 
    info (strfmt("The mouse pointer has left the %1 control.", 
                 this.name()) ); 
    super(); 
}
```

## Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

```xpp
public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - dropEx

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

## Method endDrag

Is called when the user has finished dragging a form control.

```xpp
public void endDrag()
```

### Remarks - endDrag

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

## Method cut

Cuts the contents of the control.

```xpp
public void cut()
```

## Method paste

Pastes the contents of the clipboard into the control.

```xpp
public void paste()
```

## Method OnLeaving

```xpp
private void OnLeaving([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLeaving

sender  

<!-- -->

e  

## Method prefColumnSize

Specifies the preferred column width and height for the form control.

```xpp
public void prefColumnSize(int width, int height)
```

### Parameters - prefColumnSize

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

## Method OnLostFocus

```xpp
private void OnLostFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLostFocus

sender  

<!-- -->

e  

## Method OnEnter

```xpp
private void OnEnter([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnEnter

sender  

<!-- -->

e  

## Method setFocus

Sets the focus on the control.

```xpp
public void setFocus()
```

## Method lostFocus

Indicates that the control has lost focus.

```xpp
public void lostFocus()
```

