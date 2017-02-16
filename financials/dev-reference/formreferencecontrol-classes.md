---
# required metadata

title: F Classes - FormReferenceControl to FormStringControl
description: API reference for classes from FormReferenceControl to FormStringControl.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-08 23 - 43 - 07
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
ms.custom: 63733
ms.assetid: e26aa57e-42d8-43a8-9b44-340612ae4193
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# F Classes - FormReferenceControl to FormStringControl

API reference for classes from FormReferenceControl to FormStringControl.

Class FormReferenceControl
--------------------------

    class FormReferenceControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                           | Description                                                                                                                                                             |
|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                   | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                      | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])         | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public str countryRegionCodes(\[str value\])                                     | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                      |                                                                                                                                                                         |
| public int dataField()                                                           |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                       | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                         | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int displayTarget(\[int value\])                                          | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                               | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public boolean enabled(\[boolean value\])                                        | Determines whether to enable or disable the object.                                                                                                                     |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                 |                                                                                                                                                                         |
| public FilterValue filterValue(FieldBinding fieldBinding)                        |                                                                                                                                                                         |
| public int height(int value, \[int mode\])                                       | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                             | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                            | Gets or sets the height of the control.                                                                                                                                 |
| public str helpText(\[str value\])                                               | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                        | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public boolean isResolvingReference()                                            |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                               | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                              | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public Common lookupReference()                                                  |                                                                                                                                                                         |
| public boolean mandatory(\[boolean value\])                                      |                                                                                                                                                                         |
| public str name(\[str value\])                                                   | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                       |                                                                                                                                                                         |
| public FormObjectSet referenceDataSource()                                       |                                                                                                                                                                         |
| public FieldId referenceField(\[FieldId value\])                                 |                                                                                                                                                                         |
| public str replacementFieldGroup(\[str value\])                                  |                                                                                                                                                                         |
| public Common resolveReference()                                                 |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                        | Sets or returns the ID of the security key for the control.                                                                                                             |
| public boolean skip(\[boolean value\])                                           | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int top(int value, \[int mode\])                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                               | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                   |                                                                                                                                                                         |
| public int userData(\[int value\])                                               | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                           | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                          | Gets or sets the number of user data items for the control.                                                                                                             |
| public Int64 value(\[Int64 value\])                                              |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                     | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                           | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                   | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                        | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                        | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                              | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                             | Gets or sets the width of the control.                                                                                                                                  |
| ::public static boolean CanUserAdd(FormDataSource formDataSource, str fieldName) |                                                                                                                                                                         |
| public void resolveChanges()                                                     |                                                                                                                                                                         |
| public void performFormLookup(xFormRun form)                                     |                                                                                                                                                                         |

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

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

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

    public int dataField()

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

### Method filterValue

    public FilterValue filterValue(FieldBinding fieldBinding)

#### Parameters

fieldBinding  

#### Return Value

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

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

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

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table.

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

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

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

### Method isResolvingReference

    public boolean isResolvingReference()

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

### Method lookupReference

    public Common lookupReference()

#### Return Value

### Method mandatory

    public boolean mandatory([boolean value])

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

### Method referenceDataSource

    public FormObjectSet referenceDataSource()

#### Return Value

### Method referenceField

    public FieldId referenceField([FieldId value])

#### Parameters

value  

#### Return Value

### Method replacementFieldGroup

    public str replacementFieldGroup([str value])

#### Parameters

value  

#### Return Value

### Method resolveReference

    public Common resolveReference()

#### Return Value

### Method securityKey

Sets or returns the ID of the security key for the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The ID of the security key to assign to the control; optional.

#### Return Value

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

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

### Method value

    public Int64 value([Int64 value])

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

<!-- -->

mode  

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

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table.

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

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method CanUserAdd

    public static boolean CanUserAdd(FormDataSource formDataSource, str fieldName)

#### Parameters

formDataSource  

<!-- -->

fieldName  

#### Return Value

### Method resolveChanges

    public void resolveChanges()

### Method performFormLookup

    public void performFormLookup(xFormRun form)

#### Parameters

form  

## Class FormReferenceGroupControl
    class FormReferenceGroupControl extends FormReferenceControl

### Remarks

### Examples

