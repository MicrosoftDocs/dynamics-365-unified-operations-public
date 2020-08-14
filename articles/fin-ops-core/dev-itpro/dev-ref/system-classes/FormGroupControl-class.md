---
title: FormGroupControl class
description: This topic describes the FormGroupControl class.
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

# Class FormGroupControl

[!include [banner](../../includes/banner.md)]


```xpp
class FormGroupControl extends FormControl
```

## Remarks

## Examples

## Methods

| Method                                                                                                              | Description                                                                                                                                                                                         |
|---------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            | Adds a form control to a form group control.                                                                                                                                                        |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |                                                                                                                                                                                                     |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) | Adds a table field.                                                                                                                                                                                 |
| public boolean alignChild(\[boolean value\])                                                                        | Sets or returns a Boolean value that indicates whether a form group control is aligned in the same manner as other controls in a form.                                                              |
| public boolean alignChildren(\[boolean value\])                                                                     | Sets or returns a Boolean value that indicates whether the child controls are aligned.                                                                                                              |
| public boolean alignControl(\[boolean value\])                                                                      | Determines whether the control is aligned with other controls.                                                                                                                                      |
| public boolean allowEdit(\[boolean value\])                                                                         | Determines whether the user can modify the contents of the control.                                                                                                                                 |
| public boolean allowSysSetup()                                                                                      | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                                                 |
| public int allowUserSetup(\[int value\])                                                                            | Sets or gets the level of modification that can be performed for a form group control.                                                                                                              |
| public int arrangeGuide(\[int value\])                                                                              |                                                                                                                                                                                                     |
| public int arrangeMethod(\[int value\])                                                                             | Sets or returns an integer value that indicates how controls in a form group control are arranged.                                                                                                  |
| public int arrangeWhen(\[int value\])                                                                               | Sets or returns an integer value that specifies when the controls are arranged.                                                                                                                     |
| public boolean autoDataGroup(\[boolean value\])                                                                     | Sets or returns a Boolean value that specifies whether a form group control can contain only the fields in the data group that are specified for the control.                                       |
| public boolean autoDeclaration(\[boolean value\])                                                                   | Determines whether the system can declare a member variable that has the same name as the control.                                                                                                  |
| public int backgroundColor(\[int value\])                                                                           | Gets or sets the background color of the control.                                                                                                                                                   |
| public Image backgroundImage(\[Image image\], \[int drawMode\])                                                     | Specifies the background image for a form group control.                                                                                                                                            |
| public int backStyle(\[int value\])                                                                                 | Determines whether the control background can be transparent.                                                                                                                                       |
| public int beginDrag(int x, int y)                                                                                  | Is called when the user starts to move a form group control.                                                                                                                                        |
| public int bold(\[int value\])                                                                                      | Gets or sets the weight of font that is used to display text in the control.                                                                                                                        |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                           | Sets or returns the bottom margin of a form group control in pixels and specifies whether the margin is automatically adjusted.                                                                     |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                                 | Sets or returns an AutoMode enumeration value that indicates whether the bottom margin is automatically adjusted.                                                                                   |
| public int bottomMarginValue(\[int value\])                                                                         | Sets or returns the bottom margin of a form group control in pixels.                                                                                                                                |
| public boolean breakable(\[boolean value\])                                                                         |                                                                                                                                                                                                     |
| public container calcControlSize(int chars, int lines)                                                              | Calculates the size of a form group control, based on the number of characters and the number of lines.                                                                                             |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                               | Indicates whether a table field can be added.                                                                                                                                                       |
| public boolean canContain(FormControl control)                                                                      | Specifies whether a form group control can contain the specified form control.                                                                                                                      |
| public str caption(\[str value\])                                                                                   | Gets or set the caption of the control.                                                                                                                                                             |
| public int characterSet(\[int value\])                                                                              | Gets or sets the character set of the font.                                                                                                                                                         |
| public int colorScheme(\[int value\])                                                                               | Gets or sets the color scheme of the control.                                                                                                                                                       |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                             | Sets or returns the number of columns in a form group control in pixels, and specifies whether the number is automatically adjusted.                                                                |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                                | Sets or returns a value that indicates whether the number of columns in a form group control is fixed, or whether it is automatically adjusted based on other form settings, such as the form size. |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                            | Sets or returns the amount of space between columns in a form group control in pixels and indicates whether the space is automatically adjusted based on other form settings, such the font size.   |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                                  | Sets or returns an AutoMode enumeration value that indicates whether the amount of space between columns in a form group control is automatically adjusted.                                         |
| public int columnspaceValue(\[int value\])                                                                          | Sets or returns the amount of space between columns in a form group control in pixels.                                                                                                              |
| public int columnsValue(\[int value\])                                                                              | Sets or returns the number of columns in a form group control.                                                                                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                            | Gets or sets the configuration key that is assigned to the control.                                                                                                                                 |
| public List configurationKeyEx()                                                                                    | Retrieves a list that contains the IDs of configuration keys that are activated for a form group control.                                                                                           |
| public boolean contains(FormControl control)                                                                        | Specifies whether a form group control contains a specified form control.                                                                                                                           |
| public int controlCount()                                                                                           | Returns the number of controls in a form group control.                                                                                                                                             |
| public FormControl controlNum(int controlNo)                                                                        | Returns a FormControl object for a specified control in a form group control.                                                                                                                       |
| public str countryRegionCodes(\[str value\])                                                                        | Gets or sets the comma-separated list of country/region codes for the control.                                                                                                                      |
| public FieldId countryRegionContextField(\[FieldId value\])                                                         |                                                                                                                                                                                                     |
| public str dataGroup(\[str value\])                                                                                 | Sets or returns a data group for a form group control.                                                                                                                                              |
| public str dataRelationPath(\[str value\])                                                                          | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                                                       |
| public int dataSource(\[AnyType value\])                                                                            | Gets or sets a data source that will be used by the control or the form.                                                                                                                            |
| public int displayTarget(\[int value\])                                                                             | Gets or sets the value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both.                             |
| public int dragDrop(\[int value\])                                                                                  | Determines whether drag-and-drop operations are enabled or disabled for the control.                                                                                                                |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Is called when an object is dragged over the bounds of a form group control.                                                                                                                        |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                                                    |
| public str dragText()                                                                                               | Retrieves the text that is displayed when the form control is dragged.                                                                                                                              |
| public boolean enableChilds(\[boolean enable\])                                                                     | Specifies whether the child controls are enabled for a form group control.                                                                                                                          |
| public boolean enabled(\[boolean value\])                                                                           | Determines whether the object is enabled or disabled.                                                                                                                                               |
| public boolean expand(\[boolean expand\])                                                                           | Specifies whether a form group control is expanded.                                                                                                                                                 |
| public str font(\[str value\])                                                                                      | Gets or sets the name of the font that is used for text in a control.                                                                                                                               |
| public int fontSize(\[int value\])                                                                                  | Gets or sets the font size to use for text in a control.                                                                                                                                            |
| public int frameOptionButton(\[int value\])                                                                         | Sets or returns the option button for a form group control.                                                                                                                                         |
| public int framePosition(\[int value\])                                                                             | Sets or returns the location of the frame for a form group control.                                                                                                                                 |
| public int frameType(\[int value\])                                                                                 | Sets or returns the frame style for a form group control.                                                                                                                                           |
| public boolean hasChanged(\[boolean val\])                                                                          | Sets or returns a Boolean value that indicates whether the contents of a form group control have changed.                                                                                           |
| public boolean hasUserSetting()                                                                                     | Indicates whether the control has custom user settings.                                                                                                                                             |
| public int height(int value, \[int mode\])                                                                          | Gets or sets the height of the control.                                                                                                                                                             |
| public int heightMode(\[int value\])                                                                                | Gets or sets a calculation mode for the height of the control.                                                                                                                                      |
| public int heightValue(\[int value\])                                                                               | Gets or sets the height of the control.                                                                                                                                                             |
| public str helpField()                                                                                              | Returns the Help text that is displayed in the status bar when a form group control is selected.                                                                                                    |
| public str helpText(\[str value\])                                                                                  | Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.                                                                                     |
| public boolean hideIfEmpty(\[boolean value\])                                                                       | Sets or gets a Boolean value that indicates whether a form group control is visible when the controls in the group are not visible.                                                                 |
| public str hierarchyParent(\[str value\])                                                                           | Gets or sets the HierarchyParent property value of the control.                                                                                                                                     |
| public int hWnd()                                                                                                   | Returns a handle for a form group control.                                                                                                                                                          |
| public boolean isContainer()                                                                                        | Indicates whether a form group control is a container.                                                                                                                                              |
| public boolean isDisplayed()                                                                                        | Indicates whether a form group control is displayed.                                                                                                                                                |
| public boolean isRestricted()                                                                                       | Retrieves a value that indicates whether the control is restricted.                                                                                                                                 |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            | Returns a value that indicates whether the control allows for the specified level of customization.                                                                                                 |
| public boolean italic(\[boolean value\])                                                                            | Sets or returns a Boolean value that indicates whether the text for a form group control is italic.                                                                                                 |
| public int labelBold(\[int value\])                                                                                 | Sets or returns the font weight of the label text for a form group control.                                                                                                                         |
| public int labelCharacterSet(\[int value\])                                                                         | Sets or returns the character set of the font for the label text for a form group control.                                                                                                          |
| public str labelFont(\[str value\])                                                                                 | Sets or returns the font for the label text for a form group control.                                                                                                                               |
| public int labelFontSize(\[int value\])                                                                             | Sets or returns the font size of the label text for a form group control.                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                                                                       | Sets or returns a Boolean data type that indicates whether the label text for a form group control is italic.                                                                                       |
| public boolean labelUnderline(\[boolean value\])                                                                    | Sets or returns a Boolean data type that indicates whether the label text for a form group control is underlined.                                                                                   |
| public boolean leave()                                                                                              | Is called when the user moves the mouse pointer out of a form group control.                                                                                                                        |
| public int left(int value, \[int mode\])                                                                            | Sets or returns the horizontal position of a form group control in pixels and specifies how the position is calculated.                                                                             |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                             | Sets or returns the size of the left margin for a form group control in pixels and specifies whether the size is automatically adjusted.                                                            |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                                   | Sets or returns a value that indicates whether the size of the left margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.        |
| public int leftMarginValue(\[int value\])                                                                           | Sets or returns the size of the left margin for a form group control in pixels.                                                                                                                     |
| public int leftMode(\[int value\])                                                                                  | Sets or returns a value that indicates how the horizontal position of a form group control is calculated.                                                                                           |
| public int leftValue(\[int value\])                                                                                 | Sets or returns the horizontal position of a form group control in pixels.                                                                                                                          |
| public boolean markAsUserAdd(\[boolean value\])                                                                     | Marks or unmarks the control as a user-added control.                                                                                                                                               |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                     | Is called when the user double-clicks a form group control.                                                                                                                                         |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user presses the mouse button in a form group control.                                                                                                                           |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user moves the mouse pointer over a form group control.                                                                                                                          |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                           | Is called when the user releases the mouse button over a form group control.                                                                                                                        |
| public int moveControl(int controlId, \[int insertAfterId\])                                                        | Moves a specified control.                                                                                                                                                                          |
| public str name(\[str value\])                                                                                      | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.                                                             |
| public int neededPermission(\[int value\])                                                                          |                                                                                                                                                                                                     |
| public int optionValue(\[int value\])                                                                               | Sets or returns the value for the option button that is associated with a form group control.                                                                                                       |
| public container SysObsoleteAttribute()                                                                             |                                                                                                                                                                                                     |
| public FormControl parentControl()                                                                                  | Retrieves the parent control for the control.                                                                                                                                                       |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                            | Sets or returns the size of the right margin for a form group control in pixels and specifies whether the size is automatically adjusted.                                                           |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                                  | Sets or returns a value that indicates whether the size of the right margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.       |
| public int rightMarginValue(\[int value\])                                                                          | Sets or returns the size of the right margin for a form group control in pixels.                                                                                                                    |
| public boolean saveFilter(\[boolean value\])                                                                        |                                                                                                                                                                                                     |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                           | Sets or returns the security key ID for a form group control.                                                                                                                                       |
| public int showContextMenu(int menuHandle)                                                                          | Shows a shortcut menu for a form group control.                                                                                                                                                     |
| public boolean skip(\[boolean value\])                                                                              | Sets or returns a Boolean value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                                             |
| public int sort(\[SortOrder sortDirection\])                                                                        | Sorts the controls that are contained in a form group control.                                                                                                                                      |
| public int style(\[int value\])                                                                                     |                                                                                                                                                                                                     |
| public str toolTip()                                                                                                | Returns the text string for the tooltip for a form group control.                                                                                                                                   |
| public int top(int value, \[int mode\])                                                                             | Sets or returns the vertical position of a form group control in pixels and specifies how the position is calculated.                                                                               |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                              | Sets or returns the top margin for a form group control in pixels and specifies whether the size is automatically adjusted.                                                                         |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                                    | Sets or returns a value that indicates whether the size of the top margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.         |
| public int topMarginValue(\[int value\])                                                                            |                                                                                                                                                                                                     |
| public int topMode(\[int value\])                                                                                   | Sets or returns a value that indicates how the vertical position of a form group control is calculated.                                                                                             |
| public int topValue(\[int value\])                                                                                  | Sets or returns the vertical position of a form group control in pixels.                                                                                                                            |
| public int type(\[int value\])                                                                                      |                                                                                                                                                                                                     |
| public boolean underline(\[boolean value\])                                                                         | Sets or returns the underline property for the text in the control.                                                                                                                                 |
| public boolean SysObsoleteAttribute(container data)                                                                 |                                                                                                                                                                                                     |
| public int userData(\[int value\])                                                                                  | Gets or sets the user data for the control.                                                                                                                                                         |
| public int userDataItem(\[int value\])                                                                              | Gets or sets the user data item for the control.                                                                                                                                                    |
| public int userDataItems(\[int value\])                                                                             | Gets or sets the number of user data items for the control.                                                                                                                                         |
| public int userDisable(\[int value\])                                                                               | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                                                 |
| public int userHeight(\[int value\])                                                                                | Gets or sets the custom user height for the control.                                                                                                                                                |
| public int userHide(\[int value\])                                                                                  | Sets or returns an integer data type that indicates whether a control is hidden from the user.                                                                                                      |
| public int userOrgContainer(\[int value\])                                                                          | Gets or sets the organization container for the control.                                                                                                                                            |
| public int userOrgSibling(\[int value\])                                                                            | Gets or sets the organization sibling for the control.                                                                                                                                              |
| public str userPromptText(\[str value\])                                                                            | Gets or sets the user label text for the control.                                                                                                                                                   |
| public int userSecurityLevel(\[int value\])                                                                         | Gets or sets the user security level for the control.                                                                                                                                               |
| public int userSkip(\[int value\])                                                                                  | Sets or returns an integer that indicates whether the form group control is skipped when the user presses the TAB key to move to controls.                                                          |
| public int userWidth(\[int value\])                                                                                 | Sets or returns an integer that indicates the width of a form group control in pixels.                                                                                                              |
| public boolean useUserLayout(\[boolean value\])                                                                     | Specifies whether to use the user-specified layout of a form group control.                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                        | Gets or sets the amount of space above and below a form group control in pixels, and specifies how the space is calculated.                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                              | Sets or returns a value that indicates how the amount of space above and below a form group control is calculated.                                                                                  |
| public int verticalSpacingValue(\[int value\])                                                                      | Gets or sets the amount of space above and below a form group control in pixels.                                                                                                                    |
| public int viewEditMode(\[int value\])                                                                              |                                                                                                                                                                                                     |
| public boolean visible(\[boolean value\])                                                                           | Gets or sets a Boolean data type that displays or hides a form group control.                                                                                                                       |
| public int width(int value, \[int mode\])                                                                           | Gets or sets the width of the control.                                                                                                                                                              |
| public int widthMode(\[int value\])                                                                                 | Gets or sets the calculation mode for the width of the control.                                                                                                                                     |
| public int widthValue(\[int value\])                                                                                | Gets or sets the width of the control.                                                                                                                                                              |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\])         |                                                                                                                                                                                                     |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                           | Is called when a user drops a form group control or an item in a form group control into a new position.                                                                                            |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                        |                                                                                                                                                                                                     |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                            |                                                                                                                                                                                                     |
| public void mouseLeave()                                                                                            | Is called when the user moves the mouse pointer away from the control.                                                                                                                              |
| public void context()                                                                                               | Is called when the user right-clicks a form group control.                                                                                                                                          |
| public void copy()                                                                                                  | Copies a form group control.                                                                                                                                                                        |
| public void cut()                                                                                                   | Cuts the contents of the control.                                                                                                                                                                   |
| public void paste()                                                                                                 | Pastes a form group control.                                                                                                                                                                        |
| public void arrange()                                                                                               |                                                                                                                                                                                                     |
| public void clicked()                                                                                               | Is called when a form group control is clicked by the user.                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                          |                                                                                                                                                                                                     |
| public void inputSearch(str searchStr)                                                                              | Is called when the user enters a search string in a bound control.                                                                                                                                  |
| public void resetUserSetting()                                                                                      | Resets the user settings for a form group control.                                                                                                                                                  |
| private void OnClicked(\[FormControl sender\], \[FormControlEventArgs e\])                                          |                                                                                                                                                                                                     |
| public void lostFocus()                                                                                             | Is called when the user brings a form group control out of focus.                                                                                                                                   |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                               | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                                                |
| public void endDrag()                                                                                               | Is called when the user has finished moving a form group control.                                                                                                                                   |
| public void jumpRef()                                                                                               | Is called when a user clicks the Go to the Main Table Form command on a control shortcut menu in a form group control.                                                                              |
| public void setFocus()                                                                                              | Sets the focus on the control.                                                                                                                                                                      |
| public void filter(\[str filterStr\])                                                                               | Is called when the user right-clicks a form group control and then clicks Filter By Selection.                                                                                                      |
| public void displayControl()                                                                                        | Displays a form group control.                                                                                                                                                                      |
| public void gotFocus()                                                                                              | Determines when the user brings a form group control into focus.                                                                                                                                    |
| public void prefColumnSize(int width, int height)                                                                   | Specifies the height and width of columns for a form group control.                                                                                                                                 |
| public void dragLeave()                                                                                             | Is called when the user drags an object out of the bounds of a form group control.                                                                                                                  |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                         |                                                                                                                                                                                                     |
| public void enter()                                                                                                 | Is called when the user moves focus to a form group control.                                                                                                                                        |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                       | Is called when the user moves the mouse pointer into the control area.                                                                                                                              |

