---
title: QueryRun class
description: This topic describes the QueryRun class.
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

# Class QueryRun

[!include [banner](../../includes/banner.md)]

```xpp
class QueryRun extends ObjectRun
```

The QueryRun class traverses tables in the database, fetches records that satisfy constraints that are given by the user, and helps to gather such constraints from user input.

## Remarks

QueryRun objects are used to traverse tables in the database and fetch records that satisfy the constraints that are given by the user. A QueryRun object may interact with the user to let the user enter such constraints. Queries are used internally by reports to delineate and fetch the data to be presented in the report. A QueryRun object relies on a Query object to define the structure of the query (for example, which tables are searched and how the records are sorted). A QueryRun object defines the dynamic behavior of the query, whereas a Query object defines the static characteristics of the query.

## Examples

In the following example, it is assumed that there is a query named Customer in the Application Object Tree (AOT), and that it has one data source, the CustTable table.

```xpp
static void example() 
{ 
    // Create a QueryRun object from a query stored in the AOT. 
    QueryRun qr = new QueryRun ("Customer"); 
    CustTable customerRecord; 
    // Display a window enabling the user to choose which records to print. 
    if (qr.prompt()) 
    { 
        // The user clicked OK. 
        while (qr.next()) 
        { 
            // Get the fetched record. 
            CustomerRecord = qr.GetNo(1); 
            // Do something with it 
            print CustomerRecord.AccountNum; 
        } 
    } 
    else 
    { 
        // The user pressed Cancel, so do nothing. 
    } 
}
```

## Methods

