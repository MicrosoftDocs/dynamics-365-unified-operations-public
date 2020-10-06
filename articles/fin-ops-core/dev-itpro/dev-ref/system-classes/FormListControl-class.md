---
title: FormListControl class
description: This topic describes the FormListControl class.
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

# Class FormListControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormListControl extends FormControl
```

## Remarks

## Examples

## Methods

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
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both. |
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
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.                                 |
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

## Method add

```xpp
public int add(str Text, [int image], [int index])
```

### Parameters - add

Text  

<!-- -->

image  

<!-- -->

index  

### Return Value - add

## Method addColumn

```xpp
public boolean addColumn(int Idx, FormListColumn Column)
```

### Parameters - addColumn

Idx  

<!-- -->

Column  

### Return Value - addColumn

## Method addItem

```xpp
public int addItem(FormListItem item)
```

### Parameters - addItem

item  

### Return Value - addItem

## Method alignControl

Determines whether the control is aligned with other controls.

```xpp
public boolean alignControl([boolean value])
```

### Parameters - alignControl

value  
A Boolean value that indicates whether a form list control is aligned with other controls.

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
A Boolean data type that indicates whether data can be modified.

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

## Method arrangeItem

```xpp
public boolean arrangeItem(FormListArrange ArrangeMethod)
```

### Parameters - arrangeItem

ArrangeMethod  

### Return Value - arrangeItem

## Method autoArrange

```xpp
public boolean autoArrange([boolean value])
```

### Parameters - autoArrange

value  

### Return Value - autoArrange

## Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  
A Boolean data type that indicates whether the system can declare a variable of the same name as a form list control.

### Return Value - autoDeclaration

true if the member variable can be declared for this control; otherwise, false.

### Remarks - autoDeclaration

Controls cannot have identical names.

### Examples - autoDeclaration

The following example shows a call to the autoDeclaration method that specifies that the system can declare a variable that has the same name as a form list control.

```xpp
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
```

## Method backgroundColor

Gets or sets the background color of the control.

```xpp
public int backgroundColor([int value])
```

### Parameters - backgroundColor

value  
An Integer data type that specifies the background color.

### Return Value - backgroundColor

An integer that contains a packed RGB color.

### Remarks - backgroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

## Method backStyle

Determines whether the control background can be transparent.

```xpp
public int backStyle([int value])
```

### Parameters - backStyle

value  
An Integer data type that indicates the background style.

### Return Value - backStyle

1 if the control background can be transparent; otherwise, 0.

## Method beginDrag

Identifies when the user starts to move a form list control or an item in a form list control.

```xpp
public int beginDrag(int x, int y)
```

### Parameters - beginDrag

x  
An Integer data type that indicates the y-coordinate for the move event.

<!-- -->

y  
An Integer data type that indicates the y-coordinate for the move event.

### Return Value - beginDrag

0 (zero) if the event has been handled.

### Remarks - beginDrag

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click beginDrag. For information about best practices for forms and code, see No Code in Forms.

## Method bold

Gets or sets the font weight that is used fort text in the control.

```xpp
public int bold([int value])
```

### Parameters - bold

value  
An Integer data type that specifies the font weight.

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

### Examples - bold

The following example shows a call to the bold method to set the font weight to 9, which indicates heavy.

```xpp
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
```

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

The integer that is returned contains the style of the borderline of the control as follows:

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

## Method calcControlSize

Calculates the font size that is used for a form list control, based on the number of characters and the number of lines.

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

A Container data type value that specifies the size of a form list control.

## Method canScroll

```xpp
public boolean canScroll([boolean value])
```

### Parameters - canScroll

value  

### Return Value - canScroll

## Method characterSet

Gets or sets the character set of the font.

```xpp
public int characterSet([int value])
```

### Parameters - characterSet

value  
An Integer data type that specifies the character set for the text font.

### Return Value - characterSet

An integer value that indicates the character set of the font.

### Remarks - characterSet

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

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set based on the current system locale. For example, if the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the [MSDN website](https://go.microsoft.com/fwlink/?LinkID=85972).

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
An Integer data type that specifies the color palette for a form list control.

### Return Value - colorScheme

An integer between 0 (zero) and 2, inclusive.

### Remarks - colorScheme

The color scheme is defined according to the following table.

| Value | Style                 |
|-------|-----------------------|
| 0     | Default               |
| 1     | The Windows palette   |
| 2     | The true-color scheme |

## Method columnHeader

Sets or gets a Boolean data type value that indicates whether a form list control has a column header.

```xpp
public boolean columnHeader([boolean value])
```

### Parameters - columnHeader

value  
A Boolean data type that indicates whether a form list control has a column header.

### Return Value - columnHeader

true if the control has a column header; otherwise, false.

### Remarks - columnHeader

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value. You must call the columnHeader method before you add a column to the form; otherwise, the column does not appear in the form list control.

### Examples - columnHeader

The following example shows a call to the columnHeader method to indicate that the form list control does not have a column header. The FormListControl.addColumn method adds the column to the form list control.

```xpp
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
```

## Method columnHeaderButton

Sets or gets a Boolean data type value that indicates whether a form list control has a column header button.

```xpp
public boolean columnHeaderButton([boolean value])
```

### Parameters - columnHeaderButton

value  
A Boolean data type that indicates whether a form list control has a column header button.

### Return Value - columnHeaderButton

true if the control has a column header button; otherwise, false.

### Remarks - columnHeaderButton

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value. You must call the columnHeaderButton method before you add a column to the form; otherwise, the column does not appear in the form list control.

### Examples - columnHeaderButton

The following example shows a call to the columnHeaderButton method to indicate that the form list control has a column header button. The FormListControl.addColumn method adds the column to the form list control.

```xpp
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
```

## Method columnImages

Sets or gets a Boolean data type value that indicates whether a form list control has column images.

```xpp
public boolean columnImages([boolean value])
```

### Parameters - columnImages

value  
A Boolean data type that indicates whether a form list control has column images.

### Return Value - columnImages

true if the form list control has column images; otherwise, false.

### Remarks - columnImages

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

### Examples - columnImages

The following example shows a call to the columnImages method to indicate that the form list control has column images. The FormListControl.addColumn method adds the column to the form list control.


```xpp
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
```

## Method configurationKey

Gets or sets the configuration key that is assigned to the control.

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  
A configurationKeyId system data type that specifies the configuration key ID.

### Return Value - configurationKey

The identifier of the configuration key that is assigned to the control.

### Remarks - configurationKey

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Examples - configurationKey

The following example shows a call to the configurationKey method to assign the Bank configuration key to the form list control.

```xpp
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
```

## Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are activated for a form list control.

```xpp
public List configurationKeyEx()
```

### Return Value - configurationKeyEx

A List object that contains the IDs of configuration keys that are activated for a form list control.

### Remarks - configurationKeyEx

If the control is bound to a data source, the retrieved list of configuration key IDs also includes the configuration key ID for the table and field. In addition, the retrieved list contains any configuration key IDs that are applied to the extended data type. The list does not contain duplicate IDs.

### Examples - configurationKeyEx

The following example shows a call to the configurationKeyEx method. The ListEnumerator object is used to traverse the elements throughout a list.

```xpp
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
```

## Method copyItem

Copies a specified item in a form list control.

```xpp
public int copyItem(int Item, int InsertAt)
```

### Parameters - copyItem

Item  
An Integer data type that specifies the position in the list that the item is copied to.

<!-- -->

InsertAt  
An Integer data type that specifies the position in the list that the item is copied to.

### Return Value - copyItem

An Integer data type that specifies the position in the list that the item is copied to.

### Remarks - copyItem

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

### Examples - copyItem

The following example shows a call to the copyItem method to copy an item to the tenth position in the form list control. The FormListControl.getCount method returns the number of items in the control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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

Deletes a specified item from a form list control.

```xpp
public boolean delete(int Idx)
```

### Parameters - delete

Idx  
The zero-based index for the item that is being deleted.

### Return Value - delete

true if the item is deleted; otherwise, false.

### Examples - delete

The following example shows a call to the delete method to delete an item from the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method deleteAll

Deletes all the items from a form list control.

```xpp
public boolean deleteAll()
```

### Return Value - deleteAll

true if all the items are deleted; otherwise, false.

### Examples - deleteAll

The following example shows a call to the deleteAll method to delete all the items from the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method deleteColumn

Deletes a specified column in a form list control.

```xpp
public boolean deleteColumn(int Idx)
```

### Parameters - deleteColumn

Idx  
An Integer data type that specifies a column in a form list control.

### Return Value - deleteColumn

true if the column is deleted; otherwise, false.

### Examples - deleteColumn

The following example shows a call to the deleteColumn method to delete the first column in the form list control. The FormListControl.addColumn method adds two columns to the form list control.

```xpp
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

