---
title: X++ compile-time functions
description: Learn about and access compile-time functions and describes their syntax, parameters, and return values via an overview.
author: pvillads
ms.author: pvillads
ms.topic: language-reference
ms.date: 02/24/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ compile-time functions

[!include [banner](../includes/banner.md)]

This article lists the compile-time functions and describes their syntax, parameters, and return values.

## Overview

Compile-time functions are executed early during the compilation of X++ code. They should be used wherever possible to make the code resilient to changes to the metadata stored in the Application Explorer. Compile-time functions have their input value verified by the compiler. If the input value isn't found to match any existing object in the Application Explorer, the compiler issues an error. The inputs to these functions must be literal values, because the compiler can't determine the value that a variable contains at run time. A compile-time function is a metadata assertion function. It takes arguments that represent an entity in the Application Explorer and validates the arguments at compile time. It has no effect at run time. To support the validation of form, report, query, and menu metadata, use the **AutoDeclaration** property on controls. It's always better to get a compilation error than us a string literal and get errors at runtime.

Some common compile time functions are as follows:

-   `tableStr` - Verifies that the name provided designates a table.
-   `classStr` – Verifies that a class of that name exists. 

Intrinsic functions are special syntactic forms in X++. The arguments can be provided as strings enclosed in quotes, or by simply listing the arguments. The following references:

```xpp
str s = classStr(MyClass); // No quotes
```
and 

```xpp
str s = classStr("MyClass"); // class name in quotes.
```

are semantically identical. In the descriptions below we'll simply show the arguments, and not specify a type, that's obvious from the context.

> [!NOTE]
> X++ compile time functions can't be called from a .NET program.

### Functions

## attributeStr
Validates that the specified attribute class exists in the Application Explorer; if not, a compiler error occurs.

### Syntax

```xpp
str classStr(name)
```

### Parameters

| Parameter | Description                            |
|-----------|----------------------------------------|
| name      | The name of the attribute to validate. |

### Return Value

The name of the attribute.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example
```xpp
str s = attributeStr(AifDocumentOperationAttribute);
```

## classStr
Retrieves the name of a class as a string.

### Syntax

```xpp
str classStr(name)
```

### Parameters

| Parameter | Description                      |
|-----------|----------------------------------|
| name      | The name of the class to return. |

### Return Value

The name of the class.

### Remarks

Use this function instead of literal text to retrieve a string that contains the class name. For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
s = classStr(Global); // returns "Global", since there is a class by that name.
```

## configurationKeyStr
Retrieves the name of a configuration key as a string.

### Syntax

```xpp
str configurationKeyStr(name)
```

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| name      | The name of the configuration key. |

### Return Value

The name of the configuration key.

### Remarks

Use this function instead of literal text to retrieve a string that contains the configuration key name. If the key doesn't exist, the function generates a syntax error at compile time. For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
s = configurationKeyStr(AIF); // Returns "AIF" if there is a configuration key of that name
```

## dataEntityDataSourceStr
Retrieves the name of a data source of a data entity.

### Syntax

```xpp
str dataEntityDataSourceStr(dataEntity, dataSource)
```

### Parameters

| Parameter  | Description                  |
|------------|------------------------------|
| dataEntity | The name of the data entity. |
| dataSource | The name of the data source. |

### Return Value

The name of the data source.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

## delegateStr
Returns the name of the delegate.

### Syntax

```xpp
str delegateStr(class, instanceDelegate)
```

### Parameters

| Parameter        | Description                            |
|------------------|----------------------------------------|
| class            | The name of the class, table, or form. |
| instanceDelegate | The name of the instance delegate.     |

### Return Value

The name of the delegate.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

## dimensionHierarchyLevelStr
Returns the name of the dimension hierarchy level.

### Syntax

```xpp
str dimensionHierarchyLevelStr(dimensionHierarchyLevel)
```

### Parameters

| Parameter               | Description                                |
|-------------------------|--------------------------------------------|
| dimensionHierarchyLevel | The name of the dimension hierarchy level. |