## Method addControl

Adds a form control to a form group control.

```xpp
public FormControl addControl(FormControlType controlType, str controlName, [FormControl insertAfter])
```

### Parameters - addControl

controlType  
A value that indicates the position of the control; optional. The default value is nullNothingnullptrunita null reference (Nothing in Visual Basic).

<!-- -->

controlName  
A value that indicates the position of the control; optional. The default value is nullNothingnullptrunita null reference (Nothing in Visual Basic).

<!-- -->

insertAfter  
A value that indicates the position of the control; optional. The default value is nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Return Value - addControl

A FormControl object that configures form controls.

## Method addControlEx

```xpp
public FormControl addControlEx(str controlClass, str controlName, [FormControl insertAfter])
```

### Parameters - addControlEx

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

### Return Value - addControlEx

## Method addDataField

Adds a table field.

```xpp
public FormControl addDataField(int dataSourceId, FieldId fieldId, [FormControl insertAfter], [int arrayIndex])
```

### Parameters - addDataField

dataSourceId  

<!-- -->

fieldId  

<!-- -->

insertAfter  

<!-- -->

arrayIndex  

### Return Value - addDataField

A FormControl object that modifies a form control.

## Method alignChild

Sets or returns a Boolean value that indicates whether a form group control is aligned in the same manner as other controls in a form.

