---
# required metadata

title: X++ compile-time functions
description: This topic lists the compile-time functions and describes their syntax, parameters, and return values.
author: RobinARH
manager: AnnBe
ms.date: 2016-01-15 19 - 29 - 32
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 29581
ms.assetid: bdf82ff6-5373-4f4d-8a95-86f1660591ad
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# X++ compile-time functions

This topic lists the compile-time functions and describes their syntax, parameters, and return values.

Overview
--------

Compile-time functions are executed early during compilation of X++ code. They should be used wherever possible in X++ code to make the code resilient to changes to the metadata stored in the Application Explorer. Compile-time functions have their input value verified by the compiler. If the input value is not found to match any existing object in the Application Explorer, the compiler issues an error. The inputs to these functions must be literals, because the compiler cannot determine the value that a variable contains at run time. A compile-time function is a metadata assertion function. It takes arguments that represents an entity in the Application Explorer and validates the arguments at compile time. It has no effect at run time. Attributes are classes that inherit from the **SysAttribute** class. To support the validation of form, report, query, and menu metadata, use the **AutoDeclaration** property on controls. Most of these functions retrieve metadata about items that are in the Application Explorer. Some common compile time functions are as follows:

-   `classNum` – Retrieves the ID of a class.
-   `classStr` – During compile time, verifies that a class of that name exists. This approach is better than discovering the error later during run time.
-   `evalBuf`– Evaluates the input string of X++ code, and then returns the results as a string.
-   `literalStr` – retrieves a label ID when given the string representation of a label, such as the string `"@SYS12345"`. For example, `myLabel.exists(literalStr("@SYS12345"));`.

| **Note**                                                         |
|------------------------------------------------------------------|
| X++ compile time functions cannot be called from a .NET program. |

### Functions

## attributeStr
Validates that the specified attribute class exists in the Application Explorer; if not, a compiler error occurs.

### Syntax

    str classStr(class class)

### Parameters

| Parameter | Description                            |
|-----------|----------------------------------------|
| class     | The name of the attribute to validate. |

### Return Value

The name of the attribute.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void attributeStrExample(Args _args)
    {
        str s;
        ;
        s = attributeStr(AifDocumentOperationAttribute);
        print s;
        pause;
    }

## classNum
Retrieves the ID of the specified class.

### Syntax

    int classNum(class class)

### Parameters

| Parameter | Description                             |
|-----------|-----------------------------------------|
| class     | The class for which to retrieve the ID. |

### Return Value

The ID of the specified class.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void classNumExample(Args _args)
    {
        int i;
        ;
        i = classNum(Global);
        print i;
        pause;
    }

## classStr
Retrieves the name of a class as a string.

### Syntax

    str classStr(class class)

### Parameters

| Parameter | Description                      |
|-----------|----------------------------------|
| class     | The name of the class to return. |

### Return Value

The name of the class.

### Remarks

Use this function instead of literal text to retrieve a string that contains the class name. If the class does not exist, the function generates a syntax error at compile time. This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void clStrExample(Args _args)
    {
        str s;
        ;
        s = classStr(Global);
        print s;
        pause;
    }

## configurationKeyNum
Retrieves the ID of the specified configuration key.

### Syntax

    int configurationKeyNum(str keyname)

### Parameters

| Parameter | Description                                       |
|-----------|---------------------------------------------------|
| keyname   | The configuration key for which to return the ID. |

### Return Value

The ID of the specified configuration key.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void configurationKeyNum(Args _args)
    {
        int i;
        ;
        i = configurationKeyNum(AIF);
        print i;
        pause;
    }

## configurationKeyStr
Retrieves the name of a configuration key as a string.

### Syntax

    str configurationKeyStr(str keyname)

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| keyname   | The name of the configuration key. |

### Return Value

The name of the configuration key.

### Remarks

Use this function instead of literal text to retrieve a string that contains the configuration key name. If the key does not exist, the function generates a syntax error at compile time. This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void configurationKeyStrExample(Args _args)
    {
        str s;
        ;
        s = configurationKeyStr(AIF);
        print s;
        pause;
    }

## dataEntityDataSourceStr
Retrieves the name of a data source of a data entity.

### Syntax

    str dataEntityDataSourceStr(str dataEntity, str dataSource)

### Parameters

| Parameter  | Description                  |
|------------|------------------------------|
| dataEntity | The name of the data entity. |
| dataSource | The name of the data source. |

### Return Value

The name of the data source.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## delegateStr
Returns the name of the delegate.

### Syntax

    str delegateStr(str class, str instanceDelegate)

### Parameters

| Parameter        | Description                            |
|------------------|----------------------------------------|
| class            | The name of the class, table, or form. |
| instanceDelegate | The name of the instance delegate.     |

### Return Value

The name of the delegate.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## dimensionHierarchyLevelStr
Returns the name of the dimension hierarchy level.

### Syntax

    str dimensionHierarchyLevelStr(str dimensionHierarchyLevel)

### Parameters

