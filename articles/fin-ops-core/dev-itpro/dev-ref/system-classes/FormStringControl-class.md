---
title: FormStringControl class
description: This topic describes the FormStringControl class.
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

# Class FormStringControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormStringControl extends FormControl
```

## Remarks

## Examples

## Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Indicates whether to align the control.                                                                                                                                 |
| public int alignment(\[int value\])                                                                         |                                                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Indicates whether the user can change the contents of the control.                                                                                                      |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Indicates whether the system can declare a member variable that has the same name as the control.                                                                       |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Indicates whether the control background can be transparent.                                                                                                            |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to output text in the control.                                                                                             |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                                                |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public int changeCase(\[int value\])                                                                        |                                                                                                                                                                         |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public int charFromPos(int x, int y)                                                                        |                                                                                                                                                                         |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public int dataFieldArrayIndex()                                                                            |                                                                                                                                                                         |
| public FieldName dataFieldName()                                                                            |                                                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                                                |
| public int direction(\[int value\])                                                                         |                                                                                                                                                                         |
| public int displayHeight(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayHeightMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayHeightValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both. |
| public int dragDrop(\[int value\])                                                                          | Indicates whether to enable or disable drag-and-drop operations for the control.                                                                                        |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Indicates whether to enable or disable the object.                                                                                                                      |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                               |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public container getCursorPos()                                                                             |                                                                                                                                                                         |
| public int getFirstVisibleLine()                                                                            |                                                                                                                                                                         |
| public str getLine(int lineNo)                                                                              |                                                                                                                                                                         |
| public int getLineCount()                                                                                   |                                                                                                                                                                         |
| public container getSelection()                                                                             |                                                                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public int iMEMode(\[int value\])                                                                           |                                                                                                                                                                         |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                   |
| public boolean isValid()                                                                                    |                                                                                                                                                                         |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                                                         |
| public str label(\[str value\])                                                                             | Gets or sets the label for a control.                                                                                                                                   |
| public int labelAlignment(\[int value\])                                                                    |                                                                                                                                                                         |
| public int labelBold(\[int value\])                                                                         |                                                                                                                                                                         |
| public int labelCharacterSet(\[int value\])                                                                 |                                                                                                                                                                         |
| public str labelFont(\[str value\])                                                                         |                                                                                                                                                                         |
| public int labelFontSize(\[int value\])                                                                     |                                                                                                                                                                         |
| public int labelForegroundColor(\[int value\])                                                              |                                                                                                                                                                         |
| public int labelGuide(\[int value\])                                                                        |                                                                                                                                                                         |
| public int labelHeight(int value, \[int mode\])                                                             |                                                                                                                                                                         |
| public int labelHeightMode(\[int value\])                                                                   |                                                                                                                                                                         |
| public int labelHeightValue(\[int value\])                                                                  |                                                                                                                                                                         |
| public boolean labelItalic(\[boolean value\])                                                               |                                                                                                                                                                         |
| public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                        |                                                                                                                                                                         |
| public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                            |                                                                                                                                                                         |
| public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                              |                                                                                                                                                                         |
| public int labelPosition(\[int value\])                                                                     |                                                                                                                                                                         |
| public boolean labelUnderline(\[boolean value\])                                                            |                                                                                                                                                                         |
| public int labelWidth(int value, \[int mode\])                                                              |                                                                                                                                                                         |
| public int labelWidthMode(\[int value\])                                                                    |                                                                                                                                                                         |
| public int labelWidthValue(\[int value\])                                                                   |                                                                                                                                                                         |
| public boolean leave()                                                                                      |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int limitText(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                                                         |
| public AutoMode limitTextMode(\[AutoMode mode\])                                                            |                                                                                                                                                                         |
| public int limitTextValue(\[int value\])                                                                    |                                                                                                                                                                         |
| public int lineFromChar(int charIndex)                                                                      |                                                                                                                                                                         |
| public int lineIndex(int lineNo)                                                                            |                                                                                                                                                                         |
| public int lineLength(int lineNo)                                                                           |                                                                                                                                                                         |
| public int lookupButton(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean lookupOnly(\[boolean value\])                                                                |                                                                                                                                                                         |
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public boolean multiLine(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public boolean passwordStyle(\[boolean value\])                                                             |                                                                                                                                                                         |
| public container posFromChar(int charIndex)                                                                 |                                                                                                                                                                         |
| public FieldId presenceDataField(\[FieldId value\])                                                         |                                                                                                                                                                         |
| public int presenceDataSource(\[AnyType value\])                                                            |                                                                                                                                                                         |
| public int presenceIndicatorAllowed(\[int value\])                                                          |                                                                                                                                                                         |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean replaceOnLookup(\[boolean value\])                                                           |                                                                                                                                                                         |
| public str resolveAmbiguousReference()                                                                      |                                                                                                                                                                         |
| public FieldBinding disambiguationLookupTarget()                                                            |                                                                                                                                                                         |
| public str lookupDisambiguateReference(FieldBinding fieldBinding)                                           |                                                                                                                                                                         |
| public int searchAfterInput(\[int value\])                                                                  |                                                                                                                                                                         |
| public int searchMode(\[int value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public int style(\[int value\])                                                                             |                                                                                                                                                                         |
| public str text(\[str value\])                                                                              |                                                                                                                                                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userFastTabSummary(\[int value\])                                                                |                                                                                                                                                                         |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void presenceRefresh()                                                                               |                                                                                                                                                                         |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void performTypeLookup(\[int userType\], \[int arrayIndex\], \[SelectableDataArea company\])         |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void setSelection(int charIndexFrom, int charIndexTo)                                                |                                                                                                                                                                         |
| public void scrollCursor()                                                                                  |                                                                                                                                                                         |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void performDBLookup(\[FieldId fieldId\], \[TableId tableId\], \[SelectableDataArea company\])       |                                                                                                                                                                         |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void setCursorPos(int x, int y)                                                                      |                                                                                                                                                                         |
| public void performFormLookup(xFormRun form)                                                                |                                                                                                                                                                         |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void lineScroll(int dx, int dy)                                                                      |                                                                                                                                                                         |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void textChange()                                                                                    |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| public void pasteText(str pasteStr, \[boolean InsertSel\])                                                  |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |

## Method alignControl

Indicates whether to align the control.

```xpp
public boolean alignControl([boolean value])
```

### Parameters - alignControl

value  

### Return Value - alignControl

true if the control should be aligned; otherwise, false.

### Remarks - alignControl

The upper-left corner of the control is aligned according to the longest label.

## Method alignment

```xpp
public int alignment([int value])
```

### Parameters - alignment

value  

### Return Value - alignment

## Method allowEdit

Indicates whether the user can change the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

true if the control can be edited; otherwise, false.

### Remarks - allowEdit

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

## Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

```xpp
public boolean allowSysSetup()
```

### Return Value - allowSysSetup

true if the control is shown in the SysSetup form; otherwise, false.

## Method arrayIndex

```xpp
public int arrayIndex([int value])
```

### Parameters - arrayIndex

value  

### Return Value - arrayIndex

## Method autoDeclaration

Indicates whether the system can declare a member variable that has the same name as the control.

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  

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

### Return Value - backgroundColor

An integer that contains a packed RGB color.

### Remarks - backgroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

## Method backStyle

Indicates whether the control background can be transparent.

```xpp
public int backStyle([int value])
```

### Parameters - backStyle

value  

### Return Value - backStyle

1 if the control background can be transparent; otherwise, 0.

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

## Method bold

Gets or sets the weight of font that is used to output text in the control.

```xpp
public int bold([int value])
```

### Parameters - bold

value  

### Return Value - bold

An integer value between zero and nine, inclusive.

### Remarks - bold

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

## Method border

Gets or sets the style of the borderline of the control.

```xpp
public int border([int value])
```

### Parameters - border

value  

### Return Value - border

An integer between zero and four, inclusive.

### Remarks - border

The integer that is returned contains the style of the borderline of the control as follows.

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

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

## Method changeCase

```xpp
public int changeCase([int value])
```

### Parameters - changeCase

value  

### Return Value - changeCase

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

## Method charFromPos

```xpp
public int charFromPos(int x, int y)
```

### Parameters - charFromPos

x  

<!-- -->

y  

### Return Value - charFromPos

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

## Method countryRegionContextField

```xpp
public FieldId countryRegionContextField([FieldId value])
```

### Parameters - countryRegionContextField

value  

### Return Value - countryRegionContextField

## Method dataField

```xpp
public FieldId dataField([FieldId value])
```

### Parameters - dataField

value  

### Return Value - dataField

## Method dataFieldArrayIndex

```xpp
public int dataFieldArrayIndex()
```

### Return Value - dataFieldArrayIndex

## Method dataFieldName

```xpp
public FieldName dataFieldName()
```

### Return Value - dataFieldName

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

Gets or sets a data source that will be used by the control or the form.

```xpp
public int dataSource([AnyType value])
```

### Parameters - dataSource

value  

### Return Value - dataSource

The identifier of the data source that will be used.

## Method direction

```xpp
public int direction([int value])
```

### Parameters - direction

value  

### Return Value - direction

## Method displayHeight

```xpp
public int displayHeight([int value], [AutoMode mode])
```

### Parameters - displayHeight

value  

<!-- -->

mode  

### Return Value - displayHeight

## Method displayHeightMode

```xpp
public AutoMode displayHeightMode([AutoMode mode])
```

### Parameters - displayHeightMode

mode  

### Return Value - displayHeightMode

## Method displayHeightValue

```xpp
public int displayHeightValue([int value])
```

### Parameters - displayHeightValue

value  

### Return Value - displayHeightValue

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

Indicates whether to enable or disable drag-and-drop operations for the control.

```xpp
public int dragDrop([int value])
```

### Parameters - dragDrop

value  

### Return Value - dragDrop

1 if drag-and-drop operations are enabled; otherwise, false.

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

Indicates whether to enable or disable the object.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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

## Method font

Gets or sets the name of the font for the control to use.

```xpp
public str font([str value])
```

### Parameters - font

value  

### Return Value - font

The name of the font to use, such as Tahoma or Verdana.

## Method fontSize

Gets or sets the size of the font for the control to use.

```xpp
public int fontSize([int value])
```

### Parameters - fontSize

value  

### Return Value - fontSize

The height of the font in points.

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

## Method getCursorPos

```xpp
public container getCursorPos()
```

### Return Value - getCursorPos

## Method getFirstVisibleLine

```xpp
public int getFirstVisibleLine()
```

### Return Value - getFirstVisibleLine

## Method getLine

```xpp
public str getLine(int lineNo)
```

### Parameters - getLine

lineNo  

### Return Value - getLine

## Method getLineCount

```xpp
public int getLineCount()
```

### Return Value - getLineCount

## Method getSelection

```xpp
public container getSelection()
```

### Return Value - getSelection

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

<!-- -->

mode  

### Return Value - height

The height of the control in pixels.

### Remarks - height

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

| Mode            | Height calculation                                                                        |
|-----------------|-------------------------------------------------------------------------------------------|
| -1 Exact        | The exact height in pixels of the controls is used.                                       |
| 0 Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

## Method heightMode

Gets or sets a calculation mode for the height of the control.

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  

### Return Value - heightMode

The calculation mode.

### Remarks - heightMode

Calculate the height according to the following table.

| Mode          | Height calculation                                                                        |
|---------------|-------------------------------------------------------------------------------------------|
| Exact         | The exact height in pixels of the controls is used.                                       |
| Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

## Method heightValue

Gets or sets the height of the control.

```xpp
public int heightValue([int value])
```

### Parameters - heightValue

value  

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

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

## Method helpText

Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  

### Return Value - helpText

The string to be displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property dialog box. The Help text must not exceed 250 characters.

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

Retrieves the Windows handle for the control.

```xpp
public int hWnd()
```

### Return Value - hWnd

The handle for the control.

### Remarks - hWnd

The handle can be used with the Windows API.

## Method iMEMode

```xpp
public int iMEMode([int value])
```

### Parameters - iMEMode

value  

### Return Value - iMEMode

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

Retrieves a value that indicates whether the control allows for the specified level of customization.

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

For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

## Method isValid

```xpp
public boolean isValid()
```

### Return Value - isValid

## Method italic

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  

### Return Value - italic

## Method label

Gets or sets the label for a control.

```xpp
public str label([str value])
```

### Parameters - label

value  

### Return Value - label

The current value of the label string.

### Remarks - label

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

## Method labelAlignment

```xpp
public int labelAlignment([int value])
```

### Parameters - labelAlignment

value  

### Return Value - labelAlignment

## Method labelBold

```xpp
public int labelBold([int value])
```

### Parameters - labelBold

value  

### Return Value - labelBold

## Method labelCharacterSet

```xpp
public int labelCharacterSet([int value])
```

### Parameters - labelCharacterSet

value  

### Return Value - labelCharacterSet

## Method labelFont

```xpp
public str labelFont([str value])
```

### Parameters - labelFont

value  

### Return Value - labelFont

## Method labelFontSize

```xpp
public int labelFontSize([int value])
```

### Parameters - labelFontSize

value  

### Return Value - labelFontSize

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

```xpp
public boolean labelItalic([boolean value])
```

### Parameters - labelItalic

value  

### Return Value - labelItalic

## Method labelMouseDblClick

```xpp
public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - labelMouseDblClick

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

