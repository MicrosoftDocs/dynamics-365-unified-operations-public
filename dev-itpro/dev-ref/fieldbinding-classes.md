---
# required metadata

title: F Classes - FieldBinding to FormBuildAnimateControl
description: System API classes that start with the letter F.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 52411
ms.assetid: 64592da4-d509-4309-a30c-729e7cddd510
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# F Classes - FieldBinding to FormBuildAnimateControl

[!include[banner](../includes/banner.md)]


System API classes that start with the letter F.

Class FieldBinding
------------------

    class FieldBinding extends Object

### Remarks

### Examples

### Methods

| Method                                                   | Description                                                |
|----------------------------------------------------------|------------------------------------------------------------|
| public int fieldArrayIndex()                             |                                                            |
| public int fieldId()                                     |                                                            |
| public str fieldName()                                   |                                                            |
| public boolean isEqualTo(FieldBinding otherFieldBinding) |                                                            |
| public boolean isNull()                                  |                                                            |
| public boolean isValid()                                 |                                                            |
| public container pack()                                  | Serializes the current instance of the FieldBinding class. |
| public int tableId()                                     |                                                            |
| public str tableName()                                   |                                                            |
| public void new()                                        | Initializes a new instance of the FieldBinding class.      |

### Method fieldArrayIndex

    public int fieldArrayIndex()

#### Return Value

### Method fieldId

    public int fieldId()

#### Return Value

### Method fieldName

    public str fieldName()

#### Return Value

### Method isEqualTo

    public boolean isEqualTo(FieldBinding otherFieldBinding)

#### Parameters

otherFieldBinding  

#### Return Value

### Method isNull

    public boolean isNull()

#### Return Value

### Method isValid

    public boolean isValid()

#### Return Value

### Method pack

Serializes the current instance of the FieldBinding class.

    public container pack()

#### Return Value

A container that contains the current instance of the FieldBinding class.

### Method tableId

    public int tableId()

#### Return Value

### Method tableName

    public str tableName()

#### Return Value

### Method new

Initializes a new instance of the FieldBinding class.

    public void new()

## Class FieldFilterValue
    class FieldFilterValue extends FilterValue

### Remarks

### Examples

### Methods

| Method                                                      | Description                                     |
|-------------------------------------------------------------|-------------------------------------------------|
| public AnyType valueAnyType()                               |                                                 |
| public void new(FieldBinding fieldBinding, str filterValue) | Initializes a new instance of the Object class. |

### Method valueAnyType

    public AnyType valueAnyType()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(FieldBinding fieldBinding, str filterValue)

#### Parameters

fieldBinding  

<!-- -->

filterValue  

## Class FileIOPermission
    class FileIOPermission extends CodeAccessPermission

The FileIOPermission class controls the ability to access files and folders.

### Remarks

The FileIoPermission class is designed to check permissions for specific APIs. For a list of all APIs that are protected by permissions, see Secured APIs. Before the protected API is run, you must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission::demand method is called on. Call a method on the server tier from one of the following:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property

### Examples

The following code example shows a new instance of the FileIoPermission class that specifies read access for the File.txt file. The assert method is called to declare that the code can then call the AsciiIo.new method.

    server static void main(Args args) 
    { 
        FileIoPermission _perm; 
        AsciiIo a; 
        _perm = new FileIoPermission("c:\\File.txt",'r'); 
        _perm.assert(); 
        // Invoke the protected API. 
        a = new AsciiIo("c:\\File.txt",'r'); 
    }

### Methods

| Method                                                 | Description                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.               |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether the current permission is a subset of a specified permission. |
| public void new(str filename, str mode)                | Initializes a new instance of the CodeAccessPermission class.                    |

### Method copy

Creates and returns a copy of the current permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the current permission object.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class. For more information, see copy.

### Method isSubsetOf

Determines whether the current permission is a subset of a specified permission.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if the current permission is a subset of the specified permission; otherwise, false.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class. For more information, see M: CodeAccessPermission.isSubsetOf.

### Method new

Initializes a new instance of the CodeAccessPermission class.

    public void new(str filename, str mode)

#### Parameters

filename  
A String data type that specifies the type of access.

<!-- -->

mode  
A String data type that specifies the type of access.

#### Remarks

The following table lists the possible values for the \_mode parameter.

|     |                |
|-----|----------------|
| R   | Read           |
| W   | Write          |
| RW  | Read and write |

#### Examples

The following code example shows a new instance of the FileIoPermission class that specifies read access for the File.txt file.

    server static void main(Args args) 
    { 
        FileIoPermission _perm; 
        _perm = new FileIoPermission("c:\\File.txt",'r'); 
    }

## Class FilterValue
    class FilterValue extends Object

### Remarks

### Examples

### Methods

| Method                             | Description |
|------------------------------------|-------------|
| public FieldBinding fieldBinding() |             |
| public str value(\[str fvalue\])   |             |
| public str valueForQueryRange()    |             |

### Method fieldBinding

    public FieldBinding fieldBinding()

#### Return Value

### Method value

    public str value([str fvalue])

#### Parameters

fvalue  

#### Return Value

### Method valueForQueryRange

    public str valueForQueryRange()

#### Return Value

## Class Form
    class Form extends TreeNode

The Form class represents an instance of a design-time form.

### Remarks

### Examples

### Methods

| Method                                                                                                                           | Description                                                                                                               |
|----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public FormBuildControl addControl(FormControlType controlType, str controlName)                                                 |                                                                                                                           |
| public FormBuildControl addControlEx(str controlClass, str controlName, \[FormBuildControl insertAfter\], \[boolean pushFront\]) |                                                                                                                           |
| public FormBuildDataSource addDataSource(str name, \[str tableName\])                                                            |                                                                                                                           |
| public List rootFormDataSources()                                                                                                |                                                                                                                           |
| public FormBuildDesign addDesign(str name)                                                                                       |                                                                                                                           |
| public Query query(str queryName)                                                                                                |                                                                                                                           |
| public boolean allowPreLoading(\[boolean value\])                                                                                | A Boolean value that determines whether a preloaded instance can be used when the associated FormRun instance is created. |
| public boolean autoCacheUpdate(\[boolean value\])                                                                                |                                                                                                                           |
| public str changedBy(\[str value\])                                                                                              | Gets or sets the name of the user who last changed the application object.                                                |
| public Date changedDate(\[Date value\])                                                                                          | Gets or sets the date an application object was last changed.                                                             |
| public str changedTime(\[str value\])                                                                                            | Gets or sets the time an application object was last changed.                                                             |
| public ChangeGroupMode changeGroupMode(\[ChangeGroupMode value\])                                                                |                                                                                                                           |
| public str createdBy(\[str value\])                                                                                              | Gets or sets the name of the user who created the application object.                                                     |
| public Date creationDate(\[Date value\])                                                                                         | Gets or sets the date an application object was created.                                                                  |
| public str creationTime(\[str value\])                                                                                           |                                                                                                                           |
| public FormBuildDataSource dataSource(AnyType objectSet)                                                                         |                                                                                                                           |
| public int dataSourceCount()                                                                                                     |                                                                                                                           |
| public FormBuildDesign design(\[int designNo\])                                                                                  |                                                                                                                           |
| public int formTemplate(\[int value\])                                                                                           |                                                                                                                           |
| public str interactionClass(\[str value\])                                                                                       |                                                                                                                           |
| public boolean isLoadedForInference()                                                                                            |                                                                                                                           |
| public str name(\[str value\])                                                                                                   | Gets or sets the name that is used in code to identify a form, report, rable, query, or another MSDAX application object. |
| public Guid origin(\[Guid value\])                                                                                               |                                                                                                                           |
| ::public static boolean formKernelObjectHasMethod(Object kernelObject, str methodName)                                           |                                                                                                                           |
| ::public static boolean formObjectSetHasMethod(FormObjectSet formObjectSet, str methodName)                                      |                                                                                                                           |
| ::public static boolean formRunHasMethod(xFormRun formRun, str methodName)                                                       |                                                                                                                           |
| ::public static str getSetupUserQueryElementName(MenuItemType menuItemType, str menuItemName)                                    |                                                                                                                           |
| public void new(\[str name\], \[boolean buildMode\])                                                                             | Initializes a new instance of the Form class.                                                                             |
| public void inInitializeDesign(\[boolean value\])                                                                                |                                                                                                                           |
| public void save()                                                                                                               |                                                                                                                           |
| public void load(str name, \[boolean buildMode\])                                                                                |                                                                                                                           |
| public void finalize()                                                                                                           |                                                                                                                           |

