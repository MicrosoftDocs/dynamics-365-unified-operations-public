---
# required metadata

title: F Classes - FormListBoxControl to FormNotifyEventArgs | Microsoft Docs
description: API reference for classes from FormListBoxControl to FormNotifyEventArgs.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-08 23:44:57
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 63763
ms.assetid: 40223b06-435e-45c8-862d-9f419c5bcec6
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# F Classes - FormListBoxControl to FormNotifyEventArgs

API reference for classes from FormListBoxControl to FormNotifyEventArgs.

Class FormListBoxControl
------------------------

    class FormListBoxControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                                                     |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                                                |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the names of configuration keys that are checked for the control.                                                                        |
| public int count()                                                                                          |                                                                                                                                                                         |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int doubleClick()                                                                                    |                                                                                                                                                                         |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public EnumId enumType(\[EnumId value\])                                                                    |                                                                                                                                                                         |
| public EnumId enumTypeValue()                                                                               |                                                                                                                                                                         |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int find(str string)                                                                                 |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                               |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public str getText(int index)                                                                               |                                                                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public boolean hideFirstEntry(\[boolean value\])                                                            |                                                                                                                                                                         |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Returns the Windows handle (hWnd) of the control.                                                                                                                       |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean isValid()                                                                                    |                                                                                                                                                                         |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                                                         |
| public int item(\[int value\])                                                                              |                                                                                                                                                                         |
| public int items(\[int value\])                                                                             |                                                                                                                                                                         |
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
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int selection(\[int value\])                                                                         |                                                                                                                                                                         |
| public int selectionChange()                                                                                |                                                                                                                                                                         |
| public int selectText(str string)                                                                           |                                                                                                                                                                         |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public str text(\[str value\])                                                                              |                                                                                                                                                                         |
| public str toolTip()                                                                                        | Retrieves a tooltip for the control.                                                                                                                                    |
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
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                                     |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void insert(str string, int index)                                                                   |                                                                                                                                                                         |
| public void delete(str string)                                                                              |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void add(str string)                                                                                 |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void endUpdate()                                                                                     |                                                                                                                                                                         |
| public void clear()                                                                                         |                                                                                                                                                                         |
| public void beginUpdate()                                                                                   |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| private void OnSelectionChanging(\[FormControl sender\], \[FormControlEventArgs e\])                        |                                                                                                                                                                         |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| private void OnSelectionChanged(\[FormControl sender\], \[FormControlEventArgs e\])                         |                                                                                                                                                                         |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  
The new value for the property; optional.

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The value to assign to the allowEdit property.

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
The value to assign to the property; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method bold

Gets or sets the weight of font used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method cacheDataMethod

    public int cacheDataMethod([int value])

#### Parameters

value  

#### Return Value

### Method calcControlSize

Retrieves the size of the control.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

#### Return Value

The container that holds the width and height.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The value in the following table is for the Korean language edition of MicrosoftWindows.

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

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key being assigned to the control; optional.

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method configurationKeyEx

Retrieves a list that contains the names of configuration keys that are checked for the control.

    public List configurationKeyEx()

#### Return Value

A list of strings that contain the configuration key names.

#### Remarks

The list that is retrieved does not contain duplicates. It applies to all form controls. If the control is data-bound, the list also contains the configuration key of the table and field. The configuration keys on these elements are also added to the list if the control has non-empty values in the properties, extended data type, or Enumtype methods. Because of implementation details for the FormBuildMenuButtonControl class, the list does not contain the configuration keys that found on the specified menu item. However, the list does include these if the method is invoked on the FormMenuButtonControl class.

### Method count

    public int count()

#### Return Value

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.

    public str dataRelationPath([str value])

#### Parameters

value  
The string that contains the period-delimited list of relations; optional.

#### Return Value

The period-delimited list of relations that links the field binding of the DataField object to a relative table.

#### Remarks

This method is used by the reference group control to track exactly which relations produce the replacement field that is used. It enables the reference group control to bind consistently to the controls that it contains.

### Method dataSource

Gets or sets a data source to be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to be used.