```xpp
public boolean alignChild([boolean value])
```

### Parameters - alignChild

value  
A Boolean value that indicates whether a form group control is aligned in the same manner as other controls in a form; optional.

### Return Value - alignChild

true if a control is aligned; otherwise, false.

## Method alignChildren

Sets or returns a Boolean value that indicates whether the child controls are aligned.

```xpp
public boolean alignChildren([boolean value])
```

### Parameters - alignChildren

value  
A Boolean value that indicates whether the child controls are aligned; optional.

### Return Value - alignChildren

true if the child controls are aligned; otherwise, false.

## Method alignControl

Determines whether the control is aligned with other controls.

```xpp
public boolean alignControl([boolean value])
```

### Parameters - alignControl

value  
A Boolean value that indicates whether a form group control is aligned with other controls.

### Return Value - alignControl

true if the control should be aligned; otherwise, false.

### Remarks - alignControl

The upper-left corner of the control is aligned based on the longest label.

## Method allowEdit

Determines whether the user can modify the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  
A Boolean value that indicates whether data can be modified; optional.

### Return Value - allowEdit

true if the control can be modified; otherwise, false.

### Remarks - allowEdit

If this property is set on a container control, modifications are disabled or enabled for all controls in the container.

## Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

```xpp
public boolean allowSysSetup()
```

### Return Value - allowSysSetup

true if the control is shown in the SysSetup form; otherwise, false.

## Method allowUserSetup

Sets or gets the level of modification that can be performed for a form group control.

```xpp
public int allowUserSetup([int value])
```

### Parameters - allowUserSetup

value  
An Integer data type that indicates the level of modification that can be performed; optional.

### Return Value - allowUserSetup

An integer value that indicates the level of modification that can be performed.

### Remarks - allowUserSetup

You can use a FormAllowUserSetup enumeration value for the value parameter.

## Method arrangeGuide

```xpp
public int arrangeGuide([int value])
```

### Parameters - arrangeGuide

value  

### Return Value - arrangeGuide

## Method arrangeMethod

Sets or returns an integer value that indicates how controls in a form group control are arranged.

```xpp
public int arrangeMethod([int value])
```

### Parameters - arrangeMethod

value  
An integer value that indicates how controls in a form group control are arranged; optional.

### Return Value - arrangeMethod

An integer value that indicates how controls in a form group control are arranged.

### Remarks - arrangeMethod

You can use an ArrangeMethod enumeration value for the \_value parameter.

## Method arrangeWhen

Sets or returns an integer value that specifies when the controls are arranged.

```xpp
public int arrangeWhen([int value])
```

### Parameters - arrangeWhen

value  
An integer value that specifies when the controls are arranged; optional.

### Return Value - arrangeWhen

An integer value that specifies when the controls are arranged.

## Method autoDataGroup

Sets or returns a Boolean value that specifies whether a form group control can contain only the fields in the data group that are specified for the control.

```xpp
public boolean autoDataGroup([boolean value])
```

### Parameters - autoDataGroup

value  
A Boolean data type that indicates whether a form group control can contain only fields in the data group; optional.

### Return Value - autoDataGroup

