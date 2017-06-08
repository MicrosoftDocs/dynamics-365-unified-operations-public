---
# required metadata

title: X++ reflection run-time functions
description: This topic describes the reflection run-time functions.
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
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31381
ms.assetid: d0d4043e-5abb-42ae-bcc2-c6b678f4ef5b
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ reflection run-time functions

[!include[banner](../includes/banner.md)]


This topic describes the reflection run-time functions.

classIdGet
----------

Retrieves the numeric identifier (the class ID) of the class that the object that is initialized belongs to.

    int classIdGet(class object)

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| object    | The object to get the class ID for. |

### Return value

The class ID of the specified object.

### Example

    static void classIdGetExample(Args _args)
    {
            int i;
            WorkTimeCheck w;

            i = classIdGet(w);
            print "Class ID for object is " + int2Str(i);
    }

## dimOf
Retrieves the number of index elements that space has been allocated for in an X++ array.

    int dimOf(anytype object)

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| object    | The array to determine the dimension size of. |

### Return value

If the value of the *object* parameter is an array, the number of elements in the array; otherwise, **0** (zero).

### Remarks

The **dimOf** function is intended for X++ arrays that are declared as the following X++ primitive types:

-   boolean
-   date
-   int
-   int64
-   real
-   utcDateTime

An example is **int iAmounts\[6\];**. Arrays of enumeration values and extended data types are also supported if they are ultimately based on one of the preceding primitive data types (such as **int**). The **dimOf** function doesn't accept arrays of all X++ primitive types. Here are the array types that the **dimOf** function doesn't accept:

-   **str**
-   **container**
-   **anytype**
-   Arrays of class objects
-   Instances of the **Array** class

### Example

    static void JobDimOfArrays(Args _args)
    {
            int iAmounts[20], iCounts[];
            ABCModel enumAbcModel[22]; // Enum
            ABCModelType exdtAbcModelType[24]; // Extended data type
            anytype anyThings[26];
            str sNames[28];
            Array myArrayObj; // Class

            info("Start of job.");
            info("--(Next, normal int array, dimOf() accepts it.)");
            info(int2Str(dimOf(iAmounts)));
            info("--(Next, normal enum array, dimOf() accepts it.)");
            info(int2Str(dimOf(enumAbcModel)));
            info("--(Next, normal extended data type array (based on enum), dimOf() accepts it.)");
            info(int2Str(dimOf(exdtAbcModelType)));
            info("--(Next, dynamic int array, dimension not yet set.)");
            info(int2Str(dimOf(iCounts)));
            info("--(Next, dynamic int array, after dimension established.)");
            
            iCounts[13] = 13;
            info(int2Str(dimOf(iCounts)));
            info(" == == == == == (Next, array types that dimOf() does not support.)");
            info("--(Next, normal anytype array, dimOf() always returns 0.)");
            info(int2Str(dimOf(anyThings)));
            info("--(Next, an instance of class X++ Array, dimOf() always returns 0.)");

            myArrayObj = new Array(Types::Integer);
            myArrayObj.value(1,501);
            info(int2Str(dimOf(myArrayObj)));
            info("--(Next, the lastIndex method provides size information about Array instances.)");
            info(int2Str(myArrayObj.lastIndex()));
            info("--(Next, normal str array, dimOf() does not accept it, job is halted.)");
            info(int2Str(dimOf(sNames)));
            info("End of job.");

    }
    /************  Actual Infolog output
    Message (11:10:06 am)
    Start of job.
    --(Next, normal int array, dimOf() accepts it.)
    20
    --(Next, normal enum array, dimOf() accepts it.)
    22
    --(Next, normal extended data type array (based on enum), dimOf() accepts it.)
    24
    --(Next, dynamic int array, dimension not yet set.)
    0
    --(Next, dynamic int array, after dimension established.)
    16
    == == == == == (Next, array types that dimOf() does not support.)
    --(Next, normal anytype array, dimOf() always returns 0.)
    0
    --(Next, an instance of class X++ Array, dimOf() always returns 0.)
    0
    --(Next, the lastIndex method provides size information about Array instances.)
    1
    --(Next, normal str array, dimOf() does not accept it, job is halted.)
    Error executing code: Illegal operation on this type of array. (C)JobsJobDimOfArrays - line 41
    ************/
    /***********  Pop-up error dialog box
    "Internal error number 25 in script."
    This error is caused by the code line...
    info(int2Str(dimOf(iCounts)));
    ...before iCounts was assigned at any index.
    ***********/

## fieldId2Name
Retrieves a string that represents the name of the field that is specified by a table ID number and a field ID number.

    str fieldId2Name(int tableid, int fieldid)

### Parameters

| Parameter | Description                                                                                           |
|-----------|-------------------------------------------------------------------------------------------------------|
| tableid   | The ID number of the table. **Note:** Use the **tableName2Id** function to specify the ID of a table. |
| fieldid   | The ID number of the field.                                                                           |

### Return value

The name of the field.

### Remarks

To return a printable version of the field name, use the **fieldId2PName** function.

### Example

The following example sets **fn** to the name of the field in the Customer (CustGroup) table that has a field ID of 7.

    static void fieldId2NameExample(Args _arg)
    {
            str fn;
            fn = fieldId2Name(tableName2Id("Customer"),7);
    }

## fieldId2PName
Retrieves the printable name of the field that is specified by a table ID number and a field ID number.

    str fieldId2PName(int tableid, int fieldid)

### Parameters