### Method displayLength

    public int displayLength([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayLengthMode

    public AutoMode displayLengthMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayLengthValue

    public int displayLengthValue([int value])

#### Parameters

value  

#### Return Value

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method doubleClick

    public int doubleClick()

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An integer that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the dragLeave, the dragOver, and the dragOverEx to specify the behavior.

### Method dragOver

Raises the dragOver event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragOverEx

Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragText

Retrieves the text that is displayed when the form control is dragged.

    public str dragText()

#### Return Value

The text that is displayed when the control is dragged; an empty string if there is no text to display when the control is dragged.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method enumType

    public EnumId enumType([EnumId value])

#### Parameters

value  

#### Return Value

### Method enumTypeValue

    public EnumId enumTypeValue()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method find

    public int find(str string)

#### Parameters

string  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method getText

    public str getText(int index)

#### Parameters

index  

#### Return Value

### Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
The value to assign as the hasChanged value for the control; optional.

#### Return Value

true if the contents of the control have changed; otherwise, false.

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

true if the control has custom user settings; otherwise, false.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  
An integer data type that specifies how the height is calculated; optional.

<!-- -->

mode  
An integer data type that specifies how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An integer data type value that specifies how control height is calculated; optional.

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  
An integer data type that specifies the height in pixels; optional.

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpField

Retrieves the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

### Method helpText

Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the Help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Method hideFirstEntry

    public boolean hideFirstEntry([boolean value])

#### Parameters

value  

#### Return Value

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hWnd

Returns the Windows handle (hWnd) of the control.

    public int hWnd()

#### Return Value

A 32-bit handle (hWnd).

#### Remarks

This handle applies to all controls. This is useful when you work with the Windows API.

### Method isContainer

    public boolean isContainer()

#### Return Value

### Method isDisplayed

Retrieves a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

#### Remarks

To modify the visible state of the control, call the visible method.

### Method isRestricted

Retrieves a value that indicates whether the control is restricted.

    public boolean isRestricted()

#### Return Value

true if the control is restricted; otherwise, false.

### Method isUserSetupEnabled

Returns a value that indicates whether the control allows for the specified level of customization.

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise false. For this method to return true, the AllowUserSetup property of the design and all parent containers must permit the level of access that is specified by the neededSetupRights parameter.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

### Method isValid

    public boolean isValid()

#### Return Value

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method item

    public int item([int value])

#### Parameters

value  

#### Return Value

### Method items

    public int items([int value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method labelAlignment

    public int labelAlignment([int value])

#### Parameters

value  

#### Return Value

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelForegroundColor

    public int labelForegroundColor([int value])

#### Parameters

value  

#### Return Value

### Method labelGuide

    public int labelGuide([int value])

#### Parameters

value  

#### Return Value

### Method labelHeight

    public int labelHeight(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelHeightMode

    public int labelHeightMode([int value])

#### Parameters

value  

#### Return Value

### Method labelHeightValue

    public int labelHeightValue([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelMouseDblClick

    public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

#### Return Value

### Method labelMouseDown

    public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

#### Return Value

### Method labelMouseUp

    public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidth

    public int labelWidth(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public int labelWidthValue([int value])

#### Parameters

value  

#### Return Value

### Method leave

    public boolean leave()

#### Return Value

### Method left

Gets or sets the horizontal position of the control in the form.

    public int left(int value, [int mode])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method leftMode

Sets the horizontal arrange mode for the control in the form.

    public int leftMode([int value])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal arrange mode for the control in the form.

### Method leftValue

Gets or sets the horizontal position of the control in the form.

    public int leftValue([int value])

#### Parameters

value  
An integer value that indicates the horizontal position of the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

#### Return Value

true if the control was marked as a user-added control; otherwise, false.

### Method modified

    public boolean modified()

#### Return Value

### Method mouseDblClick

Is called when the control is double-clicked by the user.

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseDown

Is called when the user clicks the mouse button over the control.

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method mouseMove

Is called when the user moves the mouse pointer over the control.

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseUp

Is called when the user releases the mouse button over the control area.

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control; optional.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method previewPartRef

    public str previewPartRef([str value])

#### Parameters

value  

#### Return Value

### Method promptrect

    public int promptrect([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

Sets or returns the ID of the security key for the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The ID of the security key to assign to the control; optional.

#### Return Value

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

### Method selection

    public int selection([int value])

#### Parameters

value  

#### Return Value

### Method selectionChange

    public int selectionChange()

#### Return Value

### Method selectText

    public int selectText(str string)

#### Parameters

string  

#### Return Value

### Method showContextMenu

Shows the shortcut menu for the control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
The ID of the menu to show.

#### Return Value

An integer value that indicates whether the call succeeded.

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise false.

### Method sort

    public int sort([SortOrder sortDirection])

#### Parameters

sortDirection  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method toolTip

Retrieves a tooltip for the control.

    public str toolTip()

#### Return Value

The text to show in the tooltip.

#### Remarks

Whenever the pointer hovers over the control, the tooltip is displayed to the user. This method can be overridden to present instructive text to the user about the values that are entered in the control.

#### Examples

    str tooltip() 
    { 
        return "Account numbers of customers eligible for discount"; 
    }

### Method top

Gets or sets the vertical position of the control in the form.

    public int top(int value, [int mode])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method topMode

Sets the vertical arrange mode for the control in the form.

    public int topMode([int value])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical arrange mode for the control in the form.

### Method topValue

Gets or sets the vertical position of the control in the form.

    public int topValue([int value])

#### Parameters

value  
An integer value that indicates the vertical position of the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control.

#### Return Value

true if the text in the control is underlined; otherwise false.

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method userData

Gets or sets the user data for the control.

    public int userData([int value])

#### Parameters

value  
An integer value that indicates the user data for the control; optional.

#### Return Value

The user data for the control.

### Method userDataItem

Gets or sets the user data item for the control.

    public int userDataItem([int value])

#### Parameters

value  
An integer value that indicates the user data item for the control; optional.

#### Return Value

The user data item for the control.

### Method userDataItems

Gets or sets the number of user data items for the control.

    public int userDataItems([int value])

#### Parameters

value  
An integer value that indicates the number of user data items for the control; optional.

#### Return Value

The number of user data items for the control.

### Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

    public int userDisable([int value])

#### Parameters

value  
The value that indicates whether the control is disabled for the user; optional.

#### Return Value

1 if the control is disabled for the user; otherwise, 0.

### Method userHeight

Gets or sets the custom user height for the control.

    public int userHeight([int value])

#### Parameters

value  
The user height for the control; optional.

#### Return Value

The custom user height for the control.

### Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
The value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Method userOrgContainer

Gets or sets the organization container for the control.

    public int userOrgContainer([int value])

#### Parameters

value  
The organization container to set for the control; optional.

#### Return Value

The organization container for the control.

### Method userOrgSibling

Gets or sets the organization sibling for the control.

    public int userOrgSibling([int value])

#### Parameters

value  
The organization sibling to set for the control; optional.

#### Return Value

The organization sibling for the control.

### Method userPromptText

Gets or sets the user label text for the control.

    public str userPromptText([str value])

#### Parameters

value  
The user label text to set for the control; optional.

#### Return Value

The user label text for the control.

### Method userSecurityLevel

Gets or sets the user security level for the control.

    public int userSecurityLevel([int value])

#### Parameters

value  
The user security level to set for the control; optional.

#### Return Value

The user security level for the control.

### Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

### Method userWidth

Sets or returns the width of the control in pixels.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method validate

    public boolean validate()

#### Return Value

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode value for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode value for the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method verticalSpacingMode

Sets the vertical spacing mode for the control in the form.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

The vertical spacing mode for the control in the form.

### Method verticalSpacingValue

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacingValue([int value])

#### Parameters

value  
An integer value that indicates the vertical spacing of the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value to assign to the visibility setting for the control; optional.

#### Return Value

true if the control is visible; otherwise, false.

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  
An integer data type that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer data type that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer data type value that indicates how control width is calculated; optional.

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An integer data type that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method insert

    public void insert(str string, int index)

#### Parameters

string  

<!-- -->

index  

### Method delete

    public void delete(str string)

#### Parameters

string  

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method enter

    public void enter()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

### Method drop

Raises the drop event to indicate that a drop operation is being performed on the current control.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method add

    public void add(str string)

#### Parameters

string  

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

### Method undo

    public void undo()

### Method endUpdate

    public void endUpdate()

### Method clear

    public void clear()

### Method beginUpdate

    public void beginUpdate()

### Method jumpRef

    public void jumpRef()

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method OnSelectionChanging

    private void OnSelectionChanging([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lookup

    public void lookup()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method displayControl

Displays the control.

    public void displayControl()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnSelectionChanged

    private void OnSelectionChanged([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

## Class FormListColumn
    class FormListColumn extends Object

The FormListColumn class provides list column functionality for a form.

### Remarks

### Examples

### Methods

| Method                                                      | Description                                               |
|-------------------------------------------------------------|-----------------------------------------------------------|
| public FormListFormat format(\[FormListFormat value\])      |                                                           |
| public int image(\[int value\])                             |                                                           |
| public int order(\[int value\])                             |                                                           |
| public int subItem(\[int value\])                           |                                                           |
| public str text(\[str value\])                              |                                                           |
| public str toString()                                       | Returns a string that contains the class handle and name. |
| public int width(\[int value\])                             | Gets or sets the width of the control.                    |
| public void new(\[str Text\], \[int ColNo\], \[int Width\]) | Initializes a new instance of the Object class.           |
| public void finalize()                                      |                                                           |

### Method format

    public FormListFormat format([FormListFormat value])

#### Parameters

value  

#### Return Value

### Method image

    public int image([int value])

#### Parameters

value  

#### Return Value

### Method order

    public int order([int value])

#### Parameters

value  

#### Return Value

### Method subItem

    public int subItem([int value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method toString

Returns a string that contains the class handle and name.

    public str toString()

#### Return Value

A text representation of the class.

### Method width

Gets or sets the width of the control.

    public int width([int value])

#### Parameters

value  
The value to assign as the width of the list column; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode             | Width calculation                                                                         |
|------------------|-------------------------------------------------------------------------------------------|
| -1 – Exact       | The exact width of the control in pixels is used.                                         |
| 0 – Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| 1 – Column width | The layout of the form determines the width of the control.                               |

The width and the width calculation mode can be set separately.

### Method new

Initializes a new instance of the Object class.

    public void new([str Text], [int ColNo], [int Width])

#### Parameters

Text  

<!-- -->

ColNo  

<!-- -->

Width  

### Method finalize

    public void finalize()

## Class FormListControl
    class FormListControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int add(str Text, \[int image\], \[int index\])                                                      |                                                                                                                                                                         |
| public boolean addColumn(int Idx, FormListColumn Column)                                                    |                                                                                                                                                                         |
| public int addItem(FormListItem item)                                                                       |                                                                                                                                                                         |
| public boolean alignControl(\[boolean value\])                                                              | Determines whether the control is aligned with other controls.                                                                                                          |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can modify the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean arrangeItem(FormListArrange ArrangeMethod)                                                   |                                                                                                                                                                         |
| public boolean autoArrange(\[boolean value\])                                                               |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determines whether the control background can be transparent.                                                                                                           |
| public int beginDrag(int x, int y)                                                                          | Identifies when the user starts to move a form list control or an item in a form list control.                                                                          |
| public int bold(\[int value\])                                                                              | Gets or sets the font weight that is used fort text in the control.                                                                                                     |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                                                |
| public container calcControlSize(int chars, int lines)                                                      | Calculates the font size that is used for a form list control, based on the number of characters and the number of lines.                                               |
| public boolean canScroll(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public boolean checkBox(\[boolean value\])                                                                  |                                                                                                                                                                         |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public boolean columnHeader(\[boolean value\])                                                              | Sets or gets a Boolean data type value that indicates whether a form list control has a column header.                                                                  |
| public boolean columnHeaderButton(\[boolean value\])                                                        | Sets or gets a Boolean data type value that indicates whether a form list control has a column header button.                                                           |
| public boolean columnImages(\[boolean value\])                                                              | Sets or gets a Boolean data type value that indicates whether a form list control has column images.                                                                    |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are activated for a form list control.                                                                |
| public int copyItem(int Item, int InsertAt)                                                                 | Copies a specified item in a form list control.                                                                                                                         |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public boolean delete(int Idx)                                                                              | Deletes a specified item from a form list control.                                                                                                                      |
| public boolean deleteAll()                                                                                  | Deletes all the items from a form list control.                                                                                                                         |
| public boolean deleteColumn(int Idx)                                                                        | Deletes a specified column in a form list control.                                                                                                                      |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Identifies when a user drags an object over an item within the bounds of a form list control.                                                                           |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when a user drags an item in a form list control.                                                                                  |
| public boolean editLabels(\[boolean value\])                                                                | Indicates whether users can modify item names in a form list control.                                                                                                   |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public int ensureVisible(int Idx)                                                                           |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                               |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control.                                                                                                                            |
| public FormListColumn getColumn(int Idx)                                                                    | Retrieves a FormListColumn object for a specified column in a form list control.                                                                                        |
| public int getColumnCount()                                                                                 | Retrieves the number of columns in a form list control.                                                                                                                 |
| public int getColumnWidth(int Idx)                                                                          | Retrieves the width of a column in a form list control.                                                                                                                 |
| public int getCount()                                                                                       | Retrieves the number of items that are contained in a form list control.                                                                                                |
| public int getCountPerPage()                                                                                |                                                                                                                                                                         |
| public Imagelist getImagelist(\[boolean GetLarge\])                                                         |                                                                                                                                                                         |
| public FormListItem getItem(int Idx, \[int SubItem\])                                                       | Retrieves a FormListItem object for an item in a form list control.                                                                                                     |
| public container getItemPos(int Item)                                                                       | Retrieves the position of an item in a form list control.                                                                                                               |
| public int getNextItem(FormListNext nextType, \[int startIdx\])                                             | Retrieves the number of the next item in a form list control.                                                                                                           |
| public int getSelectedCount()                                                                               | Retrieves the number of items that are selected in a form list control.                                                                                                 |
| public int getStringWidth(str Text)                                                                         |                                                                                                                                                                         |
| public int getTopIndex()                                                                                    |                                                                                                                                                                         |
| public boolean gridLines(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public boolean headerdragdrop(\[boolean value\])                                                            |                                                                                                                                                                         |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public container hitTest(int x, int y)                                                                      |                                                                                                                                                                         |
| public container hitTestSubItem(int x, int y)                                                               |                                                                                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Gets a value that indicates whether the control allows for the specified level of customization.                                                                        |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                                                         |
| public int itemAlign(\[int value\])                                                                         |                                                                                                                                                                         |
| public boolean itemChanging(int Idx, AnyType Data)                                                          |                                                                                                                                                                         |
| public boolean keyDown(int vKey, boolean Ctrl, boolean Shift)                                               |                                                                                                                                                                         |
| public boolean leave()                                                                                      | Identifies when a user moves focus away from a form list control.                                                                                                       |
| public int left(int value, \[int mode\])                                                                    | Sets or returns the horizontal position of a form list control in pixels, and specifies how the position is calculated.                                                 |
| public int leftMode(\[int value\])                                                                          | Sets or returns a value that indicates how the horizontal position of a form list control is calculated.                                                                |
| public int leftValue(\[int value\])                                                                         | Sets or returns the horizontal position of a form list control in pixels.                                                                                               |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Identifies when a user presses the left mouse button.                                                                                                                   |
| public int moveItem(int Item, int InsertAt)                                                                 | Moves a specified item in a form list control.                                                                                                                          |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public boolean oneClickActivate(\[boolean value\])                                                          |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public boolean redrawItems(int idxFirst, int idxLast)                                                       | Updates a range of items in a form list control.                                                                                                                        |
| public boolean rowSelect(\[boolean value\])                                                                 | Sets or gets a Boolean data type value that indicates whether a row in a form list control is selected when the row is clicked.                                         |
| public boolean scroll(int dx, int dy)                                                                       |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public boolean selectionChanging(int Idx, AnyType Data)                                                     |                                                                                                                                                                         |
| public boolean setColumn(int Idx, FormListColumn Column)                                                    |                                                                                                                                                                         |
| public boolean setColumnWidth(int Idx, int Width)                                                           | Specifies the width of a column in a form list control.                                                                                                                 |
| public boolean setItem(FormListItem item)                                                                   | Indicates whether an item is contained in a form list control.                                                                                                          |
| public Imagelist setStateImagelist(Imagelist imageList)                                                     |                                                                                                                                                                         |
| public int showContextMenu(int menuHandle)                                                                  | Identifies when a shortcut menu appears.                                                                                                                                |
| public boolean showSelAlways(\[boolean value\])                                                             |                                                                                                                                                                         |
| public boolean singleSelection(\[boolean value\])                                                           | Indicates whether multiple items can be selected in a form list control.                                                                                                |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean sortTextItems(\[int column\], \[boolean ascending\])                                         |                                                                                                                                                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                     | Sets or returns the vertical position of a form list control in pixels, and specifies how the position is calculated.                                                   |
| public int topMode(\[int value\])                                                                           | Sets or returns a value that indicates how the vertical position for a form list control is calculated.                                                                 |
| public int topValue(\[int value\])                                                                          | Sets or returns the vertical position of a form list control in pixels.                                                                                                 |
| public boolean trackSelect(\[boolean value\])                                                               |                                                                                                                                                                         |
| public boolean twoClickActivate(\[boolean value\])                                                          |                                                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the value of the underline property for the text in the control.                                                                                        |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Sets or gets the amount of space above and below a form list control in pixels, and specifies how the space is calculated.                                              |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets or returns a value that indicates how the space above and below a form list control is calculated.                                                                 |
| public int verticalSpacingValue(\[int value\])                                                              | Sets or returns the amount of space above and below a form list control in pixels.                                                                                      |
| public int viewType(\[int value\])                                                                          |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void selectionChanged(int Idx, AnyType Data)                                                         |                                                                                                                                                                         |
| public void activateItem(int Idx)                                                                           |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Identifies when the search begins for a specified text string.                                                                                                          |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void update(\[int idx\])                                                                             | Updates the control.                                                                                                                                                    |
| public void endDrag()                                                                                       | Identifies when the user has finished moving a form list control.                                                                                                       |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void setImagelist(Imagelist imageList, \[boolean SetLarge\])                                         |                                                                                                                                                                         |
| public void copy()                                                                                          | Identifies when a user performs a copy operation.                                                                                                                       |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void itemCopy(int Idx, int newIdx)                                                                   |                                                                                                                                                                         |
| public void cut()                                                                                           | Identifies when the user performs a cut operation.                                                                                                                      |
| public void itemMoved(int Idx, int newIdx)                                                                  |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| private void OnSelectionChanged(\[FormControl sender\], \[FormControlEventArgs e\])                         |                                                                                                                                                                         |
| public void hotTrackItem(int Idx)                                                                           | Identifies when a user moves the mouse pointer over a form list control.                                                                                                |
| public void setCount(int count)                                                                             |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Identifies when a user drags an object out of the bounds of a form list control.                                                                                        |
| public void itemDeleted(int Idx, AnyType Data)                                                              |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void setText(int Idx, str Text, \[int SubItem\])                                                     |                                                                                                                                                                         |
| public void itemChanged(int Idx, AnyType Data)                                                              |                                                                                                                                                                         |
| public void doubleClick()                                                                                   | Identifies when a user double-clicks an item in a form list control.                                                                                                    |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void allItemsDeleted()                                                                               | Identifies when all the items in a form list control are deleted.                                                                                                       |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Identifies when a user drops a form list control or an item in a form list control into a new position.                                                                 |
| public void columnClicked(int Column)                                                                       | Identifies when a user clicks a column in a list view control in a form.                                                                                                |
| public void getStateImagelist()                                                                             |                                                                                                                                                                         |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void setItemPos(int Item, int x, int y)                                                              | Sets the position of an item in a form list control.                                                                                                                    |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void enter()                                                                                         |                                                                                                                                                                         |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void context()                                                                                       | Identifies when the user opens a shortcut menu in a form list control.                                                                                                  |
| public void beginEditLabel(int Idx)                                                                         |                                                                                                                                                                         |
| public void itemInserted(int Idx, AnyType Data)                                                             |                                                                                                                                                                         |

### Method add

    public int add(str Text, [int image], [int index])

#### Parameters

Text  

<!-- -->

image  

<!-- -->

index  

#### Return Value

### Method addColumn

    public boolean addColumn(int Idx, FormListColumn Column)

#### Parameters

Idx  

<!-- -->

Column  

#### Return Value

### Method addItem

    public int addItem(FormListItem item)

#### Parameters

item  

#### Return Value

### Method alignControl

Determines whether the control is aligned with other controls.

    public boolean alignControl([boolean value])

#### Parameters

value  
A Boolean value that indicates whether a form list control is aligned with other controls.

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned based on the longest label.

### Method allowEdit

Determines whether the user can modify the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
A Boolean data type that indicates whether data can be modified.

#### Return Value

true if the control can be modified; otherwise, false.

#### Remarks

If this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method arrangeItem

    public boolean arrangeItem(FormListArrange ArrangeMethod)

#### Parameters

ArrangeMethod  

#### Return Value

### Method autoArrange

    public boolean autoArrange([boolean value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
A Boolean data type that indicates whether the system can declare a variable of the same name as a form list control.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

#### Examples

The following example shows a call to the autoDeclaration method that specifies that the system can declare a variable that has the same name as a form list control.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.autoDeclaration(true); 
    }

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  
An Integer data type that specifies the background color.

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  
An Integer data type that indicates the background style.

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method beginDrag

Identifies when the user starts to move a form list control or an item in a form list control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An Integer data type that indicates the y-coordinate for the move event.

<!-- -->

y  
An Integer data type that indicates the y-coordinate for the move event.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click beginDrag. For information about best practices for forms and code, see No Code in Forms.

### Method bold

Gets or sets the font weight that is used fort text in the control.

    public int bold([int value])

#### Parameters

value  
An Integer data type that specifies the font weight.

#### Return Value

An integer value between 0 (zero) and 9, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 – Use the default font weight.
-   1 – Thin.
-   2 – Extra-light.
-   3 – Light.
-   4 – Normal.
-   5 – Medium.
-   6 – Semibold.
-   7 – Bold.
-   8 – Extra-bold.
-   9 – Heavy.

#### Examples

The following example shows a call to the bold method to set the font weight to 9, which indicates heavy.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        int boldLevel; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        boldLevel = formListControl.bold(9); 
    }

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

### Method calcControlSize

Calculates the font size that is used for a form list control, based on the number of characters and the number of lines.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
An Integer data type that specifies the number of lines.

<!-- -->

lines  
An Integer data type that specifies the number of lines.

#### Return Value

A Container data type value that specifies the size of a form list control.

### Method canScroll

    public boolean canScroll([boolean value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  
An Integer data type that specifies the character set for the text font.

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set, according to the following table.

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

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value | Description    |
|-------|----------------|
| 130   | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value | Description     |
|-------|-----------------|
| 177   | HEBREW\_CHARSET |
| 178   | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set based on the current system locale. For example, if the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method checkBox

    public boolean checkBox([boolean value])

#### Parameters

value  

#### Return Value

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  
An Integer data type that specifies the color palette for a form list control.

#### Return Value

An integer between 0 (zero) and 2, inclusive.

#### Remarks

The color scheme is defined according to the following table.

| Value | Style                 |
|-------|-----------------------|
| 0     | Default               |
| 1     | The Windows palette   |
| 2     | The true-color scheme |

### Method columnHeader

Sets or gets a Boolean data type value that indicates whether a form list control has a column header.

    public boolean columnHeader([boolean value])

#### Parameters

value  
A Boolean data type that indicates whether a form list control has a column header.

#### Return Value

true if the control has a column header; otherwise, false.

#### Remarks

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value. You must call the columnHeader method before you add a column to the form; otherwise, the column does not appear in the form list control.

#### Examples

The following example shows a call to the columnHeader method to indicate that the form list control does not have a column header. The FormListControl.addColumn method adds the column to the form list control.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListColumn formListColumn; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        boolean columnHeader; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        columnHeader = formListControl.columnHeader(false); 
        // Add a column to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
    }

### Method columnHeaderButton

Sets or gets a Boolean data type value that indicates whether a form list control has a column header button.

    public boolean columnHeaderButton([boolean value])

#### Parameters

value  
A Boolean data type that indicates whether a form list control has a column header button.

#### Return Value

true if the control has a column header button; otherwise, false.

#### Remarks

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value. You must call the columnHeaderButton method before you add a column to the form; otherwise, the column does not appear in the form list control.

#### Examples

The following example shows a call to the columnHeaderButton method to indicate that the form list control has a column header button. The FormListControl.addColumn method adds the column to the form list control.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListColumn formListColumn; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        boolean columnHeaderBtn; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        columnHeaderBtn = formListControl.columnHeaderButton(true); 
        // Add a column to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
    }

### Method columnImages

Sets or gets a Boolean data type value that indicates whether a form list control has column images.

    public boolean columnImages([boolean value])

#### Parameters

value  
A Boolean data type that indicates whether a form list control has column images.

#### Return Value

true if the form list control has column images; otherwise, false.

#### Remarks

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

#### Examples

The following example shows a call to the columnImages method to indicate that the form list control has column images. The FormListControl.addColumn method adds the column to the form list control.

     
    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListColumn formListColumn; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        formListControl.columnImages(true); 
        // Add a column to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
    }

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
A configurationKeyId system data type that specifies the configuration key ID.

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

#### Examples

The following example shows a call to the configurationKey method to assign the Bank configuration key to the form list control.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        configurationKeyId ID; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run time-form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        ID = formListControl.configurationKey(configurationKeyNum(Bank)); 
    }

### Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are activated for a form list control.

    public List configurationKeyEx()

#### Return Value

A List object that contains the IDs of configuration keys that are activated for a form list control.

#### Remarks

If the control is bound to a data source, the retrieved list of configuration key IDs also includes the configuration key ID for the table and field. In addition, the retrieved list contains any configuration key IDs that are applied to the extended data type. The list does not contain duplicate IDs.

#### Examples

The following example shows a call to the configurationKeyEx method. The ListEnumerator object is used to traverse the elements throughout a list.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        configurationKeyId ID; 
        List list; 
        ListEnumerator enum; 
        DictConfigurationKey dck; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        ID = formListControl.configurationKey(configurationKeyNum(Bank)); 
        list = formListControl.configurationKeyEx(); 
        if (0 != list.elements()) 
        { 
            enum = list.getEnumerator(); 
            while (enum.moveNext()) 
            { 
                dck = new DictConfigurationKey(enum.current()); 
                if (dck) 
                { 
                    print strfmt("Configuration Key ID: %1" 
                      + "Configuration Key Name: %2",enum.current(),dck.name()); 
                    pause; 
                } 
            } 
        } 
    }

### Method copyItem

Copies a specified item in a form list control.

    public int copyItem(int Item, int InsertAt)

#### Parameters

Item  
An Integer data type that specifies the position in the list that the item is copied to.

<!-- -->

InsertAt  
An Integer data type that specifies the position in the list that the item is copied to.

#### Return Value

An Integer data type that specifies the position in the list that the item is copied to.

#### Remarks

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

#### Examples

The following example shows a call to the copyItem method to copy an item to the tenth position in the form list control. The FormListControl.getCount method returns the number of items in the control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        int idx4; 
        str string; 
        container conAccountNum; 
        DictTable dictTable; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add a column to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
       } 
        formListControl.getCount(); 
        formListControl.copyItem(2,10); 
    }

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method dataRelationPath

Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.

    public str dataRelationPath([str value])

#### Parameters

value  
The string that contains the period-delimited list of relations; optional.

#### Return Value

The period-delimited list of relations that links the field binding of the DataField object to a relative table.

#### Remarks

This method is used by the reference group control to track exactly which relations produce the replacement field that is used. It enables the reference group control to bind consistently to the controls that it contains.

### Method delete

Deletes a specified item from a form list control.

    public boolean delete(int Idx)

#### Parameters

Idx  
The zero-based index for the item that is being deleted.

#### Return Value

true if the item is deleted; otherwise, false.

#### Examples

The following example shows a call to the delete method to delete an item from the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        int idx4; 
        str string; 
        container conAccountNum; 
        DictTable dictTable; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        boolean itemDel; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        } 
        // Delete an item. 
        itemDel = formListControl.delete(2); 
    }

### Method deleteAll

Deletes all the items from a form list control.

    public boolean deleteAll()

#### Return Value

true if all the items are deleted; otherwise, false.

#### Examples

The following example shows a call to the deleteAll method to delete all the items from the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        int idx4; 
        str string; 
        container conAccountNum; 
        DictTable dictTable; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        boolean itemsDel; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        } 
        // Delete all items. 
        itemsDel = formListControl.deleteAll(); 
    }

### Method deleteColumn

Deletes a specified column in a form list control.

    public boolean deleteColumn(int Idx)

#### Parameters

Idx  
An Integer data type that specifies a column in a form list control.

#### Return Value

true if the column is deleted; otherwise, false.

#### Examples

The following example shows a call to the deleteColumn method to delete the first column in the form list control. The FormListControl.addColumn method adds two columns to the form list control.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListColumn formListColumn; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        boolean columnDel; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add columns to the form list control. 
        formListControl.addColumn(0, new FormListColumn("Column1",1,120)); 
        formListControl.addColumn(1, new FormListColumn("Column2",2,120)); 
        // Delete a column. 
        columnDel = formListControl.deleteColumn(0); 
    }

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the dragLeave, the dragOver, and the dragOverEx to specify the behavior.

### Method dragOver

Identifies when a user drags an object over an item within the bounds of a form list control.

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An Integer data type that indicates the y-coordinate of the object's position.

<!-- -->

dragMode  
An Integer data type that indicates the y-coordinate of the object's position.

<!-- -->

x  
An Integer data type that indicates the y-coordinate of the object's position.

<!-- -->

y  
An Integer data type that indicates the y-coordinate of the object's position.

#### Return Value

A FormDrag system enumeration value that specifies whether the object is moved, copied, or not moved to a specified position.

#### Remarks

This method is called only if the DragDrop property is set to Manual for the control and a beginDrag event has already been started. For more information about the event, see beginDrag. To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click dragOver. For information about best practices for forms and code, see No Code in Forms.

### Method dragOverEx

Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragText

Retrieves the text that is displayed when a user drags an item in a form list control.

    public str dragText()

#### Return Value

A String data type value that specifies the text that is displayed when a user drags a form list control.

#### Remarks

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click dragText. For information about best practices for forms and code, see No Code in Forms.

### Method editLabels

Indicates whether users can modify item names in a form list control.

    public boolean editLabels([boolean value])

#### Parameters

value  
A Boolean data type that specifies whether users can modify item names in a form list control.

#### Return Value

true if users can modify item names; otherwise, false.

#### Remarks

You must call the editLabels method before you add columns to a form list control; otherwise, the columns do not appear in the control.

#### Examples

The following example shows a call to the editLabels method to enable users to modify item names in the form list control. The DictField.label method returns a label for a specified table field that is added as an item to the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        DictTable dictTable; 
        int idx4; 
        str string; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        DictField dictField; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        formListControl.editLabels(true); 
        // Add a column to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1",1,120)); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
            dictField = new DictField(77,1); 
            formListItem = new FormListItem(dictField.label()); 
            item = formListControl.addItem(formListItem); 
        } 
    }

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that specifies whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method ensureVisible

    public int ensureVisible(int Idx)

#### Parameters

Idx  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control.

    public int foregroundColor([int value])

#### Parameters

value  
An Integer data type that specifies the foreground color.

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

#### Examples

The following example shows a call to the foregroundColor method to set the foreground color to the color of the menu text on the desktop. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        int idx4; 
        str string; 
        container conAccountNum; 
        DictTable dictTable; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.foregroundColor(WindowsPalette::MenuText); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add a column to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        } 
    }

### Method getColumn

Retrieves a FormListColumn object for a specified column in a form list control.

    public FormListColumn getColumn(int Idx)

#### Parameters

Idx  
An Integer data type that specifies a column in a form list control.

#### Return Value

A FormListColumn object for a specified column in a form list control.

#### Remarks

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

#### Examples

The following example shows a call to the getColumn method to return a FormListColumn object for the column in the form list control. The FormListControl.addColumn method adds the column to the form list control.

     
    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        str columnName; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add a column to the form list control, 
        // and then set the column width. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
        formListColumn = formListControl.getColumn(0); 
        columnName = formListColumn.toString(); 
    }

### Method getColumnCount

Retrieves the number of columns in a form list control.

    public int getColumnCount()

#### Return Value

An Integer data type value that specifies the number of columns in a form list control.

#### Remarks

To display columns in a form list control, call the FormListControl.viewType method and then pass the FormListViewType::Report enumeration value.

#### Examples

The following example shows a call to the getColumnCount method to return the number of columns in the form list control. The FormListControl.addColumn method adds the column to the form list control.

     
    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListColumn formListColumn; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        int columnCnt; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add a column to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
        columnCnt = formListControl.getColumnCount(); 
    }

### Method getColumnWidth

Retrieves the width of a column in a form list control.

    public int getColumnWidth(int Idx)

#### Parameters

Idx  
An Integer data type that specifies a column in a form list control.

#### Return Value

An Integer data type that specifies the width of a column in a form list control.

#### Remarks

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

#### Examples

The following example shows a call to the getColumnWidth method to return the width of a column in the form list control. The FormListControl.setColumnWidth method specifies the column width. The FormListControl.addColumn method adds the column to the form list control.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        int idx4; 
        DictTable dictTable; 
        CustTable custTable; 
        int width; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add a column to the form list control, 
        // and then set the column width. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
        formListControl.setColumnWidth(0,100); 
        width = formListControl.getColumnWidth(0); 
    }

### Method getCount

Retrieves the number of items that are contained in a form list control.

    public int getCount()

#### Return Value

An Integer data type value that specifies the number of items that are contained in a form list control.

#### Examples

The following example shows a call to the getCount method. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        DictTable dictTable; 
        int idx4; 
        str string; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        } 
        numItems = formListControl.getCount(); 
    }