### Method addControl

    public FormBuildControl addControl(FormControlType controlType, str controlName)

#### Parameters

controlType  

<!-- -->

controlName  

#### Return Value

### Method addControlEx

    public FormBuildControl addControlEx(str controlClass, str controlName, [FormBuildControl insertAfter], [boolean pushFront])

#### Parameters

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

<!-- -->

pushFront  

#### Return Value

### Method addDataSource

    public FormBuildDataSource addDataSource(str name, [str tableName])

#### Parameters

name  

<!-- -->

tableName  

#### Return Value

### Method rootFormDataSources

    public List rootFormDataSources()

#### Return Value

### Method addDesign

    public FormBuildDesign addDesign(str name)

#### Parameters

name  

#### Return Value

### Method query

    public Query query(str queryName)

#### Parameters

queryName  

#### Return Value

### Method allowPreLoading

A Boolean value that determines whether a preloaded instance can be used when the associated FormRun instance is created.

    public boolean allowPreLoading([boolean value])

#### Parameters

value  
true if a preloaded instance can be used when the associated FormRun instance is created; otherwise, false.

#### Return Value

true if a preloaded instance can be used when the associated FormRun instance is created; otherwise, false.

### Method autoCacheUpdate

    public boolean autoCacheUpdate([boolean value])

#### Parameters

value  

#### Return Value

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method changeGroupMode

    public ChangeGroupMode changeGroupMode([ChangeGroupMode value])

#### Parameters

value  

#### Return Value

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

    public FormBuildDataSource dataSource(AnyType objectSet)

#### Parameters

objectSet  

#### Return Value

### Method dataSourceCount

    public int dataSourceCount()

#### Return Value

### Method design

    public FormBuildDesign design([int designNo])

#### Parameters

designNo  

#### Return Value

### Method formTemplate

    public int formTemplate([int value])

#### Parameters

value  

#### Return Value

### Method interactionClass

    public str interactionClass([str value])

#### Parameters

value  

#### Return Value

### Method isLoadedForInference

    public boolean isLoadedForInference()

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another MSDAX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method formKernelObjectHasMethod

    public static boolean formKernelObjectHasMethod(Object kernelObject, str methodName)

#### Parameters

kernelObject  

<!-- -->

methodName  

#### Return Value

### Method formObjectSetHasMethod

    public static boolean formObjectSetHasMethod(FormObjectSet formObjectSet, str methodName)

#### Parameters

formObjectSet  

<!-- -->

methodName  

#### Return Value

### Method formRunHasMethod

    public static boolean formRunHasMethod(xFormRun formRun, str methodName)

#### Parameters

formRun  

<!-- -->

methodName  

#### Return Value

### Method getSetupUserQueryElementName

    public static str getSetupUserQueryElementName(MenuItemType menuItemType, str menuItemName)

#### Parameters

menuItemType  

<!-- -->

menuItemName  

#### Return Value

### Method new

Initializes a new instance of the Form class.

    public void new([str name], [boolean buildMode])

#### Parameters

name  

<!-- -->

buildMode  

### Method inInitializeDesign

    public void inInitializeDesign([boolean value])

#### Parameters

value  

### Method save

    public void save()

### Method load

    public void load(str name, [boolean buildMode])

#### Parameters

name  

<!-- -->

buildMode  

### Method finalize

    public void finalize()

## Class FormActionPaneControl
    class FormActionPaneControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                              | Description                                                                                                                                          |
