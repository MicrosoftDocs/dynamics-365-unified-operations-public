---
title: xArgs class
description: This topic describes the xArgs class.
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

# Class xArgs

[!include [banner](../../includes/banner.md)]

```xpp
class xArgs extends Object
```

The xArgs class is used to pass arguments such as a name, a caller, and parameters between application objects.

## Remarks

Forms, reports and queries all use this class as their first argument in the constructor. The preferred way to use this class is to construct an xArgs object, supply a name-string, and then pass the xArgs object to the forms constructor or a ClassFactory method. If you want to refer to the xArgs object passed to one of these classes, it can be reached using args method of that class. There are four methods that can be used to pass extra information to the new class:

-   The parm - to pass strings
-   The parmEnum and parmEnumType methods - to pass enumeration values
-   The parmObject method - to pass an object of any type

The instance of the xArgs class that is sent from the caller can be created automatically by the kernel or explicitly by the caller. When the caller uses a menu item to call an object, an instance of the xArgs class is created by the kernel code. The menu item name will be set to the name of the menu item used. If the menu item has values for the Parameters, EnumParameter, or EnumTypeParameter properties set, the kernel will set the values of the corresponding Parm, ParmEnum, or ParmEnumType properties for this instance of the xArgs class.

## Examples

## Methods

| Method                                                                                                       | Description                                                                                                                           |
|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| public boolean allowUseOfPreloadedForm(\[boolean value\])                                                    | Determines if the form launched for this instance may come from the pre-loaded form pool.                                             |
| public int arrIdx(\[int value\])                                                                             |                                                                                                                                       |
| public Object caller(\[Object value\])                                                                       | Gets or sets the instance of the object that created this instance of the xArgs class.                                                |
| public IDispatcherProxy callerDispatcher()                                                                   |                                                                                                                                       |
| public FormControl callerFormControl(\[FormControl value\])                                                  |                                                                                                                                       |
| public str callerName()                                                                                      |                                                                                                                                       |
| public UtilElementType callerType()                                                                          |                                                                                                                                       |
| public Guid callerId()                                                                                       |                                                                                                                                       |
| public str clientId(\[str value\])                                                                           |                                                                                                                                       |
| public CopyCallerQuery copyCallerQuery(\[CopyCallerQuery value\])                                            |                                                                                                                                       |
| public TableId dataset()                                                                                     | Gets the table ID of the table in which the caller object is working.                                                                 |
| public str designName(\[str value\])                                                                         | Gets or sets a string that indicates a design on a report or form.                                                                    |
| public ExtendedTypeId extType(\[ExtendedTypeId edt\], \[int arrayIndex\])                                    |                                                                                                                                       |
| public FormViewOption formViewOption(\[FormViewOption value\])                                               |                                                                                                                                       |
| public InitialQueryParameter initialQuery(\[InitialQueryParameter initialQueryParameter\])                   |                                                                                                                                       |
| public FieldId lookupField(\[FieldId value\])                                                                | Gets or sets the field ID in a table to use to look up a specified record.                                                            |
| public Common lookupRecord(\[Common value\])                                                                 | Finds a record in the specified table.                                                                                                |
| public TableId lookupTable(\[TableId value\])                                                                |                                                                                                                                       |
| public str lookupValue(\[str value\])                                                                        | Gets or sets a string to use with the LookupField method to find a value in a field of a table.                                       |
| public str managedContentItemName(\[str value\])                                                             |                                                                                                                                       |
| public str menuItemName(\[str value\])                                                                       | Gets or sets the name of the menu item to use to start the application object.                                                        |
| public MenuItemType menuItemType(\[MenuItemType value\])                                                     | Gets or sets the type of the menu item to use to start the called application object.                                                 |
| public MultiSelectionContext multiSelectionContext()                                                         |                                                                                                                                       |
| public str name(\[str value\])                                                                               | Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.             |
| public Object object(\[Object value\])                                                                       | Gets and sets the application name of the object for which to open a new instance.                                                    |
| public OpenMode openMode(\[OpenMode value\])                                                                 |                                                                                                                                       |
| public Int64 parentWnd(\[Int64 value\])                                                                      |                                                                                                                                       |
| public str parm(\[str value\])                                                                               | Gets or sets a string that specifies miscellaneous information for the called object.                                                 |
| public AnyType parmEnum(\[int value\])                                                                       | Gets or sets the enumeration value of the enumeration type that is specified in the parmEnumType method.                              |
| public int parmEnumType(\[int value\])                                                                       | Gets or sets the ID value of any enumeration type.                                                                                    |
| public Object parmObject(\[Object value\])                                                                   | Gets or sets the instance of any object to pass to the called object.                                                                 |
| public Common record(\[Common value\])                                                                       | Gets or sets the record from the table on which the caller object is working.                                                         |
| public FieldId refField(\[FieldId value\])                                                                   |                                                                                                                                       |
| public str getRequestContextQuery()                                                                          |                                                                                                                                       |
| public str requestContextQuery(str value)                                                                    |                                                                                                                                       |
| public FieldId selectField(\[FieldId value\])                                                                |                                                                                                                                       |
| public str toString()                                                                                        | Retrieves a string representation of an instance of the xArgs.                                                                        |
| public boolean applyRecordAsDynalink(\[boolean applyAsDynalink\])                                            |                                                                                                                                       |
| public void onCallerChanged(\[Object value\])                                                                |                                                                                                                                       |
| public void new(\[AnyType nameOrCaller\], \[Object object\])                                                 | Constructs an instance of this class, which is used to pass information to high-level classes such as the FormRun or ReportRun class. |
| public void finalize()                                                                                       | Removes the current instance of the xArgs class from memory.                                                                          |
| public void setupArgs(str parm, int enumType, AnyType enumValue, \[str menuItemName\], \[int menuItemType\]) |                                                                                                                                       |

