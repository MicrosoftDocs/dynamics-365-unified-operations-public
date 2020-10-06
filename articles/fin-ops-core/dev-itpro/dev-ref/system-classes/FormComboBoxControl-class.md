---
title: FormComboBoxControl class
description: This topic describes the FormComboBoxControl class.
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

# Class FormComboBoxControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormComboBoxControl extends FormControl
```

## Remarks

## Examples

## Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether the control should be aligned with other controls.                                                                                                   |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can modify the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean appendNew(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determines whether the control�s background can be transparent.                                                                                                         |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to display text in the control.                                                                                            |
| public int border(\[int value\])                                                                            | Gets or sets the style of the border line for the control.                                                                                                              |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public int comboType(\[int value\])                                                                         | Sets or returns the type of combo box for the control.                                                                                                                  |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Returns a list that contains the IDs of configuration keys that are in effect for the control.                                                                          |
| public int count()                                                                                          | Returns the number of items in the combo box control.                                                                                                                   |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 | Sets or returns the data field for the combo box control.                                                                                                               |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that should be used by the control or the form.                                                                                              |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether drag-and-drop operations are enabled or disabled for the control.                                                                                    |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Returns the text that is displayed when the form combo box control is dragged.                                                                                          |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether the object is enabled or disabled.                                                                                                                   |
| public EnumId enumType(\[EnumId value\])                                                                    |                                                                                                                                                                         |
| public EnumId enumTypeValue()                                                                               |                                                                                                                                                                         |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                                                         |
| public int find(str string)                                                                                 |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font that should be used for the control.                                                                                                  |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font that should be used for the control.                                                                                                  |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public str getEditText()                                                                                    |                                                                                                                                                                         |
| public str getText(int index)                                                                               |                                                                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the form combo box control have changed.                                                                 |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control in pixels.                                                                                                                       |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Returns the Help text for the control.                                                                                                                                  |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.                                                         |
| public boolean hideFirstEntry(\[boolean value\])                                                            | Sets or returns a value that indicates whether the first entry in the combo box control is hidden.                                                                      |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Returns the Windows handle for the control.                                                                                                                             |
| public boolean isContainer()                                                                                | Returns a value that indicates whether the control is a container.                                                                                                      |
| public boolean isDisplayed()                                                                                | Returns a value that indicates whether the control is displayed.                                                                                                        |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean isValid()                                                                                    |                                                                                                                                                                         |
| public boolean italic(\[boolean value\])                                                                    | Sets or returns a value that indicates whether the text in the control is italic.                                                                                       |
| public int item(\[int value\])                                                                              |                                                                                                                                                                         |
| public int items(\[int value\])                                                                             |                                                                                                                                                                         |
| public str label(\[str value\])                                                                             | Gets or sets the label for a control.                                                                                                                                   |
| public int labelAlignment(\[int value\])                                                                    |                                                                                                                                                                         |
| public int labelBold(\[int value\])                                                                         | Sets or returns a value that indicates the bold setting for the label in the control.                                                                                   |
| public int labelCharacterSet(\[int value\])                                                                 |                                                                                                                                                                         |
| public str labelFont(\[str value\])                                                                         | Sets or returns a font for the label text in a form combo box control.                                                                                                  |
| public int labelFontSize(\[int value\])                                                                     | Sets or returns the font size in points for the label text in a form combo box control.                                                                                 |
| public int labelForegroundColor(\[int value\])                                                              |                                                                                                                                                                         |
| public int labelGuide(\[int value\])                                                                        |                                                                                                                                                                         |
| public int labelHeight(int value, \[int mode\])                                                             |                                                                                                                                                                         |
| public int labelHeightMode(\[int value\])                                                                   |                                                                                                                                                                         |
| public int labelHeightValue(\[int value\])                                                                  |                                                                                                                                                                         |
| public boolean labelItalic(\[boolean value\])                                                               | Sets or returns a value that indicates whether the text in the label of the control is italic.                                                                          |
| public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                        | Is called when the label for the control is double-clicked by the user.                                                                                                 |
| public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                            | Is called when the user clicks the mouse button over the label for the control.                                                                                         |
| public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                              | Is called when the user releases the mouse button over the label for the control.                                                                                       |
| public int labelPosition(\[int value\])                                                                     | Sets or returns the position of the label for the control.                                                                                                              |
| public boolean labelUnderline(\[boolean value\])                                                            | Sets or returns a value that indicates whether the text in the label of the control is underlined.                                                                      |
| public int labelWidth(int value, \[int mode\])                                                              |                                                                                                                                                                         |
| public int labelWidthMode(\[int value\])                                                                    |                                                                                                                                                                         |
| public int labelWidthValue(\[int value\])                                                                   |                                                                                                                                                                         |
| public boolean leave()                                                                                      |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control.                                                                                                     |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int selection(\[int value\])                                                                         |                                                                                                                                                                         |
| public int selectionChange()                                                                                | Indicates that the user has changed the selected item in the combo box control.                                                                                         |
| public int selectText(str string)                                                                           |                                                                                                                                                                         |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 | Sets or returns a value that indicates whether the label for the control is displayed in the form.                                                                      |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public str text(\[str value\])                                                                              | Sets or returns the text for the control.                                                                                                                               |
| public str toolTip()                                                                                        | Returns the tooltip text for the control.                                                                                                                               |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the underline property for the text in the control.                                                                                                     |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Returns or sets the value that indicates whether the form combo box control is hidden from the user.                                                                    |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form combo box control is skipped when the user presses the TAB key to navigate the controls in the form.          |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the form combo box control in pixels.                                                                                                      |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void beginUpdate()                                                                                   |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void setEditText(str string)                                                                         |                                                                                                                                                                         |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void paste()                                                                                         | Pastes the form combo box control into the form.                                                                                                                        |
| public void clear()                                                                                         | Clears the entries in the combo box list.                                                                                                                               |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void copy()                                                                                          | Copies the form combo box control.                                                                                                                                      |
| private void OnSelectionChanging(\[FormControl sender\], \[FormControlEventArgs e\])                        |                                                                                                                                                                         |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form combo box control.                                                                                                 |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void insert(str string, int index)                                                                   | Inserts a string value into the combo box list at the specified position.                                                                                               |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control.                                                                                                       |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void delete(str string)                                                                              | Removes a string value from the combo box list.                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void add(str string)                                                                                 | Adds a string value to the combo box list.                                                                                                                              |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form combo box control.                                                                                         |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| private void OnSelectionChanged(\[FormControl sender\], \[FormControlEventArgs e\])                         |                                                                                                                                                                         |
| public void endUpdate()                                                                                     |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void setDropSize(\[int lines\])                                                                      |                                                                                                                                                                         |

## Method alignControl

Determines whether the control should be aligned with other controls.

```xpp
public boolean alignControl([boolean value])
```

### Parameters - alignControl

value  
A Boolean value that indicates whether the form combo box control is aligned with other controls; optional.

### Return Value - alignControl

true if the control should be aligned; otherwise, false.

### Remarks - alignControl

The upper-left corner of the control is aligned based on the longest label.

### Examples - alignControl

The following example shows a call to the alignControl method to align a form combo box control with other controls, based on the length of the longest label.

```xpp
boolean bAlign; 
// The combo variable was previously assigned 
// as a FormComboBoxControl type. 
// Retrieve the alignControl property. 
bAlign = combo.alignControl(); 
// Set the alignControl property. 
combo.alignControl(false);
```

## Method allowEdit

Determines whether the user can modify the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  
The value to assign to the allowEdit property; optional.

### Return Value - allowEdit

true if the control can be modified; otherwise, false.

### Remarks - allowEdit

If this property is set on a container control, modifications are disabled or enabled for all controls in the container.

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

## Method appendNew

```xpp
public boolean appendNew([boolean value])
```

### Parameters - appendNew

value  

### Return Value - appendNew

## Method arrayIndex

```xpp
public int arrayIndex([int value])
```

### Parameters - arrayIndex

value  

### Return Value - arrayIndex

## Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  
The value to assign to the autoDeclaration property; optional.

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
The value to assign as the background color of the control; optional. This can be one of the values from the control�s color scheme or a Winapi::RGB2int value.

### Return Value - backgroundColor

An integer that contains a packed RGB color.

### Remarks - backgroundColor

The integer that is returned contains the RGB color as follows:

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

Determines whether the control�s background can be transparent.

```xpp
public int backStyle([int value])
```

### Parameters - backStyle

value  
The value to assign as the background style of the control; optional.

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

Is called when the user starts to drag a form control.

```xpp
public int beginDrag(int x, int y)
```

### Parameters - beginDrag

x  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

### Return Value - beginDrag

0 (zero) if the event has been handled.

### Remarks - beginDrag

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Examples - beginDrag

The following example displays the x-coordinate and y-coordinate in the Infolog when the user starts to drag the form combo box control.

```xpp
public int beginDrag(int _x, int _y) 
{ 
    int ret; 
    info(strfmt("beginDrag (x, y) : (%1, %2)", _x, _y)); 
    ret = super(_x, _y); 
    return ret; 
}
```

## Method bold

Gets or sets the weight of font that is used to display text in the control.

```xpp
public int bold([int value])
```

### Parameters - bold

value  
The value to assign to the control's bold setting; optional.

### Return Value - bold

An integer value between 0 (zero) and 9, inclusive.

### Remarks - bold

The integer that is returned contains the font weight as follows:

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

Gets or sets the style of the border line for the control.

```xpp
public int border([int value])
```

### Parameters - border

value  
The value to assign as the border style for the control; optional.

### Return Value - border

An integer between 0 (zero) and 4, inclusive.

### Remarks - border

The integer that is returned contains the border style line as follows.

-   0 � Auto.
-   1 � 3D.
-   2 � Single line.
-   3 � Flat.
-   4 � None.

### Examples - border

The following example shows how to retrieve and set the border style for a control.

```xpp
// Retrieve the border style. 
info (strfmt("border: %1", this.border())); 
// Set the border style. 
this.border(2);
```

## Method cacheDataMethod

```xpp
public int cacheDataMethod([int value])
```

### Parameters - cacheDataMethod

value  

### Return Value - cacheDataMethod

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

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of Microsoft Windows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the [MSDN website](https://go.microsoft.com/fwlink/?LinkID=85972).

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

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

## Method comboType

Sets or returns the type of combo box for the control.

```xpp
public int comboType([int value])
```

### Parameters - comboType

value  
The value to assign as the type of combo box for the control; optional.

### Return Value - comboType

The type of combo box for the control.

### Remarks - comboType

The following table shows the values for the combo box type.

| Value | Description |
|-------|-------------|
| 0     | Standard    |
| 1     | List        |

### Examples - comboType

The following example shows how to retrieve and set the type of combo box that is used for the control.

```xpp
// Retrieve the type of combo box control. 
info(strfmt("comboType: %1", this.comboType())); 
// Set the type of combo box control. 
this.comboType(1);
```

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

The following example shows the setting and retrieval of the configuration key for a control.

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

The list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. In addition, the returned list contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

### Examples - configurationKeyEx

The following example shows the retrieval of the configuration key IDs for a control.

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

## Method count

Returns the number of items in the combo box control.

```xpp
public int count()
```

### Return Value - count

The number of items in the combo box control.

### Examples - count

The following example shows how to use the count method.

```xpp
int j; 
j = this.count();
```

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

## Method countryRegionContextField

```xpp
public FieldId countryRegionContextField([FieldId value])
```

### Parameters - countryRegionContextField

value  

### Return Value - countryRegionContextField

## Method dataField

Sets or returns the data field for the combo box control.

```xpp
public FieldId dataField([FieldId value])
```

### Parameters - dataField

value  
The value to assign as the data field ID for the combo box control; optional.

### Return Value - dataField

The value of the data field ID for the combo box control.

### Examples - dataField

The following example shows how to set and return the data field for the combo box control.

```xpp
fieldID i; 
// The combo variable is a previously assigned  
// FormComboBoxControl value. 
// Retrieve the data Field. 
i = combo.dataField(); 
// Set the data field. 
combo.dataField(fieldnum(CustTable, IdentificationNumber));
```

## Method dataMethod

```xpp
public str dataMethod([str value])
```

### Parameters - dataMethod

value  

### Return Value - dataMethod

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

## Method dataSource

Gets or sets a data source that should be used by the control or the form.

```xpp
public int dataSource([AnyType value])
```

### Parameters - dataSource

value  
The value to assign as the data source for the combo box control; optional.

### Return Value - dataSource

The identifier of the data source that should be used.

### Examples - dataSource

The following example shows how to set and return the data source for the combo box control.

```xpp
int i; 
// The combo variable was previously assigned  
// as a FormComboBoxControl variable. 
// Retrieve the data source. 
i = combo.dataSource(); 
// Set the data source. 
combo.dataSource(tablenum(CustTable));
```

## Method displayLength

```xpp
public int displayLength([int value], [AutoMode mode])
```

### Parameters - displayLength

value  

<!-- -->

mode  

### Return Value - displayLength

## Method displayLengthMode

```xpp
public AutoMode displayLengthMode([AutoMode mode])
```

### Parameters - displayLengthMode

mode  

### Return Value - displayLengthMode

## Method displayLengthValue

```xpp
public int displayLengthValue([int value])
```

### Parameters - displayLengthValue

value  

### Return Value - displayLengthValue

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
An integer value that indicates whether drag-and-drop behavior is enabled; optional.

### Return Value - dragDrop

1 if drag-and-drop operations are enabled; otherwise, false.

### Examples - dragDrop

The following example shows how to return or set the value that indicates whether drag-and-drop behavior is enabled.

```xpp
boolean bDragDrop; 
// The combo variable was previously assigned  
// as a FormComboBoxControl value. 
// Retrieve the drag-and-drop-enabled value. 
bDragDrop = combo.dragDrop(); 
// Set the drag-and-drop-enabled value. 
combo.dragDrop(true);
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