true if a form group control can contain only fields in the data group; otherwise, false.

### Remarks - autoDataGroup

You use the FormGroupControl.dataGroup method to set or return a data group for a form group control.

## Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  
A Boolean value that indicates whether the system declares a variable of the same name as a form group control; optional.

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
An Integer data type that specifies the background color; optional.

### Return Value - backgroundColor

An integer that contains a packed RGB color.

### Remarks - backgroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

## Method backgroundImage

Specifies the background image for a form group control.

```xpp
public Image backgroundImage([Image image], [int drawMode])
```

### Parameters - backgroundImage

image  
An Integer data type that specifies how the image is drawn; optional.

<!-- -->

drawMode  
An Integer data type that specifies how the image is drawn; optional.

### Return Value - backgroundImage

An Image object.

## Method backStyle

Determines whether the control background can be transparent.

```xpp
public int backStyle([int value])
```

### Parameters - backStyle

value  
An Integer data type that indicates the background style; optional.

### Return Value - backStyle

1 if the control background can be transparent; otherwise, 0.

## Method beginDrag

Is called when the user starts to move a form group control.

```xpp
public int beginDrag(int x, int y)
```

### Parameters - beginDrag

x  
An integer value that indicates the y-coordinate for the move event.

<!-- -->

y  
An integer value that indicates the y-coordinate for the move event.

### Return Value - beginDrag

0 (zero) if the event has been handled.

## Method bold

Gets or sets the weight of font that is used to display text in the control.

```xpp
public int bold([int value])
```

### Parameters - bold

value  
An integer value that specifies the font weight; optional.

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

## Method bottomMargin

Sets or returns the bottom margin of a form group control in pixels and specifies whether the margin is automatically adjusted.

```xpp
public int bottomMargin([int value], [AutoMode mode])
```

### Parameters - bottomMargin

value  
An AutoMode enumeration value that indicates whether the bottom margin is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

<!-- -->

mode  
An AutoMode enumeration value that indicates whether the bottom margin is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

### Return Value - bottomMargin

An Integer data type value that specifies the bottom margin in pixels.

## Method bottomMarginMode

Sets or returns an AutoMode enumeration value that indicates whether the bottom margin is automatically adjusted.

```xpp
public AutoMode bottomMarginMode([AutoMode mode])
```

### Parameters - bottomMarginMode

mode  
An AutoMode enumeration value that indicates whether the bottom margin is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

### Return Value - bottomMarginMode

AutoMode::Auto if the margin is automatically adjusted based on other form settings, such as the font size; otherwise, AutoMode::Fixed.

## Method bottomMarginValue

Sets or returns the bottom margin of a form group control in pixels.

```xpp
public int bottomMarginValue([int value])
```

### Parameters - bottomMarginValue

value  
An Integer data type that specifies the bottom margin in pixels; optional.

### Return Value - bottomMarginValue

An Integer data type value that specifies the bottom margin in pixels.

## Method breakable

```xpp
public boolean breakable([boolean value])
```

### Parameters - breakable

value  

### Return Value - breakable

## Method calcControlSize

Calculates the size of a form group control, based on the number of characters and the number of lines.

```xpp
public container calcControlSize(int chars, int lines)
```

### Parameters - calcControlSize

chars  
An Integer data type that specifies the number of lines.

<!-- -->

lines  
An Integer data type that specifies the number of lines.

### Return Value - calcControlSize

A Container data type value that specifies the size of a form group control.

## Method canAddDataField

Indicates whether a table field can be added.

```xpp
public boolean canAddDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])
```

### Parameters - canAddDataField

dataSourceId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

### Return Value - canAddDataField

true if a table field can be added; otherwise, false.

## Method canContain

Specifies whether a form group control can contain the specified form control.

```xpp
public boolean canContain(FormControl control)
```

### Parameters - canContain

control  
A FormControl object that specifies a form control.

### Return Value - canContain

true if a form group control can contain the specified form control; otherwise, false.

## Method caption

Gets or set the caption of the control.

```xpp
public str caption([str value])
```

### Parameters - caption

value  
A String data type that specifies the caption text; optional.

### Return Value - caption

The string that is used as the caption of the control.

## Method characterSet

Gets or sets the character set of the font.

```xpp
public int characterSet([int value])
```

### Parameters - characterSet

value  
An Integer data type that specifies the character set for the text font; optional.

### Return Value - characterSet

An integer value that indicates the character set of the font.

### Remarks - characterSet

The values for the integer that is returned indicate the character set, as shown in the following table.

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