## Method allowUseOfPreloadedForm

Determines if the form launched for this instance may come from the pre-loaded form pool.

```xpp
public boolean allowUseOfPreloadedForm([boolean value])
```

### Parameters - allowUseOfPreloadedForm

value  
A Boolean value that determines whether the loaded form can come from the pre-loaded form pool.

### Return Value - allowUseOfPreloadedForm

true if the form launched for this instance may come from the pre-loaded form pool; otherwise, false.

### Remarks - allowUseOfPreloadedForm

Use of a pre-loaded form is permitted by default. Set this to false only if there are undesired side-effects from the use of a pre-loaded form.

## Method arrIdx

```xpp
public int arrIdx([int value])
```

### Parameters - arrIdx

value  

### Return Value - arrIdx

## Method caller

Gets or sets the instance of the object that created this instance of the xArgs class.

```xpp
public Object caller([Object value])
```

### Parameters - caller

value  
The value to set; optional.

### Return Value - caller

The current instance of the caller object.

## Method callerDispatcher

```xpp
public IDispatcherProxy callerDispatcher()
```

### Return Value - callerDispatcher

## Method callerFormControl

```xpp
public FormControl callerFormControl([FormControl value])
```

### Parameters - callerFormControl

value  

### Return Value - callerFormControl

## Method callerName

```xpp
public str callerName()
```

### Return Value - callerName

## Method callerType

```xpp
public UtilElementType callerType()
```

### Return Value - callerType

## Method callerId

```xpp
public Guid callerId()
```

### Return Value - callerId

## Method clientId

```xpp
public str clientId([str value])
```

### Parameters - clientId

value  

### Return Value - clientId

## Method copyCallerQuery

```xpp
public CopyCallerQuery copyCallerQuery([CopyCallerQuery value])
```

### Parameters - copyCallerQuery

value  

### Return Value - copyCallerQuery

## Method dataset

Gets the table ID of the table in which the caller object is working.

```xpp
public TableId dataset()
```

### Return Value - dataset

The table ID of the table in which the caller object is working.

### Remarks - dataset

The returned value is often used to identify which type of record is being transferred from the caller in the record method.

## Method designName

Gets or sets a string that indicates a design on a report or form.