Determines whether to enable or disable drag-and-drop operations for the control.

```xpp
public int dragDrop([int value])
```

### Parameters - dragDrop

value  
An Integer that indicates whether drag-and-drop behavior is enabled; optional.

### Return Value - dragDrop

1 if drag-and-drop operations are enabled; otherwise, false.

### Remarks - dragDrop

Use the dragLeave, the dragOver, and the dragOverEx to specify the behavior.

## Method dragOver

Identifies when a user drags an object over an item within the bounds of a form list control.

```xpp
public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - dragOver

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

### Return Value - dragOver

A FormDrag system enumeration value that specifies whether the object is moved, copied, or not moved to a specified position.

### Remarks - dragOver

This method is called only if the DragDrop property is set to Manual for the control and a beginDrag event has already been started. For more information about the event, see beginDrag. To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click dragOver. For information about best practices for forms and code, see No Code in Forms.

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

Retrieves the text that is displayed when a user drags an item in a form list control.

```xpp
public str dragText()
```

### Return Value - dragText

A String data type value that specifies the text that is displayed when a user drags a form list control.

### Remarks - dragText

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click dragText. For information about best practices for forms and code, see No Code in Forms.

## Method editLabels

Indicates whether users can modify item names in a form list control.

```xpp
public boolean editLabels([boolean value])
```

### Parameters - editLabels

value  
A Boolean data type that specifies whether users can modify item names in a form list control.

### Return Value - editLabels

true if users can modify item names; otherwise, false.

### Remarks - editLabels

You must call the editLabels method before you add columns to a form list control; otherwise, the columns do not appear in the control.

### Examples - editLabels

The following example shows a call to the editLabels method to enable users to modify item names in the form list control. The DictField.label method returns a label for a specified table field that is added as an item to the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

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

## Method ensureVisible

```xpp
public int ensureVisible(int Idx)
```

### Parameters - ensureVisible

Idx  

### Return Value - ensureVisible

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

Gets or sets the text color for the control.

```xpp
public int foregroundColor([int value])
```

### Parameters - foregroundColor

value  
An Integer data type that specifies the foreground color.

### Return Value - foregroundColor

An integer that contains a packed RGB color.

### Remarks - foregroundColor

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

### Examples - foregroundColor

The following example shows a call to the foregroundColor method to set the foreground color to the color of the menu text on the desktop. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method getColumn

Retrieves a FormListColumn object for a specified column in a form list control.

```xpp
public FormListColumn getColumn(int Idx)
```

### Parameters - getColumn

Idx  
An Integer data type that specifies a column in a form list control.

### Return Value - getColumn

A FormListColumn object for a specified column in a form list control.

### Remarks - getColumn

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

### Examples - getColumn

The following example shows a call to the getColumn method to return a FormListColumn object for the column in the form list control. The FormListControl.addColumn method adds the column to the form list control.


```xpp
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
```

## Method getColumnCount

Retrieves the number of columns in a form list control.

```xpp
public int getColumnCount()
```

### Return Value - getColumnCount

An Integer data type value that specifies the number of columns in a form list control.

### Remarks - getColumnCount

To display columns in a form list control, call the FormListControl.viewType method and then pass the FormListViewType::Report enumeration value.

### Examples - getColumnCount

The following example shows a call to the getColumnCount method to return the number of columns in the form list control. The FormListControl.addColumn method adds the column to the form list control.


```xpp
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
```

## Method getColumnWidth

Retrieves the width of a column in a form list control.

```xpp
public int getColumnWidth(int Idx)
```

### Parameters - getColumnWidth

Idx  
An Integer data type that specifies a column in a form list control.

### Return Value - getColumnWidth

An Integer data type that specifies the width of a column in a form list control.

### Remarks - getColumnWidth

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

### Examples - getColumnWidth

The following example shows a call to the getColumnWidth method to return the width of a column in the form list control. The FormListControl.setColumnWidth method specifies the column width. The FormListControl.addColumn method adds the column to the form list control.

```xpp
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
```

## Method getCount

Retrieves the number of items that are contained in a form list control.

```xpp
public int getCount()
```

### Return Value - getCount

An Integer data type value that specifies the number of items that are contained in a form list control.

### Examples - getCount

The following example shows a call to the getCount method. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method getCountPerPage

```xpp
public int getCountPerPage()
```

### Return Value - getCountPerPage

## Method getImagelist

```xpp
public Imagelist getImagelist([boolean GetLarge])
```

### Parameters - getImagelist

GetLarge  

### Return Value - getImagelist

## Method getItem

Retrieves a FormListItem object for an item in a form list control.

```xpp
public FormListItem getItem(int Idx, [int SubItem])
```

### Parameters - getItem

Idx  
An Integer data type that specifies a sub-item in a form list control.

<!-- -->

SubItem  
An Integer data type that specifies a sub-item in a form list control.

### Return Value - getItem

A FormListItem object for an item in a form list control.

### Examples - getItem

The following example shows a call to the getItem method to return a FormListItem object for each item in the form list control. The FormListItem.toString method returns a text string for each item. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method getItemPos

Retrieves the position of an item in a form list control.

```xpp
public container getItemPos(int Item)
```

### Parameters - getItemPos

Item  
An Integer data type that specifies an item in a form list control.

### Return Value - getItemPos

A Container data type that contains the position of an item in a form list control. The position of an item is specified by an x-coordinate and a y-coordinate.

### Remarks - getItemPos

Use the conPeek function to extract an item from a container.

### Examples - getItemPos

The following example shows a call to the getItemPos method to return the position of each item in the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method getNextItem

Retrieves the number of the next item in a form list control.

```xpp
public int getNextItem(FormListNext nextType, [int startIdx])
```

### Parameters - getNextItem

nextType  
An Integer data type that specifies the item that is before the next item.

<!-- -->

startIdx  
An Integer data type that specifies the item that is before the next item.

### Return Value - getNextItem

An Integer data type value that indicates which item is the next item in a form list control.

### Examples - getNextItem

The following example shows a call to the getNextItem method to retrieve the number of the next item in the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control.

```xpp
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
```

## Method getSelectedCount

Retrieves the number of items that are selected in a form list control.

```xpp
public int getSelectedCount()
```

### Return Value - getSelectedCount

An Integer data type value that indicates the number of items that are selected in a form list control.

### Examples - getSelectedCount

The following example shows a call to the getSelectedCount method to return the number of items that are selected in the form list control. The FormListControl.singleSelection method indicates whether multiple items can be selected. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method getStringWidth

```xpp
public int getStringWidth(str Text)
```

### Parameters - getStringWidth

Text  

### Return Value - getStringWidth

## Method getTopIndex

```xpp
public int getTopIndex()
```

### Return Value - getTopIndex

## Method gridLines

```xpp
public boolean gridLines([boolean value])
```

### Parameters - gridLines

value  

### Return Value - gridLines

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

## Method headerdragdrop

```xpp
public boolean headerdragdrop([boolean value])
```

### Parameters - headerdragdrop

value  

### Return Value - headerdragdrop

## Method height

Gets or sets the height of the control.

```xpp
public int height(int value, [int mode])
```

### Parameters - height

value  
An integer that indicates how the height is calculated; optional. This can be one of the following values:

<!-- -->

mode  
An integer that indicates how the height is calculated; optional. This can be one of the following values:

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

The following example shows a call to the height method to the set the height of the control to 120 pixels.

```xpp
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
```

## Method heightMode

Gets or sets a calculation mode for the height of the control.

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  
An integer that indicates how the height of the control is calculated; optional. This value can be -1 for Exact mode, 0 for Auto mode, or 1 for Column height width.

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

The following example shows a call to the heightMode method to adjust the height of the control, based on an exact pixel value.

```xpp
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