Returns the text that is displayed when the form combo box control is dragged.

```xpp
public str dragText()
```

### Return Value - dragText

The text that is displayed when the combo box control is dragged; an empty string if there is no text to display when the combo box control is dragged.

## Method enabled

Determines whether the object is enabled or disabled.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  
A Boolean value that specifies whether the control is enabled; optional.

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

## Method enumType

```xpp
public EnumId enumType([EnumId value])
```

### Parameters - enumType

value  

### Return Value - enumType

## Method enumTypeValue

```xpp
public EnumId enumTypeValue()
```

### Return Value - enumTypeValue

## Method extendedDataType

```xpp
public ExtendedTypeId extendedDataType([ExtendedTypeId value])
```

### Parameters - extendedDataType

value  

### Return Value - extendedDataType

## Method fastTabSummary

```xpp
public int fastTabSummary([int value])
```

### Parameters - fastTabSummary

value  

### Return Value - fastTabSummary

## Method find

```xpp
public int find(str string)
```

### Parameters - find

string  

### Return Value - find

## Method font

Gets or sets the name of the font that should be used for the control.

```xpp
public str font([str value])
```

### Parameters - font

value  
A String data type that indicates the font to use for text in a form combo box control; optional.

### Return Value - font

The name of the font that should be used, such as Tahoma or Verdana.