| Method                                                                                                         | Description                                                                                                                               |
|----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean allowCheck(\[boolean value\])                                                                   |                                                                                                                                           |
| public boolean allowCrossCompany(\[boolean value\])                                                            |                                                                                                                                           |
| public boolean canPage(\[boolean skipOrderByCheck\], \[boolean throwIfNotPagable\], \[boolean isValuePaging\]) |                                                                                                                                           |
| public boolean changed(TableId table, \[int occurrence\])                                                      | Determines whether the specified data source has fetched a new value since the last call to the QueryRun.next method.                     |
| public str changedBy(\[str value\])                                                                            | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])                                                                        | Gets or sets the date an application object was last changed.                                                                             |
| public boolean changedNo(int dataSourceNo)                                                                     |                                                                                                                                           |
| public str changedTime(\[str value\])                                                                          | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])                                                                            | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])                                                                       | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                                                                         |                                                                                                                                           |
| public str description(\[str value\])                                                                          |                                                                                                                                           |
| public boolean equal(Object obj)                                                                               | Determines whether the specified object is equal to the current object.                                                                   |
| public str form(\[str value\])                                                                                 |                                                                                                                                           |
| public Common get(TableId table, \[int occurrence\])                                                           | Retrieves the record fetched by the previous call to next method.                                                                         |
| public System.Type getImpExpDataContractType()                                                                 |                                                                                                                                           |
| public Common getNo(int dataSourceNo)                                                                          | Retrieves the record fetched by the previous call to QueryRun.next Method.                                                                |
| public boolean importable()                                                                                    |                                                                                                                                           |
| public boolean interactive(\[boolean value\])                                                                  |                                                                                                                                           |
| public boolean isPositionPagingEnabled()                                                                       |                                                                                                                                           |
| public boolean isQueryTimedout()                                                                               |                                                                                                                                           |
| public boolean isValueBasedPagingEnabled()                                                                     |                                                                                                                                           |
| public int literals(\[int value\])                                                                             |                                                                                                                                           |
| public Guid loadCsv(str fileName)                                                                              |                                                                                                                                           |
| public Guid loadXml(str fileName)                                                                              |                                                                                                                                           |
| public str name(\[str value\])                                                                                 | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public QueryRun newObject(AnyType source)                                                                      |                                                                                                                                           |
| public boolean next()                                                                                          | Retrieves the next record from the query.                                                                                                 |
| public int nextUniqueId(\[int value\])                                                                         |                                                                                                                                           |
| public Guid origin(\[Guid value\])                                                                             |                                                                                                                                           |
| public container pack(\[boolean doCheck\])                                                                     |                                                                                                                                           |
| public boolean prompt()                                                                                        | Presents, to the user, the options for defining the records to be fetched by the query.                                                   |
| public Query query(\[Query query\])                                                                            |                                                                                                                                           |
| public int queryType(\[int value\])                                                                            |                                                                                                                                           |
| public boolean recordLevelSecurity(\[boolean value\])                                                          |                                                                                                                                           |
| public ReportRun report()                                                                                      |                                                                                                                                           |
| public ReportRun reportRun()                                                                                   |                                                                                                                                           |
| public boolean saved()                                                                                         |                                                                                                                                           |
| public boolean saveUserSetup(\[boolean saveIt\])                                                               | Saves the user setup.                                                                                                                     |
| public boolean searchable(\[boolean value\])                                                                   |                                                                                                                                           |
| public boolean setCursor(Common record, \[int occurrence\])                                                    |                                                                                                                                           |
| public boolean setRecord(Common record, \[int occurrence\])                                                    |                                                                                                                                           |
| public str title(\[str value\])                                                                                |                                                                                                                                           |
| public str toString()                                                                                          | Returns a string that represents the current object.                                                                                      |
| public boolean userUpdate(\[boolean value\])                                                                   |                                                                                                                                           |
| public int version(\[int value\])                                                                              |                                                                                                                                           |
| ::public static int getQueryRowCount(Query query, int maxRows)                                                 |                                                                                                                                           |
| ::public static int runAndPopulate(Query sourceRuery, Common targetTable, Map queryAliasesAndTargetColumnsMap) |                                                                                                                                           |
| public void run()                                                                                              | Opens a form used to obtain information about the query from the user, and fetches the matching records.                                  |
| public void new(AnyType source)                                                                                | Initializes a new instance of the Object class.                                                                                           |
| public void addPageRange(\[Int64 startingPosition\], \[Int64 numberOfRecordsToFetch\])                         |                                                                                                                                           |
| public void reset()                                                                                            |                                                                                                                                           |
| public void setImportSession(Guid importSession)                                                               |                                                                                                                                           |
| public void setQuerytimeout(int seconds, \[boolean raiseException\])                                           |                                                                                                                                           |
| public void init()                                                                                             |                                                                                                                                           |
| public void enablePositionPaging(\[boolean enabled\])                                                          |                                                                                                                                           |
| public void shred(Guid importSession)                                                                          |                                                                                                                                           |
| public void enableValueBasedPaging(\[boolean enable\])                                                         |                                                                                                                                           |
| public void bulkNext(\[boolean fetchAllData\])                                                                 |                                                                                                                                           |
| public void applyValueBasedPaging(\[Common sourceCursor\], \[boolean isForward\])                              |                                                                                                                                           |

## Method allowCheck

```xpp
public boolean allowCheck([boolean value])
```

### Parameters - allowCheck

value  

### Return Value - allowCheck

## Method allowCrossCompany

```xpp
public boolean allowCrossCompany([boolean value])
```

### Parameters - allowCrossCompany

value  

### Return Value - allowCrossCompany

## Method canPage

```xpp
public boolean canPage([boolean skipOrderByCheck], [boolean throwIfNotPagable], [boolean isValuePaging])
```

### Parameters - canPage

skipOrderByCheck  

<!-- -->

throwIfNotPagable  

<!-- -->

isValuePaging  

### Return Value - canPage

## Method changed

Determines whether the specified data source has fetched a new value since the last call to the QueryRun.next method.

```xpp
public boolean changed(TableId table, [int occurrence])
```

### Parameters - changed

table  
The data source to check; optional. If more than one data source is assigned to a given table, this argument can be used to determine which data source to check.

<!-- -->

occurrence  
The data source to check; optional. If more than one data source is assigned to a given table, this argument can be used to determine which data source to check.

### Return Value - changed

