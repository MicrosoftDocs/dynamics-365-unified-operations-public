---
title: FormTreeControl class
description: This topic describes the FormTreeControl class.
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

# Class FormTreeControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormTreeControl extends FormControl
```

## Remarks

## Examples

## Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int add(int parent, int insertAfter, str Text, \[int image\], \[int children\])                      |                                                                                                                                                                         |
| public int addItem(int parent, int insertAfter, FormTreeItem item)                                          |                                                                                                                                                                         |
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can modify the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determines whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form tree control.                                                                                                             |
| public boolean beginLabelEdit(int Idx, str text, AnyType data)                                              |                                                                                                                                                                         |
| public int bold(\[int value\])                                                                              | Gets or sets the font weight that is used to display text in the control.                                                                                               |
| public int border(\[int value\])                                                                            | Gets or sets the style of the border for the control.                                                                                                                   |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public boolean canScroll(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean cascadeSelect(\[boolean value\])                                                             |                                                                                                                                                                         |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public boolean checkBox(\[boolean value\])                                                                  |                                                                                                                                                                         |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Returns a list that contains the IDs of configuration keys that are in effect for the control.                                                                          |
| public int copyItem(int Idx, int newParent, \[int insertAfter\])                                            |                                                                                                                                                                         |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public Imagelist createDragImagelist()                                                                      |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public boolean delete(int Idx)                                                                              | Deletes the specified item from the form tree control.                                                                                                                  |
| public boolean deleteAll()                                                                                  | Deletes all items from the form tree control.                                                                                                                           |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether drag-and-drop operations are enabled or disabled for the control.                                                                                    |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Returns the text that is displayed when the form tree control is dragged.                                                                                               |
| public boolean editLabels(\[boolean value\])                                                                |                                                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether the object is enabled or disabled.                                                                                                                   |
| public int expand(int Idx, \[FormTreeExpand action\])                                                       |                                                                                                                                                                         |
| public boolean expanding(int Idx, FormTreeExpand action, AnyType data)                                      |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font that is used for the text in the control.                                                                                             |
| public int fontSize(\[int value\])                                                                          | Gets or sets the font size that is used for the text in the control.                                                                                                    |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the color that is used for the text in the control.                                                                                                        |
| public int getChild(int Idx)                                                                                |                                                                                                                                                                         |
| public int getFirstSelected()                                                                               |                                                                                                                                                                         |
| public int getFirstVisible()                                                                                |                                                                                                                                                                         |
| public Imagelist getImagelist()                                                                             |                                                                                                                                                                         |
| public FormTreeItem getItem(int Idx)                                                                        |                                                                                                                                                                         |
| public int getNextSelected(int idx)                                                                         |                                                                                                                                                                         |
| public int getNextSibling(int Idx)                                                                          |                                                                                                                                                                         |
| public int getNextVisible(int Idx)                                                                          |                                                                                                                                                                         |
| public int getParent(int Idx)                                                                               |                                                                                                                                                                         |
| public int getPrevSelected(int idx)                                                                         |                                                                                                                                                                         |
| public int getPrevSibling(int Idx)                                                                          |                                                                                                                                                                         |
| public int getPrevVisible(int Idx)                                                                          |                                                                                                                                                                         |
| public int getRoot()                                                                                        |                                                                                                                                                                         |
| public int getSelectedCount()                                                                               |                                                                                                                                                                         |
| public int getSelection()                                                                                   |                                                                                                                                                                         |
| public Imagelist getStateImagelist()                                                                        |                                                                                                                                                                         |
| public int getVisibleCount()                                                                                | Returns the number of visible items in the tree control.                                                                                                                |
| public boolean hasButtons(\[boolean value\])                                                                | Returns a value that indicates whether the tree control uses expand/collapse buttons.                                                                                   |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the tree control have changed.                                                                           |
| public boolean hasLines(\[boolean value\])                                                                  | Returns a value that indicates whether the tree control displays tree connector lines.                                                                                  |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Returns the Help text for the control.                                                                                                                                  |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.                                                         |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public container hitTest(int x, int y)                                                                      |                                                                                                                                                                         |
| public int hWnd()                                                                                           | Returns the Windows handle for the control.                                                                                                                             |
| public boolean isContainer()                                                                                | Returns a value that indicates whether the control is a container.                                                                                                      |
| public boolean isDisplayed()                                                                                | Returns a value that indicates whether the control is displayed.                                                                                                        |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                   |
| public boolean italic(\[boolean value\])                                                                    | Sets or returns a value that indicates whether the text in the control is italic.                                                                                       |
| public boolean keyDown(int vKey, boolean Ctrl, boolean Shift)                                               |                                                                                                                                                                         |
| public boolean leave()                                                                                      |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean linesAtRoot(\[boolean value\])                                                               |                                                                                                                                                                         |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks while the mouse pointer is over the control.                                                                                             |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button while the mouse pointer is over the control.                                                                          |
| public int moveItem(int Idx, int newParent, \[int insertAfter\])                                            |                                                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.                               |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public boolean rowSelect(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int select(int Idx)                                                                                  |                                                                                                                                                                         |
| public int selectEx(int Idx, boolean setSelection)                                                          |                                                                                                                                                                         |
| public boolean selectionChanging(FormTreeItem OldItem, FormTreeItem NewItem, FormTreeSelect how)            |                                                                                                                                                                         |
| public int selectItems(int fromIdx, int toIdx)                                                              |                                                                                                                                                                         |
| public int selectSetFirstVisible(int Idx)                                                                   |                                                                                                                                                                         |
| public boolean setInsertMark(int Idx, boolean After)                                                        |                                                                                                                                                                         |
| public boolean setItem(FormTreeItem item)                                                                   |                                                                                                                                                                         |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showSelAlways(\[boolean value\])                                                             |                                                                                                                                                                         |
| public boolean singleSelection(\[boolean value\])                                                           |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public str toolTip()                                                                                        | Returns the tooltip text for the control.                                                                                                                               |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public boolean trackSelect(\[boolean value\])                                                               |                                                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Returns or sets the value that indicates whether the form tree control is hidden from the user.                                                                         |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Sets or retrieves the user prompt text for the control.                                                                                                                 |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode for the width of the control.                                                                                                         |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void checkedStateChanged(int Idx, FormTreeCheckedState newState)                                     |                                                                                                                                                                         |
| public void endLabelEdit(int Idx, str text, AnyType data)                                                   |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control.                                                                                                       |
| private void OnExpanding(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void paste()                                                                                         | Pastes the form tree control in the form.                                                                                                                               |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void itemMoved(int OldIdx, int NewIdx)                                                               |                                                                                                                                                                         |
| public void expanded(int Idx, FormTreeExpand action, AnyType data)                                          |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| private void OnSelectionChanged(\[FormControl sender\], \[FormControlEventArgs e\])                         |                                                                                                                                                                         |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void mouseLeave()                                                                                    | Is called when the user moves the mouse pointer out of the control.                                                                                                     |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form tree control.                                                                                                      |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void itemCopy(int OldIdx, int NewIdx)                                                                |                                                                                                                                                                         |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form tree control.                                                                                              |
| public void setImagelist(Imagelist imageList)                                                               |                                                                                                                                                                         |
| private void OnExpanded(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void itemDeleted(int Idx, AnyType data)                                                              |                                                                                                                                                                         |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void setStateImagelist(Imagelist imageList)                                                          |                                                                                                                                                                         |
| public void endEditLabel(boolean cancel)                                                                    |                                                                                                                                                                         |
| public void copy()                                                                                          | Copies the form tree control.                                                                                                                                           |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void selectionChanged(FormTreeItem OldItem, FormTreeItem NewItem, FormTreeSelect how)                | Indicates that the user has changed the selected item in the form tree control.                                                                                         |
| public void beginEditLabel(int Idx)                                                                         |                                                                                                                                                                         |

## Method add

```xpp
public int add(int parent, int insertAfter, str Text, [int image], [int children])
```

### Parameters - add

parent  

<!-- -->

insertAfter  

<!-- -->

Text  

<!-- -->

image  

<!-- -->

children  

### Return Value - add

## Method addItem

```xpp
public int addItem(int parent, int insertAfter, FormTreeItem item)
```

### Parameters - addItem

parent  

<!-- -->

insertAfter  

<!-- -->

item  

### Return Value - addItem

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

Determines whether the user can modify the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  
The value to assign to the allowEdit property.

### Return Value - allowEdit

true if the control can be modified; otherwise, false.

### Remarks - allowEdit

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Examples - allowEdit

The following example shows how to return and set the value of the allowEdit property.

```xpp
// Return the value. 
info (strfmt("allowEdit: %1", this.allowEdit())); 
// Set the value. 
this.allowEdit(false);
```

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
The value to assign to the autoDeclaration property.

### Return Value - autoDeclaration

true if the member variable can be declared for this control; otherwise, false.

### Remarks - autoDeclaration

Controls cannot have identical names.

## Method backgroundColor

Gets or sets the background color of the control.

```xpp
public int backgroundColor([int value])
```

### Parameters - backgroundColor

value  
The value to assign as the background color of the control.

### Return Value - backgroundColor

An integer that contains a packed RGB color.

### Remarks - backgroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

### Examples - backgroundColor

The following example shows how to return and set the background color for a control.

```xpp
// Retrieve the existing background color. 
info (strfmt("Background color: %1", this.backgroundColor())); 
// Set the background color. 
this.backgroundColor(WindowsPalette::DarkShadow3D);
```

## Method backStyle

Determines whether the control background can be transparent.

```xpp
public int backStyle([int value])
```

### Parameters - backStyle

value  
The value to assign as the background style of the control.

### Return Value - backStyle

1 if the control background can be transparent; otherwise, 0.

### Examples - backStyle

The following example shows how to return and set the background style.

```xpp
// Return the background style. 
info (strfmt("Background style: %1", this.backStyle())); 
// Set the background style. 
this.backStyle(FormBackStyle::Transparent);
```

## Method beginDrag

Is called when the user starts to drag a form tree control.

```xpp
public int beginDrag(int x, int y)
```

### Parameters - beginDrag

x  
An Integer data type that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An Integer data type that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

### Return Value - beginDrag

0 (zero) if the event has been handled.

### Remarks - beginDrag

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, the user presses the mouse button in the control area and then moves the mouse pointer.

### Examples - beginDrag

The following example displays the x-coordinates and y-coordinates in the Infolog when the user starts to drag the form tree control.

```xpp
public int beginDrag(int _x, int _y) 
{ 
    int ret; 
    info(strfmt("beginDrag (x, y) : (%1, %2)", _x, _y)); 
    ret = super(_x, _y); 
    return ret; 
}
```

## Method beginLabelEdit

```xpp
public boolean beginLabelEdit(int Idx, str text, AnyType data)
```

### Parameters - beginLabelEdit

Idx  

<!-- -->

text  

<!-- -->

data  

### Return Value - beginLabelEdit

## Method bold

Gets or sets the font weight that is used to display text in the control.

```xpp
public int bold([int value])
```

### Parameters - bold

value  
The value to assign to the bold setting for the control.

### Return Value - bold

An integer value between 0 (zero) and 9, inclusive.

### Remarks - bold

The integer that is returned contains the weight of the font as follows:

-   0 � Use the default font weight.
-   1 � Thin.
-   2 � Extra-light.
-   3 � Light.
-   4 � Normal.
-   5 � Medium.
-   6 � Semibold.
-   7 � Bold.
-   8 � Extra-bold.
-   9 � Heavy.

## Method border

Gets or sets the style of the border for the control.

```xpp
public int border([int value])
```

### Parameters - border

value  
The value to assign as the border style for the control; optional.

### Return Value - border

An integer between 0 (zero) and 4, inclusive.

### Remarks - border

The integer that is returned contains the style of the border for the control as follows.

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

### Examples - border

The following example shows how to retrieve and set the border style for a control.

```xpp
// Retrieve the border style. 
info (strfmt("border: %1", this.border())); 
// Set the border style. 
this.border(2);
```

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

The container that holds the width and height.

## Method canScroll

```xpp
public boolean canScroll([boolean value])
```

### Parameters - canScroll

value  

### Return Value - canScroll

## Method cascadeSelect

```xpp
public boolean cascadeSelect([boolean value])
```

### Parameters - cascadeSelect

value  

### Return Value - cascadeSelect

## Method characterSet

Gets or sets the character set of the font.

```xpp
public int characterSet([int value])
```

### Parameters - characterSet

value  

### Return Value - characterSet

An integer value that indicates the character set of the font.

### Remarks - characterSet

The values for the integer that is returned indicate the character set according to the following table.

| Value | Description          |
|-------|----------------------|
| 0     | ANSI\_CHARSET        |
| 1     | DEFAULT\_CHARSET     |
| 2     | SYMBOL\_CHARSET      |
| 77    | MAC\_CHARSET         |
| 128   | SHIFTJIS\_CHARSET    |
| 129   | HANGUL\_CHARSET      |
| 134   | GB2312\_CHARSET      |
| 136   | CHINESEBIG5\_CHARSET |
| 161   | GREEK\_CHARSET       |
| 162   | TURKISH\_CHARSET     |
| 163   | VIETNAMESE\_CHARSET  |
| 186   | BALTIC\_CHARSET      |
| 204   | RUSSIAN\_CHARSET     |
| 238   | EASTEUROPE\_CHARSET  |
| 255   | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of Microsoft Windows.

| Value | Description    |
|-------|----------------|
| 130   | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value | Description     |
|-------|-----------------|
| 177   | HEBREW\_CHARSET |
| 178   | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value | Description   |
|-------|---------------|
| 222   | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the [MSDN website](https://go.microsoft.com/fwlink/?LinkID=85972).

## Method checkBox

```xpp
public boolean checkBox([boolean value])
```

### Parameters - checkBox

value  

### Return Value - checkBox

## Method colorScheme

Gets or sets the color scheme of the control.

```xpp
public int colorScheme([int value])
```

### Parameters - colorScheme

value  

### Return Value - colorScheme

An integer between zero and two, inclusive.

### Remarks - colorScheme

The color scheme is defined according to the following table.

| Value | Style                 |
|-------|-----------------------|
| 0     | Default               |
| 1     | The Windows palette   |
| 2     | The true-color scheme |

## Method configurationKey

Gets or sets the configuration key that is assigned to the control.

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  
The ID of the configuration key to assign to the control.

### Return Value - configurationKey

The ID of the configuration key that is assigned to the control.

### Remarks - configurationKey

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Examples - configurationKey

The following example shows how to set and retrieve the configuration key for a control.

```xpp
DictConfigurationKey dck; 
configurationKeyId cki; 
// objCtrl previously assigned. 
// Assign a configuration key to the control. 
objCtrl.configurationKey(configurationkeynum(BankDeposit)); 
// Retrieve the configuration key ID from the control. 
cki = objCtrl.configurationKey(); 
if (cki != 0) 
{ 
    dck = new DictConfigurationKey(cki); 
    if (dck) 
    { 
    print strfmt("Configuration Key ID: %1 Configuration Key Name: %2", 
                  cki, 
                  dck.name()); 
    } 
}
```

## Method configurationKeyEx

Returns a list that contains the IDs of configuration keys that are in effect for the control.

```xpp
public List configurationKeyEx()
```

### Return Value - configurationKeyEx

A list that contains the IDs of configuration keys that are in effect for the control.

### Remarks - configurationKeyEx

If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. The returned list also contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods. The list does not contain duplicate IDs.

### Examples - configurationKeyEx

The following example shows how to retrieve the configuration key IDs for a control.

```xpp
DictConfigurationKey dck; 
configurationKeyId cki; 
List list; 
ListEnumerator enum;
// objCtrl previously assigned. 
list = objCtrl.configurationKeyEx(); 
if (0 != list.elements()) 
{ 
    enum = list.getEnumerator(); 
    while (enum.moveNext()) 
    { 
       dck = new DictConfigurationKey(enum.current()); 
       if (dck) 
       { 
        print strfmt("Configuration Key ID: %1 Configuration Key Name: %2", 
                     enum.current(), 
                     dck.name() ); 
       } 
    } 
}
```

## Method copyItem

```xpp
public int copyItem(int Idx, int newParent, [int insertAfter])
```

### Parameters - copyItem

Idx  

<!-- -->

newParent  

<!-- -->

insertAfter  

### Return Value - copyItem

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

## Method createDragImagelist

```xpp
public Imagelist createDragImagelist()
```

### Return Value - createDragImagelist

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

## Method delete

Deletes the specified item from the form tree control.

```xpp
public boolean delete(int Idx)
```

### Parameters - delete

Idx  
An integer that specifies the zero-based index of the item to delete.

### Return Value - delete

true if the item was successfully deleted; otherwise, false.

### Examples - delete

The following example shows how to delete the first item in the form tree control.

```xpp
// The ftc variable was a previously allocated  
// FormTreeControl variable. 
boolean bDelete; 
bDelete = ftc.delete(0);
```

## Method deleteAll

Deletes all items from the form tree control.

```xpp
public boolean deleteAll()
```

### Return Value - deleteAll

true if all items were successfully deleted; otherwise, false.

### Examples - deleteAll

The following example shows how to delete all items from a form tree control.

```xpp
// The ftc variable was a previously allocated 
// FormTreeControl variable. 
boolean bDelete; 
bDelete = ftc.deleteAll();
```

## Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both.

```xpp
public int displayTarget([int value])
```

### Parameters - displayTarget

value  
The integer value that indicates where the control is displayed; optional.

### Return Value - displayTarget

The value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both.

## Method dragDrop

Determines whether drag-and-drop operations are enabled or disabled for the control.

```xpp
public int dragDrop([int value])
```

### Parameters - dragDrop

value  
An Integer data type that indicates whether drag-and-drop behavior is enabled.

### Return Value - dragDrop

1 if drag-and-drop operations are enabled; otherwise, false.

### Examples - dragDrop

The following example shows how to return or set the value that indicates whether drag-and-drop behavior is enabled.

```xpp
boolean dDragDrop; 
// The ctrl variable was previously assigned  
// as a FormTreeControl value. 
// Retrieve the drag�and�drop-enabled value. 
dDragDrop = ctrl.dragDrop(); 
// Set the drag�and�drop-enabled value. 
ctrl.dragDrop(true);
```

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

Returns the text that is displayed when the form tree control is dragged.

```xpp
public str dragText()
```

### Return Value - dragText

The text that is displayed when the tree control is dragged; an empty string if there is no text to display when the tree control is dragged.

## Method editLabels

```xpp
public boolean editLabels([boolean value])
```

### Parameters - editLabels

value  

### Return Value - editLabels

## Method enabled

Determines whether the object is enabled or disabled.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  
A Boolean value that specifies whether the control is enabled.

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property lets you enable or disable controls at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message that provides read-only information.

### Examples - enabled

The following example shows how to return and set the enabled property for a control.

```xpp
// Return the value of the enabled property. 
info(strfmt("enabled: %1",this.enabled())); 
// Set the enabled property. 
this.enabled(false);
```

## Method expand

```xpp
public int expand(int Idx, [FormTreeExpand action])
```

### Parameters - expand

Idx  

<!-- -->

action  

### Return Value - expand

## Method expanding

```xpp
public boolean expanding(int Idx, FormTreeExpand action, AnyType data)
```

### Parameters - expanding

Idx  

<!-- -->

action  

<!-- -->

data  

### Return Value - expanding

## Method font

Gets or sets the name of the font that is used for the text in the control.

```xpp
public str font([str value])
```

### Parameters - font

value  
A string value that indicates the font to use for the text in a form tree control.

### Return Value - font

The name of the font to use, such as Tahoma or Verdana.

### Examples - font

The following example shows how to return and set the font for a form tree control.

```xpp
str strFont; 
// The ctrl variable was previously assigned  
// as a form tree control variable. 
// Retrieve the font. 
strFont = ctrl.font(); 
// Set the font. 
ctrl.font("Times New Roman");
```

## Method fontSize

Gets or sets the font size that is used for the text in the control.

```xpp
public int fontSize([int value])
```

### Parameters - fontSize

value  
An Integer data type that indicates the font size, in points, for the text in a form tree control.

### Return Value - fontSize

The height of the font in points.

### Examples - fontSize

The following example shows how to return and set the font size for a control.

```xpp
int nSize; 
// The ctrl variable was previously assigned  
// as a form tree control. 
// Retrieve the font size. 
nSize = ctrl.fontSize(); 
// Set the font size. 
ctrl.fontSize(16);
```

## Method foregroundColor

Gets or sets the color that is used for the text in the control.

```xpp
public int foregroundColor([int value])
```

### Parameters - foregroundColor

value  

### Return Value - foregroundColor

An integer that contains a packed RGB color.

### Remarks - foregroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

## Method getChild

```xpp
public int getChild(int Idx)
```

### Parameters - getChild

Idx  

### Return Value - getChild

## Method getFirstSelected

```xpp
public int getFirstSelected()
```

### Return Value - getFirstSelected

## Method getFirstVisible

```xpp
public int getFirstVisible()
```

### Return Value - getFirstVisible

## Method getImagelist

```xpp
public Imagelist getImagelist()
```

### Return Value - getImagelist

## Method getItem

```xpp
public FormTreeItem getItem(int Idx)
```

### Parameters - getItem

Idx  

### Return Value - getItem

## Method getNextSelected

```xpp
public int getNextSelected(int idx)
```

### Parameters - getNextSelected

idx  

### Return Value - getNextSelected

## Method getNextSibling

```xpp
public int getNextSibling(int Idx)
```

### Parameters - getNextSibling

Idx  

### Return Value - getNextSibling

## Method getNextVisible

```xpp
public int getNextVisible(int Idx)
```

### Parameters - getNextVisible

Idx  

### Return Value - getNextVisible

## Method getParent

```xpp
public int getParent(int Idx)
```

### Parameters - getParent

Idx  

### Return Value - getParent

## Method getPrevSelected

```xpp
public int getPrevSelected(int idx)
```

### Parameters - getPrevSelected

idx  

### Return Value - getPrevSelected

## Method getPrevSibling

```xpp
public int getPrevSibling(int Idx)
```

### Parameters - getPrevSibling

Idx  

### Return Value - getPrevSibling

## Method getPrevVisible

```xpp
public int getPrevVisible(int Idx)
```

### Parameters - getPrevVisible

Idx  

### Return Value - getPrevVisible

## Method getRoot

```xpp
public int getRoot()
```

### Return Value - getRoot

## Method getSelectedCount

```xpp
public int getSelectedCount()
```

### Return Value - getSelectedCount

## Method getSelection

```xpp
public int getSelection()
```

### Return Value - getSelection

## Method getStateImagelist

```xpp
public Imagelist getStateImagelist()
```

### Return Value - getStateImagelist

## Method getVisibleCount

Returns the number of visible items in the tree control.

```xpp
public int getVisibleCount()
```

### Return Value - getVisibleCount

The number of visible items in the tree control.

### Examples - getVisibleCount

The following example shows how to retrieve the number of visible items in the tree control.

```xpp
int nCount; 
nCount = this.getVisibleCount(); 
info (strfmt("getVisibleCount: %1", int2str(nCount)));
```

## Method hasButtons

Returns a value that indicates whether the tree control uses expand/collapse buttons.

```xpp
public boolean hasButtons([boolean value])
```

### Parameters - hasButtons

value  

### Return Value - hasButtons

true if the tree control uses expand/collapse buttons; otherwise, false.

### Examples - hasButtons

The following example shows how to retrieve the value that indicates whether the tree control uses expand/collapse buttons.

```xpp
boolean bHasButtons; 
// Retrieve the value. 
bHasButtons = this.hasButtons(); 
info (strfmt("hasButtons: %1",bHasButtons)); 
// Set the value. 
this.hasButtons(false);
```

## Method hasChanged

Sets or returns a value that indicates whether the contents of the tree control have changed.

```xpp
public boolean hasChanged([boolean val])
```

### Parameters - hasChanged

val  
The value to assign as the hasChanged value for the tree control.

### Return Value - hasChanged

true if the contents of the tree control have changed; otherwise, false.

### Examples - hasChanged

The following example shows how to return and set the value that indicates whether the contents of the tree control have changed.

```xpp
boolean bHasChanged; 
// The ctrl variable was previously assigned 
// as a FormTreeControl variable. 
// Retrieve the hasChanged value. 
bHasChanged = ctrl.hasChanged(); 
// Modify the hasChanged value. 
ctrl.hasChanged(true);
```

## Method hasLines

Returns a value that indicates whether the tree control displays tree connector lines.

```xpp
public boolean hasLines([boolean value])
```

### Parameters - hasLines

value  

### Return Value - hasLines

true if the tree control displays tree connector lines; otherwise, false.

### Examples - hasLines

The following example shows how to retrieve the value that indicates whether the tree control displays tree connector lines.

```xpp
boolean bHasLines; 
// Retrieve the value. 
bHasLines = this.hasLines(); 
info (strfmt("hasLines: %1", bHasLines)); 
// Set the value. 
this.hasLines(false);
```

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
An Integer data type that indicates how the height is calculated; optional. This can be one of the following values:

<!-- -->

mode  
An Integer data type that indicates how the height is calculated; optional. This can be one of the following values:

### Return Value - height

The height of the control in pixels.

### Remarks - height

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

| Mode              | Height calculation                                                                         |
|-------------------|--------------------------------------------------------------------------------------------|
| -1 � Exact        | The exact height of the control in pixels is used.                                         |
| 0 � Auto          | The height of the control is calculated automatically, and the value parameter is ignored. |
| 1 � Column height | The layout of the form determines the height of the control.                               |

The height and the height calculation mode can be set separately.

## Method heightMode

Gets or sets a calculation mode for the height of the control.

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  
An Integer data type value that indicates how the height of the control is calculated. This value can be -1 for Exact mode, 0 for Auto mode, or 1 for Column height mode.

### Return Value - heightMode

The height calculation mode.

### Remarks - heightMode

Calculate the height according to the following table.

| Mode          | Height calculation                                                                         |
|---------------|--------------------------------------------------------------------------------------------|
| Exact         | The exact height of the control in pixels is used.                                         |
| Auto          | The height of the control is calculated automatically, and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                               |

The height of the control might change when the calculation mode is set to Auto or Column height.

### Examples - heightMode

The following example shows how to return and set the height calculation mode for a form tree control.

```xpp
int nHeightMode; 
; 
// The ctrl variable was previously assigned 
// as a form tree control variable. 
// Retrieve the height mode. 
nHeightMode = ctrl.HeightMode(); 
// Set the height mode. 
ctrl.heightMode(-1); 
// Set the height. 
ctrl.heightValue(160);
```

## Method heightValue

Gets or sets the height of the control.

```xpp
public int heightValue([int value])
```

### Parameters - heightValue

value  
An Integer data type that specifies the height in pixels.

### Return Value - heightValue

The height in pixels.

### Remarks - heightValue

The height of the control is not changed unless the Exact height calculation mode is used.

### Examples - heightValue

The following example shows how to return and set the height value of a form tree control.

```xpp
int nHeightValue; 
// The ctrl variable was previously assigned 
// as a form tree control variable. 
// Retrieve the height value. 
nHeightValue = ctrl.heightValue(); 
// Set the height value. 
ctrl.heightMode(-1); 
ctrl.heightValue(160);
```

## Method helpField

Returns the Help text for the control.

```xpp
public str helpField()
```

### Return Value - helpField

The Help text for the control; an empty string if there is no Help text for the control.

### Remarks - helpField

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

### Examples - helpField

The following example shows how to use the helpField method.

```xpp
str strHelp; 
strHelp = this.helpField();
```

## Method helpText

Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  
The value to assign as the Help text for the control.

### Return Value - helpText

The string that is displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Examples - helpText

The following example shows how to set and return the Help text for a control.

```xpp
// objCtrl previously assigned to a control 
// Retrieve existing Help text. 
print objCtrl.helpText(); 
// Specify new Help text. 
objCtrl.helpText("My new Help text");
```

## Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

```xpp
public str hierarchyParent([str value])
```

### Parameters - hierarchyParent

value  
The value to assign to the HierarchyParent property of the control.

### Return Value - hierarchyParent

The HierarchyParent property value of the control.

## Method hitTest

```xpp
public container hitTest(int x, int y)
```

### Parameters - hitTest

x  

<!-- -->

y  

### Return Value - hitTest

## Method hWnd

Returns the Windows handle for the control.

```xpp
public int hWnd()
```

### Return Value - hWnd

The handle for the control.

### Remarks - hWnd

The handle can be used with the Windows API.

### Examples - hWnd

The following example shows how to retrieve the Windows handle for a control.

```xpp
int h; 
h = this.hWnd(); 
info (strfmt("hWnd: %1", h));
```

## Method isContainer

Returns a value that indicates whether the control is a container.

```xpp
public boolean isContainer()
```

### Return Value - isContainer

true if the control is a container; otherwise false.

### Examples - isContainer

The following example shows how to determine whether a control is a container.

```xpp
info(strfmt("IsContainer: %1", this.isContainer()));
```

## Method isDisplayed

Returns a value that indicates whether the control is displayed.

```xpp
public boolean isDisplayed()
```

### Return Value - isDisplayed

true if the control is displayed; otherwise, false.

### Remarks - isDisplayed

To modify the visible state of the control, call the visible method.

### Examples - isDisplayed

The following example shows how to determine whether a control is visible.

```xpp
info(strfmt("isDisplayed: %1", this.isDisplayed()));
```

## Method isRestricted

Retrieves a value that indicates whether the control is restricted.

```xpp
public boolean isRestricted()
```

### Return Value - isRestricted

true if the control is restricted; otherwise, false.

## Method isUserSetupEnabled

Retrieves a value that indicates whether the control allows for the specified level of customization.

```xpp
public boolean isUserSetupEnabled(int neededSetupRights)
```

### Parameters - isUserSetupEnabled

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control.

### Return Value - isUserSetupEnabled

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false. For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

### Remarks - isUserSetupEnabled

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

### Examples - isUserSetupEnabled

The following example shows how to determine the user setup rights for a control.

```xpp
FormAllowUserSetup formAllowUserSetup = FormAllowUserSetup::No; 
switch (true) 
{ 
    case this.isUserSetupEnabled(FormAllowUserSetup::Yes): 
        formAllowUserSetup = FormAllowUserSetup::Yes; 
        break; 
    case this.isUserSetupEnabled(FormAllowUserSetup::Restricted): 
        formAllowUserSetup = FormAllowUserSetup::Restricted; 
        break; 
    case this.isUserSetupEnabled(FormAllowUserSetup::No): 
       formAllowUserSetup = FormAllowUserSetup::No; 
        break; 
} 
info (strfmt("formAllowUserSetup: %1", formAllowUserSetup));
```

## Method italic

Sets or returns a value that indicates whether the text in the control is italic.

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  
The value to assign to the italic setting for the control.

### Return Value - italic

true if the text in the control is italic; otherwise, false.

## Method keyDown

```xpp
public boolean keyDown(int vKey, boolean Ctrl, boolean Shift)
```

### Parameters - keyDown

vKey  

<!-- -->

Ctrl  

<!-- -->

Shift  

### Return Value - keyDown

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

## Method linesAtRoot

```xpp
public boolean linesAtRoot([boolean value])
```

### Parameters - linesAtRoot

value  

### Return Value - linesAtRoot

## Method markAsUserAdd

Marks or unmarks the control as a user-added control.

```xpp
public boolean markAsUserAdd([boolean value])
```

### Parameters - markAsUserAdd

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

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

### Examples - mouseDblClick

The following example shows how to display the parameters of a mouseDblClick event in the Infolog.

```xpp
public int mouseDblClick(int x,  
                         int y,  
                         int button, 
                         boolean Ctrl, 
                         boolean Shift) 
{ 
    int ret; 
    if (Shift) 
    { 
        info( "Shift set" ); 
    } 
    if (Ctrl) 
    { 
        info( "Ctrl set"); 
    } 
    info (strfmt("x, y: %1 %2 button: %3", x, y, button)); 
    ret = super(x, y, button, Ctrl, Shift); 
    info (strfmt("ret: %1", ret)); 
    return ret; 
}
```

## Method mouseDown

Is called when the user clicks while the mouse pointer is over the control.

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

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Examples - mouseDown

The following example shows how to display the parameters of a mouseDown event in the Infolog.

```xpp
public int mouseDown(int x,  
                              int y,  
                              int button, 
                              boolean Ctrl, 
                              boolean Shift) 
{ 
    int ret; 
    if (Shift) 
    { 
        info( "Shift set" ); 
    } 
    if (Ctrl) 
    { 
        info( "Ctrl set"); 
    } 
    info (strfmt("x, y: %1 %2 button: %3", x, y, button)); 
    ret = super(x, y, button, Ctrl, Shift); 
    info (strfmt("ret: %1", ret)); 
    return ret; 
}
```

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

### Examples - mouseMove

The following example shows how to display the parameters of a mouseMove event in the Infolog.

```xpp
public int mouseMove(int x,  
                     int y,  
                     int button, 
                     boolean Ctrl, 
                     boolean Shift) 
{ 
    int ret; 
    if (Shift) 
    { 
        info( "Shift set" ); 
    } 
    if (Ctrl) 
    { 
        info( "Ctrl set"); 
    } 
    info (strfmt("x, y: %1 %2 button: %3", x, y, button)); 
    ret = super(x, y, button, Ctrl, Shift); 
    info (strfmt("ret: %1", ret)); 
    return ret; 
}
```

## Method mouseUp

Is called when the user releases the mouse button while the mouse pointer is over the control.

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

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Examples - mouseUp

The following example shows how to display the parameters of a mouseUp event in the Infolog.

```xpp
public int mouseUp(int x,  
                   int y,  
                   int button, 
                   boolean Ctrl, 
                   boolean Shift) 
{ 
    int ret; 
    if (Shift) 
    { 
        info( "Shift set" ); 
    } 
    if (Ctrl) 
    { 
        info( "Ctrl set"); 
    } 
    info (strfmt("x, y: %1 %2 button: %3", x, y, button)); 
    ret = super(x, y, button, Ctrl, Shift); 
    info (strfmt("ret: %1", ret)); 
    return ret; 
}
```

## Method moveItem

```xpp
public int moveItem(int Idx, int newParent, [int insertAfter])
```

### Parameters - moveItem

Idx  

<!-- -->

newParent  

<!-- -->

insertAfter  

### Return Value - moveItem

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  
The name to assign to the control.

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, classes, and so on.

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

## Method rowSelect

```xpp
public boolean rowSelect([boolean value])
```

### Parameters - rowSelect

value  

### Return Value - rowSelect

## Method securityKey

Sets or returns the ID of the security key for the control.

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  
The ID of the security key to assign to the control.

### Return Value - securityKey

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

### Examples - securityKey

The following example shows how to retrieve and assign a security key ID for a control.

```xpp
DictSecurityKey dsk; 
securityKeyId ski; 
// objCtrl previously assigned. 
// Assign a security key ID to the control. 
objCtrl.securityKey(securitykeynum(AdminDaily)); 
// Retrieve the security key ID from the control. 
ski = objCtrl.securityKey(); 
if (ski != 0) 
{ 
    dsk = new DictSecurityKey(ski); 
    if (dsk) 
    { 
        print strfmt("Security Key ID: %1 Security Key Name: %2", 
                     ski, 
                     dsk.name()); 
    } 
}
```

## Method select

```xpp
public int select(int Idx)
```

### Parameters - select

Idx  

### Return Value - select

## Method selectEx

```xpp
public int selectEx(int Idx, boolean setSelection)
```

### Parameters - selectEx

Idx  

<!-- -->

setSelection  

### Return Value - selectEx

## Method selectionChanging

```xpp
public boolean selectionChanging(FormTreeItem OldItem, FormTreeItem NewItem, FormTreeSelect how)
```

### Parameters - selectionChanging

OldItem  

<!-- -->

NewItem  

<!-- -->

how  

### Return Value - selectionChanging

## Method selectItems

```xpp
public int selectItems(int fromIdx, int toIdx)
```

### Parameters - selectItems

fromIdx  

<!-- -->

toIdx  

### Return Value - selectItems

## Method selectSetFirstVisible

```xpp
public int selectSetFirstVisible(int Idx)
```

### Parameters - selectSetFirstVisible

Idx  

### Return Value - selectSetFirstVisible

## Method setInsertMark

```xpp
public boolean setInsertMark(int Idx, boolean After)
```

### Parameters - setInsertMark

Idx  

<!-- -->

After  

### Return Value - setInsertMark

## Method setItem

```xpp
public boolean setItem(FormTreeItem item)
```

### Parameters - setItem

item  

### Return Value - setItem

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

## Method showSelAlways

```xpp
public boolean showSelAlways([boolean value])
```

### Parameters - showSelAlways

value  

### Return Value - showSelAlways

## Method singleSelection

```xpp
public boolean singleSelection([boolean value])
```

### Parameters - singleSelection

value  

### Return Value - singleSelection

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

### Remarks - skip

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control.

### Examples - skip

The following shows how to return and set the skip property of a control.

```xpp
// Return the value of the skip property. 
info(strfmt("skip: %1", this.skip())); 
// Set the value of the skip property. 
this.skip(true);
```

## Method toolTip

Returns the tooltip text for the control.

```xpp
public str toolTip()
```

### Return Value - toolTip

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

### Remarks - toolTip

The method can be overridden to provide a value to the toolTip method.

### Examples - toolTip

The following example shows how to override the toolTip method.

```xpp
str toolTip() 
{ 
    return "Account numbers of customers eligible for discount"; 
}
```

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

## Method trackSelect

```xpp
public boolean trackSelect([boolean value])
```

### Parameters - trackSelect

value  

### Return Value - trackSelect

## Method type

```xpp
public int type([int value])
```

### Parameters - type

value  

### Return Value - type

## Method underline

```xpp
public boolean underline([boolean value])
```

### Parameters - underline

value  

### Return Value - underline

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

Returns or sets the value that indicates whether the form tree control is hidden from the user.

```xpp
public int userHide([int value])
```

### Parameters - userHide

value  
The value that indicates whether the form tree control is hidden from the user.

### Return Value - userHide

1 if the tree control is hidden from the user; otherwise, 0.

### Remarks - userHide

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Examples - userHide

The following example shows how to return and set the value that specifies whether the form tree control is hidden from the user.

```xpp
int nUserHide; 
// The ctrl variable was previously assigned  
// as a form tree control variable. 
// Retrieve the userHide value. 
nUserHide = ctrl.userHide(); 
// Set the userHide value. 
ctrl.userHide(1);
```

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

Sets or retrieves the user prompt text for the control.

```xpp
public str userPromptText([str value])
```

### Parameters - userPromptText

value  
The value to assign as the user prompt text for the control.

### Return Value - userPromptText

The user prompt text for the control; an empty string if no user prompt text is assigned to the control.

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

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

```xpp
public int userSkip([int value])
```

### Parameters - userSkip

value  
The value to assign to the userSkip property. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

### Return Value - userSkip

1 if the user setting to skip the control is in effect; otherwise, 0.

### Examples - userSkip

The following example shows how to return and set the userSkip property.

```xpp
int nUserSkip 
// The ctrl variable was previously assigned 
// as a FormTreeControl value. 
// Return the userSkip property. 
nUserSkip = ctrl.userSkip(); 
// Set the userSkip property. 
ctrl.userSkip(1);
```

## Method userWidth

Sets or returns the width of the control in pixels, as specified by the user.

```xpp
public int userWidth([int value])
```

### Parameters - userWidth

value  
The number of pixels to use as the width of the control; optional.

### Return Value - userWidth

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

### Remarks - userWidth

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Examples - userWidth

The following example shows how to return and set the user width of a form tree control.

```xpp
int nWidth; 
// The ctrl variable was previously defined 
// as a FormTreeControl value. 
// Return the width. 
nWidth = ctrl.userWidth(); 
// Specify the width. 
ctrl.userWidth(90);  // 15 characters * 6 pixels == 90
```

## Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

```xpp
public int verticalSpacing([int value], [AutoMode mode])
```

### Parameters - verticalSpacing

value  
An integer value that indicates the AutoMode value for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode value for the control; optional.

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
The value to assign to the visibility setting for the control.

### Return Value - visible

true if the control is visible; otherwise, false.

## Method width

Gets or sets the width of the control.

```xpp
public int width(int value, [int mode])
```

### Parameters - width

value  
An integer that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer that indicates how the width is calculated; optional.

### Return Value - width

The width of the control in pixels.

### Remarks - width

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode             | Width calculation                                                                         |
|------------------|-------------------------------------------------------------------------------------------|
| -1 � Exact       | The exact width of the control in pixels is used.                                         |
| 0 � Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| 1 � Column width | The layout of the form determines the width of the control.                               |

The width and the width calculation mode can be set separately.

## Method widthMode

Gets or sets the calculation mode for the width of the control.

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  
An Integer data type value that indicates how control width is calculated. This value can be -1 for Exact mode, 0 for Auto mode, or 1 for Column width mode.

### Return Value - widthMode

An integer value that indicates the current width calculation mode.

### Remarks - widthMode

Calculate the width according to the following table.

| Mode         | Width calculation                                                                         |
|--------------|-------------------------------------------------------------------------------------------|
| Exact        | The exact width of the control in pixels is used.                                         |
| Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                               |

The width of the control might change when the calculation mode is set to Auto or Column width.

### Examples - widthMode

The following example shows how to return and set the width calculation mode for a form tree control.

```xpp
int nWidthMode; 
// The ctrl variable was previously assigned 
// as a form tree control value. 
// Retrieve the width mode. 
nWidthMode = ctrl.widthMode (); 
// Set the width mode. 
ctrl.widthMode(-1); 
// Set the width. 
ctrl.widthValue(180);
```

## Method widthValue

Gets or sets the width of the control.

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  
An Integer data type that specifies the width in pixels.

### Return Value - widthValue

The width of the control in pixels.

### Remarks - widthValue

To change the width of the control, use the Exact width calculation mode.

### Examples - widthValue

The following example shows how to return and set the width value of a form tree control.

```xpp
int nWidthValue; 
// The ctrl variable was previously assigned 
// as a form tree control value. 
// Retrieve the width value. 
nWidthValue = ctrl.widthValue(); 
// Set the width value. 
ctrl.widthMode(-1); 
ctrl.widthValue(160);
```

## Method checkedStateChanged

```xpp
public void checkedStateChanged(int Idx, FormTreeCheckedState newState)
```

### Parameters - checkedStateChanged

Idx  

<!-- -->

newState  

## Method endLabelEdit

```xpp
public void endLabelEdit(int Idx, str text, AnyType data)
```

### Parameters - endLabelEdit

Idx  

<!-- -->

text  

<!-- -->

data  

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

Is called when the user moves the mouse pointer into the control.

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

### Remarks - mouseEnter

Typically, when this method is overridden, the return value from a call to the super method is returned.

## Method OnExpanding

```xpp
private void OnExpanding([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnExpanding

sender  

<!-- -->

e  

## Method cut

Cuts the contents of the control.

```xpp
public void cut()
```

## Method paste

Pastes the form tree control in the form.

```xpp
public void paste()
```

## Method resetUserSetting

Resets the user settings for the control.

```xpp
public void resetUserSetting()
```

## Method itemMoved

```xpp
public void itemMoved(int OldIdx, int NewIdx)
```

### Parameters - itemMoved

OldIdx  

<!-- -->

NewIdx  

## Method expanded

```xpp
public void expanded(int Idx, FormTreeExpand action, AnyType data)
```

### Parameters - expanded

Idx  

<!-- -->

action  

<!-- -->

data  

## Method setFocus

Sets the focus on the control.

```xpp
public void setFocus()
```

## Method OnSelectionChanged

```xpp
private void OnSelectionChanged([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnSelectionChanged

sender  

<!-- -->

e  

## Method OnLostFocus

```xpp
private void OnLostFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLostFocus

sender  

<!-- -->

e  

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

## Method mouseLeave

Is called when the user moves the mouse pointer out of the control.

```xpp
public void mouseLeave()
```

### Examples - mouseLeave

The following example writes to the Infolog when the mouse pointer leaves the control area.

```xpp
public void mouseLeave() 
{ 
    info (strfmt("The mouse has left the %1 control.", this.name()) ); 
    super(); 
}
```

## Method endDrag

Is called when the user has finished dragging a form tree control.

```xpp
public void endDrag()
```

### Remarks - endDrag

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, the user presses the mouse button in the control area and then moves the mouse pointer.

### Examples - endDrag

The following example displays a message in the Infolog when the user has finished dragging the form tree control.

```xpp
public void endDrag() 
{ 
    info("EndDrag completed"); 
    super(); 
}
```

## Method context

Shows the shortcut menu for the control.

```xpp
public void context()
```

## Method itemCopy

```xpp
public void itemCopy(int OldIdx, int NewIdx)
```

### Parameters - itemCopy

OldIdx  

<!-- -->

NewIdx  

## Method enter

```xpp
public void enter()
```

## Method inputSearch

Performs data filtering for the control, based on the specified string.

```xpp
public void inputSearch(str searchStr)
```

### Parameters - inputSearch

searchStr  
The string value to use to filter data; optional.

## Method displayControl

Displays the control.

```xpp
public void displayControl()
```

## Method prefColumnSize

Specifies the preferred column width and height for the form tree control.

```xpp
public void prefColumnSize(int width, int height)
```

### Parameters - prefColumnSize

width  
The preferred height of the control measures in pixels.

<!-- -->

height  
The preferred height of the control measures in pixels.

### Examples - prefColumnSize

The following example shows how to set the preferred width and height of a form tree control.

```xpp
// The nWidth and nHeight variables were previously assigned 
// as int variables. 
// The ctrl variable was previously assigned 
// as a FormTreeControl value. 
ctrl.prefColumnSize( nWidth, nHeight);
```

## Method setImagelist

```xpp
public void setImagelist(Imagelist imageList)
```

### Parameters - setImagelist

imageList  

## Method OnExpanded

```xpp
private void OnExpanded([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnExpanded

sender  

<!-- -->

e  

## Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

```xpp
public void dragLeave()
```

## Method lostFocus

Indicates that the control has lost focus.

```xpp
public void lostFocus()
```

## Method OnEnter

```xpp
private void OnEnter([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnEnter

sender  

<!-- -->

e  

## Method itemDeleted

```xpp
public void itemDeleted(int Idx, AnyType data)
```

### Parameters - itemDeleted

Idx  

<!-- -->

data  

## Method gotFocus

Indicates that the control has received focus.

```xpp
public void gotFocus()
```

## Method setStateImagelist

```xpp
public void setStateImagelist(Imagelist imageList)
```

### Parameters - setStateImagelist

imageList  

## Method endEditLabel

```xpp
public void endEditLabel(boolean cancel)
```

### Parameters - endEditLabel

cancel  

## Method copy

Copies the form tree control.

```xpp
public void copy()
```

## Method OnGotFocus

```xpp
private void OnGotFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnGotFocus

sender  

<!-- -->

e  

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

## Method OnLeaving

```xpp
private void OnLeaving([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLeaving

sender  

<!-- -->

e  

## Method selectionChanged

Indicates that the user has changed the selected item in the form tree control.

```xpp
public void selectionChanged(FormTreeItem OldItem, FormTreeItem NewItem, FormTreeSelect how)
```

### Parameters - selectionChanged

OldItem  
The value that indicates how the item that is specified by the \_NewItem parameter was selected.

<!-- -->

NewItem  
The value that indicates how the item that is specified by the \_NewItem parameter was selected.

<!-- -->

how  
The value that indicates how the item that is specified by the \_NewItem parameter was selected.

## Method beginEditLabel

```xpp
public void beginEditLabel(int Idx)
```

### Parameters - beginEditLabel

Idx  