```xpp
public str designName([str value])
```

### Parameters - designName

value  
The value to set; optional.

### Return Value - designName

## Method extType

```xpp
public ExtendedTypeId extType([ExtendedTypeId edt], [int arrayIndex])
```

### Parameters - extType

edt  

<!-- -->

arrayIndex  

### Return Value - extType

## Method formViewOption

```xpp
public FormViewOption formViewOption([FormViewOption value])
```

### Parameters - formViewOption

value  

### Return Value - formViewOption

## Method initialQuery

```xpp
public InitialQueryParameter initialQuery([InitialQueryParameter initialQueryParameter])
```

### Parameters - initialQuery

initialQueryParameter  

### Return Value - initialQuery

## Method lookupField

Gets or sets the field ID in a table to use to look up a specified record.

```xpp
public FieldId lookupField([FieldId value])
```

### Parameters - lookupField

value  
The value to set; optional.

### Return Value - lookupField

The field ID of a field in a table to use to look up a specified record.

### Remarks - lookupField

The returned value can be used by the called object to look up the specified record in the LookupRecord method or the string specified in the LookupValue method. For example, the field to look up could be set with the following: xArgs.lookupField(fieldnum(TableName, FieldName));

## Method lookupRecord

Finds a record in the specified table.

```xpp
public Common lookupRecord([Common value])
```

### Parameters - lookupRecord

value  
The table in which to find a record.

### Return Value - lookupRecord

A record in the specified table.

### Remarks - lookupRecord

This method can be used by the called object in combination with the field ID that is returned from the lookupField method to find the value of the field in the record that is returned by this method.

## Method lookupTable

```xpp
public TableId lookupTable([TableId value])
```

### Parameters - lookupTable

value  

### Return Value - lookupTable

## Method lookupValue

Gets or sets a string to use with the LookupField method to find a value in a field of a table.

```xpp
public str lookupValue([str value])
```

### Parameters - lookupValue

value  
The value to set; optional.

### Return Value - lookupValue

A string to use with the LookupField method to find a value.

## Method managedContentItemName

```xpp
public str managedContentItemName([str value])
```

### Parameters - managedContentItemName

value  

### Return Value - managedContentItemName

## Method menuItemName

Gets or sets the name of the menu item to use to start the application object.

```xpp
public str menuItemName([str value])
```

### Parameters - menuItemName

value  
The value to set; optional.

### Return Value - menuItemName

The name of the menu item to use to start the application object.

### Remarks - menuItemName

For example, to set the menu item you could use the following: xArgs.menuItemName(menuitemdisplaystr(CostingVersionPeriodic));

## Method menuItemType

Gets or sets the type of the menu item to use to start the called application object.

```xpp
public MenuItemType menuItemType([MenuItemType value])
```

### Parameters - menuItemType

value  
The value to set; optional.

### Return Value - menuItemType

The type of the menu item to use to start the called application object.

### Remarks - menuItemType

The menu item type will be one of the Display, Output, or Action enumeration values.

## Method multiSelectionContext

```xpp
public MultiSelectionContext multiSelectionContext()
```

### Return Value - multiSelectionContext

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.

```xpp
public str name([str value])
```

### Parameters - name

value  
The value to set; optional.

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Does not exceed 250 characters.
-   May include numbers and underscore characters.
-   May include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

For example, to call a form from an application object you can use: args.name(formstr(FormName));

## Method object

Gets and sets the application name of the object for which to open a new instance.

```xpp
public Object object([Object value])
```

### Parameters - object

value  
The value to set; optional.

### Return Value - object

The application name of the object for which to open a new instance.

### Remarks - object

The value parameter may be one of the following types of objects:

-   Form
-   Report
-   Job
-   Class
-   Query.

## Method openMode

```xpp
public OpenMode openMode([OpenMode value])
```

### Parameters - openMode

value  

### Return Value - openMode

## Method parentWnd

```xpp
public Int64 parentWnd([Int64 value])
```

### Parameters - parentWnd

value  

### Return Value - parentWnd

