---
# required metadata

title: F Classes - FormGroupControl to FormIntControl
description: This topic contains API reference documentation for classes from FormGroupControl to FormIntControl.
author: RobinARH
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
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 63823
ms.assetid: f28e493d-2766-466d-a597-ef82e87cdfa6
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# F Classes - FormGroupControl to FormIntControl

[!include[banner](../includes/banner.md)]


This topic contains API reference documentation for classes from FormGroupControl to FormIntControl.

Class FormGroupControl
----------------------

    class FormGroupControl extends FormControl

### Remarks

### Examples

### Methods

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
| public int displayTarget(\[int value\])                                                                             | Gets or sets the value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal for Finance and Operations, or in both.                             |
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
| public str name(\[str value\])                                                                                      | Gets or sets the name that is used in code to identify a form, report, table, query, or other Finance and Operations application object.                                                             |
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

### Method addControl

Adds a form control to a form group control.

    public FormControl addControl(FormControlType controlType, str controlName, [FormControl insertAfter])

#### Parameters

controlType  
A value that indicates the position of the control; optional. The default value is nullNothingnullptrunita null reference (Nothing in Visual Basic).

<!-- -->

controlName  
A value that indicates the position of the control; optional. The default value is nullNothingnullptrunita null reference (Nothing in Visual Basic).

<!-- -->

insertAfter  
A value that indicates the position of the control; optional. The default value is nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Return Value

A FormControl object that configures form controls.

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

Adds a table field.

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

A FormControl object that modifies a form control.

### Method alignChild

Sets or returns a Boolean value that indicates whether a form group control is aligned in the same manner as other controls in a form.

    public boolean alignChild([boolean value])

#### Parameters

value  
A Boolean value that indicates whether a form group control is aligned in the same manner as other controls in a form; optional.

#### Return Value

true if a control is aligned; otherwise, false.

### Method alignChildren

Sets or returns a Boolean value that indicates whether the child controls are aligned.

    public boolean alignChildren([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the child controls are aligned; optional.

#### Return Value

true if the child controls are aligned; otherwise, false.

### Method alignControl

Determines whether the control is aligned with other controls.

    public boolean alignControl([boolean value])

#### Parameters

value  
A Boolean value that indicates whether a form group control is aligned with other controls.

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned based on the longest label.

### Method allowEdit

Determines whether the user can modify the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
A Boolean value that indicates whether data can be modified; optional.

#### Return Value

true if the control can be modified; otherwise, false.

#### Remarks

If this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method allowUserSetup

Sets or gets the level of modification that can be performed for a form group control.

    public int allowUserSetup([int value])

#### Parameters

value  
An Integer data type that indicates the level of modification that can be performed; optional.

#### Return Value

An integer value that indicates the level of modification that can be performed.

#### Remarks

You can use a FormAllowUserSetup enumeration value for the value parameter.

### Method arrangeGuide

    public int arrangeGuide([int value])

#### Parameters

value  

#### Return Value

### Method arrangeMethod

Sets or returns an integer value that indicates how controls in a form group control are arranged.

    public int arrangeMethod([int value])

#### Parameters

value  
An integer value that indicates how controls in a form group control are arranged; optional.

#### Return Value

An integer value that indicates how controls in a form group control are arranged.

#### Remarks

You can use an ArrangeMethod enumeration value for the \_value parameter.

### Method arrangeWhen

Sets or returns an integer value that specifies when the controls are arranged.

    public int arrangeWhen([int value])

#### Parameters

value  
An integer value that specifies when the controls are arranged; optional.

#### Return Value

An integer value that specifies when the controls are arranged.

### Method autoDataGroup

Sets or returns a Boolean value that specifies whether a form group control can contain only the fields in the data group that are specified for the control.

    public boolean autoDataGroup([boolean value])

#### Parameters

value  
A Boolean data type that indicates whether a form group control can contain only fields in the data group; optional.

#### Return Value

true if a form group control can contain only fields in the data group; otherwise, false.

#### Remarks

You use the FormGroupControl.dataGroup method to set or return a data group for a form group control.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the system declares a variable of the same name as a form group control; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  
An Integer data type that specifies the background color; optional.

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

### Method backgroundImage

Specifies the background image for a form group control.

    public Image backgroundImage([Image image], [int drawMode])

#### Parameters

image  
An Integer data type that specifies how the image is drawn; optional.

<!-- -->

drawMode  
An Integer data type that specifies how the image is drawn; optional.

#### Return Value

An Image object.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  
An Integer data type that indicates the background style; optional.

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method beginDrag

Is called when the user starts to move a form group control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate for the move event.

<!-- -->

y  
An integer value that indicates the y-coordinate for the move event.

#### Return Value

0 (zero) if the event has been handled.

### Method bold

Gets or sets the weight of font that is used to display text in the control.

    public int bold([int value])

#### Parameters

value  
An integer value that specifies the font weight; optional.

#### Return Value

An integer value between 0 (zero) and 9, inclusive.

#### Remarks

The integer that is returned contains the font weight as follows:

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

### Method bottomMargin

Sets or returns the bottom margin of a form group control in pixels and specifies whether the margin is automatically adjusted.

    public int bottomMargin([int value], [AutoMode mode])

#### Parameters

value  
An AutoMode enumeration value that indicates whether the bottom margin is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

<!-- -->

mode  
An AutoMode enumeration value that indicates whether the bottom margin is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

#### Return Value

An Integer data type value that specifies the bottom margin in pixels.

### Method bottomMarginMode

Sets or returns an AutoMode enumeration value that indicates whether the bottom margin is automatically adjusted.

    public AutoMode bottomMarginMode([AutoMode mode])

#### Parameters

mode  
An AutoMode enumeration value that indicates whether the bottom margin is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

#### Return Value

AutoMode::Auto if the margin is automatically adjusted based on other form settings, such as the font size; otherwise, AutoMode::Fixed.

### Method bottomMarginValue

Sets or returns the bottom margin of a form group control in pixels.

    public int bottomMarginValue([int value])

#### Parameters

value  
An Integer data type that specifies the bottom margin in pixels; optional.

#### Return Value

An Integer data type value that specifies the bottom margin in pixels.

### Method breakable

    public boolean breakable([boolean value])

#### Parameters

value  

#### Return Value

### Method calcControlSize

Calculates the size of a form group control, based on the number of characters and the number of lines.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
An Integer data type that specifies the number of lines.

<!-- -->

lines  
An Integer data type that specifies the number of lines.

#### Return Value

A Container data type value that specifies the size of a form group control.

### Method canAddDataField

Indicates whether a table field can be added.

    public boolean canAddDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])