### Examples - font

The following example shows how to return and set the font for a form combo box control.

```xpp
str strFont; 
; 
// The ctrl variable was previously assigned  
// as a form combo box control value. 
// Retrieve the font. 
strFont = ctrl.font(); 
// Set the font. 
ctrl.font("Times New Roman");
```

## Method fontSize

Gets or sets the size of the font that should be used for the control.

```xpp
public int fontSize([int value])
```

### Parameters - fontSize

value  
An Integer data type that indicates the font size in points for text in a form combo box control; optional.

### Return Value - fontSize

The height of the font in points.

### Examples - fontSize

The following example shows how to return and set the font size for a form combo box control.

```xpp
int nSize; 
// The ctrl variable was previously assigned  
// as a form combo box control. 
// Retrieve the font size. 
nSize = ctrl.fontSize(); 
// Set the font size. 
ctrl.fontSize(16);
```

## Method foregroundColor

Gets or sets the text color for the control to use.

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
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

## Method getEditText

```xpp
public str getEditText()
```

### Return Value - getEditText

## Method getText

```xpp
public str getText(int index)
```

### Parameters - getText

index  

### Return Value - getText

## Method hasChanged

Sets or returns a value that indicates whether the contents of the form combo box control have changed.

```xpp
public boolean hasChanged([boolean val])
```