| Parameter               | Description                                |
|-------------------------|--------------------------------------------|
| dimensionHierarchyLevel | The name of the dimension hierarchy level. |

### Return Value

The name of the dimension hierarchy level.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## dimensionHierarchyStr
Returns the name of the dimension hierarchy.

### Syntax

    str dimensionHierarchyStr(str dimensionHierarchy)

### Parameters

| Parameter          | Description                          |
|--------------------|--------------------------------------|
| dimensionHierarchy | The name of the dimension hierarchy. |

### Return Value

The name of the dimension hierarchy.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## dimensionReferenceStr
Returns the name of the dimension reference.

### Syntax

    str dimensionReferenceStr(str dimensionReference)

### Parameters

| Parameter          | Description                          |
|--------------------|--------------------------------------|
| dimensionReference | The name of the dimension reference. |

### Return Value

The name of the dimension reference.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## dutyStr
Retrieves a string that represents the name of the specified security duty.

### Syntax

    str dutyStr(str securityDuty)

### Parameters

| Parameter    | Description                    |
|--------------|--------------------------------|
| securityDuty | The name of the security duty. |

### Return Value

The name of the security duty in a string.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## enumCnt
Retrieves the number of elements in the specified enumeration type.

### Syntax

    int enumCnt(enum enumtype)

### Parameters

| Parameter | Description           |
|-----------|-----------------------|
| enumtype  | The enumeration type. |

### Return Value

The number of elements in the specified enumeration type.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    enumCnt(NoYes); //Returns 2, as the two elements are Yes and No.

## enumLiteralStr
Indicates whether the specified string is an element of the specified enumeration type.

### Syntax

    enumLiteralStr(enum enum, string str)

### Parameters

| Parameter | Description                                                      |
|-----------|------------------------------------------------------------------|
| enum      | The enumeration type from which to retrieve the specified value. |

### Return Value

The value of the *str* parameter if the specified string was found; otherwise, a compilation error.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void getEnumValueAsString()
    {
        str i;
        i = enumLiteralStr(ABCEnum, "valueInABCEnum");
        print i;
        pause;
    }

## enumNum
Retrieves the ID of the specified enumeration type.

### Syntax

    int enumNum(enum enum)

### Parameters

| Parameter | Description                                 |
|-----------|---------------------------------------------|
| enum      | The enumeration for which to return the ID. |

### Return Value

The ID of the specified enumeration type.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void enumNum(Args _args)
    {
        int i;
        ;
        i = enumNum(ABC);
        print i;
        pause;
    }

## enumStr
Retrieves the name of an enumeration as a string.

### Syntax

    str enumStr(enum enum)

### Parameters

| Parameter | Description                  |
|-----------|------------------------------|
| enum      | The name of the enumeration. |

### Return Value

The name of the enumeration.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void enumStrExample(Args _args)
    {
        str s;
        ;
        s = enumStr(ABC);
        print s;
        pause;
    }

## extendedTypeNum
Retrieves the ID of the specified extended data type.

### Syntax

    int extendedTypeNum(int str)

### Parameters

| Parameter | Description                                        |
|-----------|----------------------------------------------------|
| str       | The extended data type for which to return the ID. |

### Return Value

The ID of the specified extended data type.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void EDTNum(Args _args)
    {
        int i;
        str s;
        ;
     
        i = extendedTypeNum(AccountName);
        s = extendedTypeStr(AccountName);
        print  int2Str(i);
        print  s;
        pause;
    }

## extendedTypeStr
Retrieves the name of an extended data type as a string.

### Syntax

    str extendedTypeStr(int str)

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| str       | The name of the extended data type. |

### Return Value

The name of the extended data type.

### Remarks

Use this function instead of literal text to return a string that contains the extended data type name. If the data type does not exist, the **extendedTypeStr** function generates a syntax error at compile time. This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void EDTStr(Args _args)
    {
        int i;
        str s;
        ;
     
        i = extendedTypeNum(AccountName);
        s = extendedTypeStr(AccountName);
        print  int2Str(i);
        print  s;
        pause;
    }

## fieldNum
Returns the ID number of the specified field.

### Syntax

    int fieldNum(str tableName, str fieldName)

### Parameters

| Parameter | Description            |
|-----------|------------------------|
| tableName | The name of the table. |
| fieldName | The name of the field. |

### Return Value

The ID of the specified field.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example prints the number of the **CashDisc** field in the **CustTable** table.

    static void fieldNumExample(Args _args)
    {
        int myInt;
        ;

        myInt = fieldNum(CustTable, CashDisc);
        Global::info(strfmt("CashDisc has a field ID of %1 in the CustTable table.", myInt));
    }
    /****Infolog Display
    Message (10:40:00 am)
    CashDisc has a field ID of 10 in the CustTable table.
    ****/

## fieldPName
Retrieves the label of the specified field.

### Syntax

    str fieldPName(str tableid, str fieldid)

### Parameters

| Parameter | Description                                  |
|-----------|----------------------------------------------|
| tableid   | The table that contains the specified field. |
| fieldid   | The field to convert.                        |

### Return Value

