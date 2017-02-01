---
# required metadata

title: F Classes - FormChangeTracker to FormControlEventArgs | Microsoft Docs
description: API reference for classes from FormChangeTracker to FormControlEventArgs.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-08 23:54:18
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
ms.custom: 63793
ms.assetid: 7d9fbdd8-95df-4c82-8cfa-a0158c8e264e
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# F Classes - FormChangeTracker to FormControlEventArgs

API reference for classes from FormChangeTracker to FormControlEventArgs.

Class FormChangeTracker
-----------------------

    class FormChangeTracker extends Object

### Remarks

### Examples

### Methods

| Method                                         | Description |
|------------------------------------------------|-------------|
| public void notifyUpdate(\[str propertyName\]) |             |
| private void new()                             |             |

### Method notifyUpdate

    public void notifyUpdate([str propertyName])

#### Parameters

propertyName  

### Method new

    private void new()

## Class FormCheckBoxControl
    class FormCheckBoxControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public boolean checked(\[boolean check\])                                                                   | Gets or sets the value of a check box.                                                                                                                                  |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean drawFocusRect(\[boolean value\])                                                             |                                                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                   |
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
| public boolean optionalRecordControl(\[boolean value\])                                                     |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
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
| public int value(\[int value\])                                                                             |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void clicked()                                                                                       |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| private void OnClicked(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void undo()                                                                                          |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

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

### Method checked

Gets or sets the value of a check box.

    public boolean checked([boolean check])

#### Parameters

check  
A Boolean value that indicates whether the check box is selected; optional. A value of true selects the check box, and a value of false clears it.

#### Return Value

true if the check box is selected; otherwise false.

#### Remarks

This method uses the Win32 API to get and set the value of the check box without querying the properties.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

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
The string that contains the country region/codes to set; optional.

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

### Method drawFocusRect

    public boolean drawFocusRect([boolean value])

#### Parameters

value  

#### Return Value

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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

<!-- -->

mode  

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

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet.The help text must not exceed 250 characters.

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

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

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

### Method optionalRecordControl

    public boolean optionalRecordControl([boolean value])

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
The ID of the security key being assigned to the control; optional.

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

#### Remarks

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control.

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
The value to assign to the visible setting for the control; optional.

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

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

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

### Method clicked

    public void clicked()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method jumpRef

    public void jumpRef()

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnClicked

    private void OnClicked([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method undo

    public void undo()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

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

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method displayControl

Displays the control.

    public void displayControl()

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

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

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method enter

    public void enter()

### Method lookup

    public void lookup()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method cut

Cuts the contents of the control.

    public void cut()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

## Class FormComboBoxControl
    class FormComboBoxControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether the control should be aligned with other controls.                                                                                                   |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can modify the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean appendNew(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determines whether the control’s background can be transparent.                                                                                                         |
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
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
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
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
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

### Method alignControl

Determines whether the control should be aligned with other controls.

    public boolean alignControl([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the form combo box control is aligned with other controls; optional.

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned based on the longest label.

#### Examples

The following example shows a call to the alignControl method to align a form combo box control with other controls, based on the length of the longest label.

    boolean bAlign; 
    // The combo variable was previously assigned 
    // as a FormComboBoxControl type. 
    // Retrieve the alignControl property. 
    bAlign = combo.alignControl(); 
    // Set the alignControl property. 
    combo.alignControl(false);

### Method allowEdit

Determines whether the user can modify the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The value to assign to the allowEdit property; optional.

#### Return Value

true if the control can be modified; otherwise, false.

#### Remarks

If this property is set on a container control, modifications are disabled or enabled for all controls in the container.

#### Examples

The following example shows how to return and set the value of the allowEdit property.

    // Return the value. 
    info (strfmt("allowEdit: %1", this.allowEdit())); 
    // Set the value. 
    this.allowEdit(false);

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method appendNew

    public boolean appendNew([boolean value])

#### Parameters

value  

#### Return Value

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
The value to assign to the autoDeclaration property; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  
The value to assign as the background color of the control; optional. This can be one of the values from the control’s color scheme or a Winapi::RGB2int value.

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains the RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

#### Examples

The following example shows how to return and set the background color for a control.

    // Retrieve the existing background color. 
    info (strfmt("Background color: %1", this.backgroundColor())); 
    // Set the background color. 
    this.backgroundColor(WindowsPalette::DarkShadow3D);

### Method backStyle

Determines whether the control’s background can be transparent.

    public int backStyle([int value])

#### Parameters

value  
The value to assign as the background style of the control; optional.

#### Return Value

1 if the control background can be transparent; otherwise, 0.

#### Examples

The following example shows how to return and set the background style.

    // Return the background style. 
    info (strfmt("Background style: %1", this.backStyle())); 
    // Set the background style. 
    this.backStyle(FormBackStyle::Transparent);

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

#### Examples

The following example displays the x-coordinate and y-coordinate in the Infolog when the user starts to drag the form combo box control.

    public int beginDrag(int _x, int _y) 
    { 
        int ret; 
        info(strfmt("beginDrag (x, y) : (%1, %2)", _x, _y)); 
        ret = super(_x, _y); 
        return ret; 
    }

### Method bold

Gets or sets the weight of font that is used to display text in the control.

    public int bold([int value])

#### Parameters

value  
The value to assign to the control's bold setting; optional.

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

### Method border

Gets or sets the style of the border line for the control.

    public int border([int value])

#### Parameters

value  
The value to assign as the border style for the control; optional.

#### Return Value

An integer between 0 (zero) and 4, inclusive.

#### Remarks

The integer that is returned contains the border style line as follows.

-   0 – Auto.
-   1 – 3D.
-   2 – Single line.
-   3 – Flat.
-   4 – None.

#### Examples

The following example shows how to retrieve and set the border style for a control.

    // Retrieve the border style. 
    info (strfmt("border: %1", this.border())); 
    // Set the border style. 
    this.border(2);

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

### Method comboType

Sets or returns the type of combo box for the control.

    public int comboType([int value])

#### Parameters

value  
The value to assign as the type of combo box for the control; optional.

#### Return Value

The type of combo box for the control.

#### Remarks

The following table shows the values for the combo box type.

| Value | Description |
|-------|-------------|
| 0     | Standard    |
| 1     | List        |

#### Examples

The following example shows how to retrieve and set the type of combo box that is used for the control.

    // Retrieve the type of combo box control. 
    info(strfmt("comboType: %1", this.comboType())); 
    // Set the type of combo box control. 
    this.comboType(1);

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key to assign to the control.

#### Return Value

The ID of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

#### Examples

The following example shows the setting and retrieval of the configuration key for a control.

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

### Method configurationKeyEx

Returns a list that contains the IDs of configuration keys that are in effect for the control.

    public List configurationKeyEx()

#### Return Value

A list that contains the IDs of configuration keys that are in effect for the control.

#### Remarks

The list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. In addition, the returned list contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

#### Examples

The following example shows the retrieval of the configuration key IDs for a control.

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

### Method count

Returns the number of items in the combo box control.

    public int count()

#### Return Value

The number of items in the combo box control.

#### Examples

The following example shows how to use the count method.

    int j; 
    j = this.count();

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

Sets or returns the data field for the combo box control.

    public FieldId dataField([FieldId value])

#### Parameters

value  
The value to assign as the data field ID for the combo box control; optional.

#### Return Value

The value of the data field ID for the combo box control.

#### Examples

The following example shows how to set and return the data field for the combo box control.

    fieldID i; 
    // The combo variable is a previously assigned  
    // FormComboBoxControl value. 
    // Retrieve the data Field. 
    i = combo.dataField(); 
    // Set the data field. 
    combo.dataField(fieldnum(CustTable, IdentificationNumber));

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

Gets or sets a data source that should be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  
The value to assign as the data source for the combo box control; optional.

#### Return Value

The identifier of the data source that should be used.

#### Examples

The following example shows how to set and return the data source for the combo box control.

    int i; 
    // The combo variable was previously assigned  
    // as a FormComboBoxControl variable. 
    // Retrieve the data source. 
    i = combo.dataSource(); 
    // Set the data source. 
    combo.dataSource(tablenum(CustTable));

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

### Method dragDrop

Determines whether drag-and-drop operations are enabled or disabled for the control.

    public int dragDrop([int value])

#### Parameters

value  
An integer value that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Examples

The following example shows how to return or set the value that indicates whether drag-and-drop behavior is enabled.

    boolean bDragDrop; 
    // The combo variable was previously assigned  
    // as a FormComboBoxControl value. 
    // Retrieve the drag-and-drop-enabled value. 
    bDragDrop = combo.dragDrop(); 
    // Set the drag-and-drop-enabled value. 
    combo.dragDrop(true);

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

Returns the text that is displayed when the form combo box control is dragged.

    public str dragText()

#### Return Value

The text that is displayed when the combo box control is dragged; an empty string if there is no text to display when the combo box control is dragged.

### Method enabled

Determines whether the object is enabled or disabled.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that specifies whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property lets you enable or disable controls at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message that provides read-only information.

#### Examples

The following example shows how to return and set the enabled property for a control.

    // Return the value of the enabled property. 
    info(strfmt("enabled: %1",this.enabled())); 
    // Set the enabled property. 
    this.enabled(false);

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

### Method fastTabSummary

    public int fastTabSummary([int value])

#### Parameters

value  

#### Return Value

### Method find

    public int find(str string)

#### Parameters

string  

#### Return Value

### Method font

Gets or sets the name of the font that should be used for the control.

    public str font([str value])

#### Parameters

value  
A String data type that indicates the font to use for text in a form combo box control; optional.

#### Return Value

The name of the font that should be used, such as Tahoma or Verdana.

#### Examples

The following example shows how to return and set the font for a form combo box control.

    str strFont; 
    ; 
    // The ctrl variable was previously assigned  
    // as a form combo box control value. 
    // Retrieve the font. 
    strFont = ctrl.font(); 
    // Set the font. 
    ctrl.font("Times New Roman");

### Method fontSize

Gets or sets the size of the font that should be used for the control.

    public int fontSize([int value])

#### Parameters

value  
An Integer data type that indicates the font size in points for text in a form combo box control; optional.

#### Return Value

The height of the font in points.

#### Examples

The following example shows how to return and set the font size for a form combo box control.

    int nSize; 
    // The ctrl variable was previously assigned  
    // as a form combo box control. 
    // Retrieve the font size. 
    nSize = ctrl.fontSize(); 
    // Set the font size. 
    ctrl.fontSize(16);

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

### Method getEditText

    public str getEditText()

#### Return Value

### Method getText

    public str getText(int index)

#### Parameters

index  

#### Return Value

### Method hasChanged

Sets or returns a value that indicates whether the contents of the form combo box control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
A value to assign as the hasChanged value for the combo box control; optional.

#### Return Value

true if the contents of the combo box control have changed; otherwise, false.

#### Examples

The following example shows how to return and set the value that indicates whether the contents of the combo box control have changed.

    boolean bHasChanged; 
    // The ctrl variable was previously assigned 
    // as a FormComboBoxControl variable. 
    // Retrieve the hasChanged value. 
    bHasChanged = ctrl.hasChanged(); 
    // Modify the hasChanged value. 
    ctrl.hasChanged(true);

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

true if the control has custom user settings; otherwise, false.

### Method height

Gets or sets the height of the control in pixels.

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

The height and height calculation mode can be set separately.

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

The following example shows how to return and set the height calculation mode for a form combo box control:

    int nHeightMode; 
    // The ctrl variable was previously assigned 
    // as a form combo box control type. 
    // Retrieve the height mode. 
    nHeightMode = ctrl.HeightMode(); 
    // Set the height mode. 
    ctrl.heightMode(-1); 
    // Set the height. 
    ctrl.heightValue(16);

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

The following example shows how to return and set the height value of a combo box control.

    int nHeightValue; 
    // The ctrl variable was previously assigned 
    // as a form combo box control type. 
    // Retrieve the height value. 
    nHeightValue = ctrl.heightValue(); 
    // Set the height value. 
    ctrl.heightMode(-1); 
    ctrl.heightValue(22);

### Method helpField

Returns the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

#### Examples

The following example shows how to use the helpField method.

    str strHelp; 
    strHelp = this.helpField();

### Method helpText

Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value to assign as the Help text for the control; optional.

#### Return Value

The string that should be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

#### Examples

The following example shows how to set and return the Help text for a control.

    // objCtrl previously assigned to a control 
    // Retrieve existing help text. 
    print objCtrl.helpText(); 
    // Specify new help text. 
    objCtrl.helpText("My new help text");

### Method hideFirstEntry

Sets or returns a value that indicates whether the first entry in the combo box control is hidden.

    public boolean hideFirstEntry([boolean value])

#### Parameters

value  
A value that indicates whether the first entry in the combo box control is hidden; optional.

#### Return Value

true if the first entry in the combo box control is hidden; otherwise, false.

#### Remarks

By hiding the first entry in the combo box control, you enable the control to emulate the behavior of an enum database field where the Mandatory property is set to Yes.

#### Examples

The following example shows how to return and set the value that indicates whether the first entry in the combo box control is hidden.

    boolean bHideFirstEntry; 
    // The ctrl variable was previously assigned 
    // as a form combo box control type. 
    // Retrieve the hideFirstEntry value. 
    bHideFirstEntry = ctrl.hideFirstEntry(); 
    // Set the hideFirstEntry value. 
    bHideFirstEntry = ctrl.hideFirstEntry(true);

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hWnd

Returns the Windows handle for the control.

    public int hWnd()

#### Return Value

The handle for the control.

#### Remarks

The handle can be used with the Windows API.

#### Examples

The following example shows how to retrieve the Windows handle for a control.

    int h; 
    h = this.hWnd(); 
    info (strfmt("hWnd: %1", h));

### Method isContainer

Returns a value that indicates whether the control is a container.

    public boolean isContainer()

#### Return Value

true if the control is a container; otherwise, false.

#### Examples

The following example shows how to determine whether a control is a container.

    info(strfmt("IsContainer: %1", this.isContainer()));

### Method isDisplayed

Returns a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

#### Remarks

To modify the visible state of the control, call the visible method.

#### Examples

The following example shows how to determine whether a control is visible.

    info(strfmt("isDisplayed: %1", this.isDisplayed()));

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

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

For this method to return true, the AllowUserSetup property for the design and all parent containers must be at least as high as the level that is specified by the neededSetupRights parameter.

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

### Method isValid

    public boolean isValid()

#### Return Value

### Method italic

Sets or returns a value that indicates whether the text in the control is italic.

    public boolean italic([boolean value])

#### Parameters

value  
The value to assign to the italic setting of the control; optional.

#### Return Value

true if the text in the control is italic; otherwise, false.

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
The value to assign as the label of the control; optional.

#### Return Value

The current value of the label string.

#### Remarks

The label determines the text that is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

#### Examples

The following example shows how to return and set the label of the control.

    // Return the label value. 
    info(strfmt("label: %1", this.label())); 
    // Set the label value. 
    this.label("New label text goes here");

### Method labelAlignment

    public int labelAlignment([int value])

#### Parameters

value  

#### Return Value

### Method labelBold

Sets or returns a value that indicates the bold setting for the label in the control.

    public int labelBold([int value])

#### Parameters

value  
The value to assign to the label bold setting. This can be one of the values from the ReportControlBold enumeration.

#### Return Value

A value from the ReportControlBold enumeration that indicates the bold setting for the label in the control.

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelFont

Sets or returns a font for the label text in a form combo box control.

    public str labelFont([str value])

#### Parameters

value  
A String data type that indicates the font for the label text in a form combo box control; optional.

#### Return Value

A String data type value that indicates the font for the label text in a form combo box control.

#### Examples

The following example shows how to return and set the font for the label text in a form combo box control.

    str strLabelFont; 
    // The ctrl variable was previously assigned  
    // as a form combo box control variable. 
    // Retrieve the font. 
    strLabelFont = ctrl.labelFont(); 
    // Set the label font. 
    ctrl.labelFont("Times New Roman");

### Method labelFontSize

Sets or returns the font size in points for the label text in a form combo box control.

    public int labelFontSize([int value])

#### Parameters

value  
An Integer data type that indicates the font size in points for the label text in a form combo box control; optional.

#### Return Value

An Integer data type value that indicates the label font size in points for the text in a form combo box control.

#### Examples

The following example shows how to return and set the label font size for a form combo box control.

    int nSize; 
    // The ctrl variable was previously assigned  
    // as a form combo box control. 
    // Retrieve the label font size. 
    nSize = ctrl.labelFontSize(); 
    // Set the label font size. 
    ctrl.labelFontSize(16);

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

Sets or returns a value that indicates whether the text in the label of the control is italic.

    public boolean labelItalic([boolean value])

#### Parameters

value  
The value to assign to the italic setting of the label of the control; optional.

#### Return Value

true if the text in the label of the control is italic; otherwise, false.

### Method labelMouseDblClick

Is called when the label for the control is double-clicked by the user.

    public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

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

#### Examples

The following example shows how to display the parameters of a labelMouseDblClick event in the Infolog.

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

### Method labelMouseDown

Is called when the user clicks the mouse button over the label for the control.

    public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

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

#### Examples

The following example shows how to display the parameters of a labelMouseDown event in the Infolog.

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

### Method labelMouseUp

Is called when the user releases the mouse button over the label for the control.

    public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

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

#### Examples

The following example shows how to display the parameters of a labelMouseUp event in the Infolog.

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

### Method labelPosition

Sets or returns the position of the label for the control.

    public int labelPosition([int value])

#### Parameters

value  
The value to assign to the label position; optional.

#### Return Value

An integer that represents the position of the label.

#### Remarks

If the value parameter is set to 0 (zero), the label is put to the left of the control. If the value parameter is set to 1, the label is put above the control. A return value of 0 (zero) indicates that the label is put to the left of the control. A return value of 1 indicates that the label is put above the control.

#### Examples

The following example shows how to return and set the label position.

    // Retrieve the label position. 
    info (strfmt("label: %1", this.labelPosition())); 
    // Set the label position. 
    this.labelPosition(1);  // 1 == Above, 0 == Left

### Method labelUnderline

Sets or returns a value that indicates whether the text in the label of the control is underlined.

    public boolean labelUnderline([boolean value])

#### Parameters

value  
The value to assign to the underline setting of the label of the control; optional.

#### Return Value

true if the text in the label of the control is underlined; otherwise, false.

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

#### Examples

Typically, when this method is overridden, the return value from a call to the super method is returned. The following example shows how to display the parameters of a mouseDblClick event in the Infolog.

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

#### Examples

The following example shows how to display the parameters of a mouseDown event in the Infolog.

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

#### Examples

Typically, when this method is overridden, the return value from a call to the super method is returned. The following example shows how to display the parameters of a mouseMove event in the Infolog.

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

### Method mouseUp

Is called when the user releases the mouse button over the control.

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

#### Examples

Typically, when this method is overridden, the return value from a call to the super method is returned. The following example shows how to display the parameters of a mouseUp event in the Infolog.

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

#### Examples

The following example shows the retrieval and assignment of a security key ID for a control.

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

### Method selection

    public int selection([int value])

#### Parameters

value  

#### Return Value

### Method selectionChange

Indicates that the user has changed the selected item in the combo box control.

    public int selectionChange()

#### Return Value

true if the event was processed successfully; otherwise, false.

#### Examples

The following example shows how the selectionChange method can be overridden to display an Infolog message when the user changes the selected item in the combo box control.

    public int selectionChange() 
    { 
        int ret; 
        info("The selection has changed."); 
        ret = super(); 
        return ret; 
    }

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

Sets or returns a value that indicates whether the label for the control is displayed in the form.

    public boolean showLabel([boolean value])

#### Parameters

value  
The value to assign to the showLabel property for the control.

#### Return Value

true if the label should be displayed; otherwise, false.

#### Examples

The following example shows how to return and set the showLabel property for a control.

    // Return the showLabel value. 
    info(strfmt("showLabel: %1", this.showLabel())); 
    // Set the showLabel value. 
    this.showLabel(false);

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

### Method text

Sets or returns the text for the control.

    public str text([str value])

#### Parameters

value  
The value to assign as the text for the control; optional.

#### Return Value

The text for the control; an empty string if no text has been assigned for the control.

### Method toolTip

Returns the tooltip text for the control.

    public str toolTip()

#### Return Value

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

#### Remarks

The method can be overridden to provide a value to the toolTip method.

#### Examples

The following example shows how to override the toolTip method.

    str toolTip() 
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

Returns or sets the value that indicates whether the form combo box control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
A value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a combo box control is hidden by right-clicking the control when it can be viewed or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. The userHide method lets you programmatically determine and set the value.

#### Examples

The following example shows how to return and set the value that indicates whether the combo box control is hidden from the user.

    int nUserHide; 
    // The ctrl variable was previously assigned  
    // as a form combo box control variable. 
    // Retrieve the userHide value. 
    nUserHide = ctrl.userHide(); 
    // Set the userHide value. 
    ctrl.userHide(1);

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

Sets or returns the value that indicates whether the form combo box control is skipped when the user presses the TAB key to navigate the controls in the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

#### Examples

The following example shows how to return and set the userSkip property.

    int nUserSkip 
    // The ctrl variable was previously assigned as a 
    // FormComboBoxControl variable. 
    // Return the userSkip property. 
    nUserSkip = ctrl.userSkip(); 
    // Set the userSkip property. 
    ctrl.userSkip(1);

### Method userWidth

Sets or returns the width of the form combo box control in pixels.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

#### Examples

The following example shows how to return and set the user width of a form combo box control.

    int nWidth; 
    // The ctrl variable was previously defined  
    // as the FormComboBoxControl variable. 
    // Return the width. 
    nWidth = ctrl.userWidth(); 
    // Specify the width. 
    ctrl.userWidth(90);  // 15 characters * 6 pixels == 90

### Method validate

    public boolean validate()

#### Return Value

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode for the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method verticalSpacingMode

Sets the vertical spacing mode for the control in the form.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  
A AutoMode enumeration value for the control; optional.

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
An integer value that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode             | Width calculation                                                                         |
|------------------|-------------------------------------------------------------------------------------------|
| -1 – Exact       | The exact width of the control in pixels is used.                                         |
| 0 – Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| 1 – Column width | The layout of the form determines the width of the control.                               |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer value that indicates how a control width is calculated. The value can be -1 for Exact mode, 0 for Auto mode, or 1 for Column width mode.

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table.

| Mode         | Width Calculation.                                                                        |
|--------------|-------------------------------------------------------------------------------------------|
| Exact        | The exact width of the control in pixels is used.                                         |
| Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                               |

The width of the control might change when the calculation mode is set to Auto or Column width.

#### Examples

The following example shows how to return and set the width calculation mode for a combo box control in a form.

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

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An integer value that specifies the width in pixels; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

To change the width of the control, use the Exact width calculation mode.

#### Examples

The following example shows how to return and set the width value of a form combo box control.

    int nWidthValue; 
    // The ctrl variable was previously assigned 
    // as a form combo box control variable. 
    // Retrieve the width value. 
    nWidthValue = ctrl.widthValue(); 
    // Set the width value. 
    ctrl.widthMode(-1); 
    ctrl.widthValue(160);

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method displayControl

Displays the control.

    public void displayControl()

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method beginUpdate

    public void beginUpdate()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setEditText

    public void setEditText(str string)

#### Parameters

string  

### Method enter

    public void enter()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method paste

Pastes the form combo box control into the form.

    public void paste()

### Method clear

Clears the entries in the combo box list.

    public void clear()

#### Examples

The following example shows how to clear the entries in the combo box list.

    this.clear();

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method copy

Copies the form combo box control.

    public void copy()

### Method OnSelectionChanging

    private void OnSelectionChanging([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method endDrag

Is called when the user has finished dragging a form combo box control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag the control, the user presses the mouse button in the control area and then moves the mouse pointer.

#### Examples

The following example displays a message in the Infolog when the user has finished dragging the form combo box control.

    public void endDrag() 
    { 
        info("EndDrag completed"); 
        super(); 
    }

### Method lookup

    public void lookup()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method insert

Inserts a string value into the combo box list at the specified position.

    public void insert(str string, int index)

#### Parameters

string  
The position to insert the string after. If you want the string to be the first item in the list, set the value to 0 (zero).

<!-- -->

index  
The position to insert the string after. If you want the string to be the first item in the list, set the value to 0 (zero).

#### Examples

The following example shows how to insert a string into the combo box list.

    this.insert("willow", 3);

### Method mouseEnter

Is called when the user moves the mouse pointer into the control.

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

#### Examples

The following example shows how to display the parameters of a mouseEnter event in the Infolog.

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

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method delete

Removes a string value from the combo box list.

    public void delete(str string)

#### Parameters

string  
The string value to remove from the combo box list.

#### Examples

The following example shows how to remove a string value from the combo box list.

    this.delete("Model 12357");

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method add

Adds a string value to the combo box list.

    public void add(str string)

#### Parameters

string  
The string value to add to the combo box list.

#### Remarks

The string is added to the end of the list. If you want to put the string in a specific position in the list, use the insert method.

#### Examples

The following example shows how to add a string to the combo box list.

    this.add("maple"); 
    this.add("oak"); 
    this.add("pine");

### Method prefColumnSize

Specifies the preferred column width and height for the form combo box control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

#### Examples

The following example shows how to set the preferred width and height of a combo box control.

    // The nWidth and nHeight variables were  
    // previously assigned as int variables. 
    // The ctrl variable was previously assigned 
    // as a FormComboBoxControl variable. 
    ctrl.prefColumnSize( nWidth, nHeight);

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method undo

    public void undo()

### Method jumpRef

    public void jumpRef()

### Method OnSelectionChanged

    private void OnSelectionChanged([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method endUpdate

    public void endUpdate()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method cut

Cuts the contents of the control.

    public void cut()

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

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setDropSize

    public void setDropSize([int lines])

#### Parameters

lines  

## Class FormCommandButtonControl
    class FormCommandButtonControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public boolean autoRefreshData(\[boolean value\])                                                           |                                                                                                                                                                         |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public boolean big(\[boolean value\])                                                                       |                                                                                                                                                                         |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                                                     |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                                                |
| public int buttonDisplay(\[int value\])                                                                     | Gets or sets the appearance of the button control.                                                                                                                      |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                                                 |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public int command(\[int value\])                                                                           |                                                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public boolean defaultButton(\[boolean value\])                                                             | Determines whether the button should be the default button in the form.                                                                                                 |
| public str disabledImage(\[str value\])                                                                     | Gets or sets the disabled image of the button.                                                                                                                          |
| public int disabledImageLocation(\[int value\])                                                             |                                                                                                                                                                         |
| public int disabledResource(\[int value\])                                                                  | Gets or sets the resource ID of the image to use as the disabled button image.                                                                                          |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                               |
| public boolean forcedToOverflow(\[boolean value\])                                                          |                                                                                                                                                                         |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public int imageLocation(\[int value\])                                                                     |                                                                                                                                                                         |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                                                         |
| public str keyTip(\[str value\])                                                                            |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public int multiSelect(\[int value\])                                                                       |                                                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public int needsRecord(\[int value\])                                                                       |                                                                                                                                                                         |
| public str normalImage(\[str value\])                                                                       |                                                                                                                                                                         |
| public int normalResource(\[int value\])                                                                    |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public str parameters(\[str value\])                                                                        |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public boolean primary(\[boolean value\])                                                                   |                                                                                                                                                                         |
| public boolean saveRecord(\[boolean value\])                                                                |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int shortkey(\[int value\])                                                                          |                                                                                                                                                                         |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showShortCut(\[boolean value\])                                                              |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int style(\[int value\])                                                                             |                                                                                                                                                                         |
| public str text(\[str value\])                                                                              |                                                                                                                                                                         |
| public int toggleButton(\[int value\])                                                                      |                                                                                                                                                                         |
| public int toggleValue(\[int value\])                                                                       |                                                                                                                                                                         |
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
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                                     |
| public boolean value(\[boolean value\])                                                                     |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| private void OnClicked(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void clicked()                                                                                       |                                                                                                                                                                         |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |

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
If specified, the property is set to this value.

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

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method buttonDisplay

Gets or sets the appearance of the button control.

    public int buttonDisplay([int value])

#### Parameters

value  

#### Return Value

An integer between zero and five, inclusive.

#### Remarks

The value of the property defines whether the text, the image, or both should be displayed on the button. This property also controls relative positions of text and image if both are displayed.The integer value that is returned contains the appearace of the button control as follows:

| Value. | Description.                                                     |
|--------|------------------------------------------------------------------|
| 0      | Text only.                                                       |
| 1      | Image Only.                                                      |
| 2      | Text and image; the image is displayed below the text.           |
| 3      | Text and image; the image is displayed above the text.           |
| 4      | Text and image; the image is displayed to the left of the text.  |
| 5      | Text and image; the image is displayed to the right of the text. |

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

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method command

    public int command([int value])

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
An Integer data type that indicates whether drag-and-drop behavior is enabled; optional.

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
An Integer data type that indicates how the height is calculated; optional.

<!-- -->

mode  
An Integer data type that indicates how the height is calculated; optional.

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
An Integer data type value that indicates how control height is calculated; optional.

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
An Integer data type that specifies the height in pixels; optional.

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

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value to assign as the help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet.The help text must not exceed 250 characters.

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

The handle can be used with the WindowsAPI.

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

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

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

### Method parameters

    public str parameters([str value])

#### Parameters

value  

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

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

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

### Method toggleButton

    public int toggleButton([int value])

#### Parameters

value  

#### Return Value

### Method toggleValue

    public int toggleValue([int value])

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

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

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
An integer value that indicates the AutoMode for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode for the control; optional.

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
An Integer data type that indicates how the width is calculated; optional.

<!-- -->

mode  
An Integer data type that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

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
An Integer data type value that indicates how control width is calculated; optional.

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
An Integer data type that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method OnClicked

    private void OnClicked([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method displayControl

Displays the control.

    public void displayControl()

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

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

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

### Method cut

Cuts the contents of the control.

    public void cut()

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

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method clicked

    public void clicked()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

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

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

## Class FormContainer
    class FormContainer extends Object

### Remarks

### Examples

### Methods

| Method             | Description |
|--------------------|-------------|
| private void new() |             |

### Method new

    private void new()

## Class FormContainerControl
    class FormContainerControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                              | Description |
|---------------------------------------------------------------------------------------------------------------------|-------------|
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            |             |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |             |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) |             |
| public boolean alignChild(\[boolean value\])                                                                        |             |
| public boolean alignChildren(\[boolean value\])                                                                     |             |
| public boolean alignControl(\[boolean value\])                                                                      |             |
| public boolean allowEdit(\[boolean value\])                                                                         |             |
| public boolean allowSysSetup()                                                                                      |             |
| public int allowUserSetup(\[int value\])                                                                            |             |
| public int arrangeGuide(\[int value\])                                                                              |             |
| public int arrangeMethod(\[int value\])                                                                             |             |
| public int arrangeWhen(\[int value\])                                                                               |             |
| public boolean autoDataGroup(\[boolean value\])                                                                     |             |
| public boolean autoDeclaration(\[boolean value\])                                                                   |             |
| public int beginDrag(int x, int y)                                                                                  |             |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                           |             |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                                 |             |
| public int bottomMarginValue(\[int value\])                                                                         |             |
| public container calcControlSize(int chars, int lines)                                                              |             |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                               |             |
| public boolean canContain(FormControl control)                                                                      |             |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                             |             |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                                |             |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                            |             |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                                  |             |
| public int columnspaceValue(\[int value\])                                                                          |             |
| public int columnsValue(\[int value\])                                                                              |             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                            |             |
| public List configurationKeyEx()                                                                                    |             |
| public boolean contains(FormControl control)                                                                        |             |
| public int controlCount()                                                                                           |             |
| public FormControl controlNum(int controlNo)                                                                        |             |
| public str countryRegionCodes(\[str value\])                                                                        |             |
| public str dataRelationPath(\[str value\])                                                                          |             |
| public int displayTarget(\[int value\])                                                                             |             |
| public int dragDrop(\[int value\])                                                                                  |             |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                   |             |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                       |             |
| public str dragText()                                                                                               |             |
| public boolean enabled(\[boolean value\])                                                                           |             |
| public boolean hasChanged(\[boolean val\])                                                                          |             |
| public boolean hasUserSetting()                                                                                     |             |
| public int height(int value, \[int mode\])                                                                          |             |
| public int heightMode(\[int value\])                                                                                |             |
| public int heightValue(\[int value\])                                                                               |             |
| public str helpField()                                                                                              |             |
| public str helpText(\[str value\])                                                                                  |             |
| public boolean hideIfEmpty(\[boolean value\])                                                                       |             |
| public str hierarchyParent(\[str value\])                                                                           |             |
| public int hWnd()                                                                                                   |             |
| public boolean isContainer()                                                                                        |             |
| public boolean isDisplayed()                                                                                        |             |
| public boolean isRestricted()                                                                                       |             |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            |             |
| public boolean isVisible()                                                                                          |             |
| public boolean isVisibleOnClient()                                                                                  |             |
| public int left(int value, \[int mode\])                                                                            |             |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                             |             |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                                   |             |
| public int leftMarginValue(\[int value\])                                                                           |             |
| public int leftMode(\[int value\])                                                                                  |             |
| public int leftValue(\[int value\])                                                                                 |             |
| public boolean markAsUserAdd(\[boolean value\])                                                                     |             |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                     |             |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                         |             |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                         |             |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                           |             |
| public int moveControl(int controlId, \[int insertAfterId\])                                                        |             |
| public str name(\[str value\])                                                                                      |             |
| public int neededPermission(\[int value\])                                                                          |             |
| public container SysObsoleteAttribute()                                                                             |             |
| public FormControl parentControl()                                                                                  |             |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                            |             |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                                  |             |
| public int rightMarginValue(\[int value\])                                                                          |             |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                           |             |
| public int showContextMenu(int menuHandle)                                                                          |             |
| public boolean skip(\[boolean value\])                                                                              |             |
| public str toolTip()                                                                                                |             |
| public int top(int value, \[int mode\])                                                                             |             |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                              |             |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                                    |             |
| public int topMarginValue(\[int value\])                                                                            |             |
| public int topMode(\[int value\])                                                                                   |             |
| public int topValue(\[int value\])                                                                                  |             |
| public int type(\[int value\])                                                                                      |             |
| public boolean SysObsoleteAttribute(container data)                                                                 |             |
| public int userData(\[int value\])                                                                                  |             |
| public int userDataItem(\[int value\])                                                                              |             |
| public int userDataItems(\[int value\])                                                                             |             |
| public int userDisable(\[int value\])                                                                               |             |
| public int userHeight(\[int value\])                                                                                |             |
| public int userHide(\[int value\])                                                                                  |             |
| public int userOrgContainer(\[int value\])                                                                          |             |
| public int userOrgSibling(\[int value\])                                                                            |             |
| public str userPromptText(\[str value\])                                                                            |             |
| public int userSecurityLevel(\[int value\])                                                                         |             |
| public int userSkip(\[int value\])                                                                                  |             |
| public int userWidth(\[int value\])                                                                                 |             |
| public boolean useUserLayout(\[boolean value\])                                                                     |             |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                        |             |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                              |             |
| public int verticalSpacingValue(\[int value\])                                                                      |             |
| public boolean visible(\[boolean value\])                                                                           |             |
| public int width(int value, \[int mode\])                                                                           |             |
| public int widthMode(\[int value\])                                                                                 |             |
| public int widthValue(\[int value\])                                                                                |             |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                               |             |
| public void inputSearch(str searchStr)                                                                              |             |
| public void prefColumnSize(int width, int height)                                                                   |             |
| public void gotFocus()                                                                                              |             |
| public void lostFocus()                                                                                             |             |
| public void mouseLeave()                                                                                            |             |
| public void setFocus()                                                                                              |             |
| public void copy()                                                                                                  |             |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                         |             |
| public void displayControl()                                                                                        |             |
| public void paste()                                                                                                 |             |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                           |             |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                        |             |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                       |             |
| public void resetUserSetting()                                                                                      |             |
| public void endDrag()                                                                                               |             |
| public void arrange()                                                                                               |             |
| public void dragLeave()                                                                                             |             |
| public void cut()                                                                                                   |             |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\])         |             |
| public void context()                                                                                               |             |

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

### Method alignChild

    public boolean alignChild([boolean value])

#### Parameters

value  

#### Return Value

### Method alignChildren

    public boolean alignChildren([boolean value])

#### Parameters

value  

#### Return Value

### Method alignControl

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

### Method allowEdit

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

### Method allowSysSetup

    public boolean allowSysSetup()

#### Return Value

### Method allowUserSetup

    public int allowUserSetup([int value])

#### Parameters

value  

#### Return Value

### Method arrangeGuide

    public int arrangeGuide([int value])

#### Parameters

value  

#### Return Value

### Method arrangeMethod

    public int arrangeMethod([int value])

#### Parameters

value  

#### Return Value

### Method arrangeWhen

    public int arrangeWhen([int value])

#### Parameters

value  

#### Return Value

### Method autoDataGroup

    public boolean autoDataGroup([boolean value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

### Method beginDrag

    public int beginDrag(int x, int y)

#### Parameters

x  

<!-- -->

y  

#### Return Value

### Method bottomMargin

    public int bottomMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method bottomMarginMode

    public AutoMode bottomMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method bottomMarginValue

    public int bottomMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method calcControlSize

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  

<!-- -->

lines  

#### Return Value

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

### Method columns

    public int columns([int value], [ColumnsMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnsMode

    public ColumnsMode columnsMode([ColumnsMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspace

    public int columnspace([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnspaceMode

    public AutoMode columnspaceMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspaceValue

    public int columnspaceValue([int value])

#### Parameters

value  

#### Return Value

### Method columnsValue

    public int columnsValue([int value])

#### Parameters

value  

#### Return Value

### Method configurationKey

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

### Method configurationKeyEx

    public List configurationKeyEx()

#### Return Value

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

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

### Method dragOver

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  

<!-- -->

dragMode  

<!-- -->

x  

<!-- -->

y  

#### Return Value

### Method dragOverEx

    public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  

<!-- -->

dragMode  

<!-- -->

x  

<!-- -->

y  

#### Return Value

### Method dragText

    public str dragText()

#### Return Value

### Method enabled

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

### Method hasChanged

    public boolean hasChanged([boolean val])

#### Parameters

val  

#### Return Value

### Method hasUserSetting

    public boolean hasUserSetting()

#### Return Value

### Method height

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method heightMode

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

### Method heightValue

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

### Method helpField

    public str helpField()

#### Return Value

### Method helpText

    public str helpText([str value])

#### Parameters

value  

#### Return Value

### Method hideIfEmpty

    public boolean hideIfEmpty([boolean value])

#### Parameters

value  

#### Return Value

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method hWnd

    public int hWnd()

#### Return Value

### Method isContainer

    public boolean isContainer()

#### Return Value

### Method isDisplayed

    public boolean isDisplayed()

#### Return Value

### Method isRestricted

    public boolean isRestricted()

#### Return Value

### Method isUserSetupEnabled

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  

#### Return Value

### Method isVisible

    public boolean isVisible()

#### Return Value

### Method isVisibleOnClient

    public boolean isVisibleOnClient()

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMargin

    public int leftMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMarginMode

    public AutoMode leftMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method leftMarginValue

    public int leftMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method markAsUserAdd

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  

#### Return Value

### Method mouseDblClick

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

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

### Method mouseDown

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

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

### Method mouseMove

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

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

### Method mouseUp

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

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

### Method moveControl

    public int moveControl(int controlId, [int insertAfterId])

#### Parameters

controlId  

<!-- -->

insertAfterId  

#### Return Value

### Method name

    public str name([str value])

#### Parameters

value  

#### Return Value

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

    public FormControl parentControl()

#### Return Value

### Method rightMargin

    public int rightMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method rightMarginMode

    public AutoMode rightMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method rightMarginValue

    public int rightMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method showContextMenu

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  

#### Return Value

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method toolTip

    public str toolTip()

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMargin

    public int topMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMarginMode

    public AutoMode topMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method topMarginValue

    public int topMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

#### Parameters

value  

#### Return Value

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

    public int userData([int value])

#### Parameters

value  

#### Return Value

### Method userDataItem

    public int userDataItem([int value])

#### Parameters

value  

#### Return Value

### Method userDataItems

    public int userDataItems([int value])

#### Parameters

value  

#### Return Value

### Method userDisable

    public int userDisable([int value])

#### Parameters

value  

#### Return Value

### Method userHeight

    public int userHeight([int value])

#### Parameters

value  

#### Return Value

### Method userHide

    public int userHide([int value])

#### Parameters

value  

#### Return Value

### Method userOrgContainer

    public int userOrgContainer([int value])

#### Parameters

value  

#### Return Value

### Method userOrgSibling

    public int userOrgSibling([int value])

#### Parameters

value  

#### Return Value

### Method userPromptText

    public str userPromptText([str value])

#### Parameters

value  

#### Return Value

### Method userSecurityLevel

    public int userSecurityLevel([int value])

#### Parameters

value  

#### Return Value

### Method userSkip

    public int userSkip([int value])

#### Parameters

value  

#### Return Value

### Method userWidth

    public int userWidth([int value])

#### Parameters

value  

#### Return Value

### Method useUserLayout

    public boolean useUserLayout([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method verticalSpacingMode

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method verticalSpacingValue

    public int verticalSpacingValue([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method width

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method widthMode

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

### Method widthValue

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

### Method dropEx

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  

<!-- -->

dragMode  

<!-- -->

x  

<!-- -->

y  

### Method inputSearch

    public void inputSearch(str searchStr)

#### Parameters

searchStr  

### Method prefColumnSize

    public void prefColumnSize(int width, int height)

#### Parameters

width  

<!-- -->

height  

### Method gotFocus

    public void gotFocus()

### Method lostFocus

    public void lostFocus()

### Method mouseLeave

    public void mouseLeave()

### Method setFocus

    public void setFocus()

### Method copy

    public void copy()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method displayControl

    public void displayControl()

### Method paste

    public void paste()

### Method drop

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  

<!-- -->

dragMode  

<!-- -->

x  

<!-- -->

y  

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method mouseEnter

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

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

### Method resetUserSetting

    public void resetUserSetting()

### Method endDrag

    public void endDrag()

### Method arrange

    public void arrange()

### Method dragLeave

    public void dragLeave()

### Method cut

    public void cut()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method context

    public void context()

## Class FormControl
    class FormControl extends Object

The FormControl class serves as the base class for all form controls.

### Remarks

You should not create an instance of this class. Use the specific control instead.

### Examples

### Methods

| Method                                                                                                                                                 | Description                                                                                                                                                             |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                                                                         | Determines whether the control should be aligned.                                                                                                                       |
| public boolean allowEdit(\[boolean value\])                                                                                                            | Determines whether the user can modify the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                                                                         | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                                                                      | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int beginDrag(int x, int y)                                                                                                                     | Is called when the user starts to drag a form control.                                                                                                                  |
| public FormBuildControl build()                                                                                                                        |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                                                                 | Retrieves the size of the control.                                                                                                                                      |
| public FormChangeTracker changeTracker()                                                                                                               |                                                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                                                               | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                                                                       | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public int containerId()                                                                                                                               | Retrieves the ID of the parent container for the control.                                                                                                               |
| public str countryRegionCodes(\[str value\])                                                                                                           | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public int currentRow()                                                                                                                                |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                                                             | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public FormDataSource dataSourceObject()                                                                                                               |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                                                                | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                                                                     | Determines whether drag-and-drop operations are enabled or disabled for the control.                                                                                    |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                                                      | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                                                          | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                                                                  | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean editAutoPostback(\[boolean value\])                                                                                                     |                                                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                                                                                              | Determines whether the object is enabled or disabled.                                                                                                                   |
| public str extendedStyle(\[str value\])                                                                                                                |                                                                                                                                                                         |
| public FieldBinding fieldBinding()                                                                                                                     | Retrieves the table and field bindings of the control into a FieldBinding derived class.                                                                                |
| public str formatStr(\[int rowNumber\], \[boolean display\], \[int maxWidth\], \[boolean forceSignWhenDisplaceNegative\], \[boolean formatForExport\]) |                                                                                                                                                                         |
| public xFormRun formRun()                                                                                                                              |                                                                                                                                                                         |
| public FormBinding getBinding(str propertyName)                                                                                                        |                                                                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                                                             | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                                                                        | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                                                             | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                                                                   | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                                                                 | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                                                                     | Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.                                                         |
| public str hierarchyParent(\[str value\])                                                                                                              | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                                                                      | Retrieves the Windows handle for the control.                                                                                                                           |
| public int id()                                                                                                                                        | Retrieves the ID of the control.                                                                                                                                        |
| public boolean isDisplayed()                                                                                                                           | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isEditable()                                                                                                                            |                                                                                                                                                                         |
| public boolean isEnabled()                                                                                                                             |                                                                                                                                                                         |
| public boolean isRestricted()                                                                                                                          | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                                                               | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                   |
| public boolean isVisible()                                                                                                                             | Retrieves a value that indicates whether the control is visible.                                                                                                        |
| public boolean isVisibleOnClient()                                                                                                                     |                                                                                                                                                                         |
| public str labelText()                                                                                                                                 | Retrieves the label text for the control.                                                                                                                               |
| public int left(int value, \[int mode\])                                                                                                               | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                                                                     | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean lockWindowUpdate(boolean lock)                                                                                                          | Locks or unlocks the window of the control for update.                                                                                                                  |
| public boolean markAsUserAdd(\[boolean value\])                                                                                                        | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                                                        | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                                                            | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                                                            | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                                                              | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                                                                         | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                                                             |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                                                                |                                                                                                                                                                         |
| public FormControl parentControl()                                                                                                                     | Retrieves the parent control for the control.                                                                                                                           |
| public str resourceBundleName()                                                                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                                                              | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                                                             | Shows the shortcut menu for the control.                                                                                                                                |
| public str getContextMenuOptions()                                                                                                                     |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                                                                 | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public str templateId()                                                                                                                                |                                                                                                                                                                         |
| public str toolTip()                                                                                                                                   | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                                                                | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                                                                      | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                                                                         |                                                                                                                                                                         |
| public boolean SysObsoleteAttribute(container data)                                                                                                    |                                                                                                                                                                         |
| public int updateWindow()                                                                                                                              | Updates the window for the control.                                                                                                                                     |
| public int userData(\[int value\])                                                                                                                     | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                                                                 | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                                                                | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                                                                  | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                                                                   | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                                                                     | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                                                             | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                                                               | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                                                               | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                                                            | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                                                                     | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                                                                    | Sets or returns the width of the control in pixels.                                                                                                                     |
| public str valueStr()                                                                                                                                  | Retrieves the value of the control in string format.                                                                                                                    |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                                                           | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                                                                 | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                                                                         | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                                                                                              | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                                                              | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                                                                    | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public void displayControl()                                                                                                                           | Displays the control.                                                                                                                                                   |
| public void copy()                                                                                                                                     | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void paste()                                                                                                                                    | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void setFocus()                                                                                                                                 | Sets the focus on the control.                                                                                                                                          |
| public void cut()                                                                                                                                      | Cuts the contents of the control.                                                                                                                                       |
| public void gotFocus()                                                                                                                                 | Indicates that the control has received focus.                                                                                                                          |
| public void dragLeave()                                                                                                                                | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void lostFocus()                                                                                                                                | Indicates that the control has lost focus.                                                                                                                              |
| public void inputSearch(str searchStr)                                                                                                                 | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void setTemplateId(\[str value\])                                                                                                               |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                                                                      | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void update()                                                                                                                                   | Updates the control.                                                                                                                                                    |
| public void run()                                                                                                                                      |                                                                                                                                                                         |
| public void lock()                                                                                                                                     | Locks the form control.                                                                                                                                                 |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                                                          | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void applyBuild()                                                                                                                               |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                                                              | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void resetUserSetting()                                                                                                                         | Resets the user settings for the control.                                                                                                                               |
| public void new(FormBuildControl build, xFormRun formRun)                                                                                              |                                                                                                                                                                         |
| public void context()                                                                                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public void unLock(boolean update)                                                                                                                     | Unlocks a form control.                                                                                                                                                 |
| public void setResourceBundleName(\[str value\])                                                                                                       |                                                                                                                                                                         |
| public void selectedMenuOption(int selectedOption)                                                                                                     |                                                                                                                                                                         |
| public void mouseLeave()                                                                                                                               | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void onPropChanged(\[str propName\])                                                                                                            |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                                                                  | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void initialize()                                                                                                                               |                                                                                                                                                                         |
| public void endDrag()                                                                                                                                  | Is called when the user has finished dragging a form control.                                                                                                           |

### Method alignControl

Determines whether the control should be aligned.

    public boolean alignControl([boolean value])

#### Parameters

value  
The new value for the property; optional.

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned based on the longest label.

### Method allowEdit

Determines whether the user can modify the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The value to assign to the allowEdit property.

#### Return Value

true if the control can be modified; otherwise, false.

#### Remarks

If this property is set on a container control, modifications are disabled or enabled for all controls in the container.

#### Examples

The following example shows how to return and set the value of the allowEdit property.

    // Return the value. 
    info (strfmt("allowEdit: %1", this.allowEdit())); 
    // Set the value. 
    this.allowEdit(false);

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
The value to set the property to, if a value is supplied.

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

#### Examples

The following example displays the x-coordinates and y-coordinates in the Infolog when the user starts to drag the form control.

    public int beginDrag(int _x, int _y) 
    { 
        int ret; 
        info(strfmt("beginDrag (x, y) : (%1, %2)", _x, _y)); 
        ret = super(_x, _y); 
        return ret; 
    }

### Method build

    public FormBuildControl build()

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

### Method changeTracker

    public FormChangeTracker changeTracker()

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key to assign to the control; optional.

#### Return Value

The ID of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

#### Examples

The following example shows how to set and retrieve the configuration key for a control.

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

### Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are in effect for the control.

    public List configurationKeyEx()

#### Return Value

A list that contains the IDs of configuration keys that are in effect for the control.

#### Remarks

The returned list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. The returned list also contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

#### Examples

The following example shows how to retrieve the configuration key IDs for a control.

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

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method currentRow

    public int currentRow()

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

### Method dataSourceObject

    public FormDataSource dataSourceObject()

#### Return Value

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether drag-and-drop operations are enabled or disabled for the control.

    public int dragDrop([int value])

#### Parameters

value  
An integer value that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Examples

The following example shows how to return or set the value that indicates whether drag-and-drop behavior is enabled.

    boolean dDragDrop; 
    // The ctrl variable was previously assigned  
    // as a FormControl value. 
    // Retrieve the drag-and-drop-enabled value. 
    dDragDrop = ctrl.dragDrop(); 
    // Set the drag–and–drop-enabled value. 
    ctrl.dragDrop(true);

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

### Method editAutoPostback

    public boolean editAutoPostback([boolean value])

#### Parameters

value  

#### Return Value

### Method enabled

Determines whether the object is enabled or disabled.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that specifies whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property lets you enable or disable controls at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message that provides read-only information.

#### Examples

The following example shows how to return and set the enabled property for a control.

    // Return the value of the enabled property. 
    info(strfmt("enabled: %1",this.enabled())); 
    // Set the enabled property. 
    this.enabled(false);

### Method extendedStyle

    public str extendedStyle([str value])

#### Parameters

value  

#### Return Value

### Method fieldBinding

Retrieves the table and field bindings of the control into a FieldBinding derived class.

    public FieldBinding fieldBinding()

#### Return Value

A FieldBinding derived class that contains the table and field bindings of the control.

### Method formatStr

    public str formatStr([int rowNumber], [boolean display], [int maxWidth], [boolean forceSignWhenDisplaceNegative], [boolean formatForExport])

#### Parameters

rowNumber  

<!-- -->

display  

<!-- -->

maxWidth  

<!-- -->

forceSignWhenDisplaceNegative  

<!-- -->

formatForExport  

#### Return Value

### Method formRun

    public xFormRun formRun()

#### Return Value

### Method getBinding

    public FormBinding getBinding(str propertyName)

#### Parameters

propertyName  

#### Return Value

### Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
The value to assign as the hasChanged value for the control; optional.

#### Return Value

true if the contents of the control have changed; otherwise, false.

#### Examples

The following example shows how to return and set the value that indicates whether the contents of the control have changed.

    boolean bHasChanged; 
    // The ctrl variable was previously assigned 
    // as a FormControl value. 
    // Retrieve the hasChanged value. 
    bHasChanged = ctrl.hasChanged(); 
    // Modify the hasChanged value. 
    ctrl.hasChanged(true);

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

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An integer value that indicates how the control height is calculated; optional.

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

The following example shows how to return and set the height calculation mode for a form control.

    int nHeightMode; 
    // The ctrl variable was previously assigned 
    // as a form control variable. 
    // Retrieve the height mode. 
    nHeightMode = ctrl.HeightMode(); 
    // Set the height mode. 
    ctrl.heightMode(-1); 
    // Set the height. 
    ctrl.heightValue(16);

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

The following example shows how to return and set the height value of a form control.

    int nHeightValue; 
    // The ctrl variable was previously assigned 
    // as a form control variable. 
    // Retrieve the height value. 
    nHeightValue = ctrl.heightValue(); 
    // Set the height value. 
    ctrl.heightMode(-1); 
    ctrl.heightValue(22);

### Method helpField

Retrieves the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

#### Examples

The following example shows how to use the helpField method.

    str strHelp; 
    strHelp = this.helpField();

### Method helpText

Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value to assign as the Help text for the control.

#### Return Value

The string that should be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

#### Examples

The following example shows how to set and return the Help text for a control.

    // objCtrl previously assigned to a control 
    // Retrieve existing help text. 
    print objCtrl.helpText(); 
    // Specify new help text. 
    objCtrl.helpText("My new help text");

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

#### Examples

The following example shows how to retrieve the Windows handle for a control.

    int h; 
    h = this.hWnd(); 
    info (strfmt("hWnd: %1", h));

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isDisplayed

Retrieves a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

#### Remarks

To modify the visible state of the control, call the visible method.

#### Examples

The following example shows how to determine whether a control is visible.

    info(strfmt("isDisplayed: %1", this.isDisplayed()));

### Method isEditable

    public boolean isEditable()

#### Return Value

### Method isEnabled

    public boolean isEnabled()

#### Return Value

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

### Method isVisible

Retrieves a value that indicates whether the control is visible.

    public boolean isVisible()

#### Return Value

true if the control is visible; otherwise, false.

### Method isVisibleOnClient

    public boolean isVisibleOnClient()

#### Return Value

### Method labelText

Retrieves the label text for the control.

    public str labelText()

#### Return Value

The label text for the control; an empty string if there is no label text for the control.

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

### Method lockWindowUpdate

Locks or unlocks the window of the control for update.

    public boolean lockWindowUpdate(boolean lock)

#### Parameters

lock  
A Boolean value: true to lock the window, and false to unlock the window.

#### Return Value

true if the operation was successful; otherwise, false.

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

#### Examples

Typically, when this method is overridden, the return value from a call to the super method is returned. The following example shows how to display the parameters of a mouseDblClick event in the Infolog.

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

#### Examples

The following example shows how to display the parameters of a mouseDown event in the Infolog.

    public int mouseDown(int x,  
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

#### Examples

Typically, when this method is overridden, the return value from a call to the super method is returned. The following example shows how to display the parameters of a mouseMove event in the Infolog.

    public int mouseMove(int x,  
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

#### Examples

The following example shows how to display the parameters of a mouseUp event in the Infolog.

    public int mouseUp(int x,  
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

### Method resourceBundleName

    public str resourceBundleName()

#### Return Value

### Method securityKey

Sets or returns the ID of the security key for the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The ID of the security key to assign to the control; optional.

#### Return Value

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

#### Examples

The following example shows how to retrieve and assign a security key ID for a control.

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

### Method showContextMenu

Shows the shortcut menu for the control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
The ID of the menu to show.

#### Return Value

An integer value that indicates whether the call succeeded.

### Method getContextMenuOptions

    public str getContextMenuOptions()

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

#### Examples

The following code example shows how to return and set the skip property of a control.

    // Return the value of the skip property. 
    info(strfmt("skip: %1", this.skip())); 
    // Set the value of the skip property. 
    this.skip(true);

### Method templateId

    public str templateId()

#### Return Value

### Method toolTip

Retrieves the tooltip text for the control.

    public str toolTip()

#### Return Value

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

#### Remarks

The method might be overridden to provide a value to the toolTip method.

#### Examples

The following example shows how to override the toolTip method.

    str toolTip() 
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

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method updateWindow

Updates the window for the control.

    public int updateWindow()

#### Return Value

1 if the update was successful; otherwise, 0.

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

#### Examples

The following example shows how to return and set the value that indicates whether the control is hidden from the user.

    int nUserHide; 
    // The ctrl variable was previously assigned  
    // as a control variable. 
    // Retrieve the userHide value. 
    nUserHide = ctrl.userHide(); 
    // Set the userHide value. 
    ctrl.userHide(1);

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

#### Examples

The following example shows how to return and set the userSkip property.

    int nUserSkip 
    // The ctrl variable was previously assigned  
    // as a FormControl value. 
    // Return the userSkip property. 
    nUserSkip = ctrl.userSkip(); 
    // Set the userSkip property. 
    ctrl.userSkip(1);

### Method userWidth

Sets or returns the width of the control in pixels.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

#### Examples

The following example shows how to return and set the user width of a form control.

    int nWidth; 
    // The ctrl variable was previously defined 
    // as a FormControl value. 
    // Return the width. 
    nWidth = ctrl.userWidth(); 
    // Specify the width. 
    ctrl.userWidth(90);  // 15 characters * 6 pixels == 90

### Method valueStr

Retrieves the value of the control in string format.

    public str valueStr()

#### Return Value

The value of the control in string format.

#### Remarks

The valueStr method can be bound to the data source. The valueStr method should never be used in control validation methods. Instead, use the text method in control validation methods.

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode for the control; optional.

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
An integer value that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode             | Width calculation                                                                         |
|------------------|-------------------------------------------------------------------------------------------|
| -1 – Exact       | The exact width of the control in pixels is used.                                         |
| 0 – Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| 1 – Column width | The layout of the form determines the width of the control.                               |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer value that indicates how the control width is calculated; optional.

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table.

| Mode         | Width calculation                                                                         |
|--------------|-------------------------------------------------------------------------------------------|
| Exact        | The exact width of the control in pixels is used.                                         |
| Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                               |

The width of the control might change when the calculation mode is set to Auto or Column width.

#### Examples

The following example shows how to return and set the width calculation mode for a form control.

    int nWidthMode; 
    // The ctrl variable was previously assigned 
    // as a form control variable. 
    // Retrieve the width mode. 
    nWidthMode = ctrl.widthMode (); 
    // Set the width mode. 
    ctrl.widthMode(-1); 
    // Set the width. 
    ctrl.widthValue(180);

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An integer value that specifies the width in pixels; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

To change the width of the control, use the Exact width calculation mode.

#### Examples

The following example shows how to return and set the width value of a form control.

    int nWidthValue; 
    // The ctrl variable was previously assigned 
    // as a form control value. 
    // Retrieve the width value. 
    nWidthValue = ctrl.widthValue(); 
    // Set the width value. 
    ctrl.widthMode(-1); 
    ctrl.widthValue(160);

### Method displayControl

Displays the control.

    public void displayControl()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method setTemplateId

    public void setTemplateId([str value])

#### Parameters

value  

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

#### Examples

The following example shows how to set the preferred width and height of a form control.

    // nWidth and nHeight are previously assigned int variables. 
    // ctrl is a previously assigned FormControl variable. 
    ctrl.prefColumnSize( nWidth, nHeight);

### Method update

Updates the control.

    public void update()

### Method run

    public void run()

### Method lock

Locks the form control.

    public void lock()

#### Remarks

Use the Lock command when you modify an object and are not sure whether another user is about to make updates. When you have saved your updates, use the Unlock command.

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

#### Examples

The following example shows how to display the parameters of a mouseEnter event in the Infolog.

    public void mouseEnter(int x,  
                          int y,  
                          int button, 
                          boolean Ctrl, 
                          boolean Shift) 
    { 
        if (Shift) 
        { 
            info("Shift set"); 
        } 
        if (Ctrl) 
        { 
            info("Ctrl set"); 
        } 
        info (strfmt("x, y: %1 %2 button: %3", x, y, button)); 
    }

### Method applyBuild

    public void applyBuild()

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

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method new

    public void new(FormBuildControl build, xFormRun formRun)

#### Parameters

build  

<!-- -->

formRun  

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method unLock

Unlocks a form control.

    public void unLock(boolean update)

#### Parameters

update  
A Boolean value that indicates whether to save the changes that are made to the control.

### Method setResourceBundleName

    public void setResourceBundleName([str value])

#### Parameters

value  

### Method selectedMenuOption

    public void selectedMenuOption(int selectedOption)

#### Parameters

selectedOption  

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method onPropChanged

    public void onPropChanged([str propName])

#### Parameters

propName  

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

### Method initialize

    public void initialize()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

#### Examples

The following example displays a message in the Infolog when the user has finished dragging the form control.

    public void endDrag() 
    {  
        info("EndDrag completed"); 
        super(); 
    }

## Class FormControlCancelableSuperEventArgs
    class FormControlCancelableSuperEventArgs extends FormControlEventArgs

### Remarks

### Examples

### Methods

| Method                        | Description |
|-------------------------------|-------------|
| public void CancelSuperCall() |             |
| private void new()            |             |

### Method CancelSuperCall

    public void CancelSuperCall()

### Method new

    private void new()

## Class FormControlCancelEventArgs
    class FormControlCancelEventArgs extends FormControlEventArgs

### Remarks

### Examples

### Methods

| Method                                      | Description |
|---------------------------------------------|-------------|
| ::public static boolean cancelled()         |             |
| ::public static void cancel(boolean cancel) |             |
| public void new(boolean cancel)             |             |

### Method cancelled

    public static boolean cancelled()

#### Return Value

### Method cancel

    public static void cancel(boolean cancel)

#### Parameters

cancel  

### Method new

    public void new(boolean cancel)

#### Parameters

cancel  

## Class FormControlEventArgs
    class FormControlEventArgs

### Remarks

### Examples

### Methods

| Method | Description |
|--------|-------------|