The following example shows a call to the heightValue method that sets the height to 120 pixels.

```xpp
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
```

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
The value that is assigned as the Help text for the control.

### Return Value - helpText

The string to be displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

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

## Method hitTestSubItem

```xpp
public container hitTestSubItem(int x, int y)
```

### Parameters - hitTestSubItem

x  

<!-- -->

y  

### Return Value - hitTestSubItem

## Method hWnd

Retrieves the Windows handle for the control.

```xpp
public int hWnd()
```

### Return Value - hWnd

The handle for the control.

### Remarks - hWnd

The handle can be used with the Windows API.

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

Gets a value that indicates whether the control allows for the specified level of customization.

```xpp
public boolean isUserSetupEnabled(int neededSetupRights)
```

### Parameters - isUserSetupEnabled

neededSetupRights  
A FormAllowUserSetup enumeration value that specifies the level of customization that is being queried for the control.

### Return Value - isUserSetupEnabled

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

### Remarks - isUserSetupEnabled

For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter. The following table describes the values for the neededSetupRights parameter.

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

```xpp
public boolean italic([boolean value])
```

### Parameters - italic

value  

### Return Value - italic

## Method itemAlign

```xpp
public int itemAlign([int value])
```

### Parameters - itemAlign

value  

### Return Value - itemAlign