### Methods

| Method                                                                                                              | Description                                                                                                                                                             |
|---------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            |                                                                                                                                                                         |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |                                                                                                                                                                         |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) |                                                                                                                                                                         |
| public boolean alignControl(\[boolean value\])                                                                      | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                         | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                                      | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                                   | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                           | Gets or sets the background color of the control.                                                                                                                       |
| public Image backgroundImage(\[Image image\], \[int drawMode\])                                                     |                                                                                                                                                                         |
| public int backStyle(\[int value\])                                                                                 | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                                  | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                                      | Gets or sets the weight of font used to output text in the control.                                                                                                     |
| public int border(\[int value\])                                                                                    | Gets or sets the style of the borderline of the control.                                                                                                                |
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
| public FieldId countryRegionContextField(\[FieldId value\])                                                         |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                          | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                            | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int displayTarget(\[int value\])                                                                             | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                                  | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                               | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enableChilds(\[boolean enable\])                                                                     |                                                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                                                           | Determines whether to enable or disable the object.                                                                                                                     |
| public boolean expand(\[boolean expand\])                                                                           |                                                                                                                                                                         |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                                    |                                                                                                                                                                         |
| public str font(\[str value\])                                                                                      | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                                  | Gets or sets the size of the font for the control to use.                                                                                                               |
| public int foregroundColor(\[int value\])                                                                           | Gets or sets the text color for the control to use.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                          | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                                     | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                          | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                                | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                               | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                              | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                                  | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public boolean hideIfEmpty(\[boolean value\])                                                                       |                                                                                                                                                                         |
| public str hierarchyParent(\[str value\])                                                                           | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                                   | Retrieves the Windows handle for the control.                                                                                                                           |
| public boolean isContainer()                                                                                        |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                        | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                                       | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean isValid()                                                                                            |                                                                                                                                                                         |
| public boolean italic(\[boolean value\])                                                                            |                                                                                                                                                                         |
| public str label(\[str value\])                                                                                     | Gets or sets the label for a control.                                                                                                                                   |
| public int labelAlignment(\[int value\])                                                                            |                                                                                                                                                                         |
| public int labelBold(\[int value\])                                                                                 |                                                                                                                                                                         |
| public int labelCharacterSet(\[int value\])                                                                         |                                                                                                                                                                         |
| public str labelFont(\[str value\])                                                                                 |                                                                                                                                                                         |
| public int labelFontSize(\[int value\])                                                                             |                                                                                                                                                                         |
| public int labelForegroundColor(\[int value\])                                                                      |                                                                                                                                                                         |
| public int labelGuide(\[int value\])                                                                                |                                                                                                                                                                         |
| public int labelHeight(int value, \[int mode\])                                                                     |                                                                                                                                                                         |
| public int labelHeightMode(\[int value\])                                                                           |                                                                                                                                                                         |
| public int labelHeightValue(\[int value\])                                                                          |                                                                                                                                                                         |
| public boolean labelItalic(\[boolean value\])                                                                       |                                                                                                                                                                         |
| public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                |                                                                                                                                                                         |
| public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                    |                                                                                                                                                                         |
| public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                      |                                                                                                                                                                         |
| public int labelPosition(\[int value\])                                                                             |                                                                                                                                                                         |
| public boolean labelUnderline(\[boolean value\])                                                                    |                                                                                                                                                                         |
| public int labelWidth(int value, \[int mode\])                                                                      |                                                                                                                                                                         |
| public int labelWidthMode(\[int value\])                                                                            |                                                                                                                                                                         |
| public int labelWidthValue(\[int value\])                                                                           |                                                                                                                                                                         |
| public boolean leave()                                                                                              |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                            | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                                  | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                                 | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean mandatory(\[boolean value\])                                                                         |                                                                                                                                                                         |
| public boolean markAsUserAdd(\[boolean value\])                                                                     | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public boolean modified()                                                                                           |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                     | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                           | Is called when the user releases the mouse button over the control area.                                                                                                |
| public int moveControl(int controlId, \[int insertAfterId\])                                                        |                                                                                                                                                                         |
| public str name(\[str value\])                                                                                      | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                          |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                             |                                                                                                                                                                         |
| public FormControl parentControl()                                                                                  | Retrieves the parent control for the control.                                                                                                                           |
| public str previewPartRef(\[str value\])                                                                            |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                                |                                                                                                                                                                         |
| public FieldId referenceField(\[FieldId value\])                                                                    |                                                                                                                                                                         |
| public str replacementFieldGroup(\[str value\])                                                                     |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                           | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                          | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                         |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                              | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                        |                                                                                                                                                                         |
| public int style(\[int value\])                                                                                     |                                                                                                                                                                         |
| public str toolTip()                                                                                                | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                             | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                                   | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                                  | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                                      |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                         |                                                                                                                                                                         |
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
| public boolean validate()                                                                                           |                                                                                                                                                                         |
| public Int64 value(\[Int64 value\])                                                                                 |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                        | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                              | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                                      | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                           | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                           | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                                 | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                                | Gets or sets the width of the control.                                                                                                                                  |
| public void lostFocus()                                                                                             | Indicates that the control has lost focus.                                                                                                                              |
| public void displayControl()                                                                                        | Displays the control.                                                                                                                                                   |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                         |                                                                                                                                                                         |
| public void jumpRef()                                                                                               |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\])         |                                                                                                                                                                         |
| public void cut()                                                                                                   | Cuts the contents of the control.                                                                                                                                       |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                       | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                            |                                                                                                                                                                         |
| public void dragLeave()                                                                                             | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void filter(\[str filterStr\])                                                                               |                                                                                                                                                                         |
| public void arrange()                                                                                               |                                                                                                                                                                         |
| public void enter()                                                                                                 |                                                                                                                                                                         |
| public void paste()                                                                                                 | Pastes the contents of the clipboard into the control.                                                                                                                  |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                                       |                                                                                                                                                                         |
| public void setFocus()                                                                                              | Sets the focus on the control.                                                                                                                                          |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                         |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                          |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                              | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                           | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void mouseLeave()                                                                                            | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void prefColumnSize(int width, int height)                                                                   | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void undo()                                                                                                  |                                                                                                                                                                         |
| public void gotFocus()                                                                                              | Indicates that the control has received focus.                                                                                                                          |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                        |                                                                                                                                                                         |
| public void lookup()                                                                                                |                                                                                                                                                                         |
| public void resetUserSetting()                                                                                      | Resets the user settings for the control.                                                                                                                               |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                           |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                        |                                                                                                                                                                         |
| public void copy()                                                                                                  | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                               | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void context()                                                                                               | Shows the shortcut menu for the control.                                                                                                                                |
| public void endDrag()                                                                                               | Is called when the user has finished dragging a form control.                                                                                                           |

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