### Parameters - hasChanged

val  
A value to assign as the hasChanged value for the combo box control; optional.

### Return Value - hasChanged

true if the contents of the combo box control have changed; otherwise, false.

### Examples - hasChanged

The following example shows how to return and set the value that indicates whether the contents of the combo box control have changed.

```xpp
boolean bHasChanged; 
// The ctrl variable was previously assigned 
// as a FormComboBoxControl variable. 
// Retrieve the hasChanged value. 
bHasChanged = ctrl.hasChanged(); 
// Modify the hasChanged value. 
ctrl.hasChanged(true);
```

## Method hasUserSetting

Indicates whether the control has custom user settings.

```xpp
public boolean hasUserSetting()
```

### Return Value - hasUserSetting

true if the control has custom user settings; otherwise, false.

## Method height

Gets or sets the height of the control in pixels.

```xpp
public int height(int value, [int mode])
```

### Parameters - height

value  
An integer value that indicates how the height is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the height is calculated; optional.

### Return Value - height

The height of the control in pixels.

### Remarks - height

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

| Mode              | Height calculation                                                                         |
|-------------------|--------------------------------------------------------------------------------------------|
| -1 � Exact        | The exact height of the control in pixels is used.                                         |
| 0 � Auto          | The height of the control is calculated automatically, and the value parameter is ignored. |
| 1 � Column height | The layout of the form determines the height of the control.                               |

The height and height calculation mode can be set separately.

## Method heightMode

Gets or sets a calculation mode for the height of the control.

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  
An integer value that indicates how the height of the control is calculated; optional.

### Return Value - heightMode

The calculation mode.

### Remarks - heightMode

Calculate the height according to the following table.

| Mode          | Height calculation                                                                         |
|---------------|--------------------------------------------------------------------------------------------|
| Exact         | The exact height of the control in pixels is used.                                         |
| Auto          | The height of the control is calculated automatically, and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                               |

The height of the control might change when the calculation mode is set to Auto or Column height.

### Examples - heightMode

The following example shows how to return and set the height calculation mode for a form combo box control:

```xpp
int nHeightMode; 
// The ctrl variable was previously assigned 
// as a form combo box control type. 
// Retrieve the height mode. 
nHeightMode = ctrl.HeightMode(); 
// Set the height mode. 
ctrl.heightMode(-1); 
// Set the height. 
ctrl.heightValue(16);
```

## Method heightValue

Gets or sets the height of the control.

```xpp
public int heightValue([int value])
```

### Parameters - heightValue

value  
An integer value that specifies the height in pixels; optional.

### Return Value - heightValue

The height in pixels.

### Remarks - heightValue

The height of the control is not changed unless the Exact height calculation mode is used.

### Examples - heightValue

The following example shows how to return and set the height value of a combo box control.

```xpp
int nHeightValue; 
// The ctrl variable was previously assigned 
// as a form combo box control type. 
// Retrieve the height value. 
nHeightValue = ctrl.heightValue(); 
// Set the height value. 
ctrl.heightMode(-1); 
ctrl.heightValue(22);
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
The value to assign as the Help text for the control; optional.

### Return Value - helpText

The string that should be displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Examples - helpText

The following example shows how to set and return the Help text for a control.

```xpp
// objCtrl previously assigned to a control 
// Retrieve existing help text. 
print objCtrl.helpText(); 
// Specify new help text. 
objCtrl.helpText("My new help text");
```

## Method hideFirstEntry

Sets or returns a value that indicates whether the first entry in the combo box control is hidden.

```xpp
public boolean hideFirstEntry([boolean value])
```

### Parameters - hideFirstEntry

value  
A value that indicates whether the first entry in the combo box control is hidden; optional.

### Return Value - hideFirstEntry

true if the first entry in the combo box control is hidden; otherwise, false.

### Remarks - hideFirstEntry

By hiding the first entry in the combo box control, you enable the control to emulate the behavior of an enum database field where the Mandatory property is set to Yes.

### Examples - hideFirstEntry

The following example shows how to return and set the value that indicates whether the first entry in the combo box control is hidden.

```xpp
boolean bHideFirstEntry; 
// The ctrl variable was previously assigned 
// as a form combo box control type. 
// Retrieve the hideFirstEntry value. 
bHideFirstEntry = ctrl.hideFirstEntry(); 
// Set the hideFirstEntry value. 
bHideFirstEntry = ctrl.hideFirstEntry(true);
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