## Method itemChanging

```xpp
public boolean itemChanging(int Idx, AnyType Data)
```

### Parameters - itemChanging

Idx  

<!-- -->

Data  

### Return Value - itemChanging

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

Identifies when a user moves focus away from a form list control.

```xpp
public boolean leave()
```

### Return Value - leave

true if focus is moved away from the control; otherwise, false.

### Remarks - leave

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click leave. For information about best practices for forms and code, see No Code in Forms.

## Method left

Sets or returns the horizontal position of a form list control in pixels, and specifies how the position is calculated.

```xpp
public int left(int value, [int mode])
```

### Parameters - left

value  
An integer that indicates how the position is calculated; optional. This can be one of the following values:

<!-- -->

mode  
An integer that indicates how the position is calculated; optional. This can be one of the following values:

### Return Value - left

An integer that indicates the horizontal position of a form list control in pixels.

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
```

## Method leftMode

Sets or returns a value that indicates how the horizontal position of a form list control is calculated.

```xpp
public int leftMode([int value])
```

### Parameters - leftMode

value  
An integer that indicates how the horizontal position is calculated; optional.

### Return Value - leftMode

An integer that indicates how the horizontal position is calculated. The return value can be -1 or a FormLeft enumeration value.

### Remarks - leftMode

The value parameter and the return value are integer values that specify how the horizontal position is calculated. This value can be either -1 for an exact pixel value or a FormLeft enumeration value. For more information, see FormLeft Enumeration.

### Examples - leftMode

The following example shows a call to the leftMode method that calculates the horizontal position of a form list control, based on an exact pixel value.

```xpp
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
```

## Method leftValue

Sets or returns the horizontal position of a form list control in pixels.

```xpp
public int leftValue([int value])
```

### Parameters - leftValue

value  
An integer that indicates the horizontal position in pixels; optional.

### Return Value - leftValue

An integer that indicates the horizontal position in pixels.

### Remarks - leftValue

The horizontal position is not changed unless the left mode is set for an exact pixel value. For more information, see leftMode.

### Examples - leftValue

The following example shows a call to the leftValue method that sets the horizontal position to 100 pixels.

```xpp
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