true if the specified data source has changed since the last call to QueryRun.next; otherwise, false.

### Remarks - changed

This method is useful when data sources are hierarchically structured. A more embedded data source may change many times (such as the customer transactions). This occurs every time that a less embedded data source (such as the customer table) fetches a new record (another customer). The changedNo method can be used instead of this function.

## Method changedBy

Gets or sets the name of the user who last changed the application object.

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  

### Return Value - changedBy

The name of the user.

## Method changedDate

Gets or sets the date an application object was last changed.

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  

### Return Value - changedDate

The date an application object was last changed.

## Method changedNo

```xpp
public boolean changedNo(int dataSourceNo)
```

### Parameters - changedNo

dataSourceNo  

### Return Value - changedNo

## Method changedTime

Gets or sets the time an application object was last changed.

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  

### Return Value - changedTime

The time an application object was last changed.

## Method createdBy

Gets or sets the name of the user who created the application object.

```xpp
public str createdBy([str value])
```

### Parameters - createdBy

value  

### Return Value - createdBy

The name of the user.

## Method creationDate

Gets or sets the date an application object was created.

```xpp
public Date creationDate([Date value])
```

### Parameters - creationDate

value  

### Return Value - creationDate

The date an application object was created.

## Method creationTime

```xpp
public str creationTime([str value])
```

### Parameters - creationTime

value  

### Return Value - creationTime

## Method description

```xpp
public str description([str value])
```

### Parameters - description

value  

### Return Value - description

## Method equal

Determines whether the specified object is equal to the current object.

```xpp
public boolean equal(Object obj)
```

### Parameters - equal

obj  

### Return Value - equal

true if the specified object is equal to the current object; otherwise, false.

### Remarks - equal

The default implementation of the Object::equal method supports only reference equality. However, derived classes can override the Object::equal method to support value equality.

## Method form

```xpp
public str form([str value])
```

### Parameters - form

value  

### Return Value - form

## Method get

Retrieves the record fetched by the previous call to next method.

```xpp
public Common get(TableId table, [int occurrence])
```

### Parameters - get

table  
The data source to be addressed; optional. The number of the data source with the given table; 1-based. If more than one data source has the same table assigned to it, this (optional) parameter can be used to specify which one is to be addressed. It specifies the number of the data source with the given table. Thus, if the CustTable table is assigned to two data sources, and the second data source is required, this argument should have the value 2.

<!-- -->

occurrence  
The data source to be addressed; optional. The number of the data source with the given table; 1-based. If more than one data source has the same table assigned to it, this (optional) parameter can be used to specify which one is to be addressed. It specifies the number of the data source with the given table. Thus, if the CustTable table is assigned to two data sources, and the second data source is required, this argument should have the value 2.

### Return Value - get

Returns the record fetched from the data source identified by the arguments.

### Remarks - get

The data source from which to retrieve the record is specified by the table assigned to the data source and by an optional parameter. Instead of supplying the table (and optional parameter), you can use the getNo method, which takes the data source number as an argument.

## Method getImpExpDataContractType

```xpp
public System.Type getImpExpDataContractType()
```

### Return Value - getImpExpDataContractType

## Method getNo

Retrieves the record fetched by the previous call to QueryRun.next Method.

```xpp
public Common getNo(int dataSourceNo)
```

### Parameters - getNo

dataSourceNo  
The number of the data source from which to get the currently selected record.

### Return Value - getNo

Returns the record fetched for the data source identified by the argument.

### Remarks - getNo

The data source from which to retrieve the record is specified by the number of the data source. The data sources are counted consecutively, starting from 1. The QueryRun.get Method method can be used instead; that method is supplied with the table (and an optional parameter), that defines the data source.

### Examples - getNo

```xpp
{ 
    QueryRun qr; 
    // Consider a query with CustTable/CustTrans datasources. 
    // Traverse all records found in CustTable/CustTrans: 
    while (qr.next()) 
    { 
        if (qr.Changed(TableNum(CustTable)))
        { 
            // A new CustTable record 
            CustTableRecord = qr.GetNo(1); 
        } 
        if (qr.Changed(TableNum(CustTrans))) 
        { 
            // A new CustTrans record 
            CustTransRecord = qr.GetNo(1); 
        } 
    } 
}
```