true if the control is a container; otherwise, false.

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

Returns a value that indicates whether the control allows for the specified level of customization.

```xpp
public boolean isUserSetupEnabled(int neededSetupRights)
```

### Parameters - isUserSetupEnabled

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control.

### Return Value - isUserSetupEnabled

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

### Remarks - isUserSetupEnabled

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

For this method to return true, the AllowUserSetup property for the design and all parent containers must be at least as high as the level that is specified by the neededSetupRights parameter.

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

## Method isValid

```xpp
public boolean isValid()
```

### Return Value - isValid

## Method italic

Sets or returns a value that indicates whether the text in the control is italic.

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  
The value to assign to the italic setting of the control; optional.

### Return Value - italic

true if the text in the control is italic; otherwise, false.

## Method item

```xpp
public int item([int value])
```

### Parameters - item

value  

### Return Value - item

## Method items

```xpp
public int items([int value])
```

### Parameters - items

value  

### Return Value - items

## Method label

Gets or sets the label for a control.

```xpp
public str label([str value])
```

### Parameters - label

value  
The value to assign as the label of the control; optional.

### Return Value - label

The current value of the label string.

### Remarks - label

The label determines the text that is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Examples - label

The following example shows how to return and set the label of the control.

```xpp
// Return the label value. 
info(strfmt("label: %1", this.label())); 
// Set the label value. 
this.label("New label text goes here");
```

## Method labelAlignment

```xpp
public int labelAlignment([int value])
```

### Parameters - labelAlignment

value  

### Return Value - labelAlignment

## Method labelBold

Sets or returns a value that indicates the bold setting for the label in the control.

```xpp
public int labelBold([int value])
```

### Parameters - labelBold

value  
The value to assign to the label bold setting. This can be one of the values from the ReportControlBold enumeration.

### Return Value - labelBold

A value from the ReportControlBold enumeration that indicates the bold setting for the label in the control.

## Method labelCharacterSet

```xpp
public int labelCharacterSet([int value])
```

### Parameters - labelCharacterSet

value  

### Return Value - labelCharacterSet

## Method labelFont

Sets or returns a font for the label text in a form combo box control.

```xpp
public str labelFont([str value])
```

### Parameters - labelFont

value  
A String data type that indicates the font for the label text in a form combo box control; optional.

### Return Value - labelFont

A String data type value that indicates the font for the label text in a form combo box control.

### Examples - labelFont

The following example shows how to return and set the font for the label text in a form combo box control.

```xpp
str strLabelFont; 
// The ctrl variable was previously assigned  
// as a form combo box control variable. 
// Retrieve the font. 
strLabelFont = ctrl.labelFont(); 
// Set the label font. 
ctrl.labelFont("Times New Roman");
```

## Method labelFontSize

Sets or returns the font size in points for the label text in a form combo box control.

```xpp
public int labelFontSize([int value])
```

### Parameters - labelFontSize

value  
An Integer data type that indicates the font size in points for the label text in a form combo box control; optional.

### Return Value - labelFontSize

An Integer data type value that indicates the label font size in points for the text in a form combo box control.

### Examples - labelFontSize

The following example shows how to return and set the label font size for a form combo box control.

```xpp
int nSize; 
// The ctrl variable was previously assigned  
// as a form combo box control. 
// Retrieve the label font size. 
nSize = ctrl.labelFontSize(); 
// Set the label font size. 
ctrl.labelFontSize(16);
```

## Method labelForegroundColor

```xpp
public int labelForegroundColor([int value])
```

### Parameters - labelForegroundColor

value  

### Return Value - labelForegroundColor

## Method labelGuide

```xpp
public int labelGuide([int value])
```

### Parameters - labelGuide

value  

### Return Value - labelGuide

## Method labelHeight

```xpp
public int labelHeight(int value, [int mode])
```

### Parameters - labelHeight

value  

<!-- -->

mode  

### Return Value - labelHeight

## Method labelHeightMode

```xpp
public int labelHeightMode([int value])
```

### Parameters - labelHeightMode

value  

### Return Value - labelHeightMode

## Method labelHeightValue

```xpp
public int labelHeightValue([int value])
```

### Parameters - labelHeightValue

value  

### Return Value - labelHeightValue

## Method labelItalic

Sets or returns a value that indicates whether the text in the label of the control is italic.

```xpp
public boolean labelItalic([boolean value])
```

### Parameters - labelItalic

value  
The value to assign to the italic setting of the label of the control; optional.

### Return Value - labelItalic

true if the text in the label of the control is italic; otherwise, false.

## Method labelMouseDblClick

Is called when the label for the control is double-clicked by the user.