### Method getCountPerPage

    public int getCountPerPage()

#### Return Value

### Method getImagelist

    public Imagelist getImagelist([boolean GetLarge])

#### Parameters

GetLarge  

#### Return Value

### Method getItem

Retrieves a FormListItem object for an item in a form list control.

    public FormListItem getItem(int Idx, [int SubItem])

#### Parameters

Idx  
An Integer data type that specifies a sub-item in a form list control.

<!-- -->

SubItem  
An Integer data type that specifies a sub-item in a form list control.

#### Return Value

A FormListItem object for an item in a form list control.

#### Examples

The following example shows a call to the getItem method to return a FormListItem object for each item in the form list control. The FormListItem.toString method returns a text string for each item. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        DictTable dictTable; 
        int idx4; 
        boolean columnadd; 
        str string; 
        str itemTxt; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        // Add an item to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
                "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
            formListItem = formListControl.getItem(item); 
            itemTxt = formListItem.toString(); 
        } 
    }

### Method getItemPos

Retrieves the position of an item in a form list control.

    public container getItemPos(int Item)

#### Parameters

Item  
An Integer data type that specifies an item in a form list control.

#### Return Value

A Container data type that contains the position of an item in a form list control. The position of an item is specified by an x-coordinate and a y-coordinate.

#### Remarks