The label of the field.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example prints the label of the **CashDisc** field.

    static void fieldPNameExample(Args _arg)
    {
        str myText;
        ;

        myText = fieldPName(CustTable, CashDisc);
        Global::info(strfmt("%1 is the label of the CashDisc field.", myText));
    }
    /****Infolog Display
    Message (02:00:57 pm)
    Cash discount is the label of the CashDisc field.
    ****/

## fieldStr
Retrieves the field name of the specified field.

### Syntax

    str fieldStr(str tableid, str fieldid)

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| tableid   | The table that contains the field. |
| fieldid   | The field to convert.              |

### Return Value

The field name of the specified field.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example assigns the name of the **CashDisc** field to the *myText* variable.

    static void fieldStrExample(Args _arg)
    {
        str myText;
        ;

        myText = fieldStr(CustTable, CashDisc);
        Global::info(strfmt("%1 is the specified field.", myText));
    }
    /****Infolog Display
    Message (09:11:52 am)
    CashDisc is the specified field.
    ****/

## formControlStr
Causes the X++ compiler to check whether the control exists on the form, and to replace the function call with a string of the valid control name.

### Syntax

    str formControlStr(formName, controlName)

### Parameters

| Parameter   | Description                                                          |
|-------------|----------------------------------------------------------------------|
| formName    | The name of the form, not in quotation marks.                        |
| controlName | The name of the control that is on the form, not in quotation marks. |

### Return Value

A string that contains the name of the control as it appears in the Application Explorer.

### Remarks

A compile error is issued if the compiler determines that the control does not exist on the form. If your X++ code uses a string that contains quotation marks to supply the control name, the error cannot be discovered until run time. Use of this function enables the compiler to discover the error earlier at compile time. X++ functions such as **formControlStr** that are executed by the compiler are called compile-time functions or compile-time functions. That is why the input parameters are not standard strings in quotation marks. Compile-time functions are not represented in the p-code or other executable that is output by the compiler. This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## formDataFieldStr
Returns the name of a data field in a form.

### Syntax

    str formDataFieldStr(str formName, str dataSource, str dataField)

### Parameters

| Parameter  | Description                        |
|------------|------------------------------------|
| formName   | The name of the form.              |
| dataSource | The data source of the form.       |
| dataField  | The data field of the data source. |

### Return Value

The name of a data field in a form.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    str a = formDataFieldStr(FMVehicle, FMModelRate, RatePerDay);

## formDataSourceStr
Returns the name of a data source in a form.

### Syntax

    str formDataSourceStr(str formName, str dataSource)

### Parameters

| Parameter  | Description                  |
|------------|------------------------------|
| formName   | The name of the form.        |
| dataSource | The data source of the form. |

### Return Value

The name of a data source in a form.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    str b = formDataSourceStr(FMVehicle, FMModelRate);

## formMethodStr
Returns the name of a method of a form.

### Syntax

    str formMethodStr(str formName, str methodName)

### Parameters

| Parameter  | Description             |
|------------|-------------------------|
| formName   | The name of the form.   |
| methodName | The method of the form. |

### Return Value

The name of a method in a form.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example prints the name of the **showDialog** method.

    str c = formMethodStr(Batch,showDialog);

## formStr
Retrieves the name of a form.

### Syntax

    str formStr(str form)

### Parameters

| Parameter | Description         |
|-----------|---------------------|
| form      | The name of a form. |

### Return Value

A string that represents the name of the form.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example prints the name of the InventDim form.

    static void formStrExample(Args _arg)
    {
        ;

        Global::info(formStr(InventDim));
    }
    /****Infolog Display
    Message (11:04:39 am)
    InventDim
    ****/

## identifierStr
Converts the specified identifier to a string.

### Syntax

    str identifierStr(str ident)

### Parameters

| Parameter | Description                |
|-----------|----------------------------|
| ident     | The identifier to convert. |

### Return Value

A string that represents the specified identifier.

### Remarks