Identifies when a user presses the left mouse button.

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

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click mouseUp. For information about best practices for forms and code, see No Code in Forms.

## Method moveItem

Moves a specified item in a form list control.

```xpp
public int moveItem(int Item, int InsertAt)
```

### Parameters - moveItem

Item  
An Integer data type that specifies the position in the list that the item is moved to.

<!-- -->

InsertAt  
An Integer data type that specifies the position in the list that the item is moved to.

### Return Value - moveItem

An Integer data type that specifies the position in the list that the item is moved to.

### Examples - moveItem

The following example shows a call to the moveItem method to move an item to the tenth position in the form list control. The FormListControl.getCount method returns the number of items in the control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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

## Method oneClickActivate

```xpp
public boolean oneClickActivate([boolean value])
```

### Parameters - oneClickActivate

value  

### Return Value - oneClickActivate

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

## Method redrawItems

Updates a range of items in a form list control.

```xpp
public boolean redrawItems(int idxFirst, int idxLast)
```

### Parameters - redrawItems

idxFirst  
An Integer data type that specifies the zero-based index for the last item in the range.

<!-- -->

idxLast  
An Integer data type that specifies the zero-based index for the last item in the range.

### Return Value - redrawItems

true if the items are updated; otherwise, false.

### Examples - redrawItems

The following example shows a call to the redrawItems method to update a range of items in the form list control. The FormListControl.moveItem method moves a specified item. The FormListControl.getCount method retrieves the number of items in the control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method rowSelect

Sets or gets a Boolean data type value that indicates whether a row in a form list control is selected when the row is clicked.

```xpp
public boolean rowSelect([boolean value])
```

### Parameters - rowSelect

value  
A Boolean data type that indicates whether a row in a form list control is selected when the row is clicked.

### Return Value - rowSelect

true if the row in a form list control is selected; otherwise, false.

### Examples - rowSelect

The following example shows a call to the rowSelect method to specify that a row in the form list control is selected when the row is clicked. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method. The columns are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method scroll

```xpp
public boolean scroll(int dx, int dy)
```

### Parameters - scroll

dx  

<!-- -->

dy  

### Return Value - scroll

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

## Method selectionChanging

```xpp
public boolean selectionChanging(int Idx, AnyType Data)
```

### Parameters - selectionChanging

Idx  

<!-- -->

Data  

### Return Value - selectionChanging

## Method setColumn

```xpp
public boolean setColumn(int Idx, FormListColumn Column)
```

### Parameters - setColumn

Idx  

<!-- -->

Column  

### Return Value - setColumn

## Method setColumnWidth

Specifies the width of a column in a form list control.

```xpp
public boolean setColumnWidth(int Idx, int Width)
```

### Parameters - setColumnWidth

Idx  
An Integer data type that specifies the width of the column in a form list control.

<!-- -->

Width  
An Integer data type that specifies the width of the column in a form list control.

### Return Value - setColumnWidth