## Method importable

```xpp
public boolean importable()
```

### Return Value - importable

## Method interactive

```xpp
public boolean interactive([boolean value])
```

### Parameters - interactive

value  

### Return Value - interactive

## Method isPositionPagingEnabled

```xpp
public boolean isPositionPagingEnabled()
```

### Return Value - isPositionPagingEnabled

## Method isQueryTimedout

```xpp
public boolean isQueryTimedout()
```

### Return Value - isQueryTimedout

## Method isValueBasedPagingEnabled

```xpp
public boolean isValueBasedPagingEnabled()
```

### Return Value - isValueBasedPagingEnabled

## Method literals

```xpp
public int literals([int value])
```

### Parameters - literals

value  

### Return Value - literals

## Method loadCsv

```xpp
public Guid loadCsv(str fileName)
```

### Parameters - loadCsv

fileName  

### Return Value - loadCsv

## Method loadXml

```xpp
public Guid loadXml(str fileName)
```

### Parameters - loadXml

fileName  

### Return Value - loadXml

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, or classes.

## Method newObject

```xpp
public QueryRun newObject(AnyType source)
```

### Parameters - newObject

source  

### Return Value - newObject

## Method next

Retrieves the next record from the query.

```xpp
public boolean next()
```

### Return Value - next

true if the next record is available and can be fetched with the getNo method or get method; false if no there are no more records that satisfy the constraint set up in the query.

### Remarks - next

The changed method or changedNo method can be used to check whether the record from the given data source has changed since the previous call to the next method.

### Examples - next

```xpp
{ 
    queryRun qr; 
    CustTable ct; 
    // ... 
    if (qr.prompt()) 
    { 
        while (qr.next()) 
        { 
            if (qr.Changed(tableNum(CustTable))) 
            { 
                ct = qr.Get (tableNum(CustTable)); 
                print ct.AccountNum; 
            } 
        } 
    } 
}
```

## Method nextUniqueId

```xpp
public int nextUniqueId([int value])
```

### Parameters - nextUniqueId

value  

### Return Value - nextUniqueId

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method pack

```xpp
public container pack([boolean doCheck])
```

### Parameters - pack

doCheck  

### Return Value - pack

## Method prompt

Presents, to the user, the options for defining the records to be fetched by the query.

```xpp
public boolean prompt()
```

### Return Value - prompt

true if the user clicked OK and the search is to continue; false if the user clicked Cancel to stop the search.

### Remarks - prompt

The user is presented with a form to give ranges that define constraints to be fulfilled by the fetched records. Or the user may add new fields to delimit, change the sorting, and so on. This method can be overloaded to prompt the user in an application-defined way instead of in through the predefined query form. Or this method can be overloaded to avoid giving the user control over which records are fetched. To produce these results, do not call the inherited method. In any case, the function should return true if the query is to continue, and false otherwise.

### Examples - prompt

```xpp
{ 
    QueryRun qr; 
    // ... 
    if (qr.prompt()) 
    { 
        // The user pressed OK. Go ahead and do whatever is required. 
    } 
    else 
    { 
        // The user pressed Cancel. 
    } 
}
```

## Method query

```xpp
public Query query([Query query])
```

### Parameters - query

query  

### Return Value - query

## Method queryType

```xpp
public int queryType([int value])
```

### Parameters - queryType

value  

### Return Value - queryType

## Method recordLevelSecurity

```xpp
public boolean recordLevelSecurity([boolean value])
```

### Parameters - recordLevelSecurity

value  

### Return Value - recordLevelSecurity

## Method report

```xpp
public ReportRun report()
```

### Return Value - report

## Method reportRun

```xpp
public ReportRun reportRun()
```

### Return Value - reportRun

## Method saved

```xpp
public boolean saved()
```

### Return Value - saved