### Return Value - labelMouseDblClick

## Method labelMouseDown

```xpp
public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - labelMouseDown

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

### Return Value - labelMouseDown

## Method labelMouseUp

```xpp
public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)
```

### Parameters - labelMouseUp

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

### Return Value - labelMouseUp

## Method labelPosition

```xpp
public int labelPosition([int value])
```

### Parameters - labelPosition

value  

### Return Value - labelPosition

## Method labelUnderline

```xpp
public boolean labelUnderline([boolean value])
```

### Parameters - labelUnderline

value  

### Return Value - labelUnderline

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

## Method limitText

```xpp
public int limitText([int value], [AutoMode mode])
```

### Parameters - limitText

value  

<!-- -->

mode  

### Return Value - limitText

## Method limitTextMode

```xpp
public AutoMode limitTextMode([AutoMode mode])
```

### Parameters - limitTextMode

mode  

### Return Value - limitTextMode

## Method limitTextValue

```xpp
public int limitTextValue([int value])
```

### Parameters - limitTextValue

value  

### Return Value - limitTextValue

## Method lineFromChar

```xpp
public int lineFromChar(int charIndex)
```

### Parameters - lineFromChar

charIndex  

### Return Value - lineFromChar

## Method lineIndex

```xpp
public int lineIndex(int lineNo)
```

### Parameters - lineIndex

lineNo  

### Return Value - lineIndex

## Method lineLength

```xpp
public int lineLength(int lineNo)
```

### Parameters - lineLength

lineNo  

### Return Value - lineLength

## Method lookupButton

```xpp
public int lookupButton([int value])
```

### Parameters - lookupButton

value  

### Return Value - lookupButton

## Method lookupOnly

```xpp
public boolean lookupOnly([boolean value])
```

### Parameters - lookupOnly

value  

### Return Value - lookupOnly

## Method mandatory

```xpp
public boolean mandatory([boolean value])
```

### Parameters - mandatory

value  

### Return Value - mandatory

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

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

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

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

## Method multiLine

```xpp
public boolean multiLine([boolean value])
```

### Parameters - multiLine

value  

### Return Value - multiLine

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

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

## Method passwordStyle

```xpp
public boolean passwordStyle([boolean value])
```

### Parameters - passwordStyle

value  

### Return Value - passwordStyle

## Method posFromChar

```xpp
public container posFromChar(int charIndex)
```

### Parameters - posFromChar

charIndex  

### Return Value - posFromChar

## Method presenceDataField

```xpp
public FieldId presenceDataField([FieldId value])
```

### Parameters - presenceDataField

value  

### Return Value - presenceDataField

## Method presenceDataSource

```xpp
public int presenceDataSource([AnyType value])
```

### Parameters - presenceDataSource

value  

### Return Value - presenceDataSource

## Method presenceIndicatorAllowed

```xpp
public int presenceIndicatorAllowed([int value])
```

### Parameters - presenceIndicatorAllowed

value  

### Return Value - presenceIndicatorAllowed

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

## Method replaceOnLookup

```xpp
public boolean replaceOnLookup([boolean value])
```

### Parameters - replaceOnLookup

value  

### Return Value - replaceOnLookup

## Method resolveAmbiguousReference

```xpp
public str resolveAmbiguousReference()
```

### Return Value - resolveAmbiguousReference

## Method disambiguationLookupTarget

```xpp
public FieldBinding disambiguationLookupTarget()
```

### Return Value - disambiguationLookupTarget

## Method lookupDisambiguateReference

```xpp
public str lookupDisambiguateReference(FieldBinding fieldBinding)
```

### Parameters - lookupDisambiguateReference

fieldBinding  

### Return Value - lookupDisambiguateReference

## Method searchAfterInput

```xpp
public int searchAfterInput([int value])
```

### Parameters - searchAfterInput

value  

### Return Value - searchAfterInput

## Method searchMode

```xpp
public int searchMode([int value])
```

### Parameters - searchMode

value  

### Return Value - searchMode

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

## Method showLabel

```xpp
public boolean showLabel([boolean value])
```

### Parameters - showLabel

value  

### Return Value - showLabel

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

### Remarks - skip

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control.

## Method sort

```xpp
public int sort([SortOrder sortDirection])
```

### Parameters - sort

sortDirection  

### Return Value - sort

## Method style

```xpp
public int style([int value])
```

### Parameters - style

value  

### Return Value - style

## Method text

```xpp
public str text([str value])
```

### Parameters - text

value  

### Return Value - text

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

## Method userFastTabSummary

```xpp
public int userFastTabSummary([int value])
```

### Parameters - userFastTabSummary

value  

### Return Value - userFastTabSummary

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

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

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

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

```xpp
public int userSkip([int value])
```

### Parameters - userSkip

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

### Return Value - userSkip

1 if the user setting to skip the control is in effect; otherwise, 0.

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

<!-- -->

mode  

### Return Value - width

The width of the control in pixels.

### Remarks - width

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode           | Width calculation                                                                        |
|----------------|------------------------------------------------------------------------------------------|
| -1 Exact       | The exact width in pixels of the controls is used.                                       |
| 0 Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

## Method widthMode

Gets or sets the calculation mode of the width of the control.

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  

### Return Value - widthMode

An integer value that indicates the current calculation mode.

### Remarks - widthMode

Calculate the width according to the following table.

| Mode         | Width calculation                                                                        |
|--------------|------------------------------------------------------------------------------------------|
| Exact        | The exact width in pixels of the controls is used.                                       |
| Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

## Method widthValue

Gets or sets the width of the control.

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  

### Return Value - widthValue

The width in pixels of the control.

### Remarks - widthValue

To change the width of the control, use the exact width calculation mode.

## Method presenceRefresh

```xpp
public void presenceRefresh()
```

## Method OnLookup

```xpp
private void OnLookup([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLookup

sender  

<!-- -->

e  

## Method lostFocus

Indicates that the control has lost focus.

```xpp
public void lostFocus()
```

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

## Method performTypeLookup

```xpp
public void performTypeLookup([int userType], [int arrayIndex], [SelectableDataArea company])
```

### Parameters - performTypeLookup

userType  

<!-- -->

arrayIndex  

<!-- -->

company  

## Method OnLeaving

```xpp
private void OnLeaving([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLeaving

sender  

<!-- -->

e  

## Method undo

```xpp
public void undo()
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

## Method context

Shows the shortcut menu for the control.

```xpp
public void context()
```

## Method OnGotFocus

```xpp
private void OnGotFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnGotFocus

sender  

<!-- -->

e  

## Method setSelection

```xpp
public void setSelection(int charIndexFrom, int charIndexTo)
```

### Parameters - setSelection

charIndexFrom  

<!-- -->

charIndexTo  

## Method scrollCursor

```xpp
public void scrollCursor()
```

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

## Method performDBLookup

```xpp
public void performDBLookup([FieldId fieldId], [TableId tableId], [SelectableDataArea company])
```

### Parameters - performDBLookup

fieldId  

<!-- -->

tableId  

<!-- -->

company  

## Method filter

```xpp
public void filter([str filterStr])
```

### Parameters - filter

filterStr  

## Method OnModified

```xpp
private void OnModified([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnModified

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

Indicates that the mouse pointer has left the control.

```xpp
public void mouseLeave()
```

## Method displayControl

Displays the control.

```xpp
public void displayControl()
```

## Method copy

Copies the contents of the control to the clipboard.

```xpp
public void copy()
```

## Method gotFocus

Indicates that the control has received focus.

```xpp
public void gotFocus()
```

## Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

```xpp
public void dragLeave()
```

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

## Method OnValidating

```xpp
private void OnValidating([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnValidating

sender  

<!-- -->

e  

## Method setCursorPos

```xpp
public void setCursorPos(int x, int y)
```

### Parameters - setCursorPos

x  

<!-- -->

y  

## Method performFormLookup

```xpp
public void performFormLookup(xFormRun form)
```

### Parameters - performFormLookup

form  

## Method OnLostFocus

```xpp
private void OnLostFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLostFocus

sender  

<!-- -->

e  

## Method lineScroll

```xpp
public void lineScroll(int dx, int dy)
```

### Parameters - lineScroll

dx  

<!-- -->

dy  

## Method OnEnter

```xpp
private void OnEnter([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnEnter

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

## Method resetUserSetting

Resets the user settings for the control.

```xpp
public void resetUserSetting()
```

## Method textChange

```xpp
public void textChange()
```

## Method jumpRef

```xpp
public void jumpRef()
```

## Method lookup

```xpp
public void lookup()
```

## Method pasteText

```xpp
public void pasteText(str pasteStr, [boolean InsertSel])
```

### Parameters - pasteText

pasteStr  

<!-- -->

InsertSel  

## Method OnValidated

```xpp
private void OnValidated([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnValidated

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

## Method setFocus

Sets the focus on the control.

```xpp
public void setFocus()
```

## Method endDrag

Is called when the user has finished dragging a form control.

```xpp
public void endDrag()
```

### Remarks - endDrag

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.