|---------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            |                                                                                                                                                      |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |                                                                                                                                                      |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) |                                                                                                                                                      |
| public boolean alignChild(\[boolean value\])                                                                        |                                                                                                                                                      |
| public boolean alignChildren(\[boolean value\])                                                                     |                                                                                                                                                      |
| public boolean alignControl(\[boolean value\])                                                                      | Determines whether to align the control.                                                                                                             |
| public boolean allowEdit(\[boolean value\])                                                                         | Determines whether the user can change the contents of the control.                                                                                  |
| public boolean allowSysSetup()                                                                                      | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                  |
| public int allowUserSetup(\[int value\])                                                                            |                                                                                                                                                      |
| public int arrangeGuide(\[int value\])                                                                              |                                                                                                                                                      |
| public int arrangeMethod(\[int value\])                                                                             |                                                                                                                                                      |
| public int arrangeWhen(\[int value\])                                                                               |                                                                                                                                                      |
| public boolean autoDeclaration(\[boolean value\])                                                                   | Determines whether the system can declare a member variable that has the same name as the control.                                                   |
| public int beginDrag(int x, int y)                                                                                  | Is called when the user starts to drag a form control.                                                                                               |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                           |                                                                                                                                                      |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                                 |                                                                                                                                                      |
| public int bottomMarginValue(\[int value\])                                                                         |                                                                                                                                                      |
| public container calcControlSize(int chars, int lines)                                                              | Retrieves the size of the control.                                                                                                                   |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                               |                                                                                                                                                      |
| public boolean canContain(FormControl control)                                                                      |                                                                                                                                                      |
| public str caption(\[str value\])                                                                                   | Gets or set the caption of the control.                                                                                                              |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                             |                                                                                                                                                      |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                                |                                                                                                                                                      |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                            |                                                                                                                                                      |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                                  |                                                                                                                                                      |
| public int columnspaceValue(\[int value\])                                                                          |                                                                                                                                                      |
| public int columnsValue(\[int value\])                                                                              |                                                                                                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                            | Gets or sets the configuration key that is assigned to the control.                                                                                  |
| public List configurationKeyEx()                                                                                    | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                     |
| public boolean contains(FormControl control)                                                                        |                                                                                                                                                      |
| public int controlCount()                                                                                           |                                                                                                                                                      |
| public FormControl controlNum(int controlNo)                                                                        |                                                                                                                                                      |
| public str dataRelationPath(\[str value\])                                                                          | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                        |
| public int dataSource(\[AnyType value\])                                                                            | Gets or sets a data source that will be used by the control or the form.                                                                             |
| public int displayTarget(\[int value\])                                                                             | Gets or sets the value that indicates whether the control is displayed in the client, or in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both. |
| public int dragDrop(\[int value\])                                                                                  | Determines whether to enable or disable drag-and-drop operations for the control.                                                                    |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                       |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                     |
| public str dragText()                                                                                               | Retrieves the text that is displayed when the form control is dragged.                                                                               |
| public boolean enabled(\[boolean value\])                                                                           | Determines whether to enable or disable the object.                                                                                                  |
| public boolean hasChanged(\[boolean val\])                                                                          | Sets or returns a value that indicates whether the contents of the control have changed.                                                             |
| public boolean hasUserSetting()                                                                                     | Indicates whether the control has custom user settings.                                                                                              |
| public int height(int value, \[int mode\])                                                                          | Gets or sets the height of the control.                                                                                                              |
| public int heightMode(\[int value\])                                                                                | Gets or sets a calculation mode for the height of the control.                                                                                       |
| public int heightValue(\[int value\])                                                                               | Gets or sets the height of the control.                                                                                                              |
| public str helpField()                                                                                              | Retrieves the Help text for the control.                                                                                                             |
| public str helpText(\[str value\])                                                                                  | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                             |
| public boolean hideIfEmpty(\[boolean value\])                                                                       |                                                                                                                                                      |
| public str hierarchyParent(\[str value\])                                                                           | Gets or sets the HierarchyParent property value of the control.                                                                                      |
| public int hWnd()                                                                                                   | Retrieves the Windows handle for the control.                                                                                                        |
| public boolean isContainer()                                                                                        |                                                                                                                                                      |
| public boolean isDisplayed()                                                                                        | Retrieves a value that indicates whether the control is displayed.                                                                                   |
| public boolean isRestricted()                                                                                       | Retrieves a value that indicates whether the control is restricted.                                                                                  |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                |
| public boolean leave()                                                                                              |                                                                                                                                                      |
| public int left(int value, \[int mode\])                                                                            | Gets or sets the horizontal position of the control in the form.                                                                                     |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                             |                                                                                                                                                      |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                                   |                                                                                                                                                      |
| public int leftMarginValue(\[int value\])                                                                           |                                                                                                                                                      |
| public int leftMode(\[int value\])                                                                                  | Sets the horizontal arrange mode for the control in the form.                                                                                        |
| public int leftValue(\[int value\])                                                                                 | Gets or sets the horizontal position of the control in the form.                                                                                     |
| public boolean markAsUserAdd(\[boolean value\])                                                                     | Marks or unmarks the control as a user-added control.                                                                                                |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                     | Is called when the control is double-clicked by the user.                                                                                            |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user clicks the mouse button over the control.                                                                                    |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user moves the mouse pointer over the control.                                                                                    |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                           | Is called when the user releases the mouse button over the control area.                                                                             |
| public int moveControl(int controlId, \[int insertAfterId\])                                                        |                                                                                                                                                      |
| public str name(\[str value\])                                                                                      | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.        |
| public int neededPermission(\[int value\])                                                                          |                                                                                                                                                      |
| public container SysObsoleteAttribute()                                                                             |                                                                                                                                                      |
| public FormControl parentControl()                                                                                  | Retrieves the parent control for the control.                                                                                                        |
| public int position(\[int value\])                                                                                  |                                                                                                                                                      |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                            |                                                                                                                                                      |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                                  |                                                                                                                                                      |
| public int rightMarginValue(\[int value\])                                                                          |                                                                                                                                                      |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                           | Sets or returns the ID of the security key for the control.                                                                                          |
| public int showContextMenu(int menuHandle)                                                                          | Shows the shortcut menu for the control.                                                                                                             |
| public boolean skip(\[boolean value\])                                                                              | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                      |
| public int sort(\[SortOrder sortDirection\])                                                                        |                                                                                                                                                      |
| public int style(\[int value\])                                                                                     |                                                                                                                                                      |
| public str toolTip()                                                                                                | Retrieves the tooltip text for the control.                                                                                                          |
| public int top(int value, \[int mode\])                                                                             | Gets or sets the vertical position of the control in the form.                                                                                       |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                              |                                                                                                                                                      |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                                    |                                                                                                                                                      |
| public int topMarginValue(\[int value\])                                                                            |                                                                                                                                                      |
| public int topMode(\[int value\])                                                                                   | Sets the vertical arrange mode for the control in the form.                                                                                          |
| public int topValue(\[int value\])                                                                                  | Gets or sets the vertical position of the control in the form.                                                                                       |
| public int type(\[int value\])                                                                                      |                                                                                                                                                      |
| public boolean SysObsoleteAttribute(container data)                                                                 |                                                                                                                                                      |
| public int userData(\[int value\])                                                                                  | Gets or sets the user data for the control.                                                                                                          |
| public int userDataItem(\[int value\])                                                                              | Gets or sets the user data item for the control.                                                                                                     |
| public int userDataItems(\[int value\])                                                                             | Gets or sets the number of user data items for the control.                                                                                          |
| public int userDisable(\[int value\])                                                                               | Gets or sets the value that indicates whether the control is disabled for the user.                                                                  |
| public int userHeight(\[int value\])                                                                                | Gets or sets the custom user height for the control.                                                                                                 |
| public int userHide(\[int value\])                                                                                  | Gets or sets the value that indicates whether the control is hidden from the user.                                                                   |
| public int userOrgContainer(\[int value\])                                                                          | Gets or sets the organization container for the control.                                                                                             |
| public int userOrgSibling(\[int value\])                                                                            | Gets or sets the organization sibling for the control.                                                                                               |
| public str userPromptText(\[str value\])                                                                            | Gets or sets the user label text for the control.                                                                                                    |
| public int userSecurityLevel(\[int value\])                                                                         | Gets or sets the user security level for the control.                                                                                                |
| public int userSkip(\[int value\])                                                                                  | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form. |
| public int userWidth(\[int value\])                                                                                 | Sets or returns the width of the control in pixels.                                                                                                  |
| public boolean useUserLayout(\[boolean value\])                                                                     |                                                                                                                                                      |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                        | Gets or sets the vertical spacing of the control in the form.                                                                                        |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                              | Sets the vertical spacing mode for the control in the form.                                                                                          |
| public int verticalSpacingValue(\[int value\])                                                                      | Gets or sets the vertical spacing of the control in the form.                                                                                        |
| public boolean visible(\[boolean value\])                                                                           | Sets or returns a value that indicates whether the control is visible.                                                                               |
| public int width(int value, \[int mode\])                                                                           | Gets or sets the width of the control.                                                                                                               |
| public int widthMode(\[int value\])                                                                                 | Gets or sets the calculation mode of the width of the control.                                                                                       |
| public int widthValue(\[int value\])                                                                                | Gets or sets the width of the control.                                                                                                               |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                           | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                   |
| public void lostFocus()                                                                                             | Indicates that the control has lost focus.                                                                                                           |
| public void filter(\[str filterStr\])                                                                               |                                                                                                                                                      |
| public void dragLeave()                                                                                             | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                     |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                       | Is called when the user moves the mouse pointer into the control area.                                                                               |
| public void gotFocus()                                                                                              | Indicates that the control has received focus.                                                                                                       |
| public void mouseLeave()                                                                                            | Indicates that the mouse pointer has left the control.                                                                                               |
| public void setArea(str area)                                                                                       |                                                                                                                                                      |
| public void arrange()                                                                                               |                                                                                                                                                      |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                          |                                                                                                                                                      |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                         |                                                                                                                                                      |
| public void jumpRef()                                                                                               |                                                                                                                                                      |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                            |                                                                                                                                                      |
| public void inputSearch(str searchStr)                                                                              | Performs data filtering for the control, based on the specified string.                                                                              |
| public void endDrag()                                                                                               | Is called when the user has finished dragging a form control.                                                                                        |
| public void setFocus()                                                                                              | Sets the focus on the control.                                                                                                                       |
| public void tabChanged(str newTab)                                                                                  | Is called when the active tab is changed.                                                                                                            |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                        |                                                                                                                                                      |
| public void displayControl()                                                                                        | Displays the control.                                                                                                                                |
| public void prefColumnSize(int width, int height)                                                                   | Specifies the preferred column width and height for the form control.                                                                                |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\])         |                                                                                                                                                      |
| public void cut()                                                                                                   | Cuts the contents of the control.                                                                                                                    |
| public void resetUserSetting()                                                                                      | Resets the user settings for the control.                                                                                                            |
| private void OnTabChanged(\[FormControl sender\], \[FormControlEventArgs e\])                                       |                                                                                                                                                      |
| public void paste()                                                                                                 | Pastes the contents of the clipboard into the control.                                                                                               |
| public void copy()                                                                                                  | Copies the contents of the control to the clipboard.                                                                                                 |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                               | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                 |
| public void context()                                                                                               | Shows the shortcut menu for the control.                                                                                                             |
| public void enter()                                                                                                 |                                                                                                                                                      |

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

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control will be shown in the SysSetup form; otherwise, false.

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

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
The property is set to this value; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

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