You will receive a best practice warning if you use the **identifierStr** function. This occurs because existence checking is performed for **identifierStr**. Try to use a more specific compile-time function if one is available. This is a compile-time function. For more information, [Overview](#overview).

### Example

The following code example assigns the *myvar* variable name to the *thevar* variable.

    static void indentifierStrExample(Args _args)
    {
        str myvar;
        str thevar
        ;
        
        thevar = "[" + identifierStr(myvar) + "]";
        Global::info(strfmt(thevar));
    }
    /****Infolog Display
    Message (09:19:49 am)
    [myvar]
    ****/

## indexNum
Converts the specified index to a number.

### Syntax

    int indexNum(str tableid, str indexid)

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| tableid   | The table that contains the index. |
| indexid   | The index to convert.              |

### Return Value

The index number that represents the specified index.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example returns the index value of the Party index.

    static void indexNumExample(Args _arg)
    {
        ;
        
        Global::info(strfmt("%1 is the index number of Party.", indexNum(CustTable, Party)));
    }
    /****Infolog Display
    Message (11:28:03 am)
    3 is the index number of Party.
    ****/

## indexStr
Converts the specified index to a string.

### Syntax

    str indexStr(str tableid, str indexid)

### Parameters

| Parameter | Description                        |
|-----------|------------------------------------|
| tableid   | The table that contains the index. |
| indexid   | The index to convert.              |

### Return Value

A string that represents the specified index.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example assigns the **CashDisc** index value to the *myText* variable.

    static void fieldStrExample(Args _arg)
    {
        str myText;
        ;

        myText = fieldStr(CustTable, CashDisc);
        Global::info(strfmt("%1 is the specified index.", myText));
    }
    /****Infolog Display
    Message (09:11:52 am)
    CashDisc is the specified index.
    ****/

## licenseCodeNum
Validates that the specified license code exists in the Application Explorer; if not, a compiler error occurs.

### Syntax

    int licenseCodeNum(str codename)

### Parameters

| Parameter | Description                               |
|-----------|-------------------------------------------|
| codename  | The name of the license code to validate. |

### Return Value

The number of the specified license code.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void licenseCodeNumExample(Args args)
    {
        int i;
        ;

        i = licenseCodeNum(SysMorphX);
        Global::info(strfmt("%1 is the license code number for SysMorphX.", i));
    }
    /****Infolog Display
    Message (01:52:35 pm)
    24 is the license code number for SysMorphX.
    ****/

## licenseCodeStr
Validates that the specified license code exists in the Application Explorer; if not, a compiler error occurs.

### Syntax

    str licenseCodeStr(str codename)

### Parameters

| Parameter | Description                               |
|-----------|-------------------------------------------|
| codename  | The name of the license code to validate. |

### Return Value

The name of the specified license code.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void licenseCodeStrExample(Args _arg)
    {
        str s;
        ;

        s = licenseCodeStr(SysMorphX);
        Global::info(strfmt("%1 is the license code string for SysMorphX.", s));
    }
    /****Infolog Display
    Message (02:33:56 pm)
    SysMorphX is the license code string for SysMorphX.
    ****/

## literalStr
Validates that the specified string can be a literal string; if not, a compiler error occurs.

### Syntax

    str literalStr(int str)

### Parameters

| Parameter | Description             |
|-----------|-------------------------|
| codename  | The string to validate. |

### Return Value

The literal string if valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
     
        s = literalStr("This is a literal str");
        print s;
        pause;
    }

## maxDate
Retrieves the maximum value allowed for a variable of type date.

### Syntax

    date maxDate()

### Return Value

The maximum value allowed for a variable of type **date**, which is **2154-12-31**.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void maxDateExample(Args _arg)
    {
        date maximumDate;
        ;
        maximumDate = maxDate();
        print maximumDate;
        pause;
    }

## maxInt
Retrieves the maximum signed value that can be stored in an **int** type.

### Syntax

    int maxInt()

### Return Value

The maximum value allowed value of an integer.

### Remarks

Any other integer will be less than or equal to the returned value. This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void maxIntExample(Args _arg)
    {
        int i;
        ;
        print "The maximum value for type int is " + int2Str(maxInt());
        pause;
    }

## measurementStr
Returns the name of a measurement.

### Syntax

    str measurementStr(str measurement)

### Parameters

| Parameter   | Description                  |
|-------------|------------------------------|
| measurement | The name of the measurement. |

### Return Value

The name of the measurement.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## measureStr
Returns the name of a measure.

### Syntax

    str measureStr(str measure)

### Parameters

| Parameter | Description              |
|-----------|--------------------------|
| measure   | The name of the measure. |

### Return Value

The name of the measure.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## menuItemActionStr
Validates that the specified menu item action exists in the Application Object Tree (Application Explorer); if it does not, a compiler error occurs.

### Syntax

    str menuItemActionStr(class menuitem)

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| codename  | The name of the menu item action to validate. |

### Return Value

The name of the menu item action, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s1, s2, s3, s4;
        ;
     
        s1 = menuItemActionStr(AssetCopy);
        s2 = menuItemDisplayStr(Address);
        s3 = menuItemOutputStr(AssetBarcode);
        s4 = menuStr(Administration);
     
        print "menuItemActionStr for AssetCopy is " + s1;
        print "menuItemDisplayStr for Address is " + s2;
        print "menuItemOutputStr for AssetBarcode is " + s3;
        print "menuStr for Administration is " + s4;
     
        pause;
    }

## menuItemDisplayStr
Validates that the specified menu item display exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str menuitemdisplaystr(class menuItem)

### Parameters

| Parameter | Description                                    |
|-----------|------------------------------------------------|
| codename  | The name of the menu item display to validate. |

### Return Value

The name of the specified menu item display, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s1, s2, s3, s4;
        ;
     
        s1 = menuItemActionStr(AssetCopy);
        s2 = menuItemDisplayStr(Address);
        s3 = menuItemOutputStr(AssetBarcode);
        s4 = menuStr(Administration);
     
        print "menuItemActionStr for AssetCopy is " + s1;
        print "menuItemDisplayStr for Address is " + s2;
        print "menuItemOutputStr for AssetBarcode is " + s3;
        print "menuStr for Administration is " + s4;
     
        pause;
    }