### Method backgroundImage

    public Image backgroundImage([Image image], [int drawMode])

#### Parameters

image  

<!-- -->

drawMode  

#### Return Value

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

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

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

The color scheme is defined according to the following table.

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

### Method enableChilds

    public boolean enableChilds([boolean enable])

#### Parameters

enable  

#### Return Value

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

### Method expand

    public boolean expand([boolean expand])

#### Parameters

expand  

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

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

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

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

Calculate the height according to the following table.

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

### Method moveControl

    public int moveControl(int controlId, [int insertAfterId])

#### Parameters

controlId  

<!-- -->

insertAfterId  

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

### Method referenceField

    public FieldId referenceField([FieldId value])

#### Parameters

value  

#### Return Value

### Method replacementFieldGroup

    public str replacementFieldGroup([str value])

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

### Method underline

    public boolean underline([boolean value])

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

### Method useUserLayout

    public boolean useUserLayout([boolean value])

#### Parameters

value  

#### Return Value

### Method validate

    public boolean validate()

#### Return Value

### Method value

    public Int64 value([Int64 value])

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

Calculate the width according to the following table.

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

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method displayControl

Displays the control.

    public void displayControl()

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method arrange

    public void arrange()

### Method enter

    public void enter()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method undo

    public void undo()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lookup

    public void lookup()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

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

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

## Class FormReferenceObject
    class FormReferenceObject extends FormDataObject

### Remarks

### Examples

### Methods