| Parameter | Description                                                                                           |
|-----------|-------------------------------------------------------------------------------------------------------|
| tableid   | The ID number of the table. **Note:** Use the **tableName2Id** function to specify the ID of a table. |
| fieldid   | The ID number of the field. **Note:** Use the **fieldName2Id** function to specify the ID of a field. |

### Return value

The name of the field.

### Example

    static void fieldId2PNameExample(Args _arg)
    {
            str name;
            tableid _tableId;
            fieldid _fieldid;

            _tableId = tableName2Id("Address");
            _fieldId = fieldName2Id(_tableId, "Name");
            name = fieldId2PName(_tableId, _fieldid);
            print name;
    }

## fieldName2Id
Retrieves the field ID of the table field that is specified by a table ID number and a field ID number.

    int fieldName2Id(int tableid, str fieldname)

### Parameters

| Parameter | Description                                                                                           |
|-----------|-------------------------------------------------------------------------------------------------------|
| tableid   | The ID number of the table. **Note:** Use the **tableName2Id** function to specify the ID of a table. |
| fieldname | The name of the field.                                                                                |

### Return value

The ID of the field that is specified by the *tableid* and *fieldname* parameters.

### Example

    static void fieldName2IdExample(Args _arg)
    {
            int id;

            id = fieldName2Id(tableName2Id("Address"), "Name");
            // Returns 6. Name is the 6th field in the Address table.
            print id;
    }

## indexId2Name
Retrieves the name of an index.

    str indexId2Name(int tableid, int indexid)

### Parameters

| Parameter | Description                                    |
|-----------|------------------------------------------------|
| tableid   | The ID of the table that the index belongs to. |
| indexid   | The ID of the index.                           |

### Return value

The name of the index.

### Example

    static void indexId2NameExample(Args _arg)
    {
            str s;
            tableid id;
            indexid idx;

            id  = tableName2Id("Address");
            idx = indexName2Id(id, "AddrIdx");
            s = indexId2Name(id, idx);
            print "The result of calling indexId2Name is " + s;
    }

## indexName2Id
Retrieves the ID of an index.

    int indexName2Id(int tableid, str indexname)

### Parameters

| Parameter | Description                                    |
|-----------|------------------------------------------------|
| tableid   | The ID of the table that the index belongs to. |
| indexname | The name of the index.                         |

### Return value

The ID of the index.

### Example

    static void indexName2IdExample(Args _arg)
    {
            indexid idx;
            tableid id;

            id  = tableName2Id("Address");
            idx = indexName2Id(id, "AddrIdx");
            print "Index ID for index name AddrIdx of table Address is " + int2Str(idx);
    }

## refPrintAll (no content)
Summary

    void refPrintAll(class object, str filename, str title)

### Parameters

| Parameter | Description |
|-----------|-------------|
| object    | Description |
| filename  | Description |
| title     | Description |

## tableId2Name
Retrieves a string that contains the name of a table.

    str tableId2Name(int _tableid)

### Parameters

| Parameter | Description          |
|-----------|----------------------|
| \_tableid | The ID of the table. |

### Return value

The name of the table.

### Example

    static void tableId2NameExample(Args _arg)
    {
            str s;
            tableid id;

            // Get the ID for table name Address.
            id = tableName2Id("Address");
            print "ID for table name Address is " + int2Str(id);

            // Get the name from the table ID.
            s = tableId2Name(id);
            print "Name for table ID " + int2Str(id) + " is " + s;

            // Get the printable name from the table ID.
            s = tableId2PName(id);
            print "Printable name for table ID " + int2Str(id) + " is " + s;
    }

## tableId2PName
Retrieves a string that contains the printable name (the label) of a table.

    str tableId2PName(int _fieldid)

### Parameters

| Parameter | Description          |
|-----------|----------------------|
| \_fieldid | The ID of the table. |

### Return value

The label of the table.

### Example

    static void tableId2NameExample(Args _arg)
    {
            str s;
            tableid id;

            // Get the ID for table name Address.
            id = tableName2Id("Address");
            print "ID for table name Address is " + int2Str(id);

            // Get the name from the table ID.
            s = tableId2Name(id);
            print "Name for table ID " + int2Str(id) + " is " + s;

            // Get the printable name from the table ID.
            s = tableId2PName(id);
            print "Printable name for table ID " + int2Str(id) + " is " + s;
    }

## tableName2Id
Retrieves the ID of a table.

    int tableName2Id(str _name)

### Parameters

| Parameter | Description            |
|-----------|------------------------|
| \_name    | The name of the table. |

### Return value

The ID of the table.

### Example

    static void tableName2IdExample(Args _arg)
    {
            str s;
            tableid id;

            // Get the ID for the Address table name.
            id = tableName2Id("Address");
            print "ID for the Address table name is " + int2Str(id);

            // Get the name from the table ID.
            s = tableId2Name(id);
            print "Name for table ID " + int2Str(id) + " is " + s;

            // Get the printable name from the table ID.
            s = tableId2PName(id);
            print "Printable name for table ID " + int2Str(id) + " is " + s;
    }

## typeOf
Retrieves the type of an element.

    enum typeOf(anytype _object)

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| \_object  | The element to return the type for. |

### Return value

A **Types** system enumeration value.

### Example

The following example tests whether the first element in a container, **c**, is another container that contains a single integer.

    if(typeof(conpeek(c, 1)) != Types::Container ||
    conlen(conpeek(c, 1)) != 1 ||
    typeof(conpeek(conpeek(c, 1), 1)) != Types::Integer)
    {
            // More code.
    }