## menuItemOutputStr
Validates that the specified menu item output exists in the Application Explorer; if not, a compiler error occurs.

### Syntax

    str menuItemOutputStr(class menuitem)

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| codename  | The name of the menu item output to validate. |

### Return Value

The specified menu item output if valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s1, s2, s3, s4;
        ;
     
        s1 = menuItemActionStr(AssetCopy);
        s2 = menuItemDisplayStr(Address);
        s3 = menuItemOutputStr(AssetBarcode);
        s4 = menuStr(Administration);
     
        print "menuItemActionStr for AssetCopy is " + s1;
        print "menuItemDisplayStr for Address is " + s2;
        print "menuItemOutputStr for AssetBarcode is " + s3;
        print "menuStr for Administration is " + s4;
     
        pause;
    }

## menuStr
Validates that the specified menu exists in the Application Explorer; if not, a compiler error occurs.

### Syntax

    str menuStr(class menu)

### Parameters

| Parameter | Description                       |
|-----------|-----------------------------------|
| menu      | The name of the menu to validate. |

### Return Value

The name of the specified menu item if valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s1, s2, s3, s4;
        ;
     
        s1 = menuItemActionStr(AssetCopy);
        s2 = menuItemDisplayStr(Address);
        s3 = menuItemOutputStr(AssetBarcode);
        s4 = menuStr(Administration);
     
        print "menuItemActionStr for AssetCopy is " + s1;
        print "menuItemDisplayStr for Address is " + s2;
        print "menuItemOutputStr for AssetBarcode is " + s3;
        print "menuStr for Administration is " + s4;
     
        pause;
    }

## methodStr
Validates that the specified method exists in the specified class; if it does not, a compiler error occurs.

### Syntax

    str methodStr(class class, int method)

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| class     | The name of the class.              |
| method    | The name of the method to validate. |

### Return Value

The name of the specified method, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        #define.timeout(50)
        str s;
        SysHelpInitTimeOut SysHelpInitTimeOut;
        ;
     
        s = methodStr(SysHelpInitTimeOut, timeout);
        print s;
        pause;
    }

## minInt
Retrieves the minimum signed value that can be stored in an **int** type.

### Syntax

    int minInt()

### Return Value

The minimum value of an **int** type.

### Remarks

Any other integer value will be greater than or equal to the returned value. This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void minIntExample(Args _arg)
    {
        int i;
        ;
        i = minInt();
        print "minInt() is " + int2Str(i);    
        pause;
    }

## privilegeStr
Returns the name of the privilege.

### Syntax

    str privilegeStr(str privilege)

### Parameters

| Parameter | Description                                 |
|-----------|---------------------------------------------|
| privilege | The privilege for which to return the name. |

### Return Value

The name of the privilege.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## queryDatasourceStr
Causes the X++ compiler to check whether the data source exists on the query, and to replace the function call with a string of the valid data source name.

### Syntax

    str queryDataSourceStr(queryName, dataSourceName)

### Parameters

| Parameter      | Description                                                               |
|----------------|---------------------------------------------------------------------------|
| queryName      | The name of the query, not in quotation marks.                            |
| dataSourceName | The name of the data source that is on the query, not in quotation marks. |

### Return Value

A string that contains the name of the data source as it appears in the Application Explorer.

### Remarks

A compile error is issued if the compiler determines that the data source does not exist on the query. If your X++ code uses a string that contains quotation marks to supply the data source name, the error cannot be discovered until run time. Use of this function enables the compiler to discover the error earlier at compile time. X++ functions such as **queryDataSourceStr** that are executed by the compiler are referred to as compile-time functions or compile-time functions. That is why the input parameters are not standard strings in quotation marks. Compile-time functions are not represented in the p-code or other executable that is output by the compiler. This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## queryMethodStr
Returns the name of a method of a query.

### Syntax

    str queryMethodStr(str queryName, str methodName)

### Parameters

| Parameter  | Description             |
|------------|-------------------------|
| queryName  | The name of the query.  |
| methodName | The method of the form. |

### Return Value

The name of a method in a query.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## queryStr
Retrieves a string that represents an existing query.

### Syntax

    str queryStr(str query)

### Parameters

| Parameter | Description            |
|-----------|------------------------|
| query     | The query to retrieve. |

### Return Value

The name of the query.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void queryStrExample(Args _arg)
    {
        str myText;
        ;
        
        myText = queryStr(AssetTable);
        Global::info(strfmt("%1 is the name of the query.",myText));
    }
    /****Infolog Display
    Message (09:45:16 am)
    AssetTable is the name of the query.
    ****/

## reportStr
Retrieves a string that represents the name of the specified report.

### Syntax

    str reportStr(str report)

### Parameters

| Parameter | Description                              |
|-----------|------------------------------------------|
| report    | The report for which to return the name. |

### Return Value