#### Parameters

dataSourceId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

#### Return Value

true if a table field can be added; otherwise, false.

### Method canContain

Specifies whether a form group control can contain the specified form control.

    public boolean canContain(FormControl control)

#### Parameters

control  
A FormControl object that specifies a form control.

#### Return Value

true if a form group control can contain the specified form control; otherwise, false.

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  
A String data type that specifies the caption text; optional.

#### Return Value

The string that is used as the caption of the control.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  
An Integer data type that specifies the character set for the text font; optional.

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The value that the default character is set to depends on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  
An Integer data type that specifies the color palette for a form group control; optional.

#### Return Value

An integer between 0 (zero) and 2, inclusive.

#### Remarks

The color scheme is defined according to the following table.

| Value | Style                  |
|-------|------------------------|
| 0     | Default.               |
| 1     | The Windows palette.   |
| 2     | The true-color scheme. |

### Method columns

Sets or returns the number of columns in a form group control in pixels, and specifies whether the number is automatically adjusted.

    public int columns([int value], [ColumnsMode mode])

#### Parameters

value  
An AutoMode enumeration value that specifies whether the number of columns is fixed, or whether it is automatically adjusted based on other form settings, such as the form size.

<!-- -->

mode  
An AutoMode enumeration value that specifies whether the number of columns is fixed, or whether it is automatically adjusted based on other form settings, such as the form size.

#### Return Value

An integer value that specifies the number of columns in a form group control in pixels.

### Method columnsMode

Sets or returns a value that indicates whether the number of columns in a form group control is fixed, or whether it is automatically adjusted based on other form settings, such as the form size.

    public ColumnsMode columnsMode([ColumnsMode mode])

#### Parameters

mode  
An AutoMode enumeration value that specifies whether the number of columns is fixed, or whether it is automatically adjusted based on other form settings, such as the form size; optional.

#### Return Value

Automode::Auto if the number of columns is automatically adjusted; otherwise, Automode::Fixed.

### Method columnspace

Sets or returns the amount of space between columns in a form group control in pixels and indicates whether the space is automatically adjusted based on other form settings, such the font size.

    public int columnspace([int value], [AutoMode mode])

#### Parameters

value  
An AutoMode enumeration value that indicates whether the amount of space between columns is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

<!-- -->

mode  
An AutoMode enumeration value that indicates whether the amount of space between columns is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

#### Return Value

An integer value that specifies the space between columns in a form group control in pixels.

### Method columnspaceMode

Sets or returns an AutoMode enumeration value that indicates whether the amount of space between columns in a form group control is automatically adjusted.

    public AutoMode columnspaceMode([AutoMode mode])

#### Parameters

mode  
An AutoMode enumeration value that indicates whether the amount of space between columns is fixed, or whether it is automatically adjusted based on other form settings, such as the font size; optional.

#### Return Value

AutoMode::Auto if the amount of space is automatically adjusted; otherwise, AutoMode::Fixed.

### Method columnspaceValue

Sets or returns the amount of space between columns in a form group control in pixels.

    public int columnspaceValue([int value])

#### Parameters

value  
An Integer data type that specifies the amount of space between columns in a form group control in pixels; optional.

#### Return Value

An integer value that specifies the amount of space between columns in a form group control in pixels.

### Method columnsValue

Sets or returns the number of columns in a form group control.

    public int columnsValue([int value])

#### Parameters

value  
An Integer data type that specifies the number of columns in a form group control; optional.

#### Return Value

An Integer data type value that specifies the number of columns in a form group control.

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
A configurationKeyId system data type that specifies the configuration key ID; optional.

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are activated for a form group control.

    public List configurationKeyEx()

#### Return Value

A List object that contains the IDs of configuration keys that are activated for a form group control.

#### Remarks

The list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. In addition, the returned list contains any configuration key IDs that are applied to the extended data type.

### Method contains

Specifies whether a form group control contains a specified form control.

    public boolean contains(FormControl control)

#### Parameters

control  
A FormControl object that specifies a form control.

#### Return Value

true if a form group control contains the specified form control; otherwise, false.

### Method controlCount

Returns the number of controls in a form group control.

    public int controlCount()

#### Return Value

An Integer data type value that specifies the number of controls in a form group control.

#### Remarks

You can add a control to a form group control by using the FormGroupControl.addControl method.

### Method controlNum

Returns a FormControl object for a specified control in a form group control.

    public FormControl controlNum(int controlNo)

#### Parameters

controlNo  
An Integer data type that specifies a control in a form group control.

#### Return Value

A FormControl object that can be used to modify and provide information about a form control.

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

### Method dataGroup

Sets or returns a data group for a form group control.

    public str dataGroup([str value])

#### Parameters

value  
A String data type that specifies the data group; optional.

#### Return Value

A String data type value that specifies the data group.

#### Remarks

A data group corresponds to a field group on a table that is a data source for the form.

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

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal for Finance and Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether drag-and-drop operations are enabled or disabled for the control.

    public int dragDrop([int value])

#### Parameters

value  
An integer value that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

You use the FormGroupControl.dragLeave and FormGroupControl.dragOver methods to specify the behavior. You can pass a value of true or false for the value parameter.

### Method dragOver

Is called when an object is dragged over the bounds of a form group control.

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Return Value

A FormDrag system enumeration value that indicates whether the object is moved, copied, or not moved to a specified position.

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking dragOver. For information about best practices for forms and code, see No Code in Forms.

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

### Method enableChilds

Specifies whether the child controls are enabled for a form group control.

    public boolean enableChilds([boolean enable])

#### Parameters

enable  
A Boolean value that indicates whether the child controls are enabled; optional.

#### Return Value

true if the child controls are enabled; otherwise, false.

### Method enabled

Determines whether the object is enabled or disabled.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that indicates whether a form group control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property lets you enable or disable controls at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message that provides read-only information.

### Method expand

Specifies whether a form group control is expanded.

    public boolean expand([boolean expand])

#### Parameters

expand  
A Boolean value that indicates whether a form group control is expanded; optional.

#### Return Value

true if a form group control is expanded; otherwise, false.

### Method font

Gets or sets the name of the font that is used for text in a control.

    public str font([str value])