true if the width is set; otherwise, false.

### Remarks - setColumnWidth

To display columns in a form list control, call the FormListControl.viewType method, and then pass the FormListViewType::Report enumeration value.

### Examples - setColumnWidth

The following example shows a call to the setColumnWidth method to specify the width of the column in the form list control. The FormListControl.addColumn method adds the column to the form list control.

```xpp
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
```

## Method setItem

Indicates whether an item is contained in a form list control.

```xpp
public boolean setItem(FormListItem item)
```

### Parameters - setItem

item  
A FormListItem object for an item in a form list control.

### Return Value - setItem

true if an item is contained in a form list control; otherwise, false.

### Examples - setItem

The following example shows a call to the setItem method to determine whether each item is contained in the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method setStateImagelist

```xpp
public Imagelist setStateImagelist(Imagelist imageList)
```

### Parameters - setStateImagelist

imageList  

### Return Value - setStateImagelist

## Method showContextMenu

Identifies when a shortcut menu appears.

```xpp
public int showContextMenu(int menuHandle)
```

### Parameters - showContextMenu

menuHandle  
An Integer data type that specifies the menu handle.

### Return Value - showContextMenu

An Integer data type that specifies the menu handle.

### Remarks - showContextMenu

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click showContextMenu. For information about best practices for forms and code, see No Code in Forms.

## Method showSelAlways

```xpp
public boolean showSelAlways([boolean value])
```

### Parameters - showSelAlways

value  

### Return Value - showSelAlways

## Method singleSelection

Indicates whether multiple items can be selected in a form list control.

```xpp
public boolean singleSelection([boolean value])
```

### Parameters - singleSelection

value  
A Boolean data type that indicates whether multiple items can be selected in a form list control.

### Return Value - singleSelection

true if multiple items cannot be selected; otherwise, false.

### Remarks - singleSelection

Call the singleSelection method before you add items to a form list control; otherwise, the items do not appear in the control.

### Examples - singleSelection

The following example shows a call to the singleSelection method to specify that multiple items can be selected. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  
A Boolean value to assign to the skip property of the control; optional.

### Return Value - skip

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

## Method sort

```xpp
public int sort([int value])
```

### Parameters - sort

value  

### Return Value - sort

## Method sortTextItems

```xpp
public boolean sortTextItems([int column], [boolean ascending])
```

### Parameters - sortTextItems

column  

<!-- -->

ascending  

### Return Value - sortTextItems

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

Sets or returns the vertical position of a form list control in pixels, and specifies how the position is calculated.

```xpp
public int top(int value, [int mode])
```

### Parameters - top

value  
An integer that indicates how the vertical position is calculated; optional. This parameter can be one of the following values:

<!-- -->

mode  
An integer that indicates how the vertical position is calculated; optional. This parameter can be one of the following values:

### Return Value - top

An integer that indicates the vertical position of a form list control in pixels.

### Examples - top

The following example shows a call to the top method to set the vertical position to 50 pixels.

```xpp
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
```

## Method topMode

Sets or returns a value that indicates how the vertical position for a form list control is calculated.

```xpp
public int topMode([int value])
```

### Parameters - topMode

value  
An integer that indicates how the vertical position is calculated; optional.

### Return Value - topMode

An Integer data type value that indicates how the vertical position is calculated. The return value can be -1 or a FormTop enumeration value.

### Remarks - topMode

The value parameter and return value are integer values that can be either -1 for an exact pixel value or a FormTop enumeration value. For more information, see FormTop Enumeration.

### Examples - topMode

The following example shows a call to the topMode method that calculates the vertical position based on an exact pixel value.

```xpp
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
```

## Method topValue

Sets or returns the vertical position of a form list control in pixels.

```xpp
public int topValue([int value])
```

### Parameters - topValue

value  
An integer that specifies the vertical position; optional.

### Return Value - topValue

An integer that specifies the vertical position of a form list control.

### Remarks - topValue

The vertical position is not changed unless the top mode is set for an exact pixel value. For more information, see topMode.

### Examples - topValue

The following example shows a call to the topValue method that sets the vertical position to 50 pixels.

```xpp
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
```

## Method trackSelect

```xpp
public boolean trackSelect([boolean value])
```

### Parameters - trackSelect

value  

### Return Value - trackSelect

## Method twoClickActivate

```xpp
public boolean twoClickActivate([boolean value])
```

### Parameters - twoClickActivate

value  

### Return Value - twoClickActivate

## Method type

```xpp
public int type([int value])
```

### Parameters - type

value  

### Return Value - type

## Method underline

Sets or returns the value of the underline property for the text in the control.

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
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, 0.

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