The name of the report.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example assigns the name of the **AssetAddition** report to the *MyTxt* variable.

    static void reportStrExample(Args _args)
    {
        str MyTxt;
        ;

        MyTxt = reportStr(AssetAddition);
        Global::info(strfmt("%1 is the name of the report.", MyTxt));
    }
    /****Infolog Display.
    Message (10:46:36 am)
    AssetAddition is the name of the report.
    ****/

## resourceStr
Validates that the specified resource exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str resourceStr(str resourcename)

### Parameters

| Parameter    | Description                           |
|--------------|---------------------------------------|
| resourcename | The name of the resource to validate. |

### Return Value

The name of the specified resource, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        print "Str for resource StyleSheet_Help_Axapta is " 
            + resourceStr(StyleSheet_Help_Axapta);
        pause;
    }

## roleStr
Retrieves a string that represents the name of the specified security role.

### Syntax

    str roleStr(str securityRole)

### Parameters

| Parameter    | Description                    |
|--------------|--------------------------------|
| securityRole | The name of the security role. |

### Return Value

The name of the security role in a string.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## ssrsReportStr
Retrieves a string that represents the name of the specified report. Use this function when you want to specify the report that should be run by a report controller class.

### Syntax

    str ssrsReportStr(str report, str design)

### Parameters

| Parameter | Description                                                |
|-----------|------------------------------------------------------------|
| report    | The report to return the name for.                         |
| design    | The name of the design that is associated with the report. |

### Return Value

The name of the report.

### Remarks

The **ssrsReportStr** function parses the two values that are passed to it, to validate whether they belong to a valid report. The report name must be set when a menu item points to a controller(), so that the controller can determine which report-design combination must be invoked. Use of the **ssrsReportStr** function provides the benefit of compile-time validation for the report and design name. This is a compile-time function. For more information, see [Overview](#overview).

### Example

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

## staticDelegateStr
Returns the name of a static delegate.

### Syntax

    str staticDelegateStr(str class, str delegate)

### Parameters

| Parameter | Description                          |
|-----------|--------------------------------------|
| class     | The name of a class, table, or form. |
| delegate  | The name of the delegate.            |

### Return Value

The name of the delegate.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## staticMethodStr
Validates that the specified static method exists in the specified class; if it does not, a compiler error occurs.

### Syntax

    str staticMethodStr(class class, int method)

### Parameters

| Parameter | Description                                |
|-----------|--------------------------------------------|
| class     | The name of the class.                     |
| method    | The name of the static method to validate. |

### Return Value

The name of the static method, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## tableCollectionStr
Validates that the specified table collection exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str tableCollectionStr(class tablecollection)

### Parameters

| Parameter       | Description                                   |
|-----------------|-----------------------------------------------|
| tablecollection | The name of the table collection to validate. |

### Return Value

The name of the specified table collection, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## tableFieldGroupStr
Retrieves the name of a field group as a string.

### Syntax

    str tableFieldGroupStr(str tableName, str fieldGroupName)

### Parameters

| Parameter      | Description                              |
|----------------|------------------------------------------|
| tableName      | The table that contains the field group. |
| fieldGroupName | The field group in the table.            |

### Return Value

The name of the field group as a string.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example retrieves the name of the **Editing** field group as a string.

    static void tableFieldGroupStrExample(Args _arg)
    {
        ;

        Global::info(tableFieldGroupStr(AccountingDistribution, Editing));
    }
    /****Infolog Display
    Message (03:14:54 pm)
    Editing
    ****/

## tableMethodStr
Validates that the specified method exists in the specified table; if it does not, a compiler error occurs.

### Syntax

    str tableMethodStr(int table, int method)

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| table     | The name of the table.              |
| method    | The name of the method to validate. |

### Return Value

The name of the method, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## tableNum
Retrieves the table ID of the specified table.

### Syntax

    int tableNum(str table)

### Parameters

| Parameter | Description                             |
|-----------|-----------------------------------------|
| table     | The table to retrieve the table ID for. |

### Return Value

The table ID of the specified table.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example sets the **tableID** variable to 77, which is the **ID** of the **CustTable** table.

    static void tableNumExample(Args _args)
    {
        int tableID;
        ;
        
        tableID = tableNum(CustTable);
        Global::info(strfmt("%1 is the table ID for the CustTable table.", tableID));

    }
    /****Infolog Display
    Message (11:15:54 am)
    77 is the table ID for the CustTable table.
    ****/

## tablePName
Retrieves a string that contains the printable name of the specified table.

### Syntax

    str tablePName(str table)

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| table     | The table to retrieve the printable name for. |

### Return Value

The name of the specified table.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example assigns the label of the **CustTable** table to the *MyText* variable.

    static void tablePNameExample(Args _args)
    {
        str MyText;
        ;

        MyText = tablePname(CustTable);
        Global::info(strfmt("%1 is the label of the CustTable table.", MyText));
    }
    /**** Infolog Display.
    Message (12:13:53 pm)
    Customers is the label of the CustTable table.
    ****/

## tableStaticMethodStr
Validates that the specified static method exists in the specified table; if it does not, a compiler error occurs.

### Syntax

    str tableStaticMethodStr(int table, int method)

### Parameters

| Parameter | Description                                |
|-----------|--------------------------------------------|
| table     | The name of the table.                     |
| method    | The name of the static method to validate. |

### Return Value

The name of the specified static method.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## tableStr
Retrieves a string that contains the name the specified table.

### Syntax

    str tableStr(str table)

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| table     | The table to retrieve a string for. |

### Return Value

A string value that contains the name of the specified table.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following example assigns the name of the **CustTable** table to the *MyTxt* variable.

    static void tableStrExample(Args _args)
    {
        str MyTxt;
        ;
        
        MyTxt = tableStr(CustTable);
        Global::info(strfmt("%1 is the str output of the input of CustTable.", MyTxt));
    }
    /**** Infolog Display. 
    Message (01:21:49 pm)
    CustTable is the str output of the input of CustTable.
    ****/

## tileStr
Retrieves a string that represents the name of the specified tile.

### Syntax

    str tileStr(str tile)

### Parameters

| Parameter | Description           |
|-----------|-----------------------|
| tile      | The name of the tile. |

### Return Value

The name of the tile in a string.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## varStr
Retrieves a string that contains the name of the specified variable.

### Syntax

    str varStr(str var)

### Parameters

| Parameter | Description               |
|-----------|---------------------------|
| var       | The name of the variable. |

### Return Value

A string that contains the name of the specified variable.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void varStrExample(Args _arg)
    {
        str myString;
        anytype myVariable;
        ;
        
        myString = varStr(myVariable);
        Global::info(strfmt("%1 is the variable name.", myString));
    }
    /****Infolog Display.
    Message (02:26:56 pm)
    myVariable is the variable name.
    ****/

## webActionItemStr
Validates that the specified web action item exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webActionItemStr(class webactionitem)

### Parameters

| Parameter     | Description                                  |
|---------------|----------------------------------------------|
| webactionitem | The name of the web action item to validate. |

### Return Value

The name of the specified web action item, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
        s = webActionItemStr(EPFlushData);
        print "webactionitem str is " + s;
        pause;
    }