### Return Value

The name of the dimension hierarchy level.

### Remarks

For more information about compile-time functions, see [Overview](#overview).


## dimensionHierarchyStr
Returns the name of the dimension hierarchy.

### Syntax

```xpp
str dimensionHierarchyStr(dimensionHierarchy)
```

### Parameters

| Parameter          | Description                          |
|--------------------|--------------------------------------|
| dimensionHierarchy | The name of the dimension hierarchy. |

### Return Value

The name of the dimension hierarchy.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## dimensionReferenceStr
Returns the name of the dimension reference.

### Syntax

```xpp
str dimensionReferenceStr(dimensionReference)
```

### Parameters

| Parameter          | Description                          |
|--------------------|--------------------------------------|
| dimensionReference | The name of the dimension reference. |

### Return Value

The name of the dimension reference.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## dutyStr
Retrieves a string that represents the name of the specified security duty.

### Syntax

```xpp
str dutyStr(securityDuty)
```

### Parameters

| Parameter    | Description                    |
|--------------|--------------------------------|
| securityDuty | The name of the security duty. |

### Return Value

The name of the security duty in a string.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## enumCnt
Retrieves the number of elements in the specified enumeration type.

### Syntax

```xpp
int enumCnt(enumtype)
```

### Parameters

| Parameter | Description           |
|-----------|-----------------------|
| enumtype  | The enumeration type. |

### Return Value

The number of elements in the specified enumeration type.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
var cnt = enumCnt(NoYes); // Returns 2, as the two elements in the NoYes enum are Yes and No.
```

## enumLiteralStr
Indicates whether the specified string is an element of the specified enumeration type.

### Syntax

```xpp
enumLiteralStr(enum, literal)
```

### Parameters

| Parameter | Description                                                      |
|-----------|------------------------------------------------------------------|
| enum      | The enumeration type from which to retrieve the specified value. |
| literal   | The literal to be returned from the enumeration type. |

### Return Value

The value of the literal parameter if the specified string was found.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
var literal = enumLiteralStr(ABCEnum, valueInABCEnum);
```

## enumStr
Retrieves the name of an enumeration as a string.

### Syntax

```xpp
str enumStr(enumName)
```

### Parameters

| Parameter | Description                  |
|-----------|------------------------------|
| enumName  | The name of the enumeration. |

### Return Value

The name of the enumeration.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
str s = enumStr(ABC); // Returns "ABC" is an enum exists by that name. Otherwise an error is diagnosed.
```


## extendedTypeStr
Retrieves the name of an extended data type as a string.

### Syntax

```xpp
str extendedTypeStr(edtName)
```

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| edtName   | The name of the extended data type. |

### Return Value

The name of the extended data type.

### Remarks

Use this function instead of literal text to return a string that contains the extended data type name. For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "AccountName" is an extended datatype by that name exists. If no
// such type exists, a error is diagnosed.
var edt = extendedTypeStr(AccountName); 
```

## fieldPName
Retrieves the label of the specified field.

### Syntax

```xpp
str fieldPName(tableid, fieldid)
```

### Parameters

| Parameter | Description                                  |
|-----------|----------------------------------------------|
| tableid   | The table that contains the specified field. |
| fieldid   | The field to convert.                        |

### Return Value

The label of the field.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

The following example prints the label of the **CashDisc** field.

```xpp
static void fieldPNameExample(Args _arg)
{
    str myText;

    myText = fieldPName(CustTable, CashDisc);
    info(strfmt("%1 is the label of the CashDisc field.", myText));
}
/****Infolog Display
Message (02:00:57 pm)
Cash discount is the label of the CashDisc field.
****/
```

## fieldStr
Retrieves the field name of the specified field.

### Syntax

```xpp
str fieldStr(tableid, fieldid)
```

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| tableid   | The table that contains the field. |
| fieldid   | The field to convert.              |

### Return Value

The field name of the specified field.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

The following example assigns the name of the **CashDisc** field to the *myText* variable.

```xpp
static void fieldStrExample(Args _arg)
{
    str myText = fieldStr(CustTable, CashDisc);
    info(strfmt("%1 is the specified field.", myText));
}
/****Infolog Display
Message (09:11:52 am)
CashDisc is the specified field.
****/
```

## formControlStr
Causes the X++ compiler to check whether the control exists on the form, and to replace the function call with a string of the valid control name.

### Syntax

```xpp
str formControlStr(formName, controlName)
```

### Parameters

| Parameter   | Description                                                          |
|-------------|----------------------------------------------------------------------|
| formName    | The name of the form, not in quotation marks.                        |
| controlName | The name of the control that is on the form, not in quotation marks. |

### Return Value

A string that contains the name of the control as it appears in the Application Explorer.

### Remarks

For more information about compile-time functions, see [Overview](#overview).


## formDataFieldStr
Returns the name of a data field in a form.

### Syntax

```xpp
str formDataFieldStr(formName, dataSource, dataField)
```

### Parameters

| Parameter  | Description                        |
|------------|------------------------------------|
| formName   | The name of the form.              |
| dataSource | The data source of the form.       |
| dataField  | The data field of the data source. |

### Return Value

The name of a data field in a form.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "RatePerDay" if the FMVehicle form contains a datasource
// called FMModelRate with a datafield called RatePerDay.
str a = formDataFieldStr(FMVehicle, FMModelRate, RatePerDay);
```

## formDataSourceStr
Returns the name of a data source in a form.

### Syntax

```xpp
str formDataSourceStr(formName, dataSource)
```

### Parameters

| Parameter  | Description                  |
|------------|------------------------------|
| formName   | The name of the form.        |
| dataSource | The data source of the form. |

### Return Value

The name of a data source in a form.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "FMModelRate" is there is a form called FmVehicle with a
// datasource called FMModelRate.
str b = formDataSourceStr(FMVehicle, FMModelRate);
```

## formMethodStr
Returns the name of a method of a form.

### Syntax

```xpp
str formMethodStr(formName, methodName)
```

### Parameters

| Parameter  | Description             |
|------------|-------------------------|
| formName   | The name of the form.   |
| methodName | The method of the form. |

### Return Value

The name of a method in a form.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "showDialog" if there is a form called Batch with a 
// method called showDialog.
str c = formMethodStr(Batch,showDialog);
```

## formStr
Retrieves the name of a form.

### Syntax

```xpp
str formStr(form)
```

### Parameters

| Parameter | Description         |
|-----------|---------------------|
| form      | The name of a form. |

### Return Value

A string that represents the name of the form.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

The following example prints the name of the InventDim form.

```xpp
// Returns "InventDim" if there is a form defined by that name.
var s = formStr(InventDim); 
```

## identifierStr
Converts the specified identifier to a string.

### Syntax

```xpp
str identifierStr(ident)
```

### Parameters

| Parameter | Description                |
|-----------|----------------------------|
| ident     | The identifier to convert. |

### Return Value

A string that represents the specified identifier.

### Remarks

Use a more specific compile-time function if one is available. This is a compile-time function. No checking of the argument is performed. For more information, [Overview](#overview).

### Example

The following code example assigns the *myvar* variable name to the *thevar* variable.

```xpp
static void indentifierStrExample(Args _args)
{
    str thevar = "[" + identifierStr(myvar) + "]";
    info(strfmt(thevar));
}
/****Infolog Display
Message (09:19:49 am)
[myvar]
****/
```

## indexStr
Converts the specified index to a string.

### Syntax

```xpp
str indexStr(str tableid, str indexid)
```

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| tableid   | The table that contains the index. |
| indexid   | The index to convert.              |

### Return Value

A string that represents the specified index.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

The following example assigns the **CashDisc** index value to the *myText* variable.

```xpp
// Returns "SSNIndex" if there is a table called MyTable with an index called SSNIndex.
var idx = indexStr(MyTable, SSNIndex);
```

## literalStr
Validates that the specified string can be a literal string; if not, a compiler error occurs.

### Syntax

```xpp
str literalStr(literal)
```

### Parameters

| Parameter | Description             |
|-----------|-------------------------|
| literal   | The string to validate. |

### Return Value

The literal string if valid.

### Remarks
This function is sometimes used to return a label string without the lookup of the label taking place, as shown in the example below.
For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "This is a literal str"
var s = literalStr("This is a literal str");

// Returns the string "@SYS12345", not the label that this
// label specifier may represent.
var labelStr = literalStr("@SYS12345");
```

## maxDate
Retrieves the maximum value allowed for a variable of type date.

### Syntax

```xpp
date maxDate()
```

### Return Value

The maximum value allowed for a variable of type **date**, which is **2154-12-31**.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
static void maxDateExample(Args _arg)
{
    date maximumDate = maxDate();
    print maximumDate;
    pause;
}
```

## maxInt
Retrieves the maximum signed value that can be stored in an **int** type.

### Syntax

```xpp
int maxInt()
```

### Return Value

The maximum value allowed value of an integer, which is 2147483647.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
static void maxIntExample(Args _arg)
{
    print "The maximum value for type int is " + int2Str(maxInt());
    pause;
}
```

## measurementStr
Returns the name of a measurement.

### Syntax

```xpp
str measurementStr(measurement)
```

### Parameters

| Parameter   | Description                  |
|-------------|------------------------------|
| measurement | The name of the measurement. |

### Return Value

The name of the measurement.

### Remarks

For more information about compile-time functions, see [Overview](#overview).


## measureStr
Returns the name of a measure.

### Syntax

```xpp
str measureStr(measure)
```

### Parameters

| Parameter | Description              |
|-----------|--------------------------|
| measure   | The name of the measure. |

### Return Value

The name of the measure.

### Remarks

For more information about compile-time functions, see [Overview](#overview).


## menuItemActionStr
Returns the value of an Action menu item. 

### Syntax

```xpp
str menuItemActionStr(menuitem)
```

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| menuitem  | The name of the action menu item to validate. |

### Return Value

The name of the action menu item, if it's valid.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// returns 'AssetCopy' if there is an Action menu of that name defined.
var s1 = menuItemActionStr(AssetCopy);
```

## menuItemDisplayStr
Returns the value of a Display menu item. 

### Syntax

```xpp
str menuitemdisplaystr(menuItem)
```

### Parameters

| Parameter | Description                                    |
|-----------|------------------------------------------------|
| menuItem  | The name of the display menu item to validate. |

### Return Value

The name of the specified display menu item display.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "Address" if a display menu item of that name is defined.
var s2 = menuItemDisplayStr(Address);
```

## menuItemOutputStr
Returns the value of an Output menu item. 

### Syntax

```xpp
str menuItemOutputStr(menuitem)
```

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| menuitem  | The name of the menu item output to validate. |

### Return Value

The specified output menu item output if valid.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "AssetBarCode" if an output menu item by that name exists.
var s = menuItemOutputStr(AssetBarcode);
```

## menuStr
Returns the name value of a menu. 

### Syntax

```xpp
str menuStr(menu)
```

### Parameters

| Parameter | Description                       |
|-----------|-----------------------------------|
| menu      | The name of the menu to validate. |

### Return Value

The name of the specified menu item if valid.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "Administration" if a menu by that name is defined.
var s = menuStr(Administration);
```

## methodStr
Returns the name of a class instance method.

### Syntax

```xpp
str methodStr(class, method)
```

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| class     | The name of the class.              |
| method    | The name of the method to validate. |

### Return Value

The name of the specified instance method, if it's valid.

### Remarks
This function diagnoses errors for methods that are static. Use staticMethodStr for static methods.
For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "timeout" if there is a class called SysHelpInitTimeout that 
// has a method called timeout.
var s = methodStr(SysHelpInitTimeOut, timeout);
```

## minInt
Retrieves the minimum signed value that can be stored in an **int** type.

### Syntax

```xpp
int minInt()
```

### Return Value

The minimum value of an **int** type, which is -2147483648.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
static void minIntExample(Args _arg)
{
    int i = minInt();
    print "minInt() is " + int2Str(i);    
    pause;
}
```

## privilegeStr
Returns the name of the privilege.

### Syntax

```xpp
str privilegeStr(privilege)
```

### Parameters

| Parameter | Description                                 |
|-----------|---------------------------------------------|
| privilege | The privilege for which to return the name. |

### Return Value

The name of the privilege.

### Remarks

For more information about compile-time functions, see [Overview](#overview).


## queryDatasourceStr
Returns the name of a datasource on a query.

### Syntax

```xpp
str queryDataSourceStr(queryName, dataSourceName)
```

### Parameters

| Parameter      | Description                                                               |
|----------------|---------------------------------------------------------------------------|
| queryName      | The name of the query, not in quotation marks.                            |
| dataSourceName | The name of the data source that is on the query, not in quotation marks. |

### Return Value

A string that contains the name of the data source.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## queryMethodStr
Returns the name of a method of a query.

### Syntax

```xpp
str queryMethodStr(queryName, methodName)
```

### Parameters

| Parameter  | Description             |
|------------|-------------------------|
| queryName  | The name of the query.  |
| methodName | The method of the form. |

### Return Value

The name of a method in a query.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## queryStr
Retrieves a string that represents an existing query.

### Syntax

```xpp
str queryStr(query)
```

### Parameters

| Parameter | Description            |
|-----------|------------------------|
| query     | The query to retrieve. |

### Return Value

The name of the query.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns 'AssetTable' if a query by that name is defined.
str myText = queryStr(AssetTable);
```

## reportStr
Retrieves a string that represents the name of the specified report.

### Syntax

```xpp
str reportStr(report)
```

### Parameters

| Parameter | Description                              |
|-----------|------------------------------------------|
| report    | The report for which to return the name. |

### Return Value

The name of the report.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns "AssetAddition" if a report by that name is defined.
var r = reportStr(AssetAddition);
```

## resourceStr
Validates that the specified resource exists in the Application Explorer; if it doesn't, a compiler error occurs.

### Syntax

```xpp
str resourceStr(resourcename)
```

### Parameters

| Parameter    | Description                           |
|--------------|---------------------------------------|
| resourcename | The name of the resource to validate. |

### Return Value

The name of the specified resource, if it's valid.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// R'eturns 'StyleSheet_Help_Axapta' if a resource by that name is defined.
var r = resourceStr(StyleSheet_Help_Axapta);
```

## roleStr
Retrieves a string that represents the name of the specified security role.

### Syntax

```xpp
str roleStr(securityRole)
```

### Parameters

| Parameter    | Description                    |
|--------------|--------------------------------|
| securityRole | The name of the security role. |

### Return Value

The name of the security role in a string.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## ssrsReportStr
Retrieves a string that represents the name of the specified SSRS report. Use this function when you want to specify the report that should be run by a report controller class.

### Syntax

```xpp
str ssrsReportStr(report, design)
```

### Parameters

| Parameter | Description                                                |
|-----------|------------------------------------------------------------|
| report    | The report to return the name for.                         |
| design    | The name of the design that is associated with the report. |

### Return Value

The name of the report.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
public static void main(Args _args)
{
    // Initializing the object for a controller class, in this case, the class named AssetListingController.
    SrsReportRunController controller = new AssetListingController();

    // Getting the properties of the called object (in this case AssetListing MenuItem)
    controller.parmArgs(_args);

    // Setting the Report name for the controller.
    controller.parmReportName(ssrsReportStr(AssetListing, Report));

    // Initiate the report execution.
    controller.startOperation();
}
```

## staticDelegateStr
Returns the name of a static delegate.

### Syntax

```xpp
str staticDelegateStr(class, delegate)
```

### Parameters

| Parameter | Description                          |
|-----------|--------------------------------------|
| class     | The name of a class, table, or form. |
| delegate  | The name of the delegate.            |

### Return Value

The name of the delegate.

### Remarks
For more information about compile-time functions, see [Overview](#overview).



## staticMethodStr
Validates that the specified static method exists in the specified class; if it doesn't, a compiler error occurs.

### Syntax

```xpp
str staticMethodStr(class, int method)
```

### Parameters

| Parameter | Description                                |
|-----------|--------------------------------------------|
| class     | The name of the class.                     |
| method    | The name of the static method to validate. |

### Return Value

The name of the static method, if it's valid.

### Remarks
This function fails if the designated method isn't static. Use the methodStr function if you wish to return the names of instance methods.
For more information about compile-time functions, see [Overview](#overview).


## tableCollectionStr
Validates that the specified table collection exists in the Application Explorer; if it doesn't, a compiler error occurs.

### Syntax

```xpp
str tableCollectionStr(tablecollection)
```

### Parameters

| Parameter       | Description                                   |
|-----------------|-----------------------------------------------|
| tablecollection | The name of the table collection to validate. |

### Return Value

The name of the specified table collection, if it's valid.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## tableFieldGroupStr
Retrieves the name of a field group as a string.

### Syntax

```xpp
str tableFieldGroupStr(tableName, fieldGroupName)
```

### Parameters

| Parameter      | Description                              |
|----------------|------------------------------------------|
| tableName      | The table that contains the field group. |
| fieldGroupName | The field group in the table.            |

### Return Value

The name of the field group as a string.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

The following example retrieves the name of the **Editing** field group as a string.

```xpp
// Returns 'Editing' if there is a table called AccountingDistribution that has a
// fieldgroup called Editing.
var fg = tableFieldGroupStr(AccountingDistribution, Editing);
```

## tableMethodStr
Validates that the specified instance method exists in the specified table; if it doesn't, a compiler error occurs.

### Syntax

```xpp
str tableMethodStr(table, method)
```

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| table     | The name of the table.              |
| method    | The name of the method to validate. |

### Return Value

The name of the instance method, if it's valid.

### Remarks

For more information about compile-time functions, see [Overview](#overview).


## tablePName
Retrieves a string that contains the printable name of the specified table.

### Syntax

```xpp
str tablePName(str table)
```

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| table     | The table to retrieve the printable name for. |

### Return Value

The name of the specified table.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

The following example assigns the label of the **CustTable** table to the *MyText* variable.

```xpp
static void tablePNameExample(Args _args)
{
    str MyText = tablePname(CustTable);
    info(strfmt("%1 is the label of the CustTable table.", MyText));
}
/**** Infolog Display.
Message (12:13:53 pm)
Customers is the label of the CustTable table.
****/
```

## tableStaticMethodStr
Validates that the specified static method exists in the specified table; if it doesn't, a compiler error occurs.

### Syntax

```xpp
str tableStaticMethodStr(table, method)
```

### Parameters

| Parameter | Description                                |
|-----------|--------------------------------------------|
| table     | The name of the table.                     |
| method    | The name of the static method to validate. |

### Return Value

The name of the specified static method.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## tableStr
Retrieves a string that contains the name the specified table.

### Syntax

```xpp
str tableStr(table)
```

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| table     | The table to retrieve a string for. |

### Return Value

A string value that contains the name of the specified table.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns 'CustTable' if a table by that name is defined.
var t = tableStr(CustTable);
```

## tileStr
Retrieves a string that represents the name of the specified tile.

### Syntax

```xpp
str tileStr(tile)
```

### Parameters

| Parameter | Description           |
|-----------|-----------------------|
| tile      | The name of the tile. |

### Return Value

The name of the tile in a string.

### Remarks

For more information about compile-time functions, see [Overview](#overview).



## varStr
Retrieves a string that contains the name of the specified variable.

### Syntax

```xpp
str varStr(name)
```

### Parameters

| Parameter | Description               |
|-----------|---------------------------|
| varName   | The name of a defined entity. |

### Return Value

A string that contains the name of an item in the scope of the call.

### Remarks
The name must match a variable defined in the method in which the call occurs, or a field in the surrounding scope.
For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
static void varStrExample(Args _arg)
{
    str myString;
    anytype myVariable;

    myString = varStr(myVariable);
    info(strfmt("%1 is the variable name.", myString));
}
/****Infolog Display.
Message (02:26:56 pm)
myVariable is the variable name.
****/
```

## webActionItemStr
Validates that the specified web action item exists in the Application Explorer; if it doesn't, a compiler error occurs.

### Syntax

```xpp
str webActionItemStr(webactionitem)
```

### Parameters

| Parameter     | Description                                  |
|---------------|----------------------------------------------|
| webactionitem | The name of the web action item to validate. |

### Return Value

The name of the specified web action item, if it's valid.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns 'EPFlushData' if a web action by that name is defined.
str s = webActionItemStr(EPFlushData);
```

## webDisplayContentItemStr
Validates that the specified web display content item exists in the Application Explorer; if it doesn't, a compiler error occurs.

### Syntax

```xpp
str webDisplayContentItemStr(webdisplaycontentitem)
```

### Parameters

| Parameter             | Description                                           |
|-----------------------|-------------------------------------------------------|
| webdisplaycontentitem | The name of the web display content item to validate. |

### Return Value

The name of the specified web display content item, if it's valid.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns 'EPAdmin' if a web display content item by that name is defined.
str s = webDisplayContentItemStr(EPAdmin);
```

## workflowApprovalStr
Retrieves the name of a workflow approval in the Application Object Tree (Application Explorer) as a string.

### Syntax

```xpp
str workflowapprovalstr(approval)
```

### Parameters

| Parameter | Description                                             |
|-----------|---------------------------------------------------------|
| approval  | The Application Explorer name of the workflow approval. |

### Return Value

A string that represents the Application Explorer name of the workflow approval.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns 'MyWorkflowApproval' if a workflow approval by that name is defined.
str s = workflowapprovalstr(MyWorkflowApproval);
```

## workflowCategoryStr
Retrieves the name of a workflow category in the Application Object Tree (Application Explorer) as a string.

### Syntax

```xpp
str workflowcategorystr(category)
```

### Parameters

| Parameter | Description                                             |
|-----------|---------------------------------------------------------|
| category  | The Application Explorer name of the workflow category. |

### Return Value

A string that represents the Application Explorer name of the workflow category.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns 'MyWorkflowCategory' if a workflow category by that name is defined.
str s = workflowcategorystr(MyWorkflowCategory);
```

## workflowTaskStr
Retrieves the name of a workflow task in the Application Object Tree (Application Explorer) as a string.

### Syntax

```xpp
str workflowtaskstr(task)
```

### Parameters

| Parameter | Description                                         |
|-----------|-----------------------------------------------------|
| task      | The Application Explorer name of the workflow task. |

### Return Value

A string that represents the Application Explorer name of the workflow task.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns 'MyWorkflowTask' si a workflow task by that name has been defined.
str s = workflowtaskstr(MyWorkflowTask);
```

## workflowTypeStr
Validates that the specified workflow type exists in the Application Explorer; if it doesn't, a compiler error occurs.

### Syntax

```xpp
str workflowTypeStr(workflow)
```

### Parameters

| Parameter | Description                                |
|-----------|--------------------------------------------|
| workflow  | The name of the workflow type to validate. |

### Return Value

The name of the workflow type.

### Remarks

For more information about compile-time functions, see [Overview](#overview).

### Example

```xpp
// Returns 'BudgetAccountEntryType' if a workflow by that name is defined.
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