| Method                                                                    | Description                                                                                                                                                             |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int allowAdd(\[int value\])                                        | Sets or returns the value of the allowAdd property for the form data object.                                                                                            |
| public boolean allowEdit(\[boolean value\])                               | Indicates whether the user can change the contents of the control.                                                                                                      |
| public FieldId dataField(\[FieldId value\])                               |                                                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                 | Indicates whether to enable or disable the object.                                                                                                                      |
| public Common lookupReference(FormReferenceControl formReferenceControl)  |                                                                                                                                                                         |
| public boolean mandatory(\[boolean value\])                               | Sets or returns a value that indicates whether the data field is mandatory.                                                                                             |
| public Common resolveReference(FormReferenceControl formReferenceControl) |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                    | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control that is associated with the data source. |
| public boolean visible(\[boolean value\])                                 | Sets or returns a value that indicates whether the control is visible.                                                                                                  |

### Method allowAdd

Sets or returns the value of the allowAdd property for the form data object.

    public int allowAdd([int value])

#### Parameters

value  
The value that is assigned to the allowEdit property.

#### Return Value

A FormAllowAdd enumeration value that indicates whether the allowAdd property is set to No, Restricted, or Yes.

### Method allowEdit

Indicates whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method enabled

Indicates whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method lookupReference

    public Common lookupReference(FormReferenceControl formReferenceControl)

#### Parameters

formReferenceControl  

#### Return Value

### Method mandatory

Sets or returns a value that indicates whether the data field is mandatory.

    public boolean mandatory([boolean value])

#### Parameters

value  
The value that is assigned to the mandatory property of the field.

#### Return Value

true if the field is mandatory; otherwise, false.

### Method resolveReference

    public Common resolveReference(FormReferenceControl formReferenceControl)

#### Parameters

formReferenceControl  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control that is associated with the data source.

    public boolean skip([boolean value])

#### Parameters

value  
The value that is assigned to the skip property of the data source that is associated with the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control associated with the data source; otherwise, false.

#### Remarks

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control. Controls are skipped if the skip value of either the control or the data source is true.

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value that is assigned to the visibility setting for the control.

#### Return Value

true if the control is visible; otherwise, false. The default is true.

#### Remarks

Controls that refer to a data source field are visible only when the visible property is set to true on both the control and the underlying data source field. By setting the property on the data source field instead of the control, you make sure that the field is handled consistently throughout the form. This makes upgrades easier.