The value that the default character is set to depends on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the [MSDN website](https://go.microsoft.com/fwlink/?LinkID=85972).

## Method colorScheme

Gets or sets the color scheme of the control.

```xpp
public int colorScheme([int value])
```

### Parameters - colorScheme

value  
An Integer data type that specifies the color palette for a form group control; optional.

### Return Value - colorScheme

An integer between 0 (zero) and 2, inclusive.

### Remarks - colorScheme

The color scheme is defined according to the following table.

| Value | Style                  |
|-------|------------------------|
| 0     | Default.               |
| 1     | The Windows palette.   |
| 2     | The true-color scheme. |

## Method columns

Sets or returns the number of columns in a form group control in pixels, and specifies whether the number is automatically adjusted.

```xpp
public int columns([int value], [ColumnsMode mode])
```

### Parameters - columns

value  
An AutoMode enumeration value that specifies whether the number of columns is fixed, or whether it is automatically adjusted based on other form settings, such as the form size.

<!-- -->

mode  
An AutoMode enumeration value that specifies whether the number of columns is fixed, or whether it is automatically adjusted based on other form settings, such as the form size.

### Return Value - columns

An integer value that specifies the number of columns in a form group control in pixels.

## Method columnsMode

Sets or returns a value that indicates whether the number of columns in a form group control is fixed, or whether it is automatically adjusted based on other form settings, such as the form size.

```xpp
public ColumnsMode columnsMode([ColumnsMode mode])
```

### Parameters - columnsMode

mode  
An AutoMode enumeration value that specifies whether the number of columns is fixed, or whether it is automatically adjusted based on other form settings, such as the form size; optional.

### Return Value - columnsMode

Automode::Auto if the number of columns is automatically adjusted; otherwise, Automode::Fixed.

## Method columnspace

Sets or returns the amount of space between columns in a form group control in pixels and indicates whether the space is automatically adjusted based on other form settings, such the font size.

```xpp
public int columnspace([int value], [AutoMode mode])
```

### Parameters - columnspace

value  
An AutoMode enumeration value that indicates whether the amount of space between columns is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

<!-- -->

mode  
An AutoMode enumeration value that indicates whether the amount of space between columns is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

### Return Value - columnspace

An integer value that specifies the space between columns in a form group control in pixels.

## Method columnspaceMode

Sets or returns an AutoMode enumeration value that indicates whether the amount of space between columns in a form group control is automatically adjusted.

```xpp
public AutoMode columnspaceMode([AutoMode mode])
```

### Parameters - columnspaceMode

mode  
An AutoMode enumeration value that indicates whether the amount of space between columns is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

### Return Value - columnspaceMode

AutoMode::Auto if the amount of space is automatically adjusted; otherwise, AutoMode::Fixed.

## Method columnspaceValue

Sets or returns the amount of space between columns in a form group control in pixels.

```xpp
public int columnspaceValue([int value])
```

### Parameters - columnspaceValue

value  
An Integer data type that specifies the amount of space between columns in a form group control in pixels; optional.

### Return Value - columnspaceValue

An integer value that specifies the amount of space between columns in a form group control in pixels.

## Method columnsValue

Sets or returns the number of columns in a form group control.

```xpp
public int columnsValue([int value])
```

### Parameters - columnsValue

value  
An Integer data type that specifies the number of columns in a form group control; optional.

### Return Value - columnsValue

An Integer data type value that specifies the number of columns in a form group control.

## Method configurationKey

Gets or sets the configuration key that is assigned to the control.

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  
A configurationKeyId system data type that specifies the configuration key ID; optional.

### Return Value - configurationKey

The identifier of the configuration key that is assigned to the control.

### Remarks - configurationKey

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

## Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are activated for a form group control.

```xpp
public List configurationKeyEx()
```

### Return Value - configurationKeyEx

A List object that contains the IDs of configuration keys that are activated for a form group control.

### Remarks - configurationKeyEx

The list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. In addition, the returned list contains any configuration key IDs that are applied to the extended data type.

## Method contains

Specifies whether a form group control contains a specified form control.

```xpp
public boolean contains(FormControl control)
```

### Parameters - contains

control  
A FormControl object that specifies a form control.

### Return Value - contains

true if a form group control contains the specified form control; otherwise, false.

## Method controlCount

Returns the number of controls in a form group control.

```xpp
public int controlCount()
```

### Return Value - controlCount

An Integer data type value that specifies the number of controls in a form group control.

### Remarks - controlCount

You can add a control to a form group control by using the FormGroupControl.addControl method.

## Method controlNum

Returns a FormControl object for a specified control in a form group control.

```xpp
public FormControl controlNum(int controlNo)
```

### Parameters - controlNum

controlNo  
An Integer data type that specifies a control in a form group control.

### Return Value - controlNum

A FormControl object that can be used to modify and provide information about a form control.

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

## Method dataGroup

Sets or returns a data group for a form group control.

```xpp
public str dataGroup([str value])
```

### Parameters - dataGroup

value  
A String data type that specifies the data group; optional.

### Return Value - dataGroup

A String data type value that specifies the data group.

### Remarks - dataGroup

A data group corresponds to a field group on a table that is a data source for the form.

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

Gets or sets a data source that will be used by the control or the form.

```xpp
public int dataSource([AnyType value])
```

### Parameters - dataSource

value  

### Return Value - dataSource

The identifier of the data source that will be used.

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

### Remarks - dragDrop

You use the FormGroupControl.dragLeave and FormGroupControl.dragOver methods to specify the behavior. You can pass a value of true or false for the value parameter.

## Method dragOver

Is called when an object is dragged over the bounds of a form group control.

```xpp
public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - dragOver

dragSource  
An Integer data type that indicates the y-coordinate of the object position.

<!-- -->

dragMode  
An Integer data type that indicates the y-coordinate of the object position.

<!-- -->

x  
An Integer data type that indicates the y-coordinate of the object position.

<!-- -->

y  
An Integer data type that indicates the y-coordinate of the object position.

### Return Value - dragOver

A FormDrag system enumeration value that indicates whether the object is moved, copied, or not moved to a specified position.

### Remarks - dragOver

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking dragOver. For information about best practices for forms and code, see No Code in Forms.

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

## Method enableChilds

Specifies whether the child controls are enabled for a form group control.

```xpp
public boolean enableChilds([boolean enable])
```

### Parameters - enableChilds

enable  
A Boolean value that indicates whether the child controls are enabled; optional.

### Return Value - enableChilds

true if the child controls are enabled; otherwise, false.

## Method enabled

Determines whether the object is enabled or disabled.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  
A Boolean value that indicates whether a form group control is enabled; optional.

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property lets you enable or disable controls at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message that provides read-only information.

## Method expand

Specifies whether a form group control is expanded.

```xpp
public boolean expand([boolean expand])
```

### Parameters - expand

expand  
A Boolean value that indicates whether a form group control is expanded; optional.

### Return Value - expand

true if a form group control is expanded; otherwise, false.

## Method font

Gets or sets the name of the font that is used for text in a control.

```xpp
public str font([str value])
```

### Parameters - font

value  
A String data type that indicates the font for text in a form group control; optional.

### Return Value - font

The name of the font that should be used, such as Tahoma or Verdana.

## Method fontSize

Gets or sets the font size to use for text in a control.

```xpp
public int fontSize([int value])
```

### Parameters - fontSize

value  
An integer value that indicates the font size in points for text in a form group control; optional.

### Return Value - fontSize

The height of the font in points.

## Method frameOptionButton

Sets or returns the option button for a form group control.

```xpp
public int frameOptionButton([int value])
```

### Parameters - frameOptionButton

value  
An Integer data type that specifies the type of option button; optional.

### Return Value - frameOptionButton

An integer value that specifies the type of option button.

### Remarks - frameOptionButton

You can use a FormFrameOptionButton enumeration value for the value parameter.

## Method framePosition

Sets or returns the location of the frame for a form group control.

```xpp
public int framePosition([int value])
```

### Parameters - framePosition

value  
An integer value that specifies the location of the frame; optional.

### Return Value - framePosition

An integer value that specifies the location of the frame.

## Method frameType

Sets or returns the frame style for a form group control.

```xpp
public int frameType([int value])
```

### Parameters - frameType

value  
An integer value that indicates the frame style for a form group control; optional.

### Return Value - frameType

An integer value that indicates the frame style for a form group control.

### Remarks - frameType

You can use a FormFrameType enumeration value for the value parameter.

## Method hasChanged

Sets or returns a Boolean value that indicates whether the contents of a form group control have changed.

```xpp
public boolean hasChanged([boolean val])
```

### Parameters - hasChanged

val  
A Boolean value that indicates whether the contents of a form group control have changed; optional.

### Return Value - hasChanged

true if the contents have changed; otherwise, false.

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

The height and the height calculation mode can be set separately.

### Examples - height

The following example shows a call to the height method to the set the control height to 120 pixels.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.height(120, -1); 
}
```

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

The following example shows a call to the heightMode method to adjust the control height, based on an exact pixel value.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.heightMode(-1); 
    formGroupControl.heightValue(120); 
}
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

The following example shows a call to the heightValue method that sets the height to 5 pixels.

```xpp
static void createForm(Args _args) 
{ 
   Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.heightMode(-1); 
    formGroupControl.heightValue(120); 
}
```

## Method helpField

Returns the Help text that is displayed in the status bar when a form group control is selected.

```xpp
public str helpField()
```

### Return Value - helpField

A String data type value that contains the Help text.

## Method helpText

Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  
A String data type value that contains the Help text.

### Return Value - helpText

The string that should be displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

## Method hideIfEmpty

Sets or gets a Boolean value that indicates whether a form group control is visible when the controls in the group are not visible.

```xpp
public boolean hideIfEmpty([boolean value])
```

### Parameters - hideIfEmpty

value  
A Boolean value that indicates whether a form group control is visible; optional.

### Return Value - hideIfEmpty

true if the form group control is not visible; otherwise, false.

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

Returns a handle for a form group control.

```xpp
public int hWnd()
```

### Return Value - hWnd

An integer value that specifies the handle.

## Method isContainer

Indicates whether a form group control is a container.

```xpp
public boolean isContainer()
```

### Return Value - isContainer

true if a form group control is a container; otherwise, false.

## Method isDisplayed

Indicates whether a form group control is displayed.

```xpp
public boolean isDisplayed()
```

### Return Value - isDisplayed

true if a form group is displayed; otherwise, false.

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

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false. For this method to return true, the AllowUserSetup property for the design and for all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

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

Sets or returns a Boolean value that indicates whether the text for a form group control is italic.

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  
A Boolean value that indicates whether the text for a form group control is italic; optional.

### Return Value - italic

true if the text is italic; otherwise, false.

## Method labelBold

Sets or returns the font weight of the label text for a form group control.

```xpp
public int labelBold([int value])
```

### Parameters - labelBold

value  
An integer value that specifies the font weight of the label text; optional.

### Return Value - labelBold

An integer value that specifies the font weight of the label text.