## Method verticalSpacing

Sets or gets the amount of space above and below a form list control in pixels, and specifies how the space is calculated.

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

An integer that indicates the amount of space above and below a control.

## Method verticalSpacingMode

Sets or returns a value that indicates how the space above and below a form list control is calculated.

```xpp
public AutoMode verticalSpacingMode([AutoMode mode])
```

### Parameters - verticalSpacingMode

mode  
An AutoMode system enumeration value that indicates how the space is calculated; optional.

### Return Value - verticalSpacingMode

Auto if the space is automatically adjusted based on other form settings, such as the font size; otherwise, Fixed.

## Method verticalSpacingValue

Sets or returns the amount of space above and below a form list control in pixels.

```xpp
public int verticalSpacingValue([int value])
```

### Parameters - verticalSpacingValue

value  
An integer that indicates the amount of space above and below a control; optional.

### Return Value - verticalSpacingValue

An integer that indicates the amount of space above and below a control.

## Method viewType

```xpp
public int viewType([int value])
```

### Parameters - viewType

value  

### Return Value - viewType

## Method visible

Sets or returns a value that indicates whether the control is visible.

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  
The value to be assigned to the visible setting for the control; optional.

### Return Value - visible

true if the control is visible; otherwise, false.

## Method width

Gets or sets the width of the control.

```xpp
public int width(int value, [int mode])
```

### Parameters - width

value  
An integer that indicates how the width is calculated; optional. This parameter can be one of the following values:

<!-- -->

mode  
An integer that indicates how the width is calculated; optional. This parameter can be one of the following values:

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

The following example shows a call to the width method to set the width of the control to 120 pixels.

```xpp
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
```

## Method widthMode

Gets or sets the calculation mode of the width of the control.

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  
An integer that indicates how the width of the control is calculated; optional.

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

The following example shows a call to the widthMode method to calculate the width of the control, based on an exact pixel value.

```xpp
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
```

## Method widthValue

Gets or sets the width of the control.

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  
An integer that specifies the width of the control in pixels; optional.

### Return Value - widthValue

The width of the control in pixels.

### Remarks - widthValue

To change the width of the control, use the Exact width calculation mode.

### Examples - widthValue

The following example shows a call to the widthValue method that sets the width of the control to 120 pixels.

```xpp
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
```

## Method selectionChanged

```xpp
public void selectionChanged(int Idx, AnyType Data)
```

### Parameters - selectionChanged

Idx  

<!-- -->

Data  

## Method activateItem

```xpp
public void activateItem(int Idx)
```

### Parameters - activateItem

Idx  

## Method inputSearch

Identifies when the search begins for a specified text string.

```xpp
public void inputSearch(str searchStr)
```

### Parameters - inputSearch

searchStr  
A String data type that specifies a text string.

### Remarks - inputSearch

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click inputSearch. For information about best practices for forms and code, see No Code in Forms.

## Method displayControl

Displays the control.

```xpp
public void displayControl()
```

## Method OnLeaving