## Class FormRichTextControl
    class FormRichTextControl extends FormControl

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
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                                                         |
| public int find(\[str findStr\], \[int start\], \[int end\], \[int flags\])                                 |                                                                                                                                                                         |
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
| public boolean multiLine(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public container posFromChar(int charIndex)                                                                 |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean replaceOnLookup(\[boolean value\])                                                           |                                                                                                                                                                         |
| public int replaceText(\[str findStr\], \[str replaceStr\], \[int start\], \[int end\], \[int flags\])      |                                                                                                                                                                         |
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
| public void lookup()                                                                                        |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void performFormLookup(xFormRun form)                                                                |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void scrollCursor()                                                                                  |                                                                                                                                                                         |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void setSelection(int charIndexFrom, int charIndexTo)                                                |                                                                                                                                                                         |
| public void pasteText(str pasteStr, \[boolean InsertSel\])                                                  |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void performTypeLookup(\[int userType\], \[int arrayIndex\], \[SelectableDataArea company\])         |                                                                                                                                                                         |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void setCursorPos(int x, int y)                                                                      |                                                                                                                                                                         |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void lineScroll(int dx, int dy)                                                                      |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void performDBLookup(\[FieldId fieldId\], \[TableId tableId\], \[SelectableDataArea company\])       |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void textChange()                                                                                    |                                                                                                                                                                         |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |

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

The integer that is returned contains the style of the borderline of the control as follows.

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

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

The color scheme is defined according to the following table.

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

### Method find

    public int find([str findStr], [int start], [int end], [int flags])

#### Parameters

findStr  

<!-- -->

start  

<!-- -->

end  

<!-- -->

flags  

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

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

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

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.         | Height calculation                                                                        |
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

### Method multiLine

    public boolean multiLine([boolean value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

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

### Method replaceText

    public int replaceText([str findStr], [str replaceStr], [int start], [int end], [int flags])

#### Parameters

findStr  

<!-- -->

replaceStr  

<!-- -->

start  

<!-- -->

end  

<!-- -->

flags  

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

    public boolean underline([boolean value])

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

Sets or returns the width of the control in pixels, as specified by the user.

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

<!-- -->

mode  

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

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table.

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

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method lookup

    public void lookup()

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

### Method performFormLookup

    public void performFormLookup(xFormRun form)

#### Parameters

form  

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

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method scrollCursor

    public void scrollCursor()

### Method undo

    public void undo()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

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

### Method setSelection

    public void setSelection(int charIndexFrom, int charIndexTo)

#### Parameters

charIndexFrom  

<!-- -->

charIndexTo  

### Method pasteText

    public void pasteText(str pasteStr, [boolean InsertSel])

#### Parameters

pasteStr  

<!-- -->

InsertSel  

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

### Method enter

    public void enter()

### Method displayControl

Displays the control.

    public void displayControl()

### Method performTypeLookup

    public void performTypeLookup([int userType], [int arrayIndex], [SelectableDataArea company])

#### Parameters

userType  

<!-- -->

arrayIndex  

<!-- -->

company  

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setCursorPos

    public void setCursorPos(int x, int y)

#### Parameters

x  

<!-- -->

y  

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method lineScroll

    public void lineScroll(int dx, int dy)

#### Parameters

dx  

<!-- -->

dy  

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method performDBLookup

    public void performDBLookup([FieldId fieldId], [TableId tableId], [SelectableDataArea company])

#### Parameters

fieldId  

<!-- -->

tableId  

<!-- -->

company  

### Method cut

Cuts the contents of the control.

    public void cut()

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

### Method textChange

    public void textChange()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

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

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method jumpRef

    public void jumpRef()

## Class FormRowDisplayOption
    class FormRowDisplayOption extends Object

### Remarks

### Examples

### Methods

| Method                                                            | Description |
|-------------------------------------------------------------------|-------------|
| public int backColor(\[int color\])                               |             |
| public boolean fontBold(\[boolean bold\])                         |             |
| public boolean fontItalic(\[boolean italic\])                     |             |
| public boolean fontStrikethrough(\[boolean strikethrough\])       |             |
| public boolean fontUnderline(\[boolean underline\])               |             |
| public int textColor(\[int color\])                               |             |
| public void clear()                                               |             |
| public void clearTextColor()                                      |             |
| public void affectedElementsByField(\[FieldId fieldId\], VarArg ) |             |
| public void affectedElementsByControl(\[int controlId\], VarArg ) |             |
| public void clearBackColor()                                      |             |

### Method backColor

    public int backColor([int color])

#### Parameters

color  

#### Return Value

### Method fontBold

    public boolean fontBold([boolean bold])

#### Parameters

bold  

#### Return Value

### Method fontItalic

    public boolean fontItalic([boolean italic])

#### Parameters

italic  

#### Return Value

### Method fontStrikethrough

    public boolean fontStrikethrough([boolean strikethrough])

#### Parameters

strikethrough  

#### Return Value

### Method fontUnderline

    public boolean fontUnderline([boolean underline])

#### Parameters

underline  

#### Return Value

### Method textColor

    public int textColor([int color])

#### Parameters

color  

#### Return Value

### Method clear

    public void clear()

### Method clearTextColor

    public void clearTextColor()

### Method affectedElementsByField

    public void affectedElementsByField([FieldId fieldId], VarArg )

#### Parameters

fieldId  

<!-- -->

  

### Method affectedElementsByControl

    public void affectedElementsByControl([int controlId], VarArg )

#### Parameters

controlId  

<!-- -->

  

### Method clearBackColor

    public void clearBackColor()

## Class FormSegment
    class FormSegment extends Object

The FormSegment class is used to represent a segment in the SegmentedEntry control.

### Remarks

### Examples

### Methods

| Method                                                          | Description                            |
|-----------------------------------------------------------------|----------------------------------------|
| public str text()                                               | Gets the current text of the segment.  |
| public boolean allowEdit(\[boolean value\])                     |                                        |
| public str description(\[str description\])                     |                                        |
| public boolean enabled(\[boolean value\])                       |                                        |
| public int getIndex()                                           |                                        |
| public str name()                                               |                                        |
| public SegmentedEntryState state(\[SegmentedEntryState state\]) |                                        |
| public str value(\[str value\])                                 | Gets the current value of the segment. |

### Method text

Gets the current text of the segment.

    public str text()

#### Return Value

The current text of the segment.

#### Remarks

This method always returns the current text of the segment, even while it is being modified. To retrieve the last value that was persisted for the segment, use the value method.

### Method allowEdit

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

### Method description

    public str description([str description])

#### Parameters

description  

#### Return Value

### Method enabled

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

### Method getIndex

    public int getIndex()

#### Return Value

### Method name

    public str name()

#### Return Value

### Method state

    public SegmentedEntryState state([SegmentedEntryState state])

#### Parameters

state  

#### Return Value

### Method value

Gets the current value of the segment.

    public str value([str value])

#### Parameters

value  

#### Return Value

The current value of the segment.

#### Remarks

This method always returns the current persisted value of the segment, even while it is being modified. To retrieve the current text of the control while it is being modified, use the text method.

## Class FormSegmentedEntryControl
    class FormSegmentedEntryControl extends FormReferenceControl

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
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                                                |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                                                |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                   |
| public boolean isValid()                                                                                    |                                                                                                                                                                         |
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
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                                                         |
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
| public FieldId referenceField(\[FieldId value\])                                                            |                                                                                                                                                                         |
| public str replacementFieldGroup(\[str value\])                                                             |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
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
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public Int64 value(\[Int64 value\])                                                                         |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |

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

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows.

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

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

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table.

| Value | Style                        |
|-------|------------------------------|
| 0     | Default                      |
| 1     | The MicrosoftWindows palette |
| 2     | The true-color scheme        |

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

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to use.

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
An integer that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the dragLeave Method, the dragOver Method, and the dragOverEx Method to specify the behavior.

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

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

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
An integer value that indicates how the height is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the valueparameter is omitted. Calculate the height according to the following table.

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

Calculate the height according to the following table.

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

This handle can be used with the Windows API.

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

### Method isValid

    public boolean isValid()

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

### Method referenceField

    public FieldId referenceField([FieldId value])

#### Parameters

value  

#### Return Value

### Method replacementFieldGroup

    public str replacementFieldGroup([str value])

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

Sets or returns the width of the control in pixels, as specified by the user.

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

    public Int64 value([Int64 value])

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
An integer value that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer value that indicates how the width is calculated; optional.

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

Calculate the width according to the following table.

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
An integer that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

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

### Method undo

    public void undo()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method jumpRef

    public void jumpRef()

### Method enter

    public void enter()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

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

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method lookup

    public void lookup()

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

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

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

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

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

## Class FormsPreloadingManager
    class FormsPreloadingManager extends Object

The FormsPreloadingManager class manages the preloading of forms, including workspace association and resource pressure management.

### Remarks

### Examples

### Methods

| Method                                              | Description                                                                                  |
|-----------------------------------------------------|----------------------------------------------------------------------------------------------|
| ::private static FormsPreloadingManager construct() |                                                                                              |
| public void workspaceActivated()                    | Sets the preloading workspace affinity to the last activated workspace.                      |
| private void new()                                  | Initializes a new instance of the FormsPreloadingManager class.                              |
| public void updateState()                           | Queues forms for loading, handles high resource pressure, and updates other internal states. |

### Method construct

    private static FormsPreloadingManager construct()

#### Return Value

### Method workspaceActivated

Sets the preloading workspace affinity to the last activated workspace.

    public void workspaceActivated()

#### Remarks

This method is typically called on a timer after a workspace has been activated. Call this method directly to force the workspace affinity to change immediately.

### Method new

Initializes a new instance of the FormsPreloadingManager class.

    private void new()

### Method updateState

Queues forms for loading, handles high resource pressure, and updates other internal states.

    public void updateState()

#### Remarks

This method is typically called on a timer during idle periods. Call this method directly to force a state update during non-idle periods, such as when long-running X++ code is running.

## Class FormStaticTextControl
    class FormStaticTextControl extends FormControl

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
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Indicates whether the control background can be transparent.                                                                                                            |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to output text in the control.                                                                                             |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source for use by the control or the form.                                                                                                          |
| public int displayHeight(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayHeightMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayHeightValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Indicates whether to enable or disable drag-and-drop operations for the control.                                                                                        |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                               |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                   |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                                                         |
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
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
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
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |

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

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

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

Indicates whether the control background can be transparent.

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

Gets or sets the weight of font that is used to output text in the control.

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

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table.

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

Gets or sets a data source for use by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to use.

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

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Indicates whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

true if drag-and-drop operations are enabled; otherwise, false.

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

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

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

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table.

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

Set the HelpText property for an object by using the property dialog box. The Help text must not exceed 250 characters.

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

### Method italic

    public boolean italic([boolean value])

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

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

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

    public boolean underline([boolean value])

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

<!-- -->

mode  

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

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table.

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

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

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

### Method jumpRef

    public void jumpRef()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

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

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

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

### Method displayControl

Displays the control.

    public void displayControl()

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

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

## Class FormStringControl
    class FormStringControl extends FormControl

### Remarks

### Examples

### Methods

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
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
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
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
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

### Method alignControl

Indicates whether to align the control.

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

Indicates whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

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

Indicates whether the system can declare a member variable that has the same name as the control.

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

Indicates whether the control background can be transparent.

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

Gets or sets the weight of font that is used to output text in the control.

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

The integer that is returned contains the style of the borderline of the control as follows.

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

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

### Method changeCase

    public int changeCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

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

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

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

The color scheme is defined according to the following table.

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

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

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

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Indicates whether to enable or disable drag-and-drop operations for the control.

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

Indicates whether to enable or disable the object.

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

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

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

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table.

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

Set the HelpText property for an object by using the property dialog box. The Help text must not exceed 250 characters.

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

### Method lookupOnly

    public boolean lookupOnly([boolean value])

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

### Method multiLine

    public boolean multiLine([boolean value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

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

### Method passwordStyle

    public boolean passwordStyle([boolean value])

#### Parameters

value  

#### Return Value

### Method posFromChar

    public container posFromChar(int charIndex)

#### Parameters

charIndex  

#### Return Value

### Method presenceDataField

    public FieldId presenceDataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method presenceDataSource

    public int presenceDataSource([AnyType value])

#### Parameters

value  

#### Return Value

### Method presenceIndicatorAllowed

    public int presenceIndicatorAllowed([int value])

#### Parameters

value  

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

### Method resolveAmbiguousReference

    public str resolveAmbiguousReference()

#### Return Value

### Method disambiguationLookupTarget

    public FieldBinding disambiguationLookupTarget()

#### Return Value

### Method lookupDisambiguateReference

    public str lookupDisambiguateReference(FieldBinding fieldBinding)

#### Parameters

fieldBinding  

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

    public boolean underline([boolean value])

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

Sets or returns the width of the control in pixels, as specified by the user.

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

<!-- -->

mode  

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

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table.

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

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method presenceRefresh

    public void presenceRefresh()

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method performTypeLookup

    public void performTypeLookup([int userType], [int arrayIndex], [SelectableDataArea company])

#### Parameters

userType  

<!-- -->

arrayIndex  

<!-- -->

company  

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method undo

    public void undo()

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

### Method scrollCursor

    public void scrollCursor()

### Method enter

    public void enter()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method performDBLookup

    public void performDBLookup([FieldId fieldId], [TableId tableId], [SelectableDataArea company])

#### Parameters

fieldId  

<!-- -->

tableId  

<!-- -->

company  

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

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

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method displayControl

Displays the control.

    public void displayControl()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setCursorPos

    public void setCursorPos(int x, int y)

#### Parameters

x  

<!-- -->

y  

### Method performFormLookup

    public void performFormLookup(xFormRun form)

#### Parameters

form  

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lineScroll

    public void lineScroll(int dx, int dy)

#### Parameters

dx  

<!-- -->

dy  

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

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

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method textChange

    public void textChange()

### Method jumpRef

    public void jumpRef()

### Method lookup

    public void lookup()

### Method pasteText

    public void pasteText(str pasteStr, [boolean InsertSel])

#### Parameters

pasteStr  

<!-- -->

InsertSel  

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

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

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