Use the conPeek function to extract an item from a container.

#### Examples

The following example shows a call to the getItemPos method to return the position of each item in the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        DictTable dictTable; 
        int idx4; 
        boolean columnadd; 
        str string; 
        container conAccountNum; 
        container itemPos; 
        CustTable custTable; 
        int numAccounts; 
        int numItems; 
        int i; 
        int x; 
        int item; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        // Add an item to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
            itemPos = formListControl.getItemPos(item); 
            numItems = conlen(itemPos); 
            for(x = 1; x<= numItems; x++) 
            { 
                print conpeek(itemPos,x); 
                pause; 
            } 
        } 
    }

### Method getNextItem

Retrieves the number of the next item in a form list control.

    public int getNextItem(FormListNext nextType, [int startIdx])

#### Parameters

nextType  
An Integer data type that specifies the item that is before the next item.

<!-- -->

startIdx  
An Integer data type that specifies the item that is before the next item.

#### Return Value

An Integer data type value that indicates which item is the next item in a form list control.

#### Examples

The following example shows a call to the getNextItem method to retrieve the number of the next item in the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        DictTable dictTable; 
        int idx4; 
        boolean columnadd; 
        str string; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(77); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = new FormRun(Args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        // Add an item to the form list control. 
        while select custTable 
           where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            formListControl.addItem(formListItem); 
        } 
        item = formListControl.getNextItem(FormListNext::ToRight); 
    }

### Method getSelectedCount

Retrieves the number of items that are selected in a form list control.

    public int getSelectedCount()

#### Return Value

An Integer data type value that indicates the number of items that are selected in a form list control.

#### Examples

The following example shows a call to the getSelectedCount method to return the number of items that are selected in the form list control. The FormListControl.singleSelection method indicates whether multiple items can be selected. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        DictTable dictTable; 
        int idx4; 
        str string; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        int numItemsSel; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        formListControl.singleSelection(false); 
        // Add columns to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1",1,120)); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        } 
        numItemsSel = formListControl.getSelectedCount(); 
    }

### Method getStringWidth

    public int getStringWidth(str Text)

#### Parameters

Text  

#### Return Value

### Method getTopIndex

    public int getTopIndex()

#### Return Value

### Method gridLines

    public boolean gridLines([boolean value])

#### Parameters

value  

#### Return Value

### Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
The value to assign as the hasChanged value for the control; optional.

#### Return Value

true if the contents of the control have changed; otherwise, false.

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

true if the control has custom user settings; otherwise, false.

### Method headerdragdrop

    public boolean headerdragdrop([boolean value])

#### Parameters

value  

#### Return Value

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  
An integer that indicates how the height is calculated; optional. This can be one of the following values:

<!-- -->

mode  
An integer that indicates how the height is calculated; optional. This can be one of the following values:

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

| Mode              | Height calculation                                                                         |
|-------------------|--------------------------------------------------------------------------------------------|
| -1 – Exact        | The exact height of the control in pixels is used.                                         |
| 0 – Auto          | The height of the control is calculated automatically, and the value parameter is ignored. |
| 1 – Column height | The layout of the form determines the height of the control.                               |

The height and the height calculation mode can be set separately.

#### Examples

The following example shows a call to the height method to the set the height of the control to 120 pixels.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form, and then specifiy the control height. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.height(120,-1); 
    }

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An integer that indicates how the height of the control is calculated; optional. This value can be -1 for Exact mode, 0 for Auto mode, or 1 for Column height width.

#### Return Value

The height calculation mode.

#### Remarks

Calculate the height according to the following table.

| Mode          | Height calculation                                                                         |
|---------------|--------------------------------------------------------------------------------------------|
| Exact         | The exact height of the control in pixels is used.                                         |
| Auto          | The height of the control is calculated automatically, and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                               |

The height of the control might change when the calculation mode is set to Auto or Column height.

#### Examples

The following example shows a call to the heightMode method to adjust the height of the control, based on an exact pixel value.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form, and then specifiy the control height. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.heightMode(-1); 
        formListControl.heightValue(120); 
    }

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  
An Integer data type that specifies the height in pixels.

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the Exact height calculation mode is used.

#### Examples

The following example shows a call to the heightValue method that sets the height to 120 pixels.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form, and then specifiy the control height. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.heightMode(-1); 
        formListControl.heightValue(120); 
    }

### Method helpField

Retrieves the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

### Method helpText

Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the Help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hitTest

    public container hitTest(int x, int y)

#### Parameters

x  

<!-- -->

y  

#### Return Value

### Method hitTestSubItem

    public container hitTestSubItem(int x, int y)

#### Parameters

x  

<!-- -->

y  

#### Return Value

### Method hWnd

Retrieves the Windows handle for the control.

    public int hWnd()

#### Return Value

The handle for the control.

#### Remarks

The handle can be used with the Windows API.

### Method isContainer

    public boolean isContainer()

#### Return Value

### Method isDisplayed

Retrieves a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

#### Remarks

To modify the visible state of the control, call the visible method.

### Method isRestricted

Retrieves a value that indicates whether the control is restricted.

    public boolean isRestricted()

#### Return Value

true if the control is restricted; otherwise, false.

### Method isUserSetupEnabled

Gets a value that indicates whether the control allows for the specified level of customization.

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  
A FormAllowUserSetup enumeration value that specifies the level of customization that is being queried for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

#### Remarks

For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter. The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

#### Examples

The following example shows how to determine the user setup rights for a control.

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

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method itemAlign

    public int itemAlign([int value])

#### Parameters

value  

#### Return Value

### Method itemChanging

    public boolean itemChanging(int Idx, AnyType Data)

#### Parameters

Idx  

<!-- -->

Data  

#### Return Value

### Method keyDown

    public boolean keyDown(int vKey, boolean Ctrl, boolean Shift)

#### Parameters

vKey  

<!-- -->

Ctrl  

<!-- -->

Shift  

#### Return Value

### Method leave

Identifies when a user moves focus away from a form list control.

    public boolean leave()

#### Return Value

true if focus is moved away from the control; otherwise, false.

#### Remarks

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click leave. For information about best practices for forms and code, see No Code in Forms.

### Method left

Sets or returns the horizontal position of a form list control in pixels, and specifies how the position is calculated.

    public int left(int value, [int mode])

#### Parameters

value  
An integer that indicates how the position is calculated; optional. This can be one of the following values:

<!-- -->

mode  
An integer that indicates how the position is calculated; optional. This can be one of the following values:

#### Return Value

An integer that indicates the horizontal position of a form list control in pixels.

#### Examples

The following example shows a call to the left method that sets the horizontal position to 50 pixels.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.left(50,-1); 
    }

### Method leftMode

Sets or returns a value that indicates how the horizontal position of a form list control is calculated.

    public int leftMode([int value])

#### Parameters

value  
An integer that indicates how the horizontal position is calculated; optional.

#### Return Value

An integer that indicates how the horizontal position is calculated. The return value can be -1 or a FormLeft enumeration value.

#### Remarks

The value parameter and the return value are integer values that specify how the horizontal position is calculated. This value can be either -1 for an exact pixel value or a FormLeft enumeration value. For more information, see FormLeft Enumeration.

#### Examples

The following example shows a call to the leftMode method that calculates the horizontal position of a form list control, based on an exact pixel value.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.leftMode(-1); 
        formListControl.leftValue(100); 
    }

### Method leftValue

Sets or returns the horizontal position of a form list control in pixels.

    public int leftValue([int value])

#### Parameters

value  
An integer that indicates the horizontal position in pixels; optional.

#### Return Value

An integer that indicates the horizontal position in pixels.

#### Remarks

The horizontal position is not changed unless the left mode is set for an exact pixel value. For more information, see leftMode.

#### Examples

The following example shows a call to the leftValue method that sets the horizontal position to 100 pixels.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form, and then specifiy the control height. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.leftMode(-1); 
        formListControl.leftValue(100); 
    }

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

#### Return Value

true if the control was marked as a user-added control; otherwise, false.

### Method mouseDblClick

Is called when the control is double-clicked by the user.

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseDown

Is called when the user clicks the mouse button over the control.

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method mouseMove

Is called when the user moves the mouse pointer over the control.

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseUp

Identifies when a user presses the left mouse button.

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click mouseUp. For information about best practices for forms and code, see No Code in Forms.

### Method moveItem

Moves a specified item in a form list control.

    public int moveItem(int Item, int InsertAt)

#### Parameters

Item  
An Integer data type that specifies the position in the list that the item is moved to.

<!-- -->

InsertAt  
An Integer data type that specifies the position in the list that the item is moved to.

#### Return Value

An Integer data type that specifies the position in the list that the item is moved to.

#### Examples