```xpp
private void OnLeaving([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLeaving

sender  

<!-- -->

e  

## Method update

Updates the control.

```xpp
public void update([int idx])
```

### Parameters - update

idx  

## Method endDrag

Identifies when the user has finished moving a form list control.

```xpp
public void endDrag()
```

### Remarks - endDrag

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click endDrag. For information about best practices for forms and code, see No Code in Forms.

## Method mouseLeave

Indicates that the mouse pointer has left the control.

```xpp
public void mouseLeave()
```

## Method setImagelist

```xpp
public void setImagelist(Imagelist imageList, [boolean SetLarge])
```

### Parameters - setImagelist

imageList  

<!-- -->

SetLarge  

## Method copy

Identifies when a user performs a copy operation.

```xpp
public void copy()
```

### Remarks - copy

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click copy. For information about best practices for forms and code, see No Code in Forms.

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

## Method itemCopy

```xpp
public void itemCopy(int Idx, int newIdx)
```

### Parameters - itemCopy

Idx  

<!-- -->

newIdx  

## Method cut

Identifies when the user performs a cut operation.

```xpp
public void cut()
```

### Remarks - cut

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click cut. For information about best practices for forms and code, see No Code in Forms.

## Method itemMoved

```xpp
public void itemMoved(int Idx, int newIdx)
```

### Parameters - itemMoved

Idx  

<!-- -->

newIdx  

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

## Method paste

Pastes the contents of the clipboard into the control.

```xpp
public void paste()
```

## Method lostFocus

Indicates that the control has lost focus.

```xpp
public void lostFocus()
```

## Method OnSelectionChanged

```xpp
private void OnSelectionChanged([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnSelectionChanged

sender  

<!-- -->

e  

## Method hotTrackItem

Identifies when a user moves the mouse pointer over a form list control.

```xpp
public void hotTrackItem(int Idx)
```

### Parameters - hotTrackItem

Idx  
An Integer data type that specifies the index for a form list control.

### Remarks - hotTrackItem

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click hotTrackItem. For information about best practices for forms and code, see No Code in Forms.

## Method setCount

```xpp
public void setCount(int count)
```

### Parameters - setCount

count  

## Method dragLeave

Identifies when a user drags an object out of the bounds of a form list control.

```xpp
public void dragLeave()
```

### Remarks - dragLeave

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click dragLeave. For information about best practices for forms and code, see No Code in Forms.

## Method itemDeleted

```xpp
public void itemDeleted(int Idx, AnyType Data)
```

### Parameters - itemDeleted

Idx  

<!-- -->

Data  

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

## Method OnGotFocus

```xpp
private void OnGotFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnGotFocus

sender  

<!-- -->

e  

## Method setText

```xpp
public void setText(int Idx, str Text, [int SubItem])
```

### Parameters - setText

Idx  

<!-- -->

Text  

<!-- -->

SubItem  

## Method itemChanged

```xpp
public void itemChanged(int Idx, AnyType Data)
```

### Parameters - itemChanged

Idx  

<!-- -->

Data  

## Method doubleClick

Identifies when a user double-clicks an item in a form list control.

```xpp
public void doubleClick()
```

### Remarks - doubleClick

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click doubleClick. For information about best practices for forms and code, see No Code in Forms.

## Method resetUserSetting

Resets the user settings for the control.

```xpp
public void resetUserSetting()
```

## Method setFocus

Sets the focus on the control.

```xpp
public void setFocus()
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

## Method allItemsDeleted

Identifies when all the items in a form list control are deleted.

```xpp
public void allItemsDeleted()
```

### Remarks - allItemsDeleted

To override this method in a form list control, right-click the Methods node below the control, point to Override Method, and then click allItemsDeleted. For information about best practices for forms and code, see No Code in Forms.

## Method drop

Identifies when a user drops a form list control or an item in a form list control into a new position.

```xpp
public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)
```

### Parameters - drop

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

### Remarks - drop

This method is called only if the DragDrop property is set to Manual for the control and a beginDrag event has already been started. For more information about the event, see beginDrag. To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click drop. For information about best practices for forms and code, see No Code in Forms.

## Method columnClicked

Identifies when a user clicks a column in a list view control in a form.

```xpp
public void columnClicked(int Column)
```

### Parameters - columnClicked

Column  
An Integer data type that specifies a form column.

### Remarks - columnClicked

To override this method on a list view control, right-click the Methods node below the control, click Override Method, and then click columnClicked. For information about best practices for forms and code, see No Code in Forms.

## Method getStateImagelist

```xpp
public void getStateImagelist()
```

## Method OnLostFocus

```xpp
private void OnLostFocus([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnLostFocus

sender  

<!-- -->

e  

## Method setItemPos

Sets the position of an item in a form list control.

```xpp
public void setItemPos(int Item, int x, int y)
```

### Parameters - setItemPos

Item  
An Integer data type that specifies the y-coordinate of the position of an item.

<!-- -->

x  
An Integer data type that specifies the y-coordinate of the position of an item.

<!-- -->

y  
An Integer data type that specifies the y-coordinate of the position of an item.

### Examples - setItemPos

The following example shows a call to the setItemPos method to specify the position of each item in the form list control. The while select statement retrieves account numbers from the CustTable table and then stores the data in a container. The items in the variable are added to the form list control by calling the FormListControl.addItem method.

```xpp
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
```

## Method gotFocus

Indicates that the control has received focus.

```xpp
public void gotFocus()
```

## Method enter

```xpp
public void enter()
```

## Method OnEnter

```xpp
private void OnEnter([FormControl sender], [FormControlEventArgs e])
```

### Parameters - OnEnter

sender  

<!-- -->

e  

## Method context

Identifies when the user opens a shortcut menu in a form list control.

```xpp
public void context()
```

### Remarks - context

To override this method on a list view control, right-click the Methods node below the control, point to Override Method, and then click context. For information about best practices for forms and code, see No Code in Forms.

## Method beginEditLabel

```xpp
public void beginEditLabel(int Idx)
```

### Parameters - beginEditLabel

Idx  

## Method itemInserted

```xpp
public void itemInserted(int Idx, AnyType Data)
```

### Parameters - itemInserted

Idx  

<!-- -->

Data  