## Method saveUserSetup

Saves the user setup.

```xpp
public boolean saveUserSetup([boolean saveIt])
```

### Parameters - saveUserSetup

saveIt  

### Return Value - saveUserSetup

true if the setup was successfully saved; otherwise false.

## Method searchable

```xpp
public boolean searchable([boolean value])
```

### Parameters - searchable

value  

### Return Value - searchable

## Method setCursor

```xpp
public boolean setCursor(Common record, [int occurrence])
```

### Parameters - setCursor

record  

<!-- -->

occurrence  

### Return Value - setCursor

## Method setRecord

```xpp
public boolean setRecord(Common record, [int occurrence])
```

### Parameters - setRecord

record  

<!-- -->

occurrence  

### Return Value - setRecord

## Method title

```xpp
public str title([str value])
```

### Parameters - title

value  

### Return Value - title

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method userUpdate

```xpp
public boolean userUpdate([boolean value])
```

### Parameters - userUpdate

value  

### Return Value - userUpdate

## Method version

```xpp
public int version([int value])
```

### Parameters - version

value  

### Return Value - version

## Method getQueryRowCount

```xpp
public static int getQueryRowCount(Query query, int maxRows)
```

### Parameters - getQueryRowCount

query  

<!-- -->

maxRows  

### Return Value - getQueryRowCount

## Method runAndPopulate

```xpp
public static int runAndPopulate(Query sourceRuery, Common targetTable, Map queryAliasesAndTargetColumnsMap)
```

### Parameters - runAndPopulate

sourceRuery  

<!-- -->

targetTable  

<!-- -->

queryAliasesAndTargetColumnsMap  

### Return Value - runAndPopulate

## Method run

Opens a form used to obtain information about the query from the user, and fetches the matching records.

```xpp
public void run()
```

### Remarks - run

Running the query will find the records that satisfy the constraints entered by the user. However, running the query in this manner has no side effects. In order to be useful, one or more of the inherited methods must be overloaded.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(AnyType source)
```

### Parameters - new

source  

### Remarks - new

When you pass an instance of the Query class into this constructor of the QueryRun class, a copy of the Query object is created. Changes that are made to this copy of the Query object do not affect the original Query object.

## Method addPageRange

```xpp
public void addPageRange([Int64 startingPosition], [Int64 numberOfRecordsToFetch])
```

### Parameters - addPageRange

startingPosition  

<!-- -->

numberOfRecordsToFetch  

## Method reset

```xpp
public void reset()
```

## Method setImportSession

```xpp
public void setImportSession(Guid importSession)
```

### Parameters - setImportSession

importSession  

## Method setQuerytimeout

```xpp
public void setQuerytimeout(int seconds, [boolean raiseException])
```

### Parameters - setQuerytimeout

seconds  

<!-- -->

raiseException  

## Method init

```xpp
public void init()
```

## Method enablePositionPaging

```xpp
public void enablePositionPaging([boolean enabled])
```

### Parameters - enablePositionPaging

enabled  

## Method shred

```xpp
public void shred(Guid importSession)
```

### Parameters - shred

importSession  

## Method enableValueBasedPaging

```xpp
public void enableValueBasedPaging([boolean enable])
```

### Parameters - enableValueBasedPaging

enable  

## Method bulkNext

```xpp
public void bulkNext([boolean fetchAllData])
```

### Parameters - bulkNext

fetchAllData  

## Method applyValueBasedPaging

```xpp
public void applyValueBasedPaging([Common sourceCursor], [boolean isForward])
```

### Parameters - applyValueBasedPaging

sourceCursor  

<!-- -->

isForward  

## Method skipAutoOrderBy

```xpp
Specifies whether an Order By clause will be generated, in case no Order By field was specified.
public boolean skipAutoOrderBy([boolean value])

```

Value
### Return Value - skipAutoOrderBy
The current value if no parameter is specified, the new value if a parameter was specified.
### Remarks - skipAutoOrderBy
SkipAutoOrderBy is false by default and available in Platform update 31 and later