Retrieves the size of the control.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

#### Return Value

The container that has the width and height.

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

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

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

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key to assign to the control; optional.

#### Return Value

The ID of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed.

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

Gets or sets the value that indicates whether the control is displayed in the client, or in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the FormControl::dragLeave method , the FormControl::dragOver method, and the FormControl::dragOverEx method to specify the behavior.

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
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An Integer value that indicates the vertical client coordinate of the mouse position.

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

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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
An Integer value that indicates how the control height is calculated; optional.

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

The helpField method cannot be used to set the value of the Help text.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box.The help text must not exceed 250 characters.

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
The value to assign as the HierarchyParent value of the control.

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
| FormAllowUserSetup::No 0         | No changes can be made to the control. Using this value for the neededSetupRights parameter always returns true.                 |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

This method returns true only if the AllowUserSetup property for the design and all parent containers allows for the level of access that is specified by the neededSetupRights parameter.

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
A Boolean value that indicates whether the control should be marked as a user-added control.

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

Typically, when this method is overridden, the return value from a call to super is returned.

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

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

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

Typically, when this method is overridden, the return value from a call to super is returned.

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

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method moveControl

    public int moveControl(int controlId, [int insertAfterId])

#### Parameters

controlId  

<!-- -->

insertAfterId  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

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

### Method position

    public int position([int value])

#### Parameters

value  

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

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. Right-clicking invokes a menu that enables the control to be hidden or displayed. This method lets you programmatically determine and set the value.

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

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to invoke the setup form in which the character specification is made.

### Method useUserLayout

    public boolean useUserLayout([boolean value])

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
An Integer value that indicates how control width is calculated; optional.

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

### Method drop

Raises the drop event to indicate that a drop operation is being performed on the current control.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An Integer value that indicates the vertical client coordinate of the mouse position.

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

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

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method setArea

    public void setArea(str area)

#### Parameters

area  

### Method arrange

    public void arrange()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

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

### Method jumpRef

    public void jumpRef()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

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

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method tabChanged

Is called when the active tab is changed.

    public void tabChanged(str newTab)

#### Parameters

newTab  

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method cut