```xpp
public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - labelMouseDblClick

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

### Return Value - labelMouseDblClick

0 (zero) if the event has been handled.

### Remarks - labelMouseDblClick

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Examples - labelMouseDblClick

The following example shows how to display the parameters of a labelMouseDblClick event in the Infolog.

```xpp
public int labelMouseDblClick(int x,  
                              int y,  
                              int button, 
                              boolean Ctrl, 
                              boolean Shift) 
{ 
    int ret; 
    ; 
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

## Method labelMouseDown

Is called when the user clicks the mouse button over the label for the control.

```xpp
public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - labelMouseDown

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

### Return Value - labelMouseDown

0 (zero) if the event has been handled.

### Remarks - labelMouseDown

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Examples - labelMouseDown

The following example shows how to display the parameters of a labelMouseDown event in the Infolog.

```xpp
public int labelMouseDown(int x,  
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

## Method labelMouseUp

Is called when the user releases the mouse button over the label for the control.

```xpp
public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - labelMouseUp

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

### Return Value - labelMouseUp

0 (zero) if the event has been handled.

### Remarks - labelMouseUp

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Examples - labelMouseUp

The following example shows how to display the parameters of a labelMouseUp event in the Infolog.

```xpp
public int labelMouseUp(int x,  
                              int y,  
                              int button, 
                              boolean Ctrl, 
                              boolean Shift) 
{ 
    int ret; 
    ; 
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

## Method labelPosition

Sets or returns the position of the label for the control.

```xpp
public int labelPosition([int value])
```

### Parameters - labelPosition

value  
The value to assign to the label position; optional.

### Return Value - labelPosition

An integer that represents the position of the label.

### Remarks - labelPosition

If the value parameter is set to 0 (zero), the label is put to the left of the control. If the value parameter is set to 1, the label is put above the control. A return value of 0 (zero) indicates that the label is put to the left of the control. A return value of 1 indicates that the label is put above the control.

### Examples - labelPosition

The following example shows how to return and set the label position.

```xpp
// Retrieve the label position. 
info (strfmt("label: %1", this.labelPosition())); 
// Set the label position. 
this.labelPosition(1);  // 1 == Above, 0 == Left
```

## Method labelUnderline

Sets or returns a value that indicates whether the text in the label of the control is underlined.

```xpp
public boolean labelUnderline([boolean value])
```

### Parameters - labelUnderline

value  
The value to assign to the underline setting of the label of the control; optional.

### Return Value - labelUnderline

true if the text in the label of the control is underlined; otherwise, false.

## Method labelWidth

```xpp
public int labelWidth(int value, [int mode])
```

### Parameters - labelWidth

value  

<!-- -->

mode  

### Return Value - labelWidth

## Method labelWidthMode

```xpp
public int labelWidthMode([int value])
```

### Parameters - labelWidthMode

value  

### Return Value - labelWidthMode

## Method labelWidthValue

```xpp
public int labelWidthValue([int value])
```

### Parameters - labelWidthValue

value  

### Return Value - labelWidthValue

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
The Boolean value that indicates whether the control should be marked as a user-added control.

### Return Value - markAsUserAdd

true if the control was marked as a user-added control; otherwise, false.

## Method modified

```xpp
public boolean modified()
```

### Return Value - modified

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

### Examples - mouseDblClick

Typically, when this method is overridden, the return value from a call to the super method is returned. The following example shows how to display the parameters of a mouseDblClick event in the Infolog.

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
        info("Shift set"); 
    } 
    if (Ctrl) 
    { 
        info("Ctrl set"); 
    } 
    info (strfmt("x, y: %1 %2 button: %3", x, y, button)); 
    ret = super(x, y, button, Ctrl, Shift); 
    info (strfmt("ret: %1", ret)); 
    return ret; 
}
```

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
    ; 
    if (Shift) 
    { 
        info("Shift set"); 
    } 
    if (Ctrl) 
    { 
        info("Ctrl set"); 
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

### Examples - mouseMove

Typically, when this method is overridden, the return value from a call to the super method is returned. The following example shows how to display the parameters of a mouseMove event in the Infolog.

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

Is called when the user releases the mouse button over the control.

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

### Examples - mouseUp

Typically, when this method is overridden, the return value from a call to the super method is returned. The following example shows how to display the parameters of a mouseUp event in the Infolog.

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

-   It must start with a letter.
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

## Method previewPartRef

```xpp
public str previewPartRef([str value])
```

### Parameters - previewPartRef

value  

### Return Value - previewPartRef

## Method promptrect

```xpp
public int promptrect([int value])
```

### Parameters - promptrect

value  

### Return Value - promptrect

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

### Examples - securityKey

The following example shows the retrieval and assignment of a security key ID for a control.

```xpp
DictSecurityKey dsk; 
securityKeyId ski; 
; 
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

## Method selection

```xpp
public int selection([int value])
```

### Parameters - selection

value  

### Return Value - selection

## Method selectionChange

Indicates that the user has changed the selected item in the combo box control.

```xpp
public int selectionChange()
```

### Return Value - selectionChange

true if the event was processed successfully; otherwise, false.

### Examples - selectionChange

The following example shows how the selectionChange method can be overridden to display an Infolog message when the user changes the selected item in the combo box control.

```xpp
public int selectionChange() 
{ 
    int ret; 
    info("The selection has changed."); 
    ret = super(); 
    return ret; 
}
```

## Method selectText

```xpp
public int selectText(str string)
```

### Parameters - selectText

string  

### Return Value - selectText

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

## Method showLabel

Sets or returns a value that indicates whether the label for the control is displayed in the form.

```xpp
public boolean showLabel([boolean value])
```

### Parameters - showLabel

value  
The value to assign to the showLabel property for the control.

### Return Value - showLabel

true if the label should be displayed; otherwise, false.

### Examples - showLabel

The following example shows how to return and set the showLabel property for a control.

```xpp
// Return the showLabel value. 
info(strfmt("showLabel: %1", this.showLabel())); 
// Set the showLabel value. 
this.showLabel(false);
```

## Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  
The value to assign to the skip property of the control; optional.

### Return Value - skip

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

## Method sort

```xpp
public int sort([SortOrder sortDirection])
```

### Parameters - sort

sortDirection  

### Return Value - sort

## Method text

Sets or returns the text for the control.

```xpp
public str text([str value])
```

### Parameters - text

value  
The value to assign as the text for the control; optional.

### Return Value - text

The text for the control; an empty string if no text has been assigned for the control.

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

## Method type

```xpp
public int type([int value])
```

### Parameters - type

value  

### Return Value - type

## Method underline

Sets or returns the underline property for the text in the control.

```xpp
public boolean underline([boolean value])
```

### Parameters - underline

value  
The value to assign to the underline property of the control; optional.

### Return Value - underline

true if the text in the control is underlined; otherwise, false.

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

Returns or sets the value that indicates whether the form combo box control is hidden from the user.

```xpp
public int userHide([int value])
```

### Parameters - userHide

value  
A value that indicates whether the control is hidden from the user; optional.

### Return Value - userHide

1 if the control is hidden from the user; otherwise, 0.

### Remarks - userHide

The user specifies whether a combo box control is hidden by right-clicking the control when it can be viewed or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. The userHide method lets you programmatically determine and set the value.

### Examples - userHide

The following example shows how to return and set the value that indicates whether the combo box control is hidden from the user.

```xpp
int nUserHide; 
// The ctrl variable was previously assigned  
// as a form combo box control variable. 
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

Sets or returns the value that indicates whether the form combo box control is skipped when the user presses the TAB key to navigate the controls in the form.

```xpp
public int userSkip([int value])
```

### Parameters - userSkip

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

### Return Value - userSkip

1 if the user setting to skip the control is in effect; otherwise, 0.

### Examples - userSkip

The following example shows how to return and set the userSkip property.

```xpp
int nUserSkip 
// The ctrl variable was previously assigned as a 
// FormComboBoxControl variable. 
// Return the userSkip property. 
nUserSkip = ctrl.userSkip(); 
// Set the userSkip property. 
ctrl.userSkip(1);
```

## Method userWidth

Sets or returns the width of the form combo box control in pixels.

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

The following example shows how to return and set the user width of a form combo box control.

```xpp
int nWidth; 
// The ctrl variable was previously defined  
// as the FormComboBoxControl variable. 
// Return the width. 
nWidth = ctrl.userWidth(); 
// Specify the width. 
ctrl.userWidth(90);  // 15 characters * 6 pixels == 90
```

## Method validate

```xpp
public boolean validate()
```

### Return Value - validate

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
A AutoMode enumeration value for the control; optional.

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

## Method viewEditMode

```xpp
public int viewEditMode([int value])
```

### Parameters - viewEditMode

value  

### Return Value - viewEditMode

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
An integer value that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the width is calculated; optional.

### Return Value - width

The width of the control in pixels.

### Remarks - width

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode             | Width calculation                                                                         |
|------------------|-------------------------------------------------------------------------------------------|
| -1 � Exact       | The exact width of the control in pixels is used.                                         |
| 0 � Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| 1 � Column width | The layout of the form determines the width of the control.                               |

The width and width calculation mode can be set separately.

## Method widthMode

Gets or sets the calculation mode of the width of the control.

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  
An integer value that indicates how a control width is calculated. The value can be -1 for Exact mode, 0 for Auto mode, or 1 for Column width mode.

### Return Value - widthMode

An integer value that indicates the current calculation mode.

### Remarks - widthMode

Calculate the width according to the following table.

| Mode         | Width Calculation.                                                                        |
|--------------|-------------------------------------------------------------------------------------------|
| Exact        | The exact width of the control in pixels is used.                                         |
| Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                               |

The width of the control might change when the calculation mode is set to Auto or Column width.

### Examples - widthMode

The following example shows how to return and set the width calculation mode for a combo box control in a form.

```xpp
int nWidthMode; 
; 
// The ctrl variable was previously assigned 
// as a form combo box control variable. 
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
An integer value that specifies the width in pixels; optional.

### Return Value - widthValue

The width of the control in pixels.

### Remarks - widthValue

To change the width of the control, use the Exact width calculation mode.

### Examples - widthValue

The following example shows how to return and set the width value of a form combo box control.

```xpp
int nWidthValue; 
// The ctrl variable was previously assigned 
// as a form combo box control variable. 
// Retrieve the width value. 
nWidthValue = ctrl.widthValue(); 
// Set the width value. 
ctrl.widthMode(-1); 
ctrl.widthValue(160);
```

## Method filter

```xpp
public void filter([str filterStr])
```

### Parameters - filter

filterStr  

## Method displayControl

Displays the control.

```xpp
public void displayControl()
```

## Method OnValidated

```xpp
private void OnValidated([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnValidated

sender  

<!-- -->

e  

## Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

```xpp
public void dragLeave()
```

## Method resetUserSetting

Resets the user settings for the control.

```xpp
public void resetUserSetting()
```

## Method OnModified

```xpp
private void OnModified([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnModified

sender  

<!-- -->

e  

## Method context

Shows the shortcut menu for the control.

```xpp
public void context()
```

## Method beginUpdate

```xpp
public void beginUpdate()
```

## Method OnGotFocus

```xpp
private void OnGotFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnGotFocus

sender  

<!-- -->

e  

## Method setEditText

```xpp
public void setEditText(str string)
```

### Parameters - setEditText

string  

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

## Method paste

Pastes the form combo box control into the form.

```xpp
public void paste()
```

## Method clear

Clears the entries in the combo box list.

```xpp
public void clear()
```

### Examples - clear

The following example shows how to clear the entries in the combo box list.

```xpp
this.clear();
```

## Method gotFocus

Indicates that the control has received focus.

```xpp
public void gotFocus()
```

## Method OnLostFocus

```xpp
private void OnLostFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLostFocus

sender  

<!-- -->

e  

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

## Method copy

Copies the form combo box control.

```xpp
public void copy()
```

## Method OnSelectionChanging

```xpp
private void OnSelectionChanging([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnSelectionChanging

sender  

<!-- -->

e  

## Method endDrag

Is called when the user has finished dragging a form combo box control.

```xpp
public void endDrag()
```

### Remarks - endDrag

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag the control, the user presses the mouse button in the control area and then moves the mouse pointer.

### Examples - endDrag

The following example displays a message in the Infolog when the user has finished dragging the form combo box control.

```xpp
public void endDrag() 
{ 
    info("EndDrag completed"); 
    super(); 
}
```

## Method lookup

```xpp
public void lookup()
```

## Method setFocus

Sets the focus on the control.

```xpp
public void setFocus()
```

## Method insert

Inserts a string value into the combo box list at the specified position.

```xpp
public void insert(str string, int index)
```

### Parameters - insert

string  
The position to insert the string after. If you want the string to be the first item in the list, set the value to 0 (zero).

<!-- -->

index  
The position to insert the string after. If you want the string to be the first item in the list, set the value to 0 (zero).

### Examples - insert

The following example shows how to insert a string into the combo box list.

```xpp
this.insert("willow", 3);
```

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

### Examples - mouseEnter

The following example shows how to display the parameters of a mouseEnter event in the Infolog.

```xpp
public void mouseEnter(int x,  
                      int y,  
                      int button, 
                      boolean Ctrl, 
                      boolean Shift) 
{ 
    int ret; 
    if (Shift) 
    { 
        info("Shift set"); 
    } 
    if (Ctrl) 
    { 
        info("Ctrl set"); 
    } 
    info (strfmt("x, y: %1 %2 button: %3", x, y, button)); 
    ret = super(x, y, button, Ctrl, Shift); 
    info (strfmt("ret: %1", ret)); 
}
```

## Method OnEnter

```xpp
private void OnEnter([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnEnter

sender  

<!-- -->

e  

## Method delete

Removes a string value from the combo box list.

```xpp
public void delete(str string)
```

### Parameters - delete

string  
The string value to remove from the combo box list.

### Examples - delete

The following example shows how to remove a string value from the combo box list.

```xpp
this.delete("Model 12357");
```

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

## Method add

Adds a string value to the combo box list.

```xpp
public void add(str string)
```

### Parameters - add

string  
The string value to add to the combo box list.

### Remarks - add

The string is added to the end of the list. If you want to put the string in a specific position in the list, use the insert method.

### Examples - add

The following example shows how to add a string to the combo box list.

```xpp
this.add("maple"); 
this.add("oak"); 
this.add("pine");
```

## Method prefColumnSize

Specifies the preferred column width and height for the form combo box control.

```xpp
public void prefColumnSize(int width, int height)
```

### Parameters - prefColumnSize

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Examples - prefColumnSize

The following example shows how to set the preferred width and height of a combo box control.

```xpp
// The nWidth and nHeight variables were  
// previously assigned as int variables. 
// The ctrl variable was previously assigned 
// as a FormComboBoxControl variable. 
ctrl.prefColumnSize( nWidth, nHeight);
```

## Method OnValidating

```xpp
private void OnValidating([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnValidating

sender  

<!-- -->

e  

## Method undo

```xpp
public void undo()
```

## Method jumpRef

```xpp
public void jumpRef()
```

## Method OnSelectionChanged

```xpp
private void OnSelectionChanged([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnSelectionChanged

sender  

<!-- -->

e  

## Method endUpdate

```xpp
public void endUpdate()
```

## Method lostFocus

Indicates that the control has lost focus.

```xpp
public void lostFocus()
```

## Method mouseLeave

Indicates that the mouse pointer has left the control.

```xpp
public void mouseLeave()
```

## Method OnLookup

```xpp
private void OnLookup([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLookup

sender  

<!-- -->

e  

## Method cut

Cuts the contents of the control.

```xpp
public void cut()
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

## Method OnLeaving

```xpp
private void OnLeaving([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLeaving

sender  

<!-- -->

e  

## Method setDropSize

```xpp
public void setDropSize([int lines])
```

### Parameters - setDropSize

lines  