## Method parm

Gets or sets a string that specifies miscellaneous information for the called object.

```xpp
public str parm([str value])
```

### Parameters - parm

value  
The value to set; optional.

### Return Value - parm

The value of the string that specifies miscellaneous information for the called object.

## Method parmEnum

Gets or sets the enumeration value of the enumeration type that is specified in the parmEnumType method.

```xpp
public AnyType parmEnum([int value])
```

### Parameters - parmEnum

value  
The key of an enumeration value to set; optional.

### Return Value - parmEnum

The enumeration value of the enumeration type that is specified in the parmEnumType method.

### Remarks - parmEnum

This method is often used with the parmEnumType method: args.parmEnumType(enumnum(AssetBookType));args.parmEnumType(enumnum(AssetBookType));

## Method parmEnumType

Gets or sets the ID value of any enumeration type.

```xpp
public int parmEnumType([int value])
```

### Parameters - parmEnumType

value  
The value to set; optional.

### Return Value - parmEnumType

The ID value of the enumeration type.

### Remarks - parmEnumType

This method is used with the parmEnum method to send a specific value of an enumeration type to the called object. For example: args.parmEnumType(enumnum(AssetBookType));args.parmEnum(AssetBookType::ValueModel);

## Method parmObject

Gets or sets the instance of any object to pass to the called object.

```xpp
public Object parmObject([Object value])
```

### Parameters - parmObject

value  
The value to set; optional.

### Return Value - parmObject

The instance of an object to pass to the called object.

### Remarks - parmObject

The object will often be a class.

## Method record

Gets or sets the record from the table on which the caller object is working.

```xpp
public Common record([Common value])
```

### Parameters - record

value  
The value to set; optional.

### Return Value - record

The record from the table on which the caller object is working.

### Remarks - record

This method is used to access the values in the record that the calling object is currently using.

## Method refField

```xpp
public FieldId refField([FieldId value])
```

### Parameters - refField

value  

### Return Value - refField

## Method getRequestContextQuery

```xpp
public str getRequestContextQuery()
```

### Return Value - getRequestContextQuery

## Method requestContextQuery

```xpp
public str requestContextQuery(str value)
```

### Parameters - requestContextQuery

value  

### Return Value - requestContextQuery

## Method selectField

```xpp
public FieldId selectField([FieldId value])
```

### Parameters - selectField

value  

### Return Value - selectField

## Method toString

Retrieves a string representation of an instance of the xArgs.

```xpp
public str toString()
```

### Return Value - toString

A string that contains a description of the instance of the xArgs class.

## Method applyRecordAsDynalink

```xpp
public boolean applyRecordAsDynalink([boolean applyAsDynalink])
```

### Parameters - applyRecordAsDynalink

applyAsDynalink  

### Return Value - applyRecordAsDynalink

## Method onCallerChanged

```xpp
public void onCallerChanged([Object value])
```

### Parameters - onCallerChanged

value  

## Method new

Constructs an instance of this class, which is used to pass information to high-level classes such as the FormRun or ReportRun class.

```xpp
public void new([AnyType nameOrCaller], [Object object])
```

### Parameters - new

nameOrCaller  
An object argument; optional. This parameter is used to create the instance of the xArgs class and is used when the nameOrCaller parameter is a caller argument.

<!-- -->

object  
An object argument; optional. This parameter is used to create the instance of the xArgs class and is used when the nameOrCaller parameter is a caller argument.

### Remarks - new

To create an xArgs object, either supply a (Caller, Object) pair or a Name argument. Both arguments are optional and all values can be set after it is constructed by calling the appropriate methods.

## Method finalize

Removes the current instance of the xArgs class from memory.

```xpp
public void finalize()
```

## Method setupArgs

```xpp
public void setupArgs(str parm, int enumType, AnyType enumValue, [str menuItemName], [int menuItemType])
```

### Parameters - setupArgs

parm  

<!-- -->

enumType  

<!-- -->

enumValue  

<!-- -->

menuItemName  

<!-- -->

menuItemType  