#### Parameters

value  
A String data type that indicates the font for text in a form group control; optional.

#### Return Value

The name of the font that should be used, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the font size to use for text in a control.

    public int fontSize([int value])

#### Parameters

value  
An integer value that indicates the font size in points for text in a form group control; optional.

#### Return Value

The height of the font in points.

### Method frameOptionButton

Sets or returns the option button for a form group control.

    public int frameOptionButton([int value])

#### Parameters

value  
An Integer data type that specifies the type of option button; optional.

#### Return Value

An integer value that specifies the type of option button.

#### Remarks

You can use a FormFrameOptionButton enumeration value for the value parameter.

### Method framePosition

Sets or returns the location of the frame for a form group control.

    public int framePosition([int value])

#### Parameters

value  
An integer value that specifies the location of the frame; optional.

#### Return Value

An integer value that specifies the location of the frame.

### Method frameType

Sets or returns the frame style for a form group control.

    public int frameType([int value])

#### Parameters

value  
An integer value that indicates the frame style for a form group control; optional.

#### Return Value

An integer value that indicates the frame style for a form group control.

#### Remarks

You can use a FormFrameType enumeration value for the value parameter.

### Method hasChanged

Sets or returns a Boolean value that indicates whether the contents of a form group control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
A Boolean value that indicates whether the contents of a form group control have changed; optional.

#### Return Value

true if the contents have changed; otherwise, false.

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
An integer value that indicates how the height is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the height is calculated; optional.

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

The following example shows a call to the height method to the set the control height to 120 pixels.

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

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An integer value that indicates how the height of the control is calculated; optional.

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table.

| Mode          | Height calculation                                                                         |
|---------------|--------------------------------------------------------------------------------------------|
| Exact         | The exact height of the control in pixels is used.                                         |
| Auto          | The height of the control is calculated automatically, and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                               |

The height of the control might change when the calculation mode is set to Auto or Column height.

#### Examples

The following example shows a call to the heightMode method to adjust the control height, based on an exact pixel value.

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

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  
An integer value that specifies the height in pixels; optional.

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the Exact height calculation mode is used.

#### Examples

The following example shows a call to the heightValue method that sets the height to 5 pixels.

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

### Method helpField

Returns the Help text that is displayed in the status bar when a form group control is selected.

    public str helpField()

#### Return Value

A String data type value that contains the Help text.

### Method helpText

Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
A String data type value that contains the Help text.

#### Return Value

The string that should be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Method hideIfEmpty

Sets or gets a Boolean value that indicates whether a form group control is visible when the controls in the group are not visible.

    public boolean hideIfEmpty([boolean value])

#### Parameters

value  
A Boolean value that indicates whether a form group control is visible; optional.

#### Return Value

true if the form group control is not visible; otherwise, false.

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hWnd

Returns a handle for a form group control.

    public int hWnd()

#### Return Value

An integer value that specifies the handle.

### Method isContainer

Indicates whether a form group control is a container.

    public boolean isContainer()

#### Return Value

true if a form group control is a container; otherwise, false.

### Method isDisplayed

Indicates whether a form group control is displayed.

    public boolean isDisplayed()

#### Return Value

true if a form group is displayed; otherwise, false.

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

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false. For this method to return true, the AllowUserSetup property for the design and for all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

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