The following example shows a call to the moveItem method to move an item to the tenth position in the form list control. The FormListControl.getCount method returns the number of items in the control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        int idx4; 
        str string; 
        container conAccountNum; 
        DictTable dictTable; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(77); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = new FormRun(Args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add columns to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Account Numbers",1,120)); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
                "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        } 
        formListControl.getCount(); 
        formListControl.moveItem(2,10); 
    }

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control; optional.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method oneClickActivate

    public boolean oneClickActivate([boolean value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method redrawItems

Updates a range of items in a form list control.

    public boolean redrawItems(int idxFirst, int idxLast)

#### Parameters

idxFirst  
An Integer data type that specifies the zero-based index for the last item in the range.

<!-- -->

idxLast  
An Integer data type that specifies the zero-based index for the last item in the range.

#### Return Value

true if the items are updated; otherwise, false.

#### Examples

The following example shows a call to the redrawItems method to update a range of items in the form list control. The FormListControl.moveItem method moves a specified item. The FormListControl.getCount method retrieves the number of items in the control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        int idx4; 
        str string; 
        container conAccountNum; 
        DictTable dictTable; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(77); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = new FormRun(Args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add columns to form list control. 
        formListControl.addColumn(1, new FormListColumn("Account Numbers",1,120)); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= "4000" 
                && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        } 
        formListControl.getCount(); 
        formListControl.moveItem(2,10); 
        formListControl.redrawItems(0,20); 
    }

### Method rowSelect

Sets or gets a Boolean data type value that indicates whether a row in a form list control is selected when the row is clicked.

    public boolean rowSelect([boolean value])

#### Parameters

value  
A Boolean data type that indicates whether a row in a form list control is selected when the row is clicked.

#### Return Value

true if the row in a form list control is selected; otherwise, false.

#### Examples

The following example shows a call to the rowSelect method to specify that a row in the form list control is selected when the row is clicked. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method. The columns are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn1; 
        FormListColumn formListColumn2; 
        FormListColumn formListColumn; 
        DictTable dictTable; 
        int idx4; 
        str string; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        formListControl.rowSelect(true); 
        // Add columns to the form list control. 
        formListControl.addColumn(1, new FormListColumn("Column1",1,120)); 
        formListControl.addColumn(2, new FormListColumn("Column2",2,120)); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        }}

### Method scroll

    public boolean scroll(int dx, int dy)

#### Parameters

dx  

<!-- -->

dy  

#### Return Value

### Method securityKey

Sets or returns the ID of the security key for the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The ID of the security key to assign to the control; optional.

#### Return Value

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

### Method selectionChanging

    public boolean selectionChanging(int Idx, AnyType Data)

#### Parameters

Idx  

<!-- -->

Data  

#### Return Value

### Method setColumn

    public boolean setColumn(int Idx, FormListColumn Column)

#### Parameters

Idx  

<!-- -->

Column  

#### Return Value

### Method setColumnWidth

Specifies the width of a column in a form list control.

    public boolean setColumnWidth(int Idx, int Width)

#### Parameters

Idx  
An Integer data type that specifies the width of the column in a form list control.

<!-- -->

Width  
An Integer data type that specifies the width of the column in a form list control.

#### Return Value

true if the width is set; otherwise, false.

#### Remarks

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

#### Examples

The following example shows a call to the setColumnWidth method to specify the width of the column in the form list control. The FormListControl.addColumn method adds the column to the form list control.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::Report); 
        formListControl.height(120); 
        formListControl.widthMode(FormWidth::ColumnWidth); 
        // Add a column to the form list control, and then set the column width. 
        formListControl.addColumn(1, new FormListColumn("Column1")); 
        formListControl.setColumnWidth(0,100); 
    }

### Method setItem

Indicates whether an item is contained in a form list control.

    public boolean setItem(FormListItem item)

#### Parameters

item  
A FormListItem object for an item in a form list control.

#### Return Value

true if an item is contained in a form list control; otherwise, false.

#### Examples

The following example shows a call to the setItem method to determine whether each item is contained in the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        DictTable dictTable; 
        int idx4; 
        str string; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        boolean itemSet; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
                "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
            itemSet = formListControl.setItem(formListItem); 
        } 
    }

### Method setStateImagelist

    public Imagelist setStateImagelist(Imagelist imageList)

#### Parameters

imageList  

#### Return Value

### Method showContextMenu

Identifies when a shortcut menu appears.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
An Integer data type that specifies the menu handle.

#### Return Value

An Integer data type that specifies the menu handle.

#### Remarks

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click showContextMenu. For information about best practices for forms and code, see No Code in Forms.

### Method showSelAlways

    public boolean showSelAlways([boolean value])

#### Parameters

value  

#### Return Value

### Method singleSelection

Indicates whether multiple items can be selected in a form list control.

    public boolean singleSelection([boolean value])

#### Parameters

value  
A Boolean data type that indicates whether multiple items can be selected in a form list control.

#### Return Value

true if multiple items cannot be selected; otherwise, false.

#### Remarks

Call the singleSelection method before you add items to a form list control; otherwise, the items do not appear in the control.

#### Examples

The following example shows a call to the singleSelection method to specify that multiple items can be selected. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void testFormListControl(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        FormListColumn formListColumn1; 
        FormListColumn formListColumn2; 
        FormListColumn formListColumn; 
        DictTable dictTable; 
        int idx4; 
        str string; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        int numItems; 
        boolean columnAdd; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.viewType(FormListViewType::List); 
        formListControl.height(120); 
        formListControl.singleSelection(false); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
                "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
        } 
    }

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
A Boolean value to assign to the skip property of the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method sort

    public int sort([int value])

#### Parameters

value  

#### Return Value

### Method sortTextItems

    public boolean sortTextItems([int column], [boolean ascending])

#### Parameters

column  

<!-- -->

ascending  

#### Return Value

### Method toolTip

Retrieves the tooltip text for the control.

    public str toolTip()

#### Return Value

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

#### Remarks

The method might be overridden to provide a value to the toolTip method.

### Method top

Sets or returns the vertical position of a form list control in pixels, and specifies how the position is calculated.

    public int top(int value, [int mode])

#### Parameters

value  
An integer that indicates how the vertical position is calculated; optional. This parameter can be one of the following values:

<!-- -->

mode  
An integer that indicates how the vertical position is calculated; optional. This parameter can be one of the following values:

#### Return Value

An integer that indicates the vertical position of a form list control in pixels.

#### Examples

The following example shows a call to the top method to set the vertical position to 50 pixels.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.top(50,-1); 
    }

### Method topMode

Sets or returns a value that indicates how the vertical position for a form list control is calculated.

    public int topMode([int value])

#### Parameters

value  
An integer that indicates how the vertical position is calculated; optional.

#### Return Value

An Integer data type value that indicates how the vertical position is calculated. The return value can be -1 or a FormTop enumeration value.

#### Remarks

The value parameter and return value are integer values that can be either -1 for an exact pixel value or a FormTop enumeration value. For more information, see FormTop Enumeration.

#### Examples

The following example shows a call to the topMode method that calculates the vertical position based on an exact pixel value.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.topMode(-1); 
        formListControl.topValue(50); 
    }

### Method topValue

Sets or returns the vertical position of a form list control in pixels.

    public int topValue([int value])

#### Parameters

value  
An integer that specifies the vertical position; optional.

#### Return Value

An integer that specifies the vertical position of a form list control.

#### Remarks

The vertical position is not changed unless the top mode is set for an exact pixel value. For more information, see topMode.

#### Examples

The following example shows a call to the topValue method that sets the vertical position to 50 pixels.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.topMode(-1); 
        formListControl.topValue(50); 
    }

### Method trackSelect

    public boolean trackSelect([boolean value])

#### Parameters

value  

#### Return Value

### Method twoClickActivate

    public boolean twoClickActivate([boolean value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the value of the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control; optional.

#### Return Value

true if the text in the control is underlined; otherwise, false.

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method userData

Gets or sets the user data for the control.

    public int userData([int value])

#### Parameters

value  
An integer value that indicates the user data for the control; optional.

#### Return Value

The user data for the control.

### Method userDataItem

Gets or sets the user data item for the control.

    public int userDataItem([int value])

#### Parameters

value  
An integer value that indicates the user data item for the control; optional.

#### Return Value

The user data item for the control.

### Method userDataItems

Gets or sets the number of user data items for the control.

    public int userDataItems([int value])

#### Parameters

value  
An integer value that indicates the number of user data items for the control; optional.

#### Return Value

The number of user data items for the control.

### Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

    public int userDisable([int value])

#### Parameters

value  
The value that indicates whether the control is disabled for the user; optional.

#### Return Value

1 if the control is disabled for the user; otherwise, 0.

### Method userHeight

Gets or sets the custom user height for the control.

    public int userHeight([int value])

#### Parameters

value  
The user height for the control; optional.

#### Return Value

The custom user height for the control.

### Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
The value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Method userOrgContainer

Gets or sets the organization container for the control.

    public int userOrgContainer([int value])

#### Parameters

value  
The organization container to set for the control; optional.

#### Return Value

The organization container for the control.

### Method userOrgSibling

Gets or sets the organization sibling for the control.

    public int userOrgSibling([int value])

#### Parameters

value  
The organization sibling to set for the control; optional.

#### Return Value

The organization sibling for the control.

### Method userPromptText

Gets or sets the user label text for the control.

    public str userPromptText([str value])

#### Parameters

value  
The user label text to set for the control; optional.

#### Return Value

The user label text for the control.

### Method userSecurityLevel

Gets or sets the user security level for the control.

    public int userSecurityLevel([int value])

#### Parameters

value  
The user security level to set for the control; optional.

#### Return Value

The user security level for the control.

### Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

### Method userWidth

Sets or returns the width of the control in pixels, as specified by the user.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method verticalSpacing

Sets or gets the amount of space above and below a form list control in pixels, and specifies how the space is calculated.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

<!-- -->

mode  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

#### Return Value

An integer that indicates the amount of space above and below a control.

### Method verticalSpacingMode

Sets or returns a value that indicates how the space above and below a form list control is calculated.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

#### Return Value

Auto if the space is automatically adjusted based on other form settings, such as the font size; otherwise, Fixed.

### Method verticalSpacingValue

Sets or returns the amount of space above and below a form list control in pixels.

    public int verticalSpacingValue([int value])

#### Parameters

value  
An integer that indicates the amount of space above and below a control; optional.

#### Return Value

An integer that indicates the amount of space above and below a control.

### Method viewType

    public int viewType([int value])

#### Parameters

value  

#### Return Value

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value to be assigned to the visible setting for the control; optional.

#### Return Value

true if the control is visible; otherwise, false.

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  
An integer that indicates how the width is calculated; optional. This parameter can be one of the following values:

<!-- -->

mode  
An integer that indicates how the width is calculated; optional. This parameter can be one of the following values:

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode             | Width calculation                                                                         |
|------------------|-------------------------------------------------------------------------------------------|
| -1 – Exact       | The exact width of the control in pixels is used.                                         |
| 0 – Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| 1 – Column width | The layout of the form determines the width of the control.                               |

The width and the width calculation mode can be set separately.

#### Examples

The following example shows a call to the width method to set the width of the control to 120 pixels.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.width(120,-1); 
    }

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer that indicates how the width of the control is calculated; optional.

#### Return Value

An integer value that indicates the current width calculation mode.

#### Remarks

Calculate the width according to the following table.

| Mode         | Width calculation                                                                         |
|--------------|-------------------------------------------------------------------------------------------|
| Exact        | The exact width of the control in pixels is used.                                         |
| Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                               |

The width of the control might change when the calculation mode is set to Auto or Column width.

#### Examples

The following example shows a call to the widthMode method to calculate the width of the control, based on an exact pixel value.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.widthMode(-1); 
        formListControl.widthValue(120); 
    }

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An integer that specifies the width of the control in pixels; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

To change the width of the control, use the Exact width calculation mode.

#### Examples

The following example shows a call to the widthValue method that sets the width of the control to 120 pixels.

    static void createForm(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        int idx4; 
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
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        formListControl.widthMode(-1); 
        formListControl.widthValue(120); 
    }

### Method selectionChanged

    public void selectionChanged(int Idx, AnyType Data)