## webDisplayContentItemStr
Validates that the specified web display content item exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webDisplayContentItemStr(class webdisplaycontentitem)

### Parameters

| Parameter             | Description                                           |
|-----------------------|-------------------------------------------------------|
| webdisplaycontentitem | The name of the web display content item to validate. |

### Return Value

The name of the specified web display content item, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;

        s = webDisplayContentItemStr(EPAdmin);
        print "string for webcontent display item EPAdmin is " + s;
        pause;
    }

## webFormStr
Validates that the specified web form exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webFormStr(str name)

### Parameters

| Parameter | Description                           |
|-----------|---------------------------------------|
| name      | The name of the web form to validate. |

### Return Value

The name of the specified web form, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
        s = webFormStr(EPAdmin);
        print "String for web form EPAdmin is " + s;
        pause;
    }

## webletItemStr
Validates that the specified weblet item exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webletItemStr(class webletitem)

### Parameters

| Parameter  | Description                              |
|------------|------------------------------------------|
| webletitem | The name of the weblet item to validate. |

### Return Value

The name of the specified weblet item, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
        s = webletItemStr(WebFormWeblet);
        print "String for WebFormWeblet is " + s;
        pause;
    }

## webMenuStr
Validates that the specified web menu exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webMenuStr(str name)

### Parameters

| Parameter | Description                           |
|-----------|---------------------------------------|
| name      | The name of the web menu to validate. |

### Return Value

The name of the specified web menu, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
        s = webMenuStr(ECPAdmin);
        print "String for web menu ECPAdmin is " + s;
        pause;
    }

## webOutputContentItemStr
Validates that the specified web output content item exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webOutputContentItemStr(class weboutputcontentitem)

### Parameters

| Parameter            | Description                                          |
|----------------------|------------------------------------------------------|
| weboutputcontentitem | The name of the web output content item to validate. |

### Return Value

The name of the specified web output content item, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
        s = webOutputContentItemStr(EPPriceList);
        print "string for weboutput content item EPPriceList is " + s;
        pause;
    }

## webpageDefStr
Validates that the specified Web page defintion exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webpageDefStr(str pagename)

### Parameters

| Parameter | Description                                      |
|-----------|--------------------------------------------------|
| pagename  | The name of the Web page definition to validate. |

### Return Value

The name of the specified web-page definition, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## webReportStr
Validates that the specified web report exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webReportStr(str name)

### Parameters

| Parameter | Description                             |
|-----------|-----------------------------------------|
| name      | The name of the web report to validate. |

### Return Value

The name of the specified web report, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
        s = webReportStr(EPCSSSalesConfirm);
        print "String for web report EPCSSalesConfirm is " + s;
        pause;
    }

## websiteDefStr
Validates that the specified web-site definition exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str websiteDefStr(str resourcename)

### Parameters