### Remarks - labelBold

For more information about possible values for the value parameter and return value, see the bold method.

## Method labelCharacterSet

Sets or returns the character set of the font for the label text for a form group control.

```xpp
public int labelCharacterSet([int value])
```

### Parameters - labelCharacterSet

value  
An integer value that specifies the character set of the font for the label text; optional.

### Return Value - labelCharacterSet

An Integer data type value that specifies the character set of the font for the label text.

### Remarks - labelCharacterSet

A character set is a group of alphabetical, numeric, and other characters that have some relationship in common. For example, a character set might be used for a specific country/region or language. For a list of possible values for the value parameter, see the characterSet method. For a list of possible return values, see the characterSet method.

## Method labelFont

Sets or returns the font for the label text for a form group control.

```xpp
public str labelFont([str value])
```

### Parameters - labelFont

value  
A String data type that specifies the font for the label text; optional.

### Return Value - labelFont

A String data type value that specifies the font for the label text.

## Method labelFontSize

Sets or returns the font size of the label text for a form group control.

```xpp
public int labelFontSize([int value])
```

### Parameters - labelFontSize

value  
An integer value that specifies the font size of the label text; optional.

### Return Value - labelFontSize

An integer value that specifies the font size of the label text.

## Method labelItalic

Sets or returns a Boolean data type that indicates whether the label text for a form group control is italic.

```xpp
public boolean labelItalic([boolean value])
```

### Parameters - labelItalic

value  
A Boolean value that indicates whether the label text is italic; optional.

### Return Value - labelItalic

true if the label text is italic; otherwise, false.

## Method labelUnderline

Sets or returns a Boolean data type that indicates whether the label text for a form group control is underlined.

```xpp
public boolean labelUnderline([boolean value])
```

### Parameters - labelUnderline

value  
A Boolean value that indicates whether the label text is underlined; optional.

### Return Value - labelUnderline

true if the label text is underlined; otherwise, false.

## Method leave

Is called when the user moves the mouse pointer out of a form group control.

```xpp
public boolean leave()
```

### Return Value - leave

true if the mouse pointer is moved out of a form group control; otherwise, false.

### Remarks - leave

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking leave. For information about best practices for forms and code, see No Code in Forms.

## Method left

Sets or returns the horizontal position of a form group control in pixels and specifies how the position is calculated.

```xpp
public int left(int value, [int mode])
```

### Parameters - left

value  
An integer value that indicates how the position is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the position is calculated; optional.

### Return Value - left

An integer value that indicates the horizontal position of a form group control in pixels.

### Remarks - left

The mode parameter can be one of the following values:

-   -1 (default) � Use Exact mode, where the value of the value parameter is used exactly.
-   A FormLeft enumeration value.

### Examples - left

The following example shows a call to the left method that sets the horizontal position to 50 pixels.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.left(50,-1); 
}
```

## Method leftMargin

Sets or returns the size of the left margin for a form group control in pixels and specifies whether the size is automatically adjusted.

```xpp
public int leftMargin([int value], [AutoMode mode])
```

### Parameters - leftMargin

value  
An AutoMode enumeration value that specifies whether the size of the left margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

<!-- -->

mode  
An AutoMode enumeration value that specifies whether the size of the left margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

### Return Value - leftMargin

An integer value that specifies the size of the left margin for a form group control in pixels.

## Method leftMarginMode

Sets or returns a value that indicates whether the size of the left margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.

```xpp
public AutoMode leftMarginMode([AutoMode mode])
```

### Parameters - leftMarginMode

mode  
An AutoMode enumeration value that specifies whether the size of the left margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

### Return Value - leftMarginMode

Automode::Auto if the size of the left margin is automatically adjusted; otherwise, Automode::Fixed.

## Method leftMarginValue

Sets or returns the size of the left margin for a form group control in pixels.

```xpp
public int leftMarginValue([int value])
```

### Parameters - leftMarginValue

value  
An integer value that specifies the size of the left margin for a form group control in pixels; optional.

### Return Value - leftMarginValue

An integer value that specifies the size of the left margin for a form group control in pixels.

## Method leftMode

Sets or returns a value that indicates how the horizontal position of a form group control is calculated.

```xpp
public int leftMode([int value])
```

### Parameters - leftMode

value  
An Integer data type that indicates how the horizontal position is calculated; optional.

### Return Value - leftMode

An Integer data type value that indicates how the horizontal position is calculated: -1 for an exact pixel value, or a FormLeft enumeration value.

### Examples - leftMode

The following example shows a call to the leftMode method that calculates the horizontal position of a form group control, based on an exact pixel value.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.leftMode(-1); 
    formGroupControl.leftValue(50); 
}
```

## Method leftValue

Sets or returns the horizontal position of a form group control in pixels.

```xpp
public int leftValue([int value])
```

### Parameters - leftValue

value  
An integer value that indicates the horizontal position in pixels; optional.

### Return Value - leftValue

An integer value that indicates the horizontal position in pixels.

### Remarks - leftValue

The horizontal position is not changed unless the left mode is set for an exact pixel value.

### Examples - leftValue

The following example shows a call to the leftValue method that sets the horizontal position to 50 pixels.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    //C reate the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.leftMode(-1); 
    formGroupControl.leftValue(50); 
}
```

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

Is called when the user double-clicks a form group control.

```xpp
public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseDblClick

x  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that specifies whether the SHIFT key is down.

### Return Value - mouseDblClick

0 (zero) if the event has been handled.

### Remarks - mouseDblClick

Typically, when this method is overridden, the return value from a call to the super method is returned. The following are the possible values for the button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseDblClick. For information about best practices for forms and code, see No Code in Forms.

## Method mouseDown

Is called when the user presses the mouse button in a form group control.

```xpp
public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseDown

x  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that specifies whether the SHIFT key is down.

### Return Value - mouseDown

0 (zero) if the event has been handled.

### Remarks - mouseDown

Typically, when this method is overridden, the return value from a call to the super method is returned. The following are the possible values for the button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseDown. For information about best practices for forms and code, see No Code in Forms.

## Method mouseMove

Is called when the user moves the mouse pointer over a form group control.

```xpp
public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseMove

x  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that specifies whether the SHIFT key is down.

### Return Value - mouseMove

0 (zero) if the event has been handled.

### Remarks - mouseMove

Typically, when this method is overridden, the return value from a call to the super method is returned. The following are the possible values for the \_button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseMove. For information about best practices for forms and code, see No Code in Forms.

## Method mouseUp

Is called when the user releases the mouse button over a form group control.