#### Parameters

Idx  

<!-- -->

Data  

### Method activateItem

    public void activateItem(int Idx)

#### Parameters

Idx  

### Method inputSearch

Identifies when the search begins for a specified text string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
A String data type that specifies a text string.

#### Remarks

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click inputSearch. For information about best practices for forms and code, see No Code in Forms.

### Method displayControl

Displays the control.

    public void displayControl()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method update

Updates the control.

    public void update([int idx])

#### Parameters

idx  

### Method endDrag

Identifies when the user has finished moving a form list control.

    public void endDrag()

#### Remarks

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click endDrag. For information about best practices for forms and code, see No Code in Forms.

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method setImagelist

    public void setImagelist(Imagelist imageList, [boolean SetLarge])

#### Parameters

imageList  

<!-- -->

SetLarge  

### Method copy

Identifies when a user performs a copy operation.

    public void copy()

#### Remarks

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click copy. For information about best practices for forms and code, see No Code in Forms.

### Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

### Method itemCopy

    public void itemCopy(int Idx, int newIdx)

#### Parameters

Idx  

<!-- -->

newIdx  

### Method cut

Identifies when the user performs a cut operation.

    public void cut()

#### Remarks

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click cut. For information about best practices for forms and code, see No Code in Forms.

### Method itemMoved

    public void itemMoved(int Idx, int newIdx)

#### Parameters

Idx  

<!-- -->