Cuts the contents of the control.

    public void cut()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method OnTabChanged

    private void OnTabChanged([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An Integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An Integer value that indicates the vertical client coordinate of the mouse position.

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method enter

    public void enter()

## Class FormActionPaneTabControl
    class FormActionPaneTabControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                              | Description                                                                                                                                          |
|---------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            |                                                                                                                                                      |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |                                                                                                                                                      |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) |                                                                                                                                                      |
| public boolean alignChild(\[boolean value\])                                                                        |                                                                                                                                                      |
| public boolean alignChildren(\[boolean value\])                                                                     |                                                                                                                                                      |
| public boolean alignControl(\[boolean value\])                                                                      | Determines whether to align the control.                                                                                                             |
| public boolean allowEdit(\[boolean value\])                                                                         | Determines whether the user can change the contents of the control.                                                                                  |
| public boolean allowSysSetup()                                                                                      | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                  |
| public int allowUserSetup(\[int value\])                                                                            |                                                                                                                                                      |
| public int arrangeGuide(\[int value\])                                                                              |                                                                                                                                                      |
| public int arrangeMethod(\[int value\])                                                                             |                                                                                                                                                      |
| public int arrangeWhen(\[int value\])                                                                               |                                                                                                                                                      |
| public boolean autoDeclaration(\[boolean value\])                                                                   | Determines whether the system can declare a member variable that has the same name as the control.                                                   |
| public int beginDrag(int x, int y)                                                                                  | Called when the user starts to drag a form control.                                                                                                  |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                           |                                                                                                                                                      |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                                 |                                                                                                                                                      |
| public int bottomMarginValue(\[int value\])                                                                         |                                                                                                                                                      |
| public container calcControlSize(int chars, int lines)                                                              | Retrieves the size of the control.                                                                                                                   |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                               |                                                                                                                                                      |
| public boolean canContain(FormControl control)                                                                      |                                                                                                                                                      |
| public str caption(\[str value\])                                                                                   | Gets or set the caption of the control.                                                                                                              |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                             |                                                                                                                                                      |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                                |                                                                                                                                                      |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                            |                                                                                                                                                      |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                                  |                                                                                                                                                      |
| public int columnspaceValue(\[int value\])                                                                          |                                                                                                                                                      |
| public int columnsValue(\[int value\])                                                                              |                                                                                                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                            | Gets or sets the configuration key that is assigned to the control.                                                                                  |
| public List configurationKeyEx()                                                                                    | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                     |
| public boolean contains(FormControl control)                                                                        |                                                                                                                                                      |
| public int controlCount()                                                                                           |                                                                                                                                                      |
| public FormControl controlNum(int controlNo)                                                                        |                                                                                                                                                      |
| public str countryRegionCodes(\[str value\])                                                                        | Gets or sets the comma-separated list of country/region codes for the control.                                                                       |
| public FieldId countryRegionContextField(\[FieldId value\])                                                         |                                                                                                                                                      |
| public str dataRelationPath(\[str value\])                                                                          | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                        |
| public int dataSource(\[AnyType value\])                                                                            | Gets or sets a data source to be used by the control or the form.                                                                                    |
| public int displayTarget(\[int value\])                                                                             | Gets or sets the value that indicates whether the control is displayed in the client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.    |
| public int dragDrop(\[int value\])                                                                                  | Determines whether to enable or disable drag-and-drop operations for the control.                                                                    |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                       |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                     |
| public str dragText()                                                                                               | Retrieves the text that is displayed when the form control is dragged.                                                                               |
| public boolean enabled(\[boolean value\])                                                                           | Determines whether to enable or disable the object.                                                                                                  |
| public boolean hasChanged(\[boolean val\])                                                                          | Sets or returns a value that indicates whether the contents of the control have changed.                                                             |
| public boolean hasUserSetting()                                                                                     | Indicates whether the control has custom user settings.                                                                                              |
| public int height(int value, \[int mode\])                                                                          | Gets or sets the height of the control.                                                                                                              |
| public int heightMode(\[int value\])                                                                                | Gets or sets a calculation mode for the height of the control.                                                                                       |
| public int heightValue(\[int value\])                                                                               | Gets or sets the height of the control.                                                                                                              |
| public str helpField()                                                                                              | Retrieves the Help text for the control.                                                                                                             |
| public str helpText(\[str value\])                                                                                  | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                             |
| public boolean hideIfEmpty(\[boolean value\])                                                                       |                                                                                                                                                      |
| public str hierarchyParent(\[str value\])                                                                           | Gets or sets the HierarchyParent property value of the control.                                                                                      |
| public int hWnd()                                                                                                   | Retrieves the Windows handle for the control.                                                                                                        |
| public int imageLocation(\[int value\])                                                                             |                                                                                                                                                      |
| public boolean isContainer()                                                                                        |                                                                                                                                                      |
| public boolean isDisplayed()                                                                                        | Retrieves a value that indicates whether the control is displayed.                                                                                   |
| public boolean isRestricted()                                                                                       | Retrieves a value that indicates whether the control is restricted.                                                                                  |
| public boolean isSelected()                                                                                         |                                                                                                                                                      |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                |
| public str keyTip(\[str value\])                                                                                    |                                                                                                                                                      |
| public boolean leave()                                                                                              |                                                                                                                                                      |
| public int left(int value, \[int mode\])                                                                            | Gets or sets the horizontal position of the control in the form.                                                                                     |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                             |                                                                                                                                                      |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                                   |                                                                                                                                                      |
| public int leftMarginValue(\[int value\])                                                                           |                                                                                                                                                      |
| public int leftMode(\[int value\])                                                                                  | Sets the horizontal arrange mode for the control in the form.                                                                                        |
| public int leftValue(\[int value\])                                                                                 | Gets or sets the horizontal position of the control in the form.                                                                                     |
| public boolean markAsUserAdd(\[boolean value\])                                                                     | Marks or unmarks the control as a user-added control.                                                                                                |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                     | Is called when the control is double-clicked by the user.                                                                                            |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user clicks the mouse button over the control.                                                                                    |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user moves the mouse pointer over the control.                                                                                    |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                           | Is called when the user releases the mouse button over the control area.                                                                             |
| public int moveControl(int controlId, \[int insertAfterId\])                                                        |                                                                                                                                                      |
| public str name(\[str value\])                                                                                      | Gets or sets the name used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.                    |
| public int neededPermission(\[int value\])                                                                          |                                                                                                                                                      |
| public str normalImage(\[str value\])                                                                               |                                                                                                                                                      |
| public int normalResource(\[int value\])                                                                            |                                                                                                                                                      |
| public container SysObsoleteAttribute()                                                                             |                                                                                                                                                      |
| public FormControl parentControl()                                                                                  | Retrieves the parent control for the control.                                                                                                        |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                            |                                                                                                                                                      |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                                  |                                                                                                                                                      |
| public int rightMarginValue(\[int value\])                                                                          |                                                                                                                                                      |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                           | Sets or returns the ID of the security key for the control.                                                                                          |
| public int showContextMenu(int menuHandle)                                                                          | Shows the shortcut menu for the control.                                                                                                             |
| public boolean skip(\[boolean value\])                                                                              | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                      |
| public int sort(\[SortOrder sortDirection\])                                                                        |                                                                                                                                                      |
| public str toolTip()                                                                                                | Retrieves the tooltip text for the control.                                                                                                          |
| public int top(int value, \[int mode\])                                                                             | Gets or sets the vertical position of the control in the form.                                                                                       |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                              |                                                                                                                                                      |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                                    |                                                                                                                                                      |
| public int topMarginValue(\[int value\])                                                                            |                                                                                                                                                      |
| public int topMode(\[int value\])                                                                                   | Sets the vertical arrange mode for the control in the form.                                                                                          |
| public int topValue(\[int value\])                                                                                  | Gets or sets the vertical position of the control in the form.                                                                                       |
| public int type(\[int value\])                                                                                      |                                                                                                                                                      |
| public boolean SysObsoleteAttribute(container data)                                                                 |                                                                                                                                                      |
| public int userData(\[int value\])                                                                                  | Gets or sets the user data for the control.                                                                                                          |
| public int userDataItem(\[int value\])                                                                              | Gets or sets the user data item for the control.                                                                                                     |
| public int userDataItems(\[int value\])                                                                             | Gets or sets the number of user data items for the control.                                                                                          |
| public int userDisable(\[int value\])                                                                               | Gets or sets the value that indicates whether the control is disabled for the user.                                                                  |
| public int userHeight(\[int value\])                                                                                | Gets or sets the custom user height for the control.                                                                                                 |
| public int userHide(\[int value\])                                                                                  | Gets or sets the value that indicates whether the control is hidden from the user.                                                                   |
| public int userOrgContainer(\[int value\])                                                                          | Gets or sets the organization container for the control.                                                                                             |
| public int userOrgSibling(\[int value\])                                                                            | Gets or sets the organization sibling for the control.                                                                                               |
| public str userPromptText(\[str value\])                                                                            | Gets or sets the user label text for the control.                                                                                                    |
| public int userSecurityLevel(\[int value\])                                                                         | Gets or sets the user security level for the control.                                                                                                |
| public int userSkip(\[int value\])                                                                                  | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form. |
| public int userWidth(\[int value\])                                                                                 | Sets or returns the width of the control in pixels.                                                                                                  |
| public boolean useUserLayout(\[boolean value\])                                                                     |                                                                                                                                                      |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                        | Gets or sets the vertical spacing of the control in the form.                                                                                        |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                              | Sets the vertical spacing mode for the control in the form.                                                                                          |
| public int verticalSpacingValue(\[int value\])                                                                      | Gets or sets the vertical spacing of the control in the form.                                                                                        |
| public boolean visible(\[boolean value\])                                                                           | Sets or returns a value that indicates whether the control is visible.                                                                               |
| public int width(int value, \[int mode\])                                                                           | Gets or sets the width of the control.                                                                                                               |
| public int widthMode(\[int value\])                                                                                 | Gets or sets the calculation mode of the width of the control.                                                                                       |
| public int widthValue(\[int value\])                                                                                | Gets or sets the width of the control.                                                                                                               |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                            |                                                                                                                                                      |
| public void setFocus()                                                                                              | Sets the focus on the control.                                                                                                                       |
| public void resetUserSetting()                                                                                      | Resets the user settings for the control.                                                                                                            |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                           | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                   |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                       | Is called when the user moves the mouse pointer into the control area.                                                                               |
| public void gotFocus()                                                                                              | Indicates that the control has received focus.                                                                                                       |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                          |                                                                                                                                                      |
| public void prefColumnSize(int width, int height)                                                                   | Specifies the preferred column width and height for the form control.                                                                                |
| public void endDrag()                                                                                               | Is called when the user has finished dragging a form control.                                                                                        |
| public void mouseLeave()                                                                                            | Indicates that the mouse pointer has left the control.                                                                                               |
| public void inputSearch(str searchStr)                                                                              | Performs data filtering for the control, based on the specified string.                                                                              |
| public void enter()                                                                                                 |                                                                                                                                                      |
| public void context()                                                                                               | Shows the shortcut menu for the control.                                                                                                             |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                               | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                 |
| public void jumpRef()                                                                                               |                                                                                                                                                      |
| private void OnSelectionChanged(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                      |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\])         |                                                                                                                                                      |
| public void cut()                                                                                                   | Cuts the contents of the control.                                                                                                                    |
| public void lostFocus()                                                                                             | Indicates that the control has lost focus.                                                                                                           |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                         |                                                                                                                                                      |
| public void copy()                                                                                                  | Copies the contents of the control to the clipboard.                                                                                                 |
| public void dragLeave()                                                                                             | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                     |
| public void selectionChanged()                                                                                      |                                                                                                                                                      |
| public void displayControl()                                                                                        | Displays the control.                                                                                                                                |
| public void paste()                                                                                                 | Pastes the contents of the clipboard into the control.                                                                                               |
| public void arrange()                                                                                               |                                                                                                                                                      |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                        |                                                                                                                                                      |
| public void filter(\[str filterStr\])                                                                               |                                                                                                                                                      |

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
The value to be assigned to the allowEdit property.

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

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

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
The property is set to this value, if supplied.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method beginDrag