```xpp
public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseUp

x  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that specifies whether the SHIFT key is down.

### Return Value - mouseUp

0 (zero) if the event has been handled.

### Remarks - mouseUp

Typically, when this method is overridden, the return value from a call to the super method is returned. The following are the possible values for the \_button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseUp. For information about best practices for forms and code, see No Code in Forms.

## Method moveControl

Moves a specified control.

```xpp
public int moveControl(int controlId, [int insertAfterId])
```

### Parameters - moveControl

controlId  
An integer value that indicates which control the specified control is inserted after; optional.

<!-- -->

insertAfterId  
An integer value that indicates which control the specified control is inserted after; optional.

### Return Value - moveControl

An Integer data type value that specifies the control ID.

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

## Method optionValue

Sets or returns the value for the option button that is associated with a form group control.

```xpp
public int optionValue([int value])
```

### Parameters - optionValue

value  
An integer value that specifies the value for the option button; optional.

### Return Value - optionValue

An integer value that specifies the value for the option button.

### Remarks - optionValue

Use the FormGroupControl.frameOptionButton method to set or return the option button for a form group control.

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

## Method rightMargin

Sets or returns the size of the right margin for a form group control in pixels and specifies whether the size is automatically adjusted.

```xpp
public int rightMargin([int value], [AutoMode mode])
```

### Parameters - rightMargin

value  
An AutoMode enumeration value that specifies whether the size of the right margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

<!-- -->

mode  
An AutoMode enumeration value that specifies whether the size of the right margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

### Return Value - rightMargin

An integer value that specifies the size of the right margin for a form group control in pixels.

## Method rightMarginMode

Sets or returns a value that indicates whether the size of the right margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.

```xpp
public AutoMode rightMarginMode([AutoMode mode])
```

### Parameters - rightMarginMode

mode  
An AutoMode enumeration value that specifies whether the size of the right margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

### Return Value - rightMarginMode

An Automode enumeration value that specifies whether the size of the right margin is fixed, or whether it is automatically adjusted: Auto if the size of the right margin is automatically adjusted; otherwise, Fixed.

## Method rightMarginValue

Sets or returns the size of the right margin for a form group control in pixels.

```xpp
public int rightMarginValue([int value])
```

### Parameters - rightMarginValue

value  
An integer value that specifies the size of the right margin for a form group control in pixels; optional.

### Return Value - rightMarginValue

An integer value that specifies the size of the right margin for a form group control in pixels.

## Method saveFilter

```xpp
public boolean saveFilter([boolean value])
```

### Parameters - saveFilter

value  

### Return Value - saveFilter

## Method securityKey

Sets or returns the security key ID for a form group control.

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  
A securityKeyId data type that contains the ID; optional.

### Return Value - securityKey

A securityKeyId data type value that contains the ID.

## Method showContextMenu

Shows a shortcut menu for a form group control.

```xpp
public int showContextMenu(int menuHandle)
```

### Parameters - showContextMenu

menuHandle  
An integer value that specifies the handle for the shortcut menu.

### Return Value - showContextMenu

An integer value that specifies the selection of the user.

## Method skip

Sets or returns a Boolean value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  
A Boolean value that indicates whether the control is skipped; optional.

### Return Value - skip

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

## Method sort

Sorts the controls that are contained in a form group control.

```xpp
public int sort([SortOrder sortDirection])
```

### Parameters - sort

sortDirection  
A system enumeration value that indicates the sort order for controls; optional.

### Return Value - sort

An integer value that contains the sort order.

## Method style

```xpp
public int style([int value])
```

### Parameters - style

value  

### Return Value - style

## Method toolTip

Returns the text string for the tooltip for a form group control.

```xpp
public str toolTip()
```

### Return Value - toolTip

A string value that contains the text for the tooltip.

## Method top

Sets or returns the vertical position of a form group control in pixels and specifies how the position is calculated.

```xpp
public int top(int value, [int mode])
```

### Parameters - top

value  
An integer value that indicates how the vertical position is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the vertical position is calculated; optional.

### Return Value - top

An integer value that indicates the vertical position of a form group control in pixels.

### Remarks - top

The mode parameter can be one of the following values:

-   -1 (default) � Use Exact mode, where the value of the value parameter is used exactly.
-   A FormTop enumeration value.

### Examples - top

The following example calls the top method to set the vertical position to 50 pixels.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.top(50,-1); 
}
```

## Method topMargin

Sets or returns the top margin for a form group control in pixels and specifies whether the size is automatically adjusted.

```xpp
public int topMargin([int value], [AutoMode mode])
```

### Parameters - topMargin

value  
An AutoMode enumeration value that specifies whether the size of the top margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

<!-- -->

mode  
An AutoMode enumeration value that specifies whether the size of the top margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

### Return Value - topMargin

An integer that specifies the size of the top margin for a form group control in pixels.

## Method topMarginMode

Sets or returns a value that indicates whether the size of the top margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.

```xpp
public AutoMode topMarginMode([AutoMode mode])
```

### Parameters - topMarginMode

mode  
An Automode enumeration value that specifies whether the size of the top margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

### Return Value - topMarginMode

An Automode enumeration value of Auto if the size of the top margin is automatically adjusted; otherwise, Fixed.

## Method topMarginValue

```xpp
public int topMarginValue([int value])
```

### Parameters - topMarginValue

value  

### Return Value - topMarginValue

## Method topMode

Sets or returns a value that indicates how the vertical position of a form group control is calculated.

```xpp
public int topMode([int value])
```

### Parameters - topMode

value  
An integer that indicates how the vertical position is calculated; optional.

### Return Value - topMode

An integer value that indicates how the vertical position is calculated: -1 for an exact pixel value, or a FormTop enumeration value.

### Examples - topMode

The following example shows a call to the topMode method that calculates the vertical position, based on an exact pixel value.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run time-form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.topMode(-1); 
    formGroupControl.topValue(50); 
}
```

## Method topValue

Sets or returns the vertical position of a form group control in pixels.

```xpp
public int topValue([int value])
```

### Parameters - topValue

value  
An Integer data type that specifies the vertical position.

### Return Value - topValue

An Integer data type value that specifies the vertical position of a form group control.

### Remarks - topValue

The vertical position is not changed unless the top mode is set for an exact pixel value. For more information, see the topMode method.

### Examples - topValue

The following example shows a call to the topValue method that sets the vertical position to 50 pixels.

```xpp
void FormGoupControl() 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.topMode(-1); 
    formGroupControl.topValue(50); 
}
```

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

Sets or returns an integer data type that indicates whether a control is hidden from the user.

```xpp
public int userHide([int value])
```

### Parameters - userHide

value  
An integer value that indicates whether a form group control is hidden from the user; optional.

### Return Value - userHide

1 if the form group control is hidden from the user; otherwise, 0.

### Remarks - userHide

The user can hide a form group control by right-clicking the control and then clicking Hide. This method lets you programmatically determine whether the control is hidden.

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

Sets or returns an integer that indicates whether the form group control is skipped when the user presses the TAB key to move to controls.

```xpp
public int userSkip([int value])
```

### Parameters - userSkip

value  
An integer that indicates the user setting for whether a form group control is skipped; optional.

### Return Value - userSkip

1 if the form group control is skipped; otherwise, 0.

### Remarks - userSkip

The user chooses whether to skip a form group control by using the User setup form.

## Method userWidth

Sets or returns an integer that indicates the width of a form group control in pixels.

```xpp
public int userWidth([int value])
```

### Parameters - userWidth

value  
An integer that indicates the width of a form group control in pixels; optional.

### Return Value - userWidth

An integer value that indicates the width of a form group control in pixels; 0 (zero) if the user did not specify a width.

### Remarks - userWidth

The user specifies the width in characters by using the User setup form. This method returns the width in pixels, based on six times the number of characters.

## Method useUserLayout

Specifies whether to use the user-specified layout of a form group control.

```xpp
public boolean useUserLayout([boolean value])
```

### Parameters - useUserLayout

value  
A Boolean value that specifies whether to use the user-specified layout of a form group control; optional.

### Return Value - useUserLayout

true if the user-specified layout of a form group control is used; otherwise, false.

### Remarks - useUserLayout

The user specifies the layout by using the User setup form.

## Method verticalSpacing

Gets or sets the amount of space above and below a form group control in pixels, and specifies how the space is calculated.

```xpp
public int verticalSpacing([int value], [AutoMode mode])
```

### Parameters - verticalSpacing

value  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

<!-- -->

mode  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

### Return Value - verticalSpacing

An integer value that indicates the amount of space above and below a control.

## Method verticalSpacingMode

Sets or returns a value that indicates how the amount of space above and below a form group control is calculated.

```xpp
public AutoMode verticalSpacingMode([AutoMode mode])
```

### Parameters - verticalSpacingMode

mode  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

### Return Value - verticalSpacingMode

An AutoMode enumeration that is set to Auto if the space is automatically adjusted based on other form settings, such as the font size; otherwise, Fixed.

## Method verticalSpacingValue

Gets or sets the amount of space above and below a form group control in pixels.

```xpp
public int verticalSpacingValue([int value])
```

### Parameters - verticalSpacingValue

value  
An integer that indicates the amount of space above and below a control; optional.

### Return Value - verticalSpacingValue

An integer value that indicates the amount of space above and below a control.

## Method viewEditMode

```xpp
public int viewEditMode([int value])
```

### Parameters - viewEditMode

value  

### Return Value - viewEditMode

## Method visible

Gets or sets a Boolean data type that displays or hides a form group control.

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  
A Boolean value that displays or hides a form group control; optional.

### Return Value - visible

true if the form group control is displayed; otherwise, false.

## Method width

Gets or sets the width of the control.

```xpp
public int width(int value, [int mode])
```

### Parameters - width

value  
An integer that indicates how the width is calculated. This can be one of the following values:

<!-- -->

mode  
An integer that indicates how the width is calculated. This can be one of the following values:

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

### Examples - width

The following example shows a call to the width method to set the control width to 200 pixels.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.width(200,-1); 
}
```