newIdx  

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method OnSelectionChanged

    private void OnSelectionChanged([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method hotTrackItem

Identifies when a user moves the mouse pointer over a form list control.

    public void hotTrackItem(int Idx)

#### Parameters

Idx  
An Integer data type that specifies the index for a form list control.

#### Remarks

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click hotTrackItem. For information about best practices for forms and code, see No Code in Forms.

### Method setCount

    public void setCount(int count)

#### Parameters

count  

### Method dragLeave

Identifies when a user drags an object out of the bounds of a form list control.

    public void dragLeave()

#### Remarks

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click dragLeave. For information about best practices for forms and code, see No Code in Forms.

### Method itemDeleted

    public void itemDeleted(int Idx, AnyType Data)

#### Parameters

Idx  

<!-- -->

Data  

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setText

    public void setText(int Idx, str Text, [int SubItem])

#### Parameters

Idx  

<!-- -->

Text  

<!-- -->

SubItem  

### Method itemChanged

    public void itemChanged(int Idx, AnyType Data)

#### Parameters

Idx  

<!-- -->

Data  

### Method doubleClick

Identifies when a user double-clicks an item in a form list control.

    public void doubleClick()

#### Remarks

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click doubleClick. For information about best practices for forms and code, see No Code in Forms.

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

### Method allItemsDeleted

Identifies when all the items in a form list control are deleted.

    public void allItemsDeleted()

#### Remarks

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click allItemsDeleted. For information about best practices for forms and code, see No Code in Forms.

### Method drop

Identifies when a user drops a form list control or an item in a form list control into a new position.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An Integer data type that indicates the y-coordinate of the object's position.

<!-- -->

dragMode  
An Integer data type that indicates the y-coordinate of the object's position.

<!-- -->

x  
An Integer data type that indicates the y-coordinate of the object's position.

<!-- -->

y  
An Integer data type that indicates the y-coordinate of the object's position.

#### Remarks

This method is called only if the DragDrop property is set to Manual for the control and a beginDrag event has already been started. For more information about the event, see beginDrag. To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click drop. For information about best practices for forms and code, see No Code in Forms.

### Method columnClicked

Identifies when a user clicks a column in a list view control in a form.

    public void columnClicked(int Column)

#### Parameters

Column  
An Integer data type that specifies a form column.

#### Remarks

To override this method on a list view control, right-click the Methods node below the control, click Override Method, and then click columnClicked. For information about best practices for forms and code, see No Code in Forms.

### Method getStateImagelist

    public void getStateImagelist()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setItemPos

Sets the position of an item in a form list control.

    public void setItemPos(int Item, int x, int y)

#### Parameters

Item  
An Integer data type that specifies the y-coordinate of the position of an item.

<!-- -->

x  
An Integer data type that specifies the y-coordinate of the position of an item.

<!-- -->

y  
An Integer data type that specifies the y-coordinate of the position of an item.

#### Examples

The following example shows a call to the setItemPos method to specify the position of each item in the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

    static void createForm2(Args _args) 
    { 
        Args args; 
        Form form; 
        FormRun formRun; 
        FormBuildDesign formBuildDesign; 
        FormBuildDataSource formBuildDataSource; 
        FormBuildListControl formBuildListControl; 
        FormListControl formListControl; 
        FormListItem formListItem; 
        DictTable dictTable; 
        int idx4; 
        str string; 
        container conAccountNum; 
        CustTable custTable; 
        int numAccounts; 
        int i; 
        int item; 
        // Create the form header. 
        form = new Form(); 
        // Add data sources to the form. 
        dictTable = new DictTable(tableNum(custTable)); 
        formBuildDataSource = form.addDataSource(dictTable.name()); 
        formBuildDataSource.table(dictTable.id()); 
        // Create the form design. 
        formBuildDesign = form.addDesign("Design"); 
        formBuildDesign.caption("myForm"); 
        // Add a form list control. 
        formBuildListControl = 
     formBuildDesign.addControl(FormControlType::ListView,"List"); 
        idx4 = formBuildListControl.id(); 
        args = new Args(); 
        args.object(form); 
        // Create the run-time form. 
        formRun = classfactory.formRunClass(args); 
        formRun.run(); 
        formRun.detach(); 
        formListControl = formRun.control(idx4); 
        // Add items to the form list control. 
        while select custTable 
            where custTable.AccountNum >= 
     "4000" && custTable.AccountNum <= "4040" 
        { 
            conAccountNum += [[custTable.AccountNum]]; 
        } 
        numAccounts = conlen(conAccountNum); 
        for(i = 1; i <= numAccounts; i++) 
        { 
            string = conPeek(conAccountNum,i); 
            formListItem = new FormListItem(string); 
            item = formListControl.addItem(formListItem); 
            formListControl.setItemPos(item,1,5); 
        } 
    }

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method enter

    public void enter()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method context

Identifies when the user opens a shortcut menu in a form list control.

    public void context()

#### Remarks

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click context. For information about best practices for forms and code, see No Code in Forms.

### Method beginEditLabel

    public void beginEditLabel(int Idx)

#### Parameters

Idx  

### Method itemInserted

    public void itemInserted(int Idx, AnyType Data)

#### Parameters

Idx  

<!-- -->

Data  

## Class FormListItem
    class FormListItem extends Object

### Remarks

### Examples

### Methods

| Method                                                         | Description                                          |
|----------------------------------------------------------------|------------------------------------------------------|
| public AnyType data(\[AnyType value\])                         |                                                      |
| public int idx(\[int value\])                                  |                                                      |
| public int image(\[int value\])                                |                                                      |
| public int indent(\[int value\])                               |                                                      |
| public int overlayImage(\[int value\])                         |                                                      |
| public boolean stateChecked(\[boolean value\])                 |                                                      |
| public boolean stateCut(\[boolean value\])                     |                                                      |
| public boolean stateDropHilited(\[boolean value\])             |                                                      |
| public boolean stateFocus(\[boolean value\])                   |                                                      |
| public int stateImage(\[int value\])                           |                                                      |
| public boolean stateSelected(\[boolean value\])                |                                                      |
| public int subItem(\[int value\])                              |                                                      |
| public str text(\[str value\])                                 |                                                      |
| public str toString()                                          | Returns a string that represents the current object. |
| public void finalize()                                         |                                                      |
| public void new(\[str Text\], \[int Image\], \[AnyType Data\]) | Initializes a new instance of the Object class.      |

### Method data

    public AnyType data([AnyType value])

#### Parameters

value  

#### Return Value

### Method idx

    public int idx([int value])

#### Parameters

value  

#### Return Value

### Method image

    public int image([int value])

#### Parameters

value  

#### Return Value

### Method indent

    public int indent([int value])

#### Parameters

value  

#### Return Value

### Method overlayImage

    public int overlayImage([int value])

#### Parameters

value  

#### Return Value

### Method stateChecked

    public boolean stateChecked([boolean value])

#### Parameters

value  

#### Return Value

### Method stateCut

    public boolean stateCut([boolean value])

#### Parameters

value  

#### Return Value

### Method stateDropHilited

    public boolean stateDropHilited([boolean value])

#### Parameters

value  

#### Return Value

### Method stateFocus

    public boolean stateFocus([boolean value])

#### Parameters

value  

#### Return Value

### Method stateImage

    public int stateImage([int value])

#### Parameters

value  

#### Return Value

### Method stateSelected

    public boolean stateSelected([boolean value])

#### Parameters

value  

#### Return Value

### Method subItem

    public int subItem([int value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the Object class.

    public void new([str Text], [int Image], [AnyType Data])

#### Parameters

Text  

<!-- -->

Image  

<!-- -->

Data  

## Class FormManagedHostControl
    class FormManagedHostControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public str assemblyName(\[str value\])                                                                      |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public CLRObject control()                                                                                  |                                                                                                                                                                         |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public boolean hideIfEmpty(\[boolean value\])                                                               |                                                                                                                                                                         |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                   |
| public boolean leave()                                                                                      |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public boolean rTLCapable(\[boolean value\])                                                                |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public int sizing(\[int value\])                                                                            |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public str typeName(\[str value\])                                                                          |                                                                                                                                                                         |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void enter()                                                                                         |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  
The new value for the property; optional.

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The value to assign to the allowEdit property.

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method assemblyName

    public str assemblyName([str value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
The new value for the property; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method calcControlSize

Retrieves the size of the control.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

#### Return Value

The container that holds the width and height.

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key to assign to the control; optional.

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are in effect for the control.

    public List configurationKeyEx()

#### Return Value

A list that contains the IDs of configuration keys that are in effect for the control.

#### Remarks

The returned list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. The returned list also contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

### Method control

    public CLRObject control()

#### Return Value

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method dataRelationPath

Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.

    public str dataRelationPath([str value])

#### Parameters

value  
The string that contains the period-delimited list of relations; optional.

#### Return Value

The period-delimited list of relations that links the field binding of the DataField object to a relative table.

#### Remarks

This method is used by the reference group control to track exactly which relations produce the replacement field that is used. It enables the reference group control to bind consistently to the controls that it contains.

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the FormControl.dragLeave, FormControl.dragOver, and the FormControl.dragOverEx methods to specify the behavior.

### Method dragOver

Raises the dragOver event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragOverEx

Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragText

Retrieves the text that is displayed when the form control is dragged.

    public str dragText()

#### Return Value

The text that is displayed when the control is dragged; an empty string if there is no text to display when the control is dragged.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that specifies whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
The value to assign as the hasChanged value for the control; optional.

#### Return Value

true if the contents of the control have changed; otherwise, false.

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

true if the control has custom user settings; otherwise, false.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  
An Integer that indicates how the height is calculated; optional.

<!-- -->

mode  
An Integer that indicates how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode            | Height calculation                                                                        |
|-----------------|-------------------------------------------------------------------------------------------|
| -1 Exact        | The exact height in pixels of the controls is used.                                       |
| 0 Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An integer value that indicates how control height is calculated; optional.

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode          | Height calculation                                                                        |
|---------------|-------------------------------------------------------------------------------------------|
| Exact         | The exact height in pixels of the controls is used.                                       |
| Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  
An Integer that specifies the height in pixels; optional.

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpField

Retrieves the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

### Method helpText

Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value to set as the Help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Method hideIfEmpty

    public boolean hideIfEmpty([boolean value])

#### Parameters

value  

#### Return Value

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hWnd

Retrieves the Windows handle for the control.

    public int hWnd()

#### Return Value

The handle for the control.

#### Remarks

The handle can be used with the Windows API.

### Method isContainer

    public boolean isContainer()

#### Return Value

### Method isDisplayed

Retrieves a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

#### Remarks

To modify the visible state of the control, call the visible method.

### Method isRestricted

Retrieves a value that indicates whether the control is restricted.

    public boolean isRestricted()

#### Return Value

true if the control is restricted; otherwise, false.

### Method isUserSetupEnabled

Retrieves a value that indicates whether the control allows for the specified level of customization.

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

### Method leave

    public boolean leave()

#### Return Value

### Method left

Gets or sets the horizontal position of the control in the form.

    public int left(int value, [int mode])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method leftMode

Sets the horizontal arrange mode for the control in the form.

    public int leftMode([int value])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal arrange mode for the control in the form.

### Method leftValue

Gets or sets the horizontal position of the control in the form.

    public int leftValue([int value])

#### Parameters

value  
An integer value that indicates the horizontal position of the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

#### Return Value

true if the control was marked as a user-added control; otherwise, false.

### Method mouseDblClick

Is called when the control is double-clicked by the user.

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseDown

Is called when the user clicks the mouse button over the control.

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method mouseMove

Is called when the user moves the mouse pointer over the control.

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseUp

Is called when the user releases the mouse button over the control area.

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method rTLCapable

    public boolean rTLCapable([boolean value])

#### Parameters

value  

#### Return Value

### Method securityKey

Sets or returns the ID of the security key for the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The ID of the security key to assign to the control; optional.

#### Return Value

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

### Method showContextMenu

Shows the shortcut menu for the control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
The ID of the menu to show.

#### Return Value

An integer value that indicates whether the call succeeded.

### Method sizing

    public int sizing([int value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

#### Remarks

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control.

### Method toolTip

Retrieves the tooltip text for the control.

    public str toolTip()

#### Return Value

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

#### Remarks

The method might be overridden to provide a value to the toolTip method.

### Method top

Gets or sets the vertical position of the control in the form.

    public int top(int value, [int mode])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method topMode

Sets the vertical arrange mode for the control in the form.

    public int topMode([int value])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical arrange mode for the control in the form.

### Method topValue

Gets or sets the vertical position of the control in the form.

    public int topValue([int value])

#### Parameters

value  
An integer value that indicates the vertical position of the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method typeName

    public str typeName([str value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method userData

Gets or sets the user data for the control.

    public int userData([int value])

#### Parameters

value  
An integer value that indicates the user data for the control; optional.

#### Return Value

The user data for the control.

### Method userDataItem

Gets or sets the user data item for the control.

    public int userDataItem([int value])

#### Parameters

value  
An integer value that indicates the user data item for the control; optional.

#### Return Value

The user data item for the control.

### Method userDataItems

Gets or sets the number of user data items for the control.

    public int userDataItems([int value])

#### Parameters

value  
An integer value that indicates the number of user data items for the control; optional.

#### Return Value

The number of user data items for the control.

### Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

    public int userDisable([int value])

#### Parameters

value  
The value that indicates whether the control is disabled for the user; optional.

#### Return Value

1 if the control is disabled for the user; otherwise, 0.

### Method userHeight

Gets or sets the custom user height for the control.

    public int userHeight([int value])

#### Parameters

value  
The user height for the control; optional.

#### Return Value

The custom user height for the control.

### Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
The value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Method userOrgContainer

Gets or sets the organization container for the control.

    public int userOrgContainer([int value])

#### Parameters

value  
The organization container to set for the control; optional.

#### Return Value

The organization container for the control.

### Method userOrgSibling

Gets or sets the organization sibling for the control.

    public int userOrgSibling([int value])

#### Parameters

value  
The organization sibling to set for the control; optional.

#### Return Value

The organization sibling for the control.

### Method userPromptText

Gets or sets the user label text for the control.

    public str userPromptText([str value])

#### Parameters

value  
The user label text to set for the control; optional.

#### Return Value

The user label text for the control.

### Method userSecurityLevel

Gets or sets the user security level for the control.

    public int userSecurityLevel([int value])

#### Parameters

value  
The user security level to set for the control; optional.

#### Return Value

The user security level for the control.

### Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

### Method userWidth

Sets or returns the width of the control in pixels, as specified by the user.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode value for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode value for the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method verticalSpacingMode

Sets the vertical spacing mode for the control in the form.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

The vertical spacing mode for the control in the form.

### Method verticalSpacingValue

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacingValue([int value])

#### Parameters

value  
An integer value that indicates the vertical spacing of the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value to assign to the visibility setting for the control; optional.

#### Return Value

true if the control is visible; otherwise, false.

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  
An Integer that indicates how the width is calculated; optional.

<!-- -->

mode  
An Integer that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode           | Width calculation                                                                        |
|----------------|------------------------------------------------------------------------------------------|
| -1 Exact       | The exact width in pixels of the controls is used.                                       |
| 0 Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer value that indicates how control width is calculated; optional.

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode         | Width calculation                                                                        |
|--------------|------------------------------------------------------------------------------------------|
| Exact        | The exact width in pixels of the controls is used.                                       |
| Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An Integer that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method enter

    public void enter()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method drop

Raises the drop event to indicate that a drop operation is being performed on the current control.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method displayControl

Displays the control.

    public void displayControl()

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

### Method setFocus

Sets the focus on the control.

    public void setFocus()

## Class FormMenuButtonControl
    class FormMenuButtonControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                              | Description                                                                                                                                                             |
|---------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int acquireFocus(\[int value\])                                                                              |                                                                                                                                                                         |
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            |                                                                                                                                                                         |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |                                                                                                                                                                         |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) |                                                                                                                                                                         |
| public boolean alignControl(\[boolean value\])                                                                      | Determines whether to align the control.                                                                                                                                |
| public int alignment(\[int value\])                                                                                 |                                                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                         | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                                      | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                                   | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public boolean autoRefreshData(\[boolean value\])                                                                   |                                                                                                                                                                         |
| public int backgroundColor(\[int value\])                                                                           | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                                 | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                                  | Is called when the user starts to drag a form control.                                                                                                                  |
| public boolean big(\[boolean value\])                                                                               |                                                                                                                                                                         |
| public int bold(\[int value\])                                                                                      | Gets or sets the weight of font used to output text in the control.                                                                                                     |
| public int border(\[int value\])                                                                                    | Gets or sets the style of the borderline of the control.                                                                                                                |
| public int bottomMargin(\[int value\])                                                                              |                                                                                                                                                                         |
| public int buttonDisplay(\[int value\])                                                                             | Gets or sets the appearance of the button control.                                                                                                                      |
| public container calcControlSize(int chars, int lines)                                                              | Retrieves the size of the control.                                                                                                                                      |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                               |                                                                                                                                                                         |
| public boolean canContain(FormControl control)                                                                      |                                                                                                                                                                         |
| public int characterSet(\[int value\])                                                                              | Gets or sets the character set of the font.                                                                                                                             |
| public int colorScheme(\[int value\])                                                                               | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                            | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                                    | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public boolean contains(FormControl control)                                                                        |                                                                                                                                                                         |
| public int controlCount()                                                                                           |                                                                                                                                                                         |
| public FormControl controlNum(int controlNo)                                                                        |                                                                                                                                                                         |
| public str countryRegionCodes(\[str value\])                                                                        | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public str dataRelationPath(\[str value\])                                                                          | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public boolean defaultButton(\[boolean value\])                                                                     | Determines whether the button should be the default button in the form.                                                                                                 |
| public str disabledImage(\[str value\])                                                                             | Gets or sets the disabled image of the button.                                                                                                                          |
| public int disabledImageLocation(\[int value\])                                                                     |                                                                                                                                                                         |
| public int disabledResource(\[int value\])                                                                          | Gets or sets the resource ID of the image to use as the disabled button image.                                                                                          |
| public int displayTarget(\[int value\])                                                                             | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                                  | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                               | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                           | Determines whether to enable or disable the object.                                                                                                                     |
| public str font(\[str value\])                                                                                      | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                                  | Gets or sets the size of the font for the control to use.                                                                                                               |
| public boolean forcedToOverflow(\[boolean value\])                                                                  |                                                                                                                                                                         |
| public int foregroundColor(\[int value\])                                                                           | Gets or sets the text color for the control to use.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                          | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                                     | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                          | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                                | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                               | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                              | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                                  | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                           | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                                   | Retrieves the Windows handle for the control.                                                                                                                           |
| public int imageLocation(\[int value\])                                                                             |                                                                                                                                                                         |
| public boolean isContainer()                                                                                        |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                        | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                                       | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean italic(\[boolean value\])                                                                            |                                                                                                                                                                         |
| public str keyTip(\[str value\])                                                                                    |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                            | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMargin(\[int value\])                                                                                |                                                                                                                                                                         |
| public int leftMode(\[int value\])                                                                                  | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                                 | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean markAsUserAdd(\[boolean value\])                                                                     | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                     | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                           | Is called when the user releases the mouse button over the control area.                                                                                                |
| public int moveControl(int controlId, \[int insertAfterId\])                                                        |                                                                                                                                                                         |
| public int multiSelect(\[int value\])                                                                               |                                                                                                                                                                         |
| public str name(\[str value\])                                                                                      | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                          |                                                                                                                                                                         |
| public int needsRecord(\[int value\])                                                                               |                                                                                                                                                                         |
| public str normalImage(\[str value\])                                                                               |                                                                                                                                                                         |
| public int normalResource(\[int value\])                                                                            |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                             |                                                                                                                                                                         |
| public FormControl parentControl()                                                                                  | Retrieves the parent control for the control.                                                                                                                           |
| public boolean primary(\[boolean value\])                                                                           |                                                                                                                                                                         |
| public int rightMargin(\[int value\])                                                                               |                                                                                                                                                                         |
| public boolean saveRecord(\[boolean value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                           | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int shortkey(\[int value\])                                                                                  |                                                                                                                                                                         |
| public int showContextMenu(int menuHandle)                                                                          | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showShortCut(\[boolean value\])                                                                      |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                              | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int style(\[int value\])                                                                                     |                                                                                                                                                                         |
| public str text(\[str value\])                                                                                      |                                                                                                                                                                         |
| public str toolTip()                                                                                                | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                             | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMargin(\[int value\])                                                                                 |                                                                                                                                                                         |
| public int topMode(\[int value\])                                                                                   | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                                  | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                                      |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                         | Sets or returns the underline property for the text in the control.                                                                                                     |
| public boolean SysObsoleteAttribute(container data)                                                                 |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                                  | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                              | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                             | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                               | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                                | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                                  | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                          | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                            | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                            | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                         | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                                  | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                                 | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public boolean useUserLayout(\[boolean value\])                                                                     |                                                                                                                                                                         |
| public boolean value(\[boolean value\])                                                                             |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                        | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                              | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                                      | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                                                           | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                           | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                                 | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                                | Gets or sets the width of the control.                                                                                                                                  |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                           | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void prefColumnSize(int width, int height)                                                                   | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void resetUserSetting()                                                                                      | Resets the user settings for the control.                                                                                                                               |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                               | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                         |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\])         |                                                                                                                                                                         |
| public void arrange()                                                                                               |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                              | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void gotFocus()                                                                                              | Indicates that the control has received focus.                                                                                                                          |
| public void clicked()                                                                                               |                                                                                                                                                                         |
| public void copy()                                                                                                  | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void setFocus()                                                                                              | Sets the focus on the control.                                                                                                                                          |
| public void cut()                                                                                                   | Cuts the contents of the control.                                                                                                                                       |
| private void OnClicked(\[FormControl sender\], \[FormControlEventArgs e\])                                          |                                                                                                                                                                         |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                        |                                                                                                                                                                         |
| public void dragLeave()                                                                                             | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void context()                                                                                               | Shows the shortcut menu for the control.                                                                                                                                |
| public void endDrag()                                                                                               | Is called when the user has finished dragging a form control.                                                                                                           |
| public void mouseLeave()                                                                                            | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                       | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void lostFocus()                                                                                             | Indicates that the control has lost focus.                                                                                                                              |
| public void paste()                                                                                                 | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void displayControl()                                                                                        | Displays the control.                                                                                                                                                   |

### Method acquireFocus

    public int acquireFocus([int value])

#### Parameters

value  

#### Return Value

### Method addControl

    public FormControl addControl(FormControlType controlType, str controlName, [FormControl insertAfter])

#### Parameters

controlType  

<!-- -->

controlName  

<!-- -->

insertAfter  

#### Return Value

### Method addControlEx

    public FormControl addControlEx(str controlClass, str controlName, [FormControl insertAfter])

#### Parameters

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

#### Return Value

### Method addDataField

    public FormControl addDataField(int dataSourceId, FieldId fieldId, [FormControl insertAfter], [int arrayIndex])

#### Parameters

dataSourceId  

<!-- -->

fieldId  

<!-- -->

insertAfter  

<!-- -->

arrayIndex  

#### Return Value

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  
The new value for the property; optional.

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The value to assign to the allowEdit property.

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
The new value for the property; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoRefreshData

    public boolean autoRefreshData([boolean value])

#### Parameters

value  

#### Return Value

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method big

    public boolean big([boolean value])

#### Parameters

value  

#### Return Value

### Method bold

Gets or sets the weight of font used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows:

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

### Method bottomMargin

    public int bottomMargin([int value])

#### Parameters

value  

#### Return Value

### Method buttonDisplay

Gets or sets the appearance of the button control.

    public int buttonDisplay([int value])

#### Parameters

value  

#### Return Value

An integer between zero and five, inclusive.

#### Remarks

The value of the property defines whether the text, the image, or both should be displayed on the button. This property also controls relative positions of text and image if both are displayed.The integer value that is returned contains the appearace of the button control as follows:

| Value | Description                                                      |
|-------|------------------------------------------------------------------|
| 0     | Text only                                                        |
| 1     | Image Only                                                       |
| 2     | Text and image; the image is displayed below the text.           |
| 3     | Text and image; the image is displayed above the text.           |
| 4     | Text and image; the image is displayed to the left of the text.  |
| 5     | Text and image; the image is displayed to the right of the text. |

### Method calcControlSize

Retrieves the size of the control.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

#### Return Value

The container that holds the width and height.

### Method canAddDataField

    public boolean canAddDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])

#### Parameters

dataSourceId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

#### Return Value

### Method canContain

    public boolean canContain(FormControl control)

#### Parameters

control  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

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

The value in the following table is for the Korean language edition of MicrosoftWindows.

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

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value | Style                 |
|-------|-----------------------|
| 0     | Default               |
| 1     | The Windows palette   |
| 2     | The true-color scheme |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key to assign to the control; optional.

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are in effect for the control.

    public List configurationKeyEx()

#### Return Value

A list that contains the IDs of configuration keys that are in effect for the control.

#### Remarks

The returned list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. The returned list also contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

### Method contains

    public boolean contains(FormControl control)

#### Parameters

control  

#### Return Value

### Method controlCount

    public int controlCount()

#### Return Value

### Method controlNum

    public FormControl controlNum(int controlNo)

#### Parameters

controlNo  

#### Return Value

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method dataRelationPath

Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.

    public str dataRelationPath([str value])

#### Parameters

value  
The string that contains the period-delimited list of relations; optional.

#### Return Value

The period-delimited list of relations that links the field binding of the DataField object to a relative table.

#### Remarks

This method is used by the reference group control to track exactly which relations produce the replacement field that is used. It enables the reference group control to bind consistently to the controls that it contains.

### Method defaultButton

Determines whether the button should be the default button in the form.

    public boolean defaultButton([boolean value])

#### Parameters

value  

#### Return Value

true if the button should be the default button; otherwise, false.

### Method disabledImage

Gets or sets the disabled image of the button.

    public str disabledImage([str value])

#### Parameters

value  

#### Return Value

The full name of an image file. The system supports all of the GDI-supported image formats.

#### Remarks

This property has precedence over the disabledResource property. It is used if both of these properties are set.

### Method disabledImageLocation

    public int disabledImageLocation([int value])

#### Parameters

value  

#### Return Value

### Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

    public int disabledResource([int value])

#### Parameters

value  

#### Return Value

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the dragLeave, the dragOver, and the dragOverEx to specify the behavior.

### Method dragOver

Raises the dragOver event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragOverEx

Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragText

Retrieves the text that is displayed when the form control is dragged.

    public str dragText()

#### Return Value

The text that is displayed when the control is dragged; an empty string if there is no text to display when the control is dragged.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method forcedToOverflow

    public boolean forcedToOverflow([boolean value])

#### Parameters

value  

#### Return Value

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
The value to assign as the hasChanged value for the control; optional.

#### Return Value

true if the contents of the control have changed; otherwise, false.

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

true if the control has custom user settings; otherwise, false.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  
An Integer that indicates how the height is calculated; optional.

<!-- -->

mode  
An Integer that indicates how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode            | Height calculation                                                                        |
|-----------------|-------------------------------------------------------------------------------------------|
| -1 Exact        | The exact height in pixels of the controls is used.                                       |
| 0 Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An integer value that indicates how control height is calculated; optional.

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode          | Height calculation                                                                        |
|---------------|-------------------------------------------------------------------------------------------|
| Exact         | The exact height in pixels of the controls is used.                                       |
| Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  
An Integer that specifies the height in pixels; optional.

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpField

Retrieves the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

### Method helpText

Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the Help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hWnd

Retrieves the Windows handle for the control.

    public int hWnd()

#### Return Value

The handle for the control.

#### Remarks

The handle can be used with the Windows API.

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method isContainer

    public boolean isContainer()

#### Return Value

### Method isDisplayed

Retrieves a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

#### Remarks

To modify the visible state of the control, call the visible method.

### Method isRestricted

Retrieves a value that indicates whether the control is restricted.

    public boolean isRestricted()

#### Return Value

true if the control is restricted; otherwise, false.

### Method isUserSetupEnabled

Returns a value that indicates whether the control allows for the specified level of customization.

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false. For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

If the clicked method is overridden, the user is limited to only restricted customization.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method keyTip

    public str keyTip([str value])

#### Parameters

value  

#### Return Value

### Method left

Gets or sets the horizontal position of the control in the form.

    public int left(int value, [int mode])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method leftMargin

    public int leftMargin([int value])

#### Parameters

value  

#### Return Value

### Method leftMode

Sets the horizontal arrange mode for the control in the form.

    public int leftMode([int value])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal arrange mode for the control in the form.

### Method leftValue

Gets or sets the horizontal position of the control in the form.

    public int leftValue([int value])

#### Parameters

value  
An integer value that indicates the horizontal position of the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

#### Return Value

true if the control was marked as a user-added control; otherwise, false.

### Method mouseDblClick

Is called when the control is double-clicked by the user.

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseDown

Is called when the user clicks the mouse button over the control.

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method mouseMove

Is called when the user moves the mouse pointer over the control.

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseUp

Is called when the user releases the mouse button over the control area.

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method moveControl

    public int moveControl(int controlId, [int insertAfterId])

#### Parameters

controlId  

<!-- -->

insertAfterId  

#### Return Value

### Method multiSelect

    public int multiSelect([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method needsRecord

    public int needsRecord([int value])

#### Parameters

value  

#### Return Value

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method primary

    public boolean primary([boolean value])

#### Parameters

value  

#### Return Value

### Method rightMargin

    public int rightMargin([int value])

#### Parameters

value  

#### Return Value

### Method saveRecord

    public boolean saveRecord([boolean value])

#### Parameters

value  

#### Return Value

### Method securityKey

Sets or returns the ID of the security key for the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The ID of the security key to assign to the control; optional.

#### Return Value

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

### Method shortkey

    public int shortkey([int value])

#### Parameters

value  

#### Return Value

### Method showContextMenu

Shows the shortcut menu for the control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
The ID of the menu to show.

#### Return Value

An integer value that indicates whether the call succeeded.

### Method showShortCut

    public boolean showShortCut([boolean value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise false.

#### Remarks

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control.

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method toolTip

Retrieves the tooltip text for the control.

    public str toolTip()

#### Return Value

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

#### Remarks

The method might be overridden to provide a value to the toolTip method.

### Method top

Gets or sets the vertical position of the control in the form.

    public int top(int value, [int mode])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method topMargin

    public int topMargin([int value])

#### Parameters

value  

#### Return Value

### Method topMode

Sets the vertical arrange mode for the control in the form.

    public int topMode([int value])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical arrange mode for the control in the form.

### Method topValue

Gets or sets the vertical position of the control in the form.

    public int topValue([int value])

#### Parameters

value  
An integer value that indicates the vertical position of the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control; optional.

#### Return Value

true if the text in the control is underlined; otherwise false.

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method userData

Gets or sets the user data for the control.

    public int userData([int value])

#### Parameters

value  
An integer value that indicates the user data for the control; optional.

#### Return Value

The user data for the control.

### Method userDataItem

Gets or sets the user data item for the control.

    public int userDataItem([int value])

#### Parameters

value  
An integer value that indicates the user data item for the control; optional.

#### Return Value

The user data item for the control.

### Method userDataItems

Gets or sets the number of user data items for the control.

    public int userDataItems([int value])

#### Parameters

value  
An integer value that indicates the number of user data items for the control; optional.

#### Return Value

The number of user data items for the control.

### Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

    public int userDisable([int value])

#### Parameters

value  
The value that indicates whether the control is disabled for the user; optional.

#### Return Value

1 if the control is disabled for the user; otherwise, 0.

### Method userHeight

Gets or sets the custom user height for the control.

    public int userHeight([int value])

#### Parameters

value  
The user height for the control; optional.

#### Return Value

The custom user height for the control.

### Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
The value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Method userOrgContainer

Gets or sets the organization container for the control.

    public int userOrgContainer([int value])

#### Parameters

value  
The organization container to set for the control; optional.

#### Return Value

The organization container for the control.

### Method userOrgSibling

Gets or sets the organization sibling for the control.

    public int userOrgSibling([int value])

#### Parameters

value  
The organization sibling to set for the control; optional.

#### Return Value

The organization sibling for the control.

### Method userPromptText

Gets or sets the user label text for the control.

    public str userPromptText([str value])

#### Parameters

value  
The user label text to set for the control; optional.

#### Return Value

The user label text for the control.

### Method userSecurityLevel

Gets or sets the user security level for the control.

    public int userSecurityLevel([int value])

#### Parameters

value  
The user security level to set for the control; optional.

#### Return Value

The user security level for the control.

### Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

### Method userWidth

Sets or returns the width of the control in pixels, as specified by the user.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method useUserLayout

    public boolean useUserLayout([boolean value])

#### Parameters

value  

#### Return Value

### Method value

    public boolean value([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode value for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode value for the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method verticalSpacingMode

Sets the vertical spacing mode for the control in the form.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

The vertical spacing mode for the control in the form.

### Method verticalSpacingValue

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacingValue([int value])

#### Parameters

value  
An integer value that indicates the vertical spacing of the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value to assign to the visibility setting for the control; optional.

#### Return Value

true if the control is visible; otherwise, false.

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  
An Integer that indicates how the width is calculated; optional.

<!-- -->

mode  
An Integer that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode           | Width calculation                                                                        |
|----------------|------------------------------------------------------------------------------------------|
| -1 Exact       | The exact width in pixels of the controls is used.                                       |
| 0 Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer value that indicates how control width is calculated; optional.

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode         | Width calculation                                                                        |
|--------------|------------------------------------------------------------------------------------------|
| Exact        | The exact width in pixels of the controls is used.                                       |
| Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An integer value that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method drop

Raises the drop event to indicate that a drop operation is being performed on the current control.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method arrange

    public void arrange()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method clicked

    public void clicked()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method OnClicked

    private void OnClicked([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method displayControl

Displays the control.

    public void displayControl()

## Class FormNotifyEventArgs
    class FormNotifyEventArgs extends Object

### Remarks

### Examples

### Methods

| Method                                                                  | Description                                                  |
|-------------------------------------------------------------------------|--------------------------------------------------------------|
| public FormDataSource formDataSource(\[FormDataSource formDataSource\]) |                                                              |
| public void new()                                                       | Initializes a new instance of the FormNotifyEventArgs class. |

### Method formDataSource

    public FormDataSource formDataSource([FormDataSource formDataSource])

#### Parameters

formDataSource  

#### Return Value

### Method new

Initializes a new instance of the FormNotifyEventArgs class.

    public void new()