| Parameter    | Description                                      |
|--------------|--------------------------------------------------|
| resourcename | The name of the Web site definition to validate. |

### Return Value

The name of the specified web-site definition, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
     
        s = websiteDefStr(AxSiteDef_1033_xip);
        print "string for web site definition AxSiteDef_1033_xip is " + s;
        pause;
    }

## webSiteTempStr
Validates that the specified web-site template exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str websiteTempStr(str resourcename)

### Parameters

| Parameter    | Description                                    |
|--------------|------------------------------------------------|
| resourcename | The name of the Web site template to validate. |

### Return Value

The name of the specified web-site template, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    No example.

## webStaticFileStr
Validates that the specified web static file exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webStaticFileStr(str pagename)

### Parameters

| Parameter | Description                                  |
|-----------|----------------------------------------------|
| pagename  | The name of the web static file to validate. |

### Return Value

The name of the specified web static file, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
     
        s = webStaticFileStr(AXEP);
        print "string for web static file AXEP is " + s;
        pause;
    }

## webUrlItemStr
Validates that the specified web URL item exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webUrlItemStr(class weburlitem)

### Parameters

| Parameter  | Description                               |
|------------|-------------------------------------------|
| weburlitem | The name of the web URL item to validate. |

### Return Value

The name of the specified web URL item, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
     
        s = webUrlItemStr(EPAdmin);
        print "string for web url item EPAdmin is " + s;
        pause;
    }

## webWebPartStr
Validates that the specified web part exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str webWebpartStr(str resourcename)

### Parameters

| Parameter    | Description                           |
|--------------|---------------------------------------|
| resourcename | The name of the web part to validate. |

### Return Value

The name of the specified web part, if it is valid.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    {
        str s;
        ;
     
        s = webWebpartStr(AxWebParts_cab);
        print "string for web part AxWebParts_cab is " + s;
        pause;
    }

## workflowApprovalStr
Retrieves the name of a workflow approval in the Application Object Tree (Application Explorer) as a string.

### Syntax

    str workflowapprovalstr(approval approval)

### Parameters

| Parameter | Description                                             |
|-----------|---------------------------------------------------------|
| approval  | The Application Explorer name of the workflow approval. |

### Return Value

A string that represents the Application Explorer name of the workflow approval.

### Remarks

Use this function instead of literal text to retrieve a string that contains the workflow approval name. If the workflow approval does not exist, the function generates a syntax error at compile time. This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following code example sets the variable *str s* to **MyWorkflowApproval** which is the name of the workflow approval in the Application Explorer.

    static void MyWorkflowApprovalStrExample(Args _args)
    {
        str s;
        ;
        s = workflowapprovalstr(MyWorkflowApproval);
        print s;
        pause;
    }

## workflowCategoryStr
Retrieves the name of a workflow category in the Application Object Tree (Application Explorer) as a string.

### Syntax

    str workflowcategorystr(category category)

### Parameters

| Parameter | Description                                             |
|-----------|---------------------------------------------------------|
| category  | The Application Explorer name of the workflow category. |

### Return Value

A string that represents the Application Explorer name of the workflow category.

### Remarks

Use this function instead of literal text to retrieve a string that contains the workflow category name. If the workflow category does not exist, the function generates a syntax error at compile time. This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following code example sets the variable *str s* to **MyWorkflowCategory** which is the name of the workflow category in the Application Explorer.

    static void MyWorkflowCategoryStrExample(Args _args)
    {
        str s;
        ;
        s = workflowcategorystr(MyWorkflowCategory);
        print s;
        pause;
    }

## workflowTaskStr
Retrieves the name of a workflow task in the Application Object Tree (Application Explorer) as a string.

### Syntax

    str workflowtaskstr(task task)

### Parameters

| Parameter | Description                                         |
|-----------|-----------------------------------------------------|
| task      | The Application Explorer name of the workflow task. |

### Return Value

A string that represents the Application Explorer name of the workflow task.

### Remarks

Use this function instead of literal text to retrieve a string that contains the workflow task name. If the workflow task does not exist, the function generates a syntax error at compile time. This is a compile-time function. For more information, see [Overview](#overview).

### Example

The following code example sets the variable *str s* to **MyWorkflowTask** which is the name of the workflow task in the Application Explorer.

    static void MyWorkflowTaskStrExample(Args _args)
    {
        str s;
        ;
        s = workflowtaskstr(MyWorkflowTask);
        print s;
        pause;
    }

## workflowTypeStr
Validates that the specified workflow type exists in the Application Explorer; if it does not, a compiler error occurs.

### Syntax

    str workflowTypeStr(str workflow)

### Parameters

| Parameter | Description                                |
|-----------|--------------------------------------------|
| workflow  | The name of the workflow type to validate. |

### Return Value

The name of the workflow type.

### Remarks

This is a compile-time function. For more information, see [Overview](#overview).

### Example

    static void workFlowTypeStrExample(Args _args)
    {
        str s;
        ;
        s = workFlowTypeStr(BudgetAccountEntryType);
        print s;
        pause;
    }