## Method widthMode

Gets or sets the calculation mode for the width of the control.

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  
An integer value that indicates how the control width is calculated; optional.

### Return Value - widthMode

An integer value that indicates the width current calculation mode.

### Remarks - widthMode

Calculate the width according to the following table.

| Mode         | Width calculation                                                                         |
|--------------|-------------------------------------------------------------------------------------------|
| Exact        | The exact width of the control in pixels is used.                                         |
| Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                               |

The width of the control might change when the calculation mode is set to Auto or Column width.

### Examples - widthMode

The following example shows a call to the widthMode method to calculate the control width, based on an exact pixel value.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.widthMode(-1); 
    formGroupControl.widthValue(200); 
}
```

## Method widthValue

Gets or sets the width of the control.

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  
An integer that specifies the width of the control in pixels.

### Return Value - widthValue

The width of the control in pixels.

### Remarks - widthValue

To change the width of the control, use the Exact width calculation mode.

### Examples - widthValue

The following example shows a call to the widthValue method that sets the control width to 200 pixels.

```xpp
static void createForm(Args _args) 
{ 
    Args args; 
    Form form; 
    FormRun formRun; 
    FormBuildDesign formBuildDesign; 
    FormBuildDataSource formBuildDataSource; 
    FormBuildStringControl formBuildStringControl; 
    FormBuildGroupControl formBuildGroupControl; 
    FormGroupControl formGroupControl; 
    int idx; 
    DictTable dictTable; 
    CustTable custTable; 
    // Create the form header. 
    form = new Form(); 
    // Add data sources to the form. 
    dictTable = new DictTable(tableNum(custTable)); 
    formBuildDataSource = form.addDataSource(dictTable.name()); 
    formBuildDataSource.table(dictTable.id()); 
    // Create the form design. 
    formBuildDesign = form.addDesign("Design"); 
    formBuildDesign.caption("myForm"); 
    // Add controls. 
    formBuildGroupControl = 
 formBuildDesign.addControl(FormControlType::Group,"Group"); 
    idx = formBuildGroupControl.id(); 
    formBuildStringControl = 
 formBuildGroupControl.addControl(FormControlType::String,"String"); 
    // Add data fields to the controls. 
    formBuildGroupControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataSource(formBuildDataSource.id()); 
    formBuildStringControl.dataField(2); 
    args = new Args(); 
    args.object(form); 
    // Create the run-time form. 
    formRun = classfactory.formRunClass(args); 
    formRun.run(); 
    formRun.detach(); 
    formGroupControl = formRun.control(idx); 
    formGroupControl.widthMode(-1); 
    formGroupControl.widthValue(200); 
}
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

## Method drop

Is called when a user drops a form group control or an item in a form group control into a new position.

```xpp
public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - drop

dragSource  
An integer value that indicates the y-coordinate of the object position.

<!-- -->

dragMode  
An integer value that indicates the y-coordinate of the object position.

<!-- -->

x  
An integer value that indicates the y-coordinate of the object position.

<!-- -->

y  
An integer value that indicates the y-coordinate of the object position.

### Remarks - drop

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking drop. For information about best practices for forms and code, see No Code in Forms.

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

## Method mouseLeave

Is called when the user moves the mouse pointer away from the control.

```xpp
public void mouseLeave()
```

### Remarks - mouseLeave

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseLeave. For information about best practices for forms and code, see No Code in Forms.

## Method context

Is called when the user right-clicks a form group control.

```xpp
public void context()
```

### Remarks - context

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking context. For information about best practices for forms and code, see No Code in Forms.

## Method copy

Copies a form group control.

```xpp
public void copy()
```

## Method cut

Cuts the contents of the control.

```xpp
public void cut()
```

## Method paste

Pastes a form group control.

```xpp
public void paste()
```

## Method arrange

```xpp
public void arrange()
```

## Method clicked

Is called when a form group control is clicked by the user.

```xpp
public void clicked()
```

## Method OnLeaving

```xpp
private void OnLeaving([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLeaving

sender  

<!-- -->

e  

## Method inputSearch

Is called when the user enters a search string in a bound control.

```xpp
public void inputSearch(str searchStr)
```

### Parameters - inputSearch

searchStr  
A String data type that contains search text; optional.

### Remarks - inputSearch

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking inputSearch. For information about best practices for forms and code, see No Code in Forms.

## Method resetUserSetting

Resets the user settings for a form group control.

```xpp
public void resetUserSetting()
```

## Method OnClicked

```xpp
private void OnClicked([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnClicked

sender  

<!-- -->

e  

## Method lostFocus

Is called when the user brings a form group control out of focus.

```xpp
public void lostFocus()
```

### Remarks - lostFocus

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking lostFocus. For information about best practices for forms and code, see the No Code in Forms form.

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

Is called when the user has finished moving a form group control.

```xpp
public void endDrag()
```

## Method jumpRef

Is called when a user clicks the Go to the Main Table Form command on a control shortcut menu in a form group control.

```xpp
public void jumpRef()
```

## Method setFocus

Sets the focus on the control.

```xpp
public void setFocus()
```

## Method filter

Is called when the user right-clicks a form group control and then clicks Filter By Selection.

```xpp
public void filter([str filterStr])
```

### Parameters - filter

filterStr  
A String data type that specifies the text for the filter; optional.

### Remarks - filter

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking filter. For information about best practices for forms and code, see No Code in Forms.

## Method displayControl

Displays a form group control.

```xpp
public void displayControl()
```

## Method gotFocus

Determines when the user brings a form group control into focus.

```xpp
public void gotFocus()
```

### Remarks - gotFocus

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking gotFocus. For information about best practices for forms and code, see No Code in Forms.

## Method prefColumnSize

Specifies the height and width of columns for a form group control.

```xpp
public void prefColumnSize(int width, int height)
```

### Parameters - prefColumnSize

width  
An integer value that specifies the height of columns.

<!-- -->

height  
An integer value that specifies the height of columns.

## Method dragLeave

Is called when the user drags an object out of the bounds of a form group control.

```xpp
public void dragLeave()
```

### Remarks - dragLeave

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking dragLeave. For information about best practices for forms and code, see No Code in Forms.

## Method OnGotFocus

```xpp
private void OnGotFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnGotFocus

sender  

<!-- -->

e  

## Method enter

Is called when the user moves focus to a form group control.

```xpp
public void enter()
```

### Remarks - enter

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking enter. For information about best practices for forms and code, see No Code in Forms.

## Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

```xpp
public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - mouseEnter

x  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that specifies whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that specifies whether the SHIFT key is down.

### Remarks - mouseEnter

The following are the possible values for the button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseEnter. For information about best practices for forms and code, see No Code in Forms.