Called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event will not be raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

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

Retrieves the size of the control.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

#### Return Value

The container that has the width and height.

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

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

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

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

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

Gets or sets the value that indicates whether the control is displayed in the client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer data type that indicates whether the drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the FormControl::dragLeave, FormControl::dragOver, and FormControl::dragOverEx methods to specify the behavior.

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
An Integer data type that indicates how the height is calculated; optional.

<!-- -->

mode  
An Integer data type that indicates how the height is calculated; optional.

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

The helpField method cannot be used to set the value of the Help text.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

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
The value to assign as the HierarchyParent value of the control.

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

### Method isSelected

    public boolean isSelected()

#### Return Value

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
| FormAllowUserSetup::No 0         | No changes can be made to the control. Using this value for the neededSetupRights parameter always returns true.                 |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

This method returns true only if the AllowUserSetup property for the design and all parent containers allows for the level of access that is specified by the neededSetupRights parameter.

### Method keyTip

    public str keyTip([str value])

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
A Boolean value that indicates whether the control should be marked as a user-added control.

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

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

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

Typically, when this method is overridden, the return value from a call to super is returned.

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

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method moveControl

    public int moveControl(int controlId, [int insertAfterId])

#### Parameters

controlId  

<!-- -->

insertAfterId  

#### Return Value

### Method name

Gets or sets the name used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name assigned to the control.

#### Return Value

The name used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, classes, and so on.

### Method neededPermission

    public int neededPermission([int value])

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

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. Right-clicking invokes a menu that enables the control to be hidden or displayed. This method lets you programmatically determine and set the value.

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

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to invoke the setup form in which the character specification is made.

### Method useUserLayout

    public boolean useUserLayout([boolean value])

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
An Integer data type that indicates how the width is calculated; optional.

<!-- -->

mode  
An Integer data type that indicates how the width is calculated; optional.

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
An Integer data type value that indicates how the control width is calculated; optional.

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

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

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

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

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

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method enter

    public void enter()

### Method context

Shows the shortcut menu for the control.

    public void context()

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

### Method jumpRef

    public void jumpRef()

### Method OnSelectionChanged

    private void OnSelectionChanged([FormControl sender], [FormControlEventArgs e])

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

### Method cut

Cuts the contents of the control.

    public void cut()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method selectionChanged

    public void selectionChanged()

### Method displayControl

Displays the control.

    public void displayControl()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method arrange

    public void arrange()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

## Class FormActiveXControl
    class FormActiveXControl extends FormControl

### Remarks

### Examples

### Methods

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
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the client, or in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both. |
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
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.              |
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
The value to be assigned to the allowEdit property.

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
The property is set to this value, if supplied.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer.

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

The container that has the width and height.

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
The ID of the configuration key that is being assigned to the control; optional.

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

Gets or sets the value that indicates whether the control is displayed in the client, or in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer data type that indicates whether the drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the FormControl::dragLeave, FormControl::dragOver, and FormControl::dragOverEx methods to specify the behavior.

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
An Integer data type value that indicates how the control height is calculated; optional.

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

The helpField method cannot be used to set the value of the Help text.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet.The help text must not exceed 250 characters.

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign as the HierarchyParent value of the control.

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
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control. For more information, see the “Remarks” section.

#### Return Value

true if the control, design, and parent container allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                 |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. Using this value for neededSetupRights always returns true.                              |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label and width properties of the control. The user can also move the control. |

This method returns true only if the AllowUserSetup property for the design and all parent containers is at least as high as the level that is specified by the neededSetupRights parameter.

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
A Boolean value that indicates whether the control should be marked as a user-added control.

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

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

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

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control; optional.

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

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. Right-clicking invokes a menu that enables the control to be hidden or displayed. This method lets you programmatically determine and set the value.

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

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls on the form.

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

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to invoke the setup form in which the character specification is made.

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

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

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

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method enter

    public void enter()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method displayControl

Displays the control.

    public void displayControl()

### Method updateSize

    public void updateSize()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method mouseLeave

Is called when the user moves the mouse pointer out of the control area.

    public void mouseLeave()

#### Examples

The following example writes to the information log when the mouse pointer leaves the control.

    public void mouseLeave() 
    { 
        info (strfmt("The mouse pointer has left the %1 control.", 
                     this.name()) ); 
        super(); 
    }

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

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method cut

Cuts the contents of the control.

    public void cut()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

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

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

## Class FormAnimateControl
    class FormAnimateControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                          |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                             |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                  |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                  |