Sets or returns a Boolean value that indicates whether the text for a form group control is italic.

    public boolean italic([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the text for a form group control is italic; optional.

#### Return Value

true if the text is italic; otherwise, false.

### Method labelBold

Sets or returns the font weight of the label text for a form group control.

    public int labelBold([int value])

#### Parameters

value  
An integer value that specifies the font weight of the label text; optional.

#### Return Value

An integer value that specifies the font weight of the label text.

#### Remarks

For more information about possible values for the value parameter and return value, see the bold method.

### Method labelCharacterSet

Sets or returns the character set of the font for the label text for a form group control.

    public int labelCharacterSet([int value])

#### Parameters

value  
An integer value that specifies the character set of the font for the label text; optional.

#### Return Value

An Integer data type value that specifies the character set of the font for the label text.

#### Remarks

A character set is a group of alphabetical, numeric, and other characters that have some relationship in common. For example, a character set might be used for a specific country/region or language. For a list of possible values for the value parameter, see the characterSet method. For a list of possible return values, see the characterSet method.

### Method labelFont

Sets or returns the font for the label text for a form group control.

    public str labelFont([str value])

#### Parameters

value  
A String data type that specifies the font for the label text; optional.

#### Return Value

A String data type value that specifies the font for the label text.

### Method labelFontSize

Sets or returns the font size of the label text for a form group control.

    public int labelFontSize([int value])

#### Parameters

value  
An integer value that specifies the font size of the label text; optional.

#### Return Value

An integer value that specifies the font size of the label text.

### Method labelItalic

Sets or returns a Boolean data type that indicates whether the label text for a form group control is italic.

    public boolean labelItalic([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the label text is italic; optional.

#### Return Value

true if the label text is italic; otherwise, false.

### Method labelUnderline

Sets or returns a Boolean data type that indicates whether the label text for a form group control is underlined.

    public boolean labelUnderline([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the label text is underlined; optional.

#### Return Value

true if the label text is underlined; otherwise, false.

### Method leave

Is called when the user moves the mouse pointer out of a form group control.

    public boolean leave()

#### Return Value

true if the mouse pointer is moved out of a form group control; otherwise, false.

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking leave. For information about best practices for forms and code, see No Code in Forms.

### Method left

Sets or returns the horizontal position of a form group control in pixels and specifies how the position is calculated.

    public int left(int value, [int mode])

#### Parameters

value  
An integer value that indicates how the position is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the position is calculated; optional.

#### Return Value

An integer value that indicates the horizontal position of a form group control in pixels.

#### Remarks

The mode parameter can be one of the following values:

-   -1 (default) – Use Exact mode, where the value of the value parameter is used exactly.
-   A FormLeft enumeration value.

#### Examples

The following example shows a call to the left method that sets the horizontal position to 50 pixels.

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

### Method leftMargin

Sets or returns the size of the left margin for a form group control in pixels and specifies whether the size is automatically adjusted.

    public int leftMargin([int value], [AutoMode mode])

#### Parameters

value  
An AutoMode enumeration value that specifies whether the size of the left margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

<!-- -->

mode  
An AutoMode enumeration value that specifies whether the size of the left margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

#### Return Value

An integer value that specifies the size of the left margin for a form group control in pixels.

### Method leftMarginMode

Sets or returns a value that indicates whether the size of the left margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.

    public AutoMode leftMarginMode([AutoMode mode])

#### Parameters

mode  
An AutoMode enumeration value that specifies whether the size of the left margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

#### Return Value

Automode::Auto if the size of the left margin is automatically adjusted; otherwise, Automode::Fixed.

### Method leftMarginValue

Sets or returns the size of the left margin for a form group control in pixels.

    public int leftMarginValue([int value])

#### Parameters

value  
An integer value that specifies the size of the left margin for a form group control in pixels; optional.

#### Return Value

An integer value that specifies the size of the left margin for a form group control in pixels.

### Method leftMode

Sets or returns a value that indicates how the horizontal position of a form group control is calculated.

    public int leftMode([int value])

#### Parameters

value  
An Integer data type that indicates how the horizontal position is calculated; optional.

#### Return Value

An Integer data type value that indicates how the horizontal position is calculated: -1 for an exact pixel value, or a FormLeft enumeration value.

#### Examples

The following example shows a call to the leftMode method that calculates the horizontal position of a form group control, based on an exact pixel value.

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

### Method leftValue

Sets or returns the horizontal position of a form group control in pixels.

    public int leftValue([int value])

#### Parameters

value  
An integer value that indicates the horizontal position in pixels; optional.

#### Return Value

An integer value that indicates the horizontal position in pixels.

#### Remarks

The horizontal position is not changed unless the left mode is set for an exact pixel value.

#### Examples

The following example shows a call to the leftValue method that sets the horizontal position to 50 pixels.

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

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

#### Return Value

true if the control was marked as a user-added control; otherwise, false.

### Method mouseDblClick

Is called when the user double-clicks a form group control.

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. The following are the possible values for the button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseDblClick. For information about best practices for forms and code, see No Code in Forms.

### Method mouseDown

Is called when the user presses the mouse button in a form group control.

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. The following are the possible values for the button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseDown. For information about best practices for forms and code, see No Code in Forms.

### Method mouseMove

Is called when the user moves the mouse pointer over a form group control.

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. The following are the possible values for the \_button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseMove. For information about best practices for forms and code, see No Code in Forms.

### Method mouseUp

Is called when the user releases the mouse button over a form group control.

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. The following are the possible values for the \_button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseUp. For information about best practices for forms and code, see No Code in Forms.

### Method moveControl

Moves a specified control.

    public int moveControl(int controlId, [int insertAfterId])

#### Parameters

controlId  
An integer value that indicates which control the specified control is inserted after; optional.

<!-- -->

insertAfterId  
An integer value that indicates which control the specified control is inserted after; optional.

#### Return Value

An Integer data type value that specifies the control ID.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Finance and Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must begin with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method optionValue

Sets or returns the value for the option button that is associated with a form group control.

    public int optionValue([int value])

#### Parameters

value  
An integer value that specifies the value for the option button; optional.

#### Return Value

An integer value that specifies the value for the option button.

#### Remarks

Use the FormGroupControl.frameOptionButton method to set or return the option button for a form group control.

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method rightMargin

Sets or returns the size of the right margin for a form group control in pixels and specifies whether the size is automatically adjusted.

    public int rightMargin([int value], [AutoMode mode])

#### Parameters

value  
An AutoMode enumeration value that specifies whether the size of the right margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

<!-- -->

mode  
An AutoMode enumeration value that specifies whether the size of the right margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

#### Return Value

An integer value that specifies the size of the right margin for a form group control in pixels.

### Method rightMarginMode

Sets or returns a value that indicates whether the size of the right margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.

    public AutoMode rightMarginMode([AutoMode mode])

#### Parameters

mode  
An AutoMode enumeration value that specifies whether the size of the right margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

#### Return Value

An Automode enumeration value that specifies whether the size of the right margin is fixed, or whether it is automatically adjusted: Auto if the size of the right margin is automatically adjusted; otherwise, Fixed.

### Method rightMarginValue

Sets or returns the size of the right margin for a form group control in pixels.

    public int rightMarginValue([int value])

#### Parameters

value  
An integer value that specifies the size of the right margin for a form group control in pixels; optional.

#### Return Value

An integer value that specifies the size of the right margin for a form group control in pixels.

### Method saveFilter

    public boolean saveFilter([boolean value])

#### Parameters

value  

#### Return Value

### Method securityKey

Sets or returns the security key ID for a form group control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
A securityKeyId data type that contains the ID; optional.

#### Return Value

A securityKeyId data type value that contains the ID.

### Method showContextMenu

Shows a shortcut menu for a form group control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
An integer value that specifies the handle for the shortcut menu.

#### Return Value

An integer value that specifies the selection of the user.

### Method skip

Sets or returns a Boolean value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the control is skipped; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method sort

Sorts the controls that are contained in a form group control.

    public int sort([SortOrder sortDirection])

#### Parameters

sortDirection  
A system enumeration value that indicates the sort order for controls; optional.

#### Return Value

An integer value that contains the sort order.

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method toolTip

Returns the text string for the tooltip for a form group control.

    public str toolTip()

#### Return Value

A string value that contains the text for the tooltip.

### Method top

Sets or returns the vertical position of a form group control in pixels and specifies how the position is calculated.

    public int top(int value, [int mode])

#### Parameters

value  
An integer value that indicates how the vertical position is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the vertical position is calculated; optional.

#### Return Value

An integer value that indicates the vertical position of a form group control in pixels.

#### Remarks

The mode parameter can be one of the following values:

-   -1 (default) – Use Exact mode, where the value of the value parameter is used exactly.
-   A FormTop enumeration value.

#### Examples

The following example calls the top method to set the vertical position to 50 pixels.

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

### Method topMargin

Sets or returns the top margin for a form group control in pixels and specifies whether the size is automatically adjusted.

    public int topMargin([int value], [AutoMode mode])

#### Parameters

value  
An AutoMode enumeration value that specifies whether the size of the top margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

<!-- -->

mode  
An AutoMode enumeration value that specifies whether the size of the top margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

#### Return Value

An integer that specifies the size of the top margin for a form group control in pixels.

### Method topMarginMode

Sets or returns a value that indicates whether the size of the top margin for a form group control is fixed, or whether it is automatically adjusted based on other form property settings.

    public AutoMode topMarginMode([AutoMode mode])

#### Parameters

mode  
An Automode enumeration value that specifies whether the size of the top margin is fixed, or whether it is automatically adjusted based on other form property settings; optional.

#### Return Value

An Automode enumeration value of Auto if the size of the top margin is automatically adjusted; otherwise, Fixed.

### Method topMarginValue

    public int topMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method topMode

Sets or returns a value that indicates how the vertical position of a form group control is calculated.

    public int topMode([int value])

#### Parameters

value  
An integer that indicates how the vertical position is calculated; optional.

#### Return Value

An integer value that indicates how the vertical position is calculated: -1 for an exact pixel value, or a FormTop enumeration value.

#### Examples

The following example shows a call to the topMode method that calculates the vertical position, based on an exact pixel value.

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

### Method topValue

Sets or returns the vertical position of a form group control in pixels.

    public int topValue([int value])

#### Parameters

value  
An Integer data type that specifies the vertical position.

#### Return Value

An Integer data type value that specifies the vertical position of a form group control.

#### Remarks

The vertical position is not changed unless the top mode is set for an exact pixel value. For more information, see the topMode method.

#### Examples

The following example shows a call to the topValue method that sets the vertical position to 50 pixels.

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

Sets or returns an integer data type that indicates whether a control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
An integer value that indicates whether a form group control is hidden from the user; optional.

#### Return Value

1 if the form group control is hidden from the user; otherwise, 0.

#### Remarks

The user can hide a form group control by right-clicking the control and then clicking Hide. This method lets you programmatically determine whether the control is hidden.

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

Sets or returns an integer that indicates whether the form group control is skipped when the user presses the TAB key to move to controls.

    public int userSkip([int value])

#### Parameters

value  
An integer that indicates the user setting for whether a form group control is skipped; optional.

#### Return Value

1 if the form group control is skipped; otherwise, 0.

#### Remarks

The user chooses whether to skip a form group control by using the User setup form.

### Method userWidth

Sets or returns an integer that indicates the width of a form group control in pixels.

    public int userWidth([int value])

#### Parameters

value  
An integer that indicates the width of a form group control in pixels; optional.

#### Return Value

An integer value that indicates the width of a form group control in pixels; 0 (zero) if the user did not specify a width.

#### Remarks

The user specifies the width in characters by using the User setup form. This method returns the width in pixels, based on six times the number of characters.

### Method useUserLayout

Specifies whether to use the user-specified layout of a form group control.

    public boolean useUserLayout([boolean value])

#### Parameters

value  
A Boolean value that specifies whether to use the user-specified layout of a form group control; optional.

#### Return Value

true if the user-specified layout of a form group control is used; otherwise, false.

#### Remarks

The user specifies the layout by using the User setup form.

### Method verticalSpacing

Gets or sets the amount of space above and below a form group control in pixels, and specifies how the space is calculated.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

<!-- -->

mode  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

#### Return Value

An integer value that indicates the amount of space above and below a control.

### Method verticalSpacingMode

Sets or returns a value that indicates how the amount of space above and below a form group control is calculated.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

#### Return Value

An AutoMode enumeration that is set to Auto if the space is automatically adjusted based on other form settings, such as the font size; otherwise, Fixed.

### Method verticalSpacingValue

Gets or sets the amount of space above and below a form group control in pixels.

    public int verticalSpacingValue([int value])

#### Parameters

value  
An integer that indicates the amount of space above and below a control; optional.

#### Return Value

An integer value that indicates the amount of space above and below a control.

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

Gets or sets a Boolean data type that displays or hides a form group control.

    public boolean visible([boolean value])

#### Parameters

value  
A Boolean value that displays or hides a form group control; optional.

#### Return Value

true if the form group control is displayed; otherwise, false.

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  
An integer that indicates how the width is calculated. This can be one of the following values:

<!-- -->

mode  
An integer that indicates how the width is calculated. This can be one of the following values:

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

The following example shows a call to the width method to set the control width to 200 pixels.

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

### Method widthMode

Gets or sets the calculation mode for the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer value that indicates how the control width is calculated; optional.

#### Return Value

An integer value that indicates the width current calculation mode.

#### Remarks

Calculate the width according to the following table.

| Mode         | Width calculation                                                                         |
|--------------|-------------------------------------------------------------------------------------------|
| Exact        | The exact width of the control in pixels is used.                                         |
| Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                               |

The width of the control might change when the calculation mode is set to Auto or Column width.

#### Examples

The following example shows a call to the widthMode method to calculate the control width, based on an exact pixel value.

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

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An integer that specifies the width of the control in pixels.

#### Return Value

The width of the control in pixels.

#### Remarks

To change the width of the control, use the Exact width calculation mode.

#### Examples

The following example shows a call to the widthValue method that sets the control width to 200 pixels.

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

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method drop

Is called when a user drops a form group control or an item in a form group control into a new position.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

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

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking drop. For information about best practices for forms and code, see No Code in Forms.

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

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

### Method mouseLeave

Is called when the user moves the mouse pointer away from the control.

    public void mouseLeave()

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseLeave. For information about best practices for forms and code, see No Code in Forms.

### Method context

Is called when the user right-clicks a form group control.

    public void context()

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking context. For information about best practices for forms and code, see No Code in Forms.

### Method copy

Copies a form group control.

    public void copy()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method paste

Pastes a form group control.

    public void paste()

### Method arrange

    public void arrange()

### Method clicked

Is called when a form group control is clicked by the user.

    public void clicked()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method inputSearch

Is called when the user enters a search string in a bound control.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
A String data type that contains search text; optional.

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking inputSearch. For information about best practices for forms and code, see No Code in Forms.

### Method resetUserSetting

Resets the user settings for a form group control.

    public void resetUserSetting()

### Method OnClicked

    private void OnClicked([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lostFocus

Is called when the user brings a form group control out of focus.

    public void lostFocus()

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking lostFocus. For information about best practices for forms and code, see the No Code in Forms form.

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

### Method endDrag

Is called when the user has finished moving a form group control.

    public void endDrag()

### Method jumpRef

Is called when a user clicks the Go to the Main Table Form command on a control shortcut menu in a form group control.

    public void jumpRef()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method filter

Is called when the user right-clicks a form group control and then clicks Filter By Selection.

    public void filter([str filterStr])

#### Parameters

filterStr  
A String data type that specifies the text for the filter; optional.

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking filter. For information about best practices for forms and code, see No Code in Forms.

### Method displayControl

Displays a form group control.

    public void displayControl()

### Method gotFocus

Determines when the user brings a form group control into focus.

    public void gotFocus()

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking gotFocus. For information about best practices for forms and code, see No Code in Forms.

### Method prefColumnSize

Specifies the height and width of columns for a form group control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
An integer value that specifies the height of columns.

<!-- -->

height  
An integer value that specifies the height of columns.

### Method dragLeave

Is called when the user drags an object out of the bounds of a form group control.

    public void dragLeave()

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking dragLeave. For information about best practices for forms and code, see No Code in Forms.

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method enter

Is called when the user moves focus to a form group control.

    public void enter()

#### Remarks

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking enter. For information about best practices for forms and code, see No Code in Forms.

### Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

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

#### Remarks

The following are the possible values for the button parameter.

|     |                      |
|-----|----------------------|
| 1   | Left mouse button.   |
| 2   | Middle mouse button. |
| 3   | Right mouse button.  |

You can override this method in a form group control by right-clicking the Methods node below the control, clicking Override Method, and then clicking mouseEnter. For information about best practices for forms and code, see No Code in Forms.

## Class FormGuidControl
    class FormGuidControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                                                         |
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
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int direction(\[int value\])                                                                         |                                                                                                                                                                         |
| public int displayHeight(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayHeightMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayHeightValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal for Finance and Operations, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
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
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
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
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Finance and Operations application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public container posFromChar(int charIndex)                                                                 |                                                                                                                                                                         |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean replaceOnLookup(\[boolean value\])                                                           |                                                                                                                                                                         |
| public int searchAfterInput(\[int value\])                                                                  |                                                                                                                                                                         |
| public int searchMode(\[int value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public int style(\[int value\])                                                                             |                                                                                                                                                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
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
| public int userFastTabSummary(\[int value\])                                                                |                                                                                                                                                                         |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                                     |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public Guid value(\[Guid value\])                                                                           |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void setCursorPos(int x, int y)                                                                      |                                                                                                                                                                         |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void performDBLookup(\[FieldId fieldId\], \[TableId tableId\], \[SelectableDataArea company\])       |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void lineScroll(int dx, int dy)                                                                      |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void performFormLookup(xFormRun form)                                                                |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void scrollCursor()                                                                                  |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void setSelection(int charIndexFrom, int charIndexTo)                                                |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void pasteText(str pasteStr, \[boolean InsertSel\])                                                  |                                                                                                                                                                         |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void performTypeLookup(\[int userType\], \[int arrayIndex\], \[SelectableDataArea company\])         |                                                                                                                                                                         |
| public void textChange()                                                                                    |                                                                                                                                                                         |
| public void lookup()                                                                                        |                                                                                                                                                                         |

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
The value to assign to the property.

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

### Method charFromPos

    public int charFromPos(int x, int y)

#### Parameters

x  

<!-- -->

y  

#### Return Value

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

### Method dataFieldArrayIndex

    public int dataFieldArrayIndex()

#### Return Value

### Method dataFieldName

    public FieldName dataFieldName()

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

### Method direction

    public int direction([int value])

#### Parameters

value  

#### Return Value

### Method displayHeight

    public int displayHeight([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayHeightMode

    public AutoMode displayHeightMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayHeightValue

    public int displayHeightValue([int value])

#### Parameters

value  

#### Return Value

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

Gets or sets the value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal for Finance and Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal, or in both.

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
A Boolean value that specifies whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method fastTabSummary

    public int fastTabSummary([int value])

#### Parameters

value  

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

### Method getCursorPos

    public container getCursorPos()

#### Return Value

### Method getFirstVisibleLine

    public int getFirstVisibleLine()

#### Return Value

### Method getLine

    public str getLine(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method getLineCount

    public int getLineCount()

#### Return Value

### Method getSelection

    public container getSelection()

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
An Integer that indicates how the height is calculated; optional.

<!-- -->

mode  
An Integer that indicates how the height is calculated; optional.

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
An integer value that indicates how control height is calculated; optional.

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
The value to assign as the Help text for the control.

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

### Method iMEMode

    public int iMEMode([int value])

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
A FormAllowUserSetup enumeration value that specifies the level of customization that is being requested for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false. For this method to return true, the AllowUserSetup property for the design and all parent containers must be at least as high as the level that is specified by the neededSetupRights parameter.

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

### Method limitText

    public int limitText([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method limitTextMode

    public AutoMode limitTextMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method limitTextValue

    public int limitTextValue([int value])

#### Parameters

value  

#### Return Value

### Method lineFromChar

    public int lineFromChar(int charIndex)

#### Parameters

charIndex  

#### Return Value

### Method lineIndex

    public int lineIndex(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method lineLength

    public int lineLength(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method lookupButton

    public int lookupButton([int value])

#### Parameters

value  

#### Return Value

### Method mandatory

    public boolean mandatory([boolean value])

#### Parameters

value  

#### Return Value

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

Gets or sets the name that is used in code to identify a form, report, table, query, or other Finance and Operations application object.

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

### Method posFromChar

    public container posFromChar(int charIndex)

#### Parameters

charIndex  

#### Return Value

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

### Method replaceOnLookup

    public boolean replaceOnLookup([boolean value])

#### Parameters

value  

#### Return Value

### Method searchAfterInput

    public int searchAfterInput([int value])

#### Parameters

value  

#### Return Value

### Method searchMode

    public int searchMode([int value])

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

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method sort

    public int sort([SortOrder sortDirection])

#### Parameters

sortDirection  

#### Return Value

### Method style

    public int style([int value])

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

### Method userFastTabSummary

    public int userFastTabSummary([int value])

#### Parameters

value  

#### Return Value

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

### Method value

    public Guid value([Guid value])

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
An Integer that indicates how the width is calculated; optional.

<!-- -->

mode  
An Integer that indicates how the width is calculated; optional.

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
An integer value that indicates how control width is calculated; optional.

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
An Integer that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method setCursorPos

    public void setCursorPos(int x, int y)

#### Parameters

x  

<!-- -->

y  

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

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

### Method performDBLookup

    public void performDBLookup([FieldId fieldId], [TableId tableId], [SelectableDataArea company])

#### Parameters

fieldId  

<!-- -->

tableId  

<!-- -->

company  

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method enter

    public void enter()

### Method displayControl

Displays the control.

    public void displayControl()

### Method undo

    public void undo()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method lineScroll

    public void lineScroll(int dx, int dy)

#### Parameters

dx  

<!-- -->

dy  

### Method cut

Cuts the contents of the control.

    public void cut()

### Method performFormLookup

    public void performFormLookup(xFormRun form)

#### Parameters

form  

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

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

### Method jumpRef

    public void jumpRef()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method scrollCursor

    public void scrollCursor()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setSelection

    public void setSelection(int charIndexFrom, int charIndexTo)

#### Parameters

charIndexFrom  

<!-- -->

charIndexTo  

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

### Method pasteText

    public void pasteText(str pasteStr, [boolean InsertSel])

#### Parameters

pasteStr  

<!-- -->

InsertSel  

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method performTypeLookup

    public void performTypeLookup([int userType], [int arrayIndex], [SelectableDataArea company])

#### Parameters

userType  

<!-- -->

arrayIndex  

<!-- -->

company  

### Method textChange

    public void textChange()

### Method lookup

    public void lookup()

## Class FormHTMLControl
    class FormHTMLControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                                                 |
| public str className(\[str value\])                                                                         |                                                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public str custom(\[str value\])                                                                            |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public AnyType dispatch(VarArg )                                                                            |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal for Finance and Operations, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public COMError error()                                                                                     |                                                                                                                                                                         |
| public str getText()                                                                                        |                                                                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public ComInterface interface()                                                                             |                                                                                                                                                                         |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean leave()                                                                                      |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Finance and Operations application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public str processPicture(str picture)                                                                      |                                                                                                                                                                         |
| public boolean rTLCapable(\[boolean value\])                                                                |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
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
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void insertText(str Text, \[NoYes repaint\])                                                         |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void processBase(str base)                                                                           |                                                                                                                                                                         |
| public void setFont(int fontid, HtmlFont htmlFont, \[NoYes repaint\])                                       |                                                                                                                                                                         |
| public void getFont(int fontid, HtmlFont htmlFont)                                                          |                                                                                                                                                                         |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void updateSize()                                                                                    |                                                                                                                                                                         |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void processLink(str link)                                                                           |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void processTitle(str title)                                                                         |                                                                                                                                                                         |
| public void read(str FileName, \[str TagName\])                                                             |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void setText(str Text, \[str TagName\])                                                              |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void save(str FileName)                                                                              |                                                                                                                                                                         |
| public void command(int command)                                                                            |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void insertLink(str Text, str Url, str Name, \[NoYes repaint\])                                      |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void clearWindow()                                                                                   |                                                                                                                                                                         |
| public void processForm(int formHandle)                                                                     |                                                                                                                                                                         |
| public void setMargin(int Left, int Right, int Top, int Bottom, \[NoYes repaint\])                          |                                                                                                                                                                         |

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

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
If supplied, the property is set to this value.

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

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method className

    public str className([str value])

#### Parameters

value  

#### Return Value

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

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method custom

    public str custom([str value])

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

### Method dispatch

    public AnyType dispatch(VarArg )

#### Parameters

  

#### Return Value

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal for Finance and Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal, or in both.

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
A Boolean value that specifies whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method error

    public COMError error()

#### Return Value

### Method getText

    public str getText()

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
An integer that indicates how the height is calculated; optional.

<!-- -->

mode  
An integer that indicates how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

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
An integer value that indicates how control height is calculated; optional.

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
An integer that specifies the height in pixels; optional.

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
The value to assign as the Help text for the control.

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

### Method interface

    public ComInterface interface()

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
A FormAllowUserSetup enumeration value that specifies the level of customization that is being requested for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false. For this method to return true, the AllowUserSetup property for the design and all parent containers must be at least as high as the level that is specified by the neededSetupRights parameter.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

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

Gets or sets the name that is used in code to identify a form, report, table, query, or other Finance and Operations application object.

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

### Method processPicture

    public str processPicture(str picture)

#### Parameters

picture  

#### Return Value

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

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

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
An integer that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer that indicates how the width is calculated; optional.

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
An integer value that indicates how control width is calculated; optional.

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
An integer that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method insertText

    public void insertText(str Text, [NoYes repaint])

#### Parameters

Text  

<!-- -->

repaint  

### Method cut

Cuts the contents of the control.

    public void cut()

### Method processBase

    public void processBase(str base)

#### Parameters

base  

### Method setFont

    public void setFont(int fontid, HtmlFont htmlFont, [NoYes repaint])

#### Parameters

fontid  

<!-- -->

htmlFont  

<!-- -->

repaint  

### Method getFont

    public void getFont(int fontid, HtmlFont htmlFont)

#### Parameters

fontid  

<!-- -->

htmlFont  

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

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

### Method updateSize

    public void updateSize()

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

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method displayControl

Displays the control.

    public void displayControl()

### Method processLink

    public void processLink(str link)

#### Parameters

link  

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method processTitle

    public void processTitle(str title)

#### Parameters

title  

### Method read

    public void read(str FileName, [str TagName])

#### Parameters

FileName  

<!-- -->

TagName  

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setText

    public void setText(str Text, [str TagName])

#### Parameters

Text  

<!-- -->

TagName  

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

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

### Method save

    public void save(str FileName)

#### Parameters

FileName  

### Method command

    public void command(int command)

#### Parameters

command  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method insertLink

    public void insertLink(str Text, str Url, str Name, [NoYes repaint])

#### Parameters

Text  

<!-- -->

Url  

<!-- -->

Name  

<!-- -->

repaint  

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method enter

    public void enter()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method clearWindow

    public void clearWindow()

### Method processForm

    public void processForm(int formHandle)

#### Parameters

formHandle  

### Method setMargin

    public void setMargin(int Left, int Right, int Top, int Bottom, [NoYes repaint])

#### Parameters

Left  

<!-- -->

Right  

<!-- -->

Top  

<!-- -->

Bottom  

<!-- -->

repaint  

## Class FormIntControl
    class FormIntControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public int allowNegative(\[int value\])                                                                     |                                                                                                                                                                         |
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
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int direction(\[int value\])                                                                         |                                                                                                                                                                         |
| public int displaceNegative(\[int value\], \[AutoMode mode\])                                               |                                                                                                                                                                         |
| public AutoMode displaceNegativeMode(\[AutoMode mode\])                                                     |                                                                                                                                                                         |
| public int displaceNegativeValue(\[int value\])                                                             |                                                                                                                                                                         |
| public int displayHeight(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayHeightMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayHeightValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal for Finance and Operations, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
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
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
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
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Finance and Operations application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public container posFromChar(int charIndex)                                                                 |                                                                                                                                                                         |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean replaceOnLookup(\[boolean value\])                                                           |                                                                                                                                                                         |
| public int rotateSign(\[int value\])                                                                        |                                                                                                                                                                         |
| public int searchAfterInput(\[int value\])                                                                  |                                                                                                                                                                         |
| public int searchMode(\[int value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public int showZero(\[int value\])                                                                          |                                                                                                                                                                         |
| public int signDisplay(\[int value\])                                                                       |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public int style(\[int value\])                                                                             |                                                                                                                                                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
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
| public int userFastTabSummary(\[int value\])                                                                |                                                                                                                                                                         |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                                     |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public int value(\[int value\])                                                                             |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void performTypeLookup(\[int userType\], \[int arrayIndex\], \[SelectableDataArea company\])         |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void textChange()                                                                                    |                                                                                                                                                                         |
| public void pasteText(str pasteStr, \[boolean InsertSel\])                                                  |                                                                                                                                                                         |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void scrollCursor()                                                                                  |                                                                                                                                                                         |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void setSelection(int charIndexFrom, int charIndexTo)                                                |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void performDBLookup(\[FieldId fieldId\], \[TableId tableId\], \[SelectableDataArea company\])       |                                                                                                                                                                         |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void setCursorPos(int x, int y)                                                                      |                                                                                                                                                                         |
| public void lineScroll(int dx, int dy)                                                                      |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void performFormLookup(xFormRun form)                                                                |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

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

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowNegative

    public int allowNegative([int value])

#### Parameters

value  

#### Return Value

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

### Method charFromPos

    public int charFromPos(int x, int y)

#### Parameters

x  

<!-- -->

y  

#### Return Value

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

### Method dataFieldArrayIndex

    public int dataFieldArrayIndex()

#### Return Value

### Method dataFieldName

    public FieldName dataFieldName()

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

### Method direction

    public int direction([int value])

#### Parameters

value  

#### Return Value

### Method displaceNegative

    public int displaceNegative([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displaceNegativeMode

    public AutoMode displaceNegativeMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displaceNegativeValue

    public int displaceNegativeValue([int value])

#### Parameters

value  

#### Return Value

### Method displayHeight

    public int displayHeight([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayHeightMode

    public AutoMode displayHeightMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayHeightValue

    public int displayHeightValue([int value])

#### Parameters

value  

#### Return Value

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

Gets or sets the value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal for Finance and Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Finance and Operations client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

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

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method fastTabSummary

    public int fastTabSummary([int value])

#### Parameters

value  

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

### Method getCursorPos

    public container getCursorPos()

#### Return Value

### Method getFirstVisibleLine

    public int getFirstVisibleLine()

#### Return Value

### Method getLine

    public str getLine(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method getLineCount

    public int getLineCount()

#### Return Value

### Method getSelection

    public container getSelection()

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

<!-- -->

mode  

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

### Method iMEMode

    public int iMEMode([int value])

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

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

#### Remarks

For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter. The following table describes the values for the neededSetupRights parameter.

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

### Method limitText

    public int limitText([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method limitTextMode

    public AutoMode limitTextMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method limitTextValue

    public int limitTextValue([int value])

#### Parameters

value  

#### Return Value

### Method lineFromChar

    public int lineFromChar(int charIndex)

#### Parameters

charIndex  

#### Return Value

### Method lineIndex

    public int lineIndex(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method lineLength

    public int lineLength(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method lookupButton

    public int lookupButton([int value])

#### Parameters

value  

#### Return Value

### Method mandatory

    public boolean mandatory([boolean value])

#### Parameters

value  

#### Return Value

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

Gets or sets the name that is used in code to identify a form, report, table, query, or other Finance and Operations application object.

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

### Method posFromChar

    public container posFromChar(int charIndex)

#### Parameters

charIndex  

#### Return Value

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

### Method replaceOnLookup

    public boolean replaceOnLookup([boolean value])

#### Parameters

value  

#### Return Value

### Method rotateSign

    public int rotateSign([int value])

#### Parameters

value  

#### Return Value

### Method searchAfterInput

    public int searchAfterInput([int value])

#### Parameters

value  

#### Return Value

### Method searchMode

    public int searchMode([int value])

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

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method showZero

    public int showZero([int value])

#### Parameters

value  

#### Return Value

### Method signDisplay

    public int signDisplay([int value])

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

### Method sort

    public int sort([SortOrder sortDirection])

#### Parameters

sortDirection  

#### Return Value

### Method style

    public int style([int value])

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

### Method userFastTabSummary

    public int userFastTabSummary([int value])

#### Parameters

value  

#### Return Value

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

### Method value

    public int value([int value])

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

<!-- -->

mode  

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

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

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

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method jumpRef

    public void jumpRef()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method performTypeLookup

    public void performTypeLookup([int userType], [int arrayIndex], [SelectableDataArea company])

#### Parameters

userType  

<!-- -->

arrayIndex  

<!-- -->

company  

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

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method textChange

    public void textChange()

### Method pasteText

    public void pasteText(str pasteStr, [boolean InsertSel])

#### Parameters

pasteStr  

<!-- -->

InsertSel  

### Method lookup

    public void lookup()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method scrollCursor

    public void scrollCursor()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

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

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method setSelection

    public void setSelection(int charIndexFrom, int charIndexTo)

#### Parameters

charIndexFrom  

<!-- -->

charIndexTo  

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method enter

    public void enter()

### Method performDBLookup

    public void performDBLookup([FieldId fieldId], [TableId tableId], [SelectableDataArea company])

#### Parameters

fieldId  

<!-- -->

tableId  

<!-- -->

company  

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method displayControl

Displays the control.

    public void displayControl()

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

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

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method undo

    public void undo()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method setCursorPos

    public void setCursorPos(int x, int y)

#### Parameters

x  

<!-- -->

y  

### Method lineScroll

    public void lineScroll(int dx, int dy)

#### Parameters

dx  

<!-- -->

dy  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method performFormLookup

    public void performFormLookup(xFormRun form)

#### Parameters

form  

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  