| public str animateFile(\[str value\])                                                                       |                                                                                                                                                      |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                   |
| public boolean autoPlay(\[boolean value\])                                                                  |                                                                                                                                                      |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                               |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                             |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                   |
| public boolean center(\[boolean value\])                                                                    |                                                                                                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                  |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                     |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                       |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                        |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the client, or in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                    |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                       |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                     |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                               |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                  |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                             |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                              |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                              |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                       |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                              |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                             |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                             |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                      |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                        |
| public boolean isContainer()                                                                                |                                                                                                                                                      |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                   |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                  |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                  |
| public boolean leave()                                                                                      |                                                                                                                                                      |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                     |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                        |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                     |
| public int loops(\[int value\])                                                                             |                                                                                                                                                      |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                            |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                    |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                    |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                             |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.              |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                      |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                      |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                        |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                          |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                             |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                      |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                          |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                       |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                          |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                       |
| public boolean transparent(\[boolean value\])                                                               |                                                                                                                                                      |
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
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form. |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                  |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                        |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                          |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                        |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                               |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                               |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                       |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                               |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                      |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                              |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                 |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                           |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                       |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                               |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                               |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                   |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                      |
| public void enter()                                                                                         |                                                                                                                                                      |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                               |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                     |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                      |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                 |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                             |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                        |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                            |
| public void play(\[int firstFrame\], \[int lastFrame\], \[int loops\])                                      |                                                                                                                                                      |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                      |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                       |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                    |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                      |
| public void stop()                                                                                          |                                                                                                                                                      |

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
The value to be assigned to the allowEdit property.

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method animateFile

    public str animateFile([str value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
The property is set to this value, if supplied.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoPlay

    public boolean autoPlay([boolean value])

#### Parameters

value  

#### Return Value

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

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

The container that has the width and height.

### Method center

    public boolean center([boolean value])

#### Parameters

value  

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key that is being assigned to the control; optional.

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

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the client, or in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer data type that indicates whether the drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the FormControl::dragLeave, FormControl::dragOver, and FormControl::dragOverEx methods to specify the behavior.

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
An Integer data type value that indicates how the control height is calculated; optional.

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

The helpField method cannot be used to set the value of the Help text.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet.The help text must not exceed 250 characters.

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign as the HierarchyParent value of the control.

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

Returns a value that indicates whether the control allows for the specified level of customization.

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control. For more information, see “Remarks.”

#### Return Value

true if the control, design, and parent container allow for the level of customization that is specified by the neededSetupRights parameter; otherwise false.

#### Remarks

The following table describes the values for the neededSetupRights parameters.

|                                  |                                                                                                                                 |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. Using this value for neededSetupRights always returns true.                              |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label and width properties of the control. The user can also move the control. |

This method returns true only if the AllowUserSetup property for the design and all parent containers is at least as high as the level that is specified by the neededSetupRights parameter.

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

### Method loops

    public int loops([int value])

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

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

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

Typically, when this method is overridden, the return value from a call to super is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control; optional.

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

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

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
The value to assign to the skip property of the control; optional.

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

### Method transparent

    public boolean transparent([boolean value])

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

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. Right-clicking invokes a menu that enables the control to be hidden or displayed. This method lets you programmatically determine and set the value.

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

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to invoke the setup form in which the character specification is made.

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

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

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

### Method setFocus

Sets the focus on the control.

    public void setFocus()

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

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

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

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method enter

    public void enter()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method play

    public void play([int firstFrame], [int lastFrame], [int loops])

#### Parameters

firstFrame  

<!-- -->

lastFrame  

<!-- -->

loops  

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method displayControl

Displays the control.

    public void displayControl()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method stop

    public void stop()

## Class FormAutoLookupFactory
    class FormAutoLookupFactory extends FieldBinding

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                              | Description                                                    |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| ::public static xFormRun buildLookupFormByField(FormControl controlHostingLookup, FieldBinding fieldBinding)                                                                        |                                                                |
| ::public static xFormRun buildLookupFromCustomForm(FormControl controlHostingLookup, Form customLookupForm, FieldBinding fieldBinding, \[xArgs customArgs\], \[Query customQuery\]) |                                                                |
| ::public static xFormRun buildReferenceLookupFromCustomForm(FormReferenceControl referenceControlHostingLookup, Form customLookupForm, \[xArgs customArgs\], \[Query customQuery\]) |                                                                |
| ::public static void createLookupForClientsideControl(xFormRun parentForm, str targetId, str controlName, int tableId, int fieldId, str controlValue, boolean isInFilterMode)       |                                                                |
| ::public static void performFormLookup(xFormRun lookupForm, \[boolean blockUntilLookupClosed\], \[FormControl controlHostingLookup\])                                               |                                                                |
| private void new()                                                                                                                                                                  | Initializes a new instance of the FormAutoLookupFactory class. |

### Method buildLookupFormByField

    public static xFormRun buildLookupFormByField(FormControl controlHostingLookup, FieldBinding fieldBinding)

#### Parameters

controlHostingLookup  

<!-- -->

fieldBinding  

#### Return Value

### Method buildLookupFromCustomForm

    public static xFormRun buildLookupFromCustomForm(FormControl controlHostingLookup, Form customLookupForm, FieldBinding fieldBinding, [xArgs customArgs], [Query customQuery])

#### Parameters

controlHostingLookup  

<!-- -->

customLookupForm  

<!-- -->

fieldBinding  

<!-- -->

customArgs  

<!-- -->

customQuery  

#### Return Value

### Method buildReferenceLookupFromCustomForm

    public static xFormRun buildReferenceLookupFromCustomForm(FormReferenceControl referenceControlHostingLookup, Form customLookupForm, [xArgs customArgs], [Query customQuery])

#### Parameters

referenceControlHostingLookup  

<!-- -->

customLookupForm  

<!-- -->

customArgs  

<!-- -->

customQuery  

#### Return Value

### Method createLookupForClientsideControl

    public static void createLookupForClientsideControl(xFormRun parentForm, str targetId, str controlName, int tableId, int fieldId, str controlValue, boolean isInFilterMode)

#### Parameters

parentForm  

<!-- -->

targetId  

<!-- -->

controlName  

<!-- -->

tableId  

<!-- -->

fieldId  

<!-- -->

controlValue  

<!-- -->

isInFilterMode  

### Method performFormLookup

    public static void performFormLookup(xFormRun lookupForm, [boolean blockUntilLookupClosed], [FormControl controlHostingLookup])

#### Parameters

lookupForm  

<!-- -->

blockUntilLookupClosed  

<!-- -->

controlHostingLookup  

### Method new

Initializes a new instance of the FormAutoLookupFactory class.

    private void new()

## Class FormBinding
    class FormBinding

### Remarks

### Examples

### Methods

| Method                       | Description |
|------------------------------|-------------|
| public Object targetObject() |             |
| public str targetProperty()  |             |

### Method targetObject

    public Object targetObject()

#### Return Value

### Method targetProperty

    public str targetProperty()

#### Return Value

## Class FormBuildActionPaneControl
    class FormBuildActionPaneControl extends FormBuildControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignChild(\[boolean value\])                                                                |                                                                                                                                               |
| public boolean alignChildren(\[boolean value\])                                                             |                                                                                                                                               |
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                      |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                           |
| public int allowUserSetup(\[int value\])                                                                    |                                                                                                                                               |
| public int arrangeGuide(\[int value\])                                                                      |                                                                                                                                               |
| public int arrangeMethod(\[int value\])                                                                     |                                                                                                                                               |
| public int arrangeWhen(\[int value\])                                                                       |                                                                                                                                               |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                            |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                   |                                                                                                                                               |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                         |                                                                                                                                               |
| public int bottomMarginValue(\[int value\])                                                                 |                                                                                                                                               |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                       |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                     |                                                                                                                                               |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                        |                                                                                                                                               |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                               |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                          |                                                                                                                                               |
| public int columnspaceValue(\[int value\])                                                                  |                                                                                                                                               |
| public int columnsValue(\[int value\])                                                                      |                                                                                                                                               |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                     |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                               |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                      |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                               |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                             |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                           |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                       |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                       |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public boolean hideIfEmpty(\[boolean value\])                                                               |                                                                                                                                               |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                               |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                              |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                                  |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                               |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                     |                                                                                                                                               |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                           |                                                                                                                                               |
| public int leftMarginValue(\[int value\])                                                                   |                                                                                                                                               |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                               |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                               |
| public int moveControl(int controlId, \[int insertAfterControlId\])                                         | Moves a control that is specified by ID to the control.                                                                                       |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                               |
| public int position(\[int value\])                                                                          |                                                                                                                                               |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                               |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                          |                                                                                                                                               |
| public int rightMarginValue(\[int value\])                                                                  |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                               |
| public boolean skip(\[boolean value\])                                                                      |                                                                                                                                               |
| public int style(\[int value\])                                                                             |                                                                                                                                               |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                               |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                               |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                            |                                                                                                                                               |
| public int topMarginValue(\[int value\])                                                                    |                                                                                                                                               |
| public int topMode(\[int value\])                                                                           |                                                                                                                                               |
| public int topValue(\[int value\])                                                                          |                                                                                                                                               |
| public int type(\[int value\])                                                                              |                                                                                                                                               |
| public int userData(\[int value\])                                                                          |                                                                                                                                               |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                               |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                               |
| public boolean useUserLayout(\[boolean value\])                                                             |                                                                                                                                               |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                               |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                               |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                               |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                               |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                        |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                        |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                               |

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

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

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

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

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

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

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

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box.The help text must not exceed 250 characters.

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

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

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

### Method moveControl

Moves a control that is specified by ID to the control.

    public int moveControl(int controlId, [int insertAfterControlId])

#### Parameters

controlId  

<!-- -->

insertAfterControlId  

#### Return Value

1 if the control was moved successfully; otherwise, 0.

#### Remarks

In general, if the specified control can be contained in the control and can be moved from the container that it is currently in, this method should succeed. However, in some cases, such as for the reference group control instance, controls cannot be moved.

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

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

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

#### Return Value

### Method style

    public int style([int value])

#### Parameters

value  

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

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildActionPaneTabControl
    class FormBuildActionPaneTabControl extends FormBuildControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignChild(\[boolean value\])                                                                |                                                                                                                                               |
| public boolean alignChildren(\[boolean value\])                                                             |                                                                                                                                               |
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                      |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                           |
| public int allowUserSetup(\[int value\])                                                                    |                                                                                                                                               |
| public int arrangeGuide(\[int value\])                                                                      |                                                                                                                                               |
| public int arrangeMethod(\[int value\])                                                                     |                                                                                                                                               |
| public int arrangeWhen(\[int value\])                                                                       |                                                                                                                                               |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                            |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                   |                                                                                                                                               |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                         |                                                                                                                                               |
| public int bottomMarginValue(\[int value\])                                                                 |                                                                                                                                               |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                       |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                     |                                                                                                                                               |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                        |                                                                                                                                               |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                               |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                          |                                                                                                                                               |
| public int columnspaceValue(\[int value\])                                                                  |                                                                                                                                               |
| public int columnsValue(\[int value\])                                                                      |                                                                                                                                               |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                                     |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                               |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                               |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                               |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                      |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                               |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                             |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                           |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                       |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                       |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public boolean hideIfEmpty(\[boolean value\])                                                               |                                                                                                                                               |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                               |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                              |
| public int imageLocation(\[int value\])                                                                     |                                                                                                                                               |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                                  |
| public str keyTip(\[str value\])                                                                            |                                                                                                                                               |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                               |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                     |                                                                                                                                               |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                           |                                                                                                                                               |
| public int leftMarginValue(\[int value\])                                                                   |                                                                                                                                               |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                               |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                               |
| public int moveControl(int controlId, \[int insertAfterControlId\])                                         | Moves a control that is specified by ID to the control.                                                                                       |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                               |
| public str normalImage(\[str value\])                                                                       |                                                                                                                                               |
| public int normalResource(\[int value\])                                                                    |                                                                                                                                               |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                               |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                          |                                                                                                                                               |
| public int rightMarginValue(\[int value\])                                                                  |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                               |
| public boolean skip(\[boolean value\])                                                                      |                                                                                                                                               |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                               |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                               |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                            |                                                                                                                                               |
| public int topMarginValue(\[int value\])                                                                    |                                                                                                                                               |
| public int topMode(\[int value\])                                                                           |                                                                                                                                               |
| public int topValue(\[int value\])                                                                          |                                                                                                                                               |
| public int type(\[int value\])                                                                              |                                                                                                                                               |
| public int userData(\[int value\])                                                                          |                                                                                                                                               |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                               |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                               |
| public boolean useUserLayout(\[boolean value\])                                                             |                                                                                                                                               |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                               |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                               |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                               |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                               |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                        |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                        |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                               |

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

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

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

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

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

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

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

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

    public str dataRelationPath([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method displayTarget

    public int displayTarget([int value])

#### Parameters

value  

#### Return Value

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box. The help text must not exceed 250 characters.

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

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method keyTip

    public str keyTip([str value])

#### Parameters

value  

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

### Method moveControl

Moves a control that is specified by ID to the control.

    public int moveControl(int controlId, [int insertAfterControlId])

#### Parameters

controlId  

<!-- -->

insertAfterControlId  

#### Return Value

1 if the control was moved successfully; otherwise, 0.

#### Remarks

In general, if the specified control can be contained in the control and can be moved from the container that it is currently in, this method should succeed. However, in some cases, such as for the reference group control instance, controls cannot be moved.

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method neededPermission

    public int neededPermission([int value])

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

### Method skip

    public boolean skip([boolean value])

#### Parameters

value  

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

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildActiveXControl
    class FormBuildActiveXControl extends FormBuildControl

The FormBuildActiveXControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                      |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                 |
| public str className(\[str value\])                                                                         |                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                               |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                         |
| public str custom(\[str value\])                                                                            |                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                         |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                       |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                     |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                 |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                         |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                        |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                            |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                         |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                         |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                         |
| public boolean rTLCapable(\[boolean value\])                                                                |                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.         |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                         |
| public int topMode(\[int value\])                                                                           |                                                                                                                                         |
| public int topValue(\[int value\])                                                                          |                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                         |
| public int userData(\[int value\])                                                                          |                                                                                                                                         |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                         |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                         |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                         |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                         |

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

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

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

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method custom

    public str custom([str value])

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

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

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

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

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

### Method rTLCapable

    public boolean rTLCapable([boolean value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

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

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormBuildAnimateControl
    class FormBuildAnimateControl extends FormBuildControl

The FormBuildAnimateControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                     |
| public str animateFile(\[str value\])                                                                       |                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                      |
| public boolean autoPlay(\[boolean value\])                                                                  |                                                                                                                                         |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                |
| public boolean center(\[boolean value\])                                                                    |                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public int containerId()                                                                                    | Retrieves the ID of the parent container for the control.                                                                               |
| public str countryRegionCodes(\[str value\])                                                                |                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  |                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     |                                                                                                                                         |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                       |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                     |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                 |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                |
| public str hierarchyParent(\[str value\])                                                                   |                                                                                                                                         |
| public int id()                                                                                             | Retrieves the ID of the control.                                                                                                        |
| public boolean isContainer()                                                                                | Retrieves a value that indicates whether the control is a container control.                                                            |
| public int left(int value, \[int mode\])                                                                    |                                                                                                                                         |
| public int leftMode(\[int value\])                                                                          |                                                                                                                                         |
| public int leftValue(\[int value\])                                                                         |                                                                                                                                         |
| public int loops(\[int value\])                                                                             |                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object. |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.         |
| public int top(int value, \[int mode\])                                                                     |                                                                                                                                         |
| public int topMode(\[int value\])                                                                           |                                                                                                                                         |
| public int topValue(\[int value\])                                                                          |                                                                                                                                         |
| public boolean transparent(\[boolean value\])                                                               |                                                                                                                                         |
| public int type(\[int value\])                                                                              |                                                                                                                                         |
| public int userData(\[int value\])                                                                          |                                                                                                                                         |
| public int userDataItem(\[int value\])                                                                      |                                                                                                                                         |
| public int userDataItems(\[int value\])                                                                     |                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |                                                                                                                                         |
| public int verticalSpacingValue(\[int value\])                                                              |                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   |                                                                                                                                         |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                         |

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

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method animateFile

    public str animateFile([str value])

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

### Method autoPlay

    public boolean autoPlay([boolean value])

#### Parameters

value  

#### Return Value

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

### Method center

    public boolean center([boolean value])

#### Parameters

value  

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method containerId

Retrieves the ID of the parent container for the control.

    public int containerId()

#### Return Value

The ID of the parent container.

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

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The help text must not exceed 250 characters.

### Method hierarchyParent

    public str hierarchyParent([str value])

#### Parameters

value  

#### Return Value

### Method id

Retrieves the ID of the control.

    public int id()

#### Return Value

The ID of the control.

### Method isContainer

Retrieves a value that indicates whether the control is a container control.

    public boolean isContainer()

#### Return Value

A Boolean value that indicates whether the control is a container control.

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

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

### Method loops

    public int loops([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

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

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

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

### Method transparent

    public boolean transparent([boolean value])

#### Parameters

value  

#### Return Value

### Method type

    public int type([int value])

#### Parameters

value  

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

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  




