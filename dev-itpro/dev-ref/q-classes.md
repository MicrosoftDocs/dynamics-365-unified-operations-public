---
# required metadata

title: Q Classes
description: System API classes that start with the letter Q.
author: RobinARH
manager: AnnBe
ms.date: 2017-04-04
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
ms.custom: 51831
ms.assetid: 279efb4c-e228-4ab5-be7d-c96d91064787
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Q Classes

System API classes that start with the letter Q.

Class Query
-----------

    class Query extends TreeNode

The Query class embodies the structure of a query.

### Remarks

Objects of this kind are not used to fetch records from the database. Instead, use a QueryRun object that can be assigned a query object. The dynamic behavior of a query is defined by the QueryRun class. The static behavior is defined by the Query class. Queries contain one or more data sources that correspond to tables in the database. The data sources are specified by using QueryBuildDataSource objects. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. Queries are used when the user wants to modify the records that are fetched by, for example, a form. One or more ranges are often added to an existing data source. Ranges are specified by using queryBuildRange objects.

### Examples

The following example creates a query object that is used to create a QueryRun object.

    { 
        Query q = new Query (QueryStr(Cust)); 
        // Use the query to build a queryRun object. 
        QueryRun qr = new QueryRun (q); 
        // Traverse some records. 
        while (qr.next()) 
        { 
            // ... 
        } 
    }

### Methods

| Method                                                                                                                                                                 | Description                                                                                                                               |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public Query addBaseQuery(str queryName)                                                                                                                               |                                                                                                                                           |
| public QueryBuildDataSource addDataSource(TableId table, \[str name\], \[UnionType unionType\], \[boolean emptyFieldList\])                                            | Adds a data source to the top level of the query.                                                                                         |
| public QueryHavingFilter addHavingFilter(QueryBuildDataSource dataSource, str fieldName, AggregateFunction aggregateFunction, \[int arrayIndex\])                      |                                                                                                                                           |
| public QueryFilter addQueryFilter(QueryBuildDataSource dataSource, str fieldName, \[int arrayIndex\])                                                                  |                                                                                                                                           |
| public boolean allowCheck(\[boolean value\])                                                                                                                           |                                                                                                                                           |
| public boolean allowCrossCompany(\[boolean value\])                                                                                                                    |                                                                                                                                           |
| public boolean allowHavingFilters(QueryBuildDataSource dataSource, FieldName fieldName, AggregateFunction aggregateFunction)                                           |                                                                                                                                           |
| public boolean allowQueryFilters(QueryBuildDataSource dataSource)                                                                                                      |                                                                                                                                           |
| public str changedBy(\[str value\])                                                                                                                                    | Gets or sets the name of the user who last changed the Query object.                                                                      |
| public Date changedDate(\[Date value\])                                                                                                                                | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])                                                                                                                                  | Gets or sets the time an application object was last changed.                                                                             |
| public int childDataSourceCount()                                                                                                                                      | Counts the number of data sources that are related to the query.                                                                          |
| public QueryBuildDataSource childDataSourceNo(int dataSourceNo)                                                                                                        | Returns the child data source that corresponds to the specified number.                                                                   |
| public boolean containsAggregateFields()                                                                                                                               |                                                                                                                                           |
| public str createdBy(\[str value\])                                                                                                                                    | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])                                                                                                                               | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                                                                                                                                 |                                                                                                                                           |
| public int dataSourceCount()                                                                                                                                           | Returns the total number of data sources for the query, including any embedded data sources.                                              |
| public QueryBuildDataSource dataSourceName(str name)                                                                                                                   | Returns the data source that has the specified name.                                                                                      |
| public QueryBuildDataSource dataSourceNo(int dataSourceNo)                                                                                                             | Returns the data source that is specified by the data source number.                                                                      |
| public QueryBuildDataSource dataSourceTable(TableId table, \[int occurrence\])                                                                                         | Returns the data source that the specified table is assigned to.                                                                          |
| public QueryBuildDataSource dataSourceUniqueId(int uniqueId)                                                                                                           |                                                                                                                                           |
| public str description(\[str value\])                                                                                                                                  |                                                                                                                                           |
| public boolean equal(Object record)                                                                                                                                    | Evaluates whether one query is equal to another.                                                                                          |
| public str exportXML()                                                                                                                                                 |                                                                                                                                           |
| public QueryHavingFilter findHavingFilterByField(QueryBuildDataSource dataSource, FieldName fieldName, \[int occurrence\], \[int arrayIndex\])                         |                                                                                                                                           |
| public QueryFilter findQueryFilter(QueryBuildDataSource dataSource, FieldName fieldName, \[int occurrence\], \[int arrayIndex\])                                       |                                                                                                                                           |
| public QueryBuildDataSource firstTopLevelDataSource()                                                                                                                  |                                                                                                                                           |
| public boolean forceNestedLoop(boolean arg)                                                                                                                            |                                                                                                                                           |
| public boolean forceSelectOrder(boolean arg)                                                                                                                           |                                                                                                                                           |
| public str form(\[str value\])                                                                                                                                         |                                                                                                                                           |
| public container getCompanyRange()                                                                                                                                     |                                                                                                                                           |
| public int getMostRestrictedQueryFilterStatus(QueryBuildDataSource dataSource, FieldName fieldName, \[int fieldId\])                                                   |                                                                                                                                           |
| public int getNextUniqueId()                                                                                                                                           |                                                                                                                                           |
| public str getSQLStatement(\[boolean noRuntimeOptimization\])                                                                                                          |                                                                                                                                           |
| public container getValidTimeStateDateRange()                                                                                                                          |                                                                                                                                           |
| public container getValidTimeStateDateTimeRange()                                                                                                                      |                                                                                                                                           |
| public ValidTimeStateQueryType getValidTimeStateQueryType()                                                                                                            |                                                                                                                                           |
| public QueryGroupByField groupByField(int index, \[QueryBuildDataSource dataSource\])                                                                                  |                                                                                                                                           |
| public int groupByFieldCount(\[QueryBuildDataSource dataSource\])                                                                                                      |                                                                                                                                           |
| public boolean hasMultipleTopLevelDataSource()                                                                                                                         |                                                                                                                                           |
| public boolean hasRangeOrFilter(QueryBuildDataSource dataSource)                                                                                                       |                                                                                                                                           |
| public QueryHavingFilter havingFilter(int count, \[QueryBuildDataSource dataSource\])                                                                                  |                                                                                                                                           |
| public int havingFilterCount(\[QueryBuildDataSource dataSource\])                                                                                                      |                                                                                                                                           |
| public boolean inReport()                                                                                                                                              | Determines whether the query is part of a report.                                                                                         |
| public boolean interactive(\[boolean value\])                                                                                                                          | Specifies whether the query is interactive.                                                                                               |
| public boolean isCompositeQuery()                                                                                                                                      |                                                                                                                                           |
| public boolean isExplicitlyOrdered()                                                                                                                                   |                                                                                                                                           |
| public boolean isExplicitlyGrouped()                                                                                                                                   |                                                                                                                                           |
| public boolean isPureUnionAll()                                                                                                                                        |                                                                                                                                           |
| public boolean isUnionType()                                                                                                                                           |                                                                                                                                           |
| public int levelNo(int dataSourceNo)                                                                                                                                   | Determines the level of indentation of the specified data source.                                                                         |
| public int levelTable(TableId table, \[int occurrence\])                                                                                                               | Determines the tree level, in the hierarchy of data sources, of the data source that is assigned to the specified table.                  |
| public int literals(\[int value\])                                                                                                                                     |                                                                                                                                           |
| public str name(\[str value\])                                                                                                                                         | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public Query newObject(AnyType source)                                                                                                                                 | Creates a query that exists on the same client side or server side as the source query.                                                   |
| public int nextUniqueId(\[int value\])                                                                                                                                 |                                                                                                                                           |
| public QueryOrderByField orderByField(int index, \[QueryBuildDataSource dataSource\])                                                                                  |                                                                                                                                           |
| public int orderByFieldCount(\[QueryBuildDataSource dataSource\])                                                                                                      |                                                                                                                                           |
| public Guid origin(\[Guid value\])                                                                                                                                     |                                                                                                                                           |
| public container pack(\[boolean doCheck\])                                                                                                                             | Packs the query into a container and returns that container, so that it can be used when you create a query.                              |
| public container packInternals()                                                                                                                                       |                                                                                                                                           |
| public QueryFilter queryFilter(int count, \[QueryBuildDataSource rootDataSource\])                                                                                     |                                                                                                                                           |
| public int queryFilterCount(\[QueryBuildDataSource rootDataSource\])                                                                                                   |                                                                                                                                           |
| public int queryType(\[int value\])                                                                                                                                    |                                                                                                                                           |
| public str quickFilterValue()                                                                                                                                          |                                                                                                                                           |
| public int quickFilterControlId()                                                                                                                                      |                                                                                                                                           |
| public boolean recordLevelSecurity(\[boolean value\])                                                                                                                  |                                                                                                                                           |
| public Report report()                                                                                                                                                 | Returns the report in which the query is defined, if the report exists.                                                                   |
| public boolean saved()                                                                                                                                                 | Indicates whether the query has been saved to disk.                                                                                       |
| public boolean searchable(\[boolean value\])                                                                                                                           |                                                                                                                                           |
| public Guid importSession(\[Guid value\])                                                                                                                              |                                                                                                                                           |
| public str title(\[str value\])                                                                                                                                        |                                                                                                                                           |
| public int topRows(\[int value\])                                                                                                                                      |                                                                                                                                           |
| public str toString()                                                                                                                                                  | Returns a string that represents the current object.                                                                                      |
| public boolean userUpdate(\[boolean value\])                                                                                                                           | Gets or sets a value that indicates whether the query can update the records that it fetches.                                             |
| public Date validTimeStateAsOfDate(\[Date asOfDate\])                                                                                                                  |                                                                                                                                           |
| public DateTime validTimeStateAsOfDateTime(\[DateTime asOfDateTime\])                                                                                                  |                                                                                                                                           |
| public int validTimeStateFlags(\[int value\])                                                                                                                          |                                                                                                                                           |
| public int version(\[int value\])                                                                                                                                      |                                                                                                                                           |
| public str xml(\[int indent\])                                                                                                                                         | Returns an XML string that represents the current object.                                                                                 |
| public void clearBaseQueries()                                                                                                                                         |                                                                                                                                           |
| public void addCompanyRange(str companyName)                                                                                                                           |                                                                                                                                           |
| public void checkRangeParsingErrors(boolean setCheckRangeParsingErrors)                                                                                                |                                                                                                                                           |
| public void clearCompanyRange()                                                                                                                                        |                                                                                                                                           |
| public void unpackInternals(container internalData)                                                                                                                    |                                                                                                                                           |
| public void new(\[AnyType source\])                                                                                                                                    | Creates a query object.                                                                                                                   |
| public void checkFieldAccess(boolean setCheckFieldAccess)                                                                                                              |                                                                                                                                           |
| public void useDbCacheOnGeneratedCursors(\[int fetchsize\])                                                                                                            |                                                                                                                                           |
| public void setValidTimeStateQueryType(\[ValidTimeStateQueryType type\])                                                                                               |                                                                                                                                           |
| public void validTimeStateDateRange(\[Date fromDate\], \[Date toDate\])                                                                                                |                                                                                                                                           |
| public void clearHavingFilters(\[QueryBuildDataSource dataSource\], \[str fieldName\], \[int occurence\], \[int arrayIndex\])                                          |                                                                                                                                           |
| public void quickFilter(\[str dataSourceName\], \[int tableId\], \[int fieldId\], \[str filterValue\], \[int controlId\], \[boolean useEqualityComparisonForStrings\]) |                                                                                                                                           |
| public void finalize()                                                                                                                                                 |                                                                                                                                           |
| public void clearQueryFilters(\[QueryBuildDataSource dataSource\], \[str fieldName\], \[int occurence\], \[int arrayIndex\])                                           |                                                                                                                                           |
| public void clearOrderBy()                                                                                                                                             |                                                                                                                                           |
| public void clearAllFields()                                                                                                                                           |                                                                                                                                           |
| public void clearGroupBy()                                                                                                                                             |                                                                                                                                           |
| public void autoAuthzMode(AutoAuthzMode mode)                                                                                                                          |                                                                                                                                           |
| ::public static void insert\_recordset(Common targetCursor, Map targetToSourceMap, Query sourceQuery)                                                                  |                                                                                                                                           |
| public void generateCursors()                                                                                                                                          |                                                                                                                                           |
| public void checkAuthorizationOnOpenRanges(boolean setCheckAuthorizationOnOpenRanges)                                                                                  |                                                                                                                                           |
| public void addContains(str containsValue, \[boolean prefixSearch\])                                                                                                   |                                                                                                                                           |
| public void resetValidTimeStateQueryType()                                                                                                                             |                                                                                                                                           |
| public void validTimeStateDateTimeRange(\[DateTime fromDateTime\], \[DateTime toDateTime\])                                                                            |                                                                                                                                           |

### Method addBaseQuery

    public Query addBaseQuery(str queryName)

#### Parameters

queryName  

#### Return Value

### Method addDataSource

Adds a data source to the top level of the query.

    public QueryBuildDataSource addDataSource(TableId table, [str name], [UnionType unionType], [boolean emptyFieldList])

#### Parameters

table  

<!-- -->

name  

<!-- -->

unionType  

<!-- -->

emptyFieldList  

#### Return Value

The data source object that is created.

#### Remarks

A name value can be specified for documentation purposes. Yo can use the name to fetch the data source by using the dataSourceName method.

### Method addHavingFilter

    public QueryHavingFilter addHavingFilter(QueryBuildDataSource dataSource, str fieldName, AggregateFunction aggregateFunction, [int arrayIndex])

#### Parameters

dataSource  

<!-- -->

fieldName  

<!-- -->

aggregateFunction  

<!-- -->

arrayIndex  

#### Return Value

### Method addQueryFilter

    public QueryFilter addQueryFilter(QueryBuildDataSource dataSource, str fieldName, [int arrayIndex])

#### Parameters

dataSource  

<!-- -->

fieldName  

<!-- -->

arrayIndex  

#### Return Value

### Method allowCheck

    public boolean allowCheck([boolean value])

#### Parameters

value  

#### Return Value

### Method allowCrossCompany

    public boolean allowCrossCompany([boolean value])

#### Parameters

value  

#### Return Value

### Method allowHavingFilters

    public boolean allowHavingFilters(QueryBuildDataSource dataSource, FieldName fieldName, AggregateFunction aggregateFunction)

#### Parameters

dataSource  

<!-- -->

fieldName  

<!-- -->

aggregateFunction  

#### Return Value

### Method allowQueryFilters

    public boolean allowQueryFilters(QueryBuildDataSource dataSource)

#### Parameters

dataSource  

#### Return Value

### Method changedBy

Gets or sets the name of the user who last changed the Query object.

    public str changedBy([str value])

#### Parameters

value  
The name of the user who last changed the Query object; optional.

#### Return Value

The name of the user who last changed the Query object.

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

### Method childDataSourceCount

Counts the number of data sources that are related to the query.

    public int childDataSourceCount()

#### Return Value

The number of data sources that are related to the query.

#### Remarks

This method is used for the top-level query. To determine the number of data sources that are embedded in another data source, use the childDataSourceCount method.

### Method childDataSourceNo

Returns the child data source that corresponds to the specified number.

    public QueryBuildDataSource childDataSourceNo(int dataSourceNo)

#### Parameters

dataSourceNo  
The number of the child data source.

#### Return Value

The child data source that has the specified number.

#### Remarks

The number that is specified must represent a data source that is immediately underneath the query. Typically, there is only one such data source.

### Method containsAggregateFields

    public boolean containsAggregateFields()

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

### Method dataSourceCount

Returns the total number of data sources for the query, including any embedded data sources.

    public int dataSourceCount()

#### Return Value

The number of data sources for this query.

#### Remarks

The number is the transitive number of data sources and includes any embedded data sources.

### Method dataSourceName

Returns the data source that has the specified name.

    public QueryBuildDataSource dataSourceName(str name)

#### Parameters

name  
The string that contains the name of the data source to return.

#### Return Value

The data source that has the specified name; an uninitialized object if the specified data source does not exist.

### Method dataSourceNo

Returns the data source that is specified by the data source number.

    public QueryBuildDataSource dataSourceNo(int dataSourceNo)

#### Parameters

dataSourceNo  
The number of the data source.

#### Return Value

The data source that has the specified number; an uninitialized object if the specified data source does not exist.

### Method dataSourceTable

Returns the data source that the specified table is assigned to.

    public QueryBuildDataSource dataSourceTable(TableId table, [int occurrence])

#### Parameters

table  
An integer that is used when more than one data source uses the specified table ID; optional. The default value is 1, which specifies the first (and typically only) instance.

<!-- -->

occurrence  
An integer that is used when more than one data source uses the specified table ID; optional. The default value is 1, which specifies the first (and typically only) instance.

#### Return Value

The data source that the specified table is assigned to.

#### Remarks

The data source can also be retrieved by calling the dataSourceNo method or the dataSourceName method.

### Method dataSourceUniqueId

    public QueryBuildDataSource dataSourceUniqueId(int uniqueId)

#### Parameters

uniqueId  

#### Return Value

### Method description

    public str description([str value])

#### Parameters

value  

#### Return Value

### Method equal

Evaluates whether one query is equal to another.

    public boolean equal(Object record)

#### Parameters

record  
The query to use as a comparison.

#### Return Value

true if the queries are equal; otherwise, false.

#### Remarks

"Equal" in this case means that the query is structurally identical to the query that it is compared to. The query has the same number of data sources assigned to the same files, and it has the same number of ranges.

### Method exportXML

    public str exportXML()

#### Return Value

### Method findHavingFilterByField

    public QueryHavingFilter findHavingFilterByField(QueryBuildDataSource dataSource, FieldName fieldName, [int occurrence], [int arrayIndex])

#### Parameters

dataSource  

<!-- -->

fieldName  

<!-- -->

occurrence  

<!-- -->

arrayIndex  

#### Return Value

### Method findQueryFilter

    public QueryFilter findQueryFilter(QueryBuildDataSource dataSource, FieldName fieldName, [int occurrence], [int arrayIndex])

#### Parameters

dataSource  

<!-- -->

fieldName  

<!-- -->

occurrence  

<!-- -->

arrayIndex  

#### Return Value

### Method firstTopLevelDataSource

    public QueryBuildDataSource firstTopLevelDataSource()

#### Return Value

### Method forceNestedLoop

    public boolean forceNestedLoop(boolean arg)

#### Parameters

arg  

#### Return Value

### Method forceSelectOrder

    public boolean forceSelectOrder(boolean arg)

#### Parameters

arg  

#### Return Value

### Method form

    public str form([str value])

#### Parameters

value  

#### Return Value

### Method getCompanyRange

    public container getCompanyRange()

#### Return Value

### Method getMostRestrictedQueryFilterStatus

    public int getMostRestrictedQueryFilterStatus(QueryBuildDataSource dataSource, FieldName fieldName, [int fieldId])

#### Parameters

dataSource  

<!-- -->

fieldName  

<!-- -->

fieldId  

#### Return Value

### Method getNextUniqueId

    public int getNextUniqueId()

#### Return Value

### Method getSQLStatement

    public str getSQLStatement([boolean noRuntimeOptimization])

#### Parameters

noRuntimeOptimization  

#### Return Value

### Method getValidTimeStateDateRange

    public container getValidTimeStateDateRange()

#### Return Value

### Method getValidTimeStateDateTimeRange

    public container getValidTimeStateDateTimeRange()

#### Return Value

### Method getValidTimeStateQueryType

    public ValidTimeStateQueryType getValidTimeStateQueryType()

#### Return Value

### Method groupByField

    public QueryGroupByField groupByField(int index, [QueryBuildDataSource dataSource])

#### Parameters

index  

<!-- -->

dataSource  

#### Return Value

### Method groupByFieldCount

    public int groupByFieldCount([QueryBuildDataSource dataSource])

#### Parameters

dataSource  

#### Return Value

### Method hasMultipleTopLevelDataSource

    public boolean hasMultipleTopLevelDataSource()

#### Return Value

### Method hasRangeOrFilter

    public boolean hasRangeOrFilter(QueryBuildDataSource dataSource)

#### Parameters

dataSource  

#### Return Value

### Method havingFilter

    public QueryHavingFilter havingFilter(int count, [QueryBuildDataSource dataSource])

#### Parameters

count  

<!-- -->

dataSource  

#### Return Value

### Method havingFilterCount

    public int havingFilterCount([QueryBuildDataSource dataSource])

#### Parameters

dataSource  

#### Return Value

### Method inReport

Determines whether the query is part of a report.

    public boolean inReport()

#### Return Value

true if the query is part of a report (is found under a report's data sources node); otherwise, false.

#### Remarks

This function is not typically used by application code. If the method returns true, the report method can be used to access the report in which the query is defined.

### Method interactive

Specifies whether the query is interactive.

    public boolean interactive([boolean value])

#### Parameters

value  
A value that indicates whether the query is interactive; optional.

#### Return Value

true if the query is interactive; otherwise, false.

#### Remarks

In an interactive query, the query can, for example, present the user with a dialog box when the prompt method is called. This functionality is used when code will be submitted to a batch and in other situations where code must run unattended.

### Method isCompositeQuery

    public boolean isCompositeQuery()

#### Return Value

### Method isExplicitlyOrdered

    public boolean isExplicitlyOrdered()

#### Return Value

### Method isExplicitlyGrouped

    public boolean isExplicitlyGrouped()

#### Return Value

### Method isPureUnionAll

    public boolean isPureUnionAll()

#### Return Value

### Method isUnionType

    public boolean isUnionType()

#### Return Value

### Method levelNo

Determines the level of indentation of the specified data source.

    public int levelNo(int dataSourceNo)

#### Parameters

dataSourceNo  
The data source number to determine the level for.

#### Return Value

The level number of the specified data source.

#### Remarks

The data sources are numbered consecutively, starting at 1.

### Method levelTable

Determines the tree level, in the hierarchy of data sources, of the data source that is assigned to the specified table.

    public int levelTable(TableId table, [int occurrence])

#### Parameters

table  
The integer that is used if more than one data source is assigned to the same table; optional.

<!-- -->

occurrence  
The integer that is used if more than one data source is assigned to the same table; optional.

#### Return Value

The level number of the query's specified data source.

### Method literals

    public int literals([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

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

### Method newObject

Creates a query that exists on the same client side or server side as the source query.

    public Query newObject(AnyType source)

#### Parameters

source  
The source query.

#### Return Value

The new query.

### Method nextUniqueId

    public int nextUniqueId([int value])

#### Parameters

value  

#### Return Value

### Method orderByField

    public QueryOrderByField orderByField(int index, [QueryBuildDataSource dataSource])

#### Parameters

index  

<!-- -->

dataSource  

#### Return Value

### Method orderByFieldCount

    public int orderByFieldCount([QueryBuildDataSource dataSource])

#### Parameters

dataSource  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method pack

Packs the query into a container and returns that container, so that it can be used when you create a query.

    public container pack([boolean doCheck])

#### Parameters

doCheck  
A Boolean value that indicates whether to flag an error when a data source in the query references an outside cursor, such as a link to a cursor that is foreign to the query's data source; optional. The default value is true, which enforces the constraint.

#### Return Value

The container that holds the query.

#### Remarks

The container that is created by this method can serve as input when you instantiate a query or queryRun object by using either the new method or the newObject method. Links to cursors that are foreign to the query's data source are not packed into the container. If you must pack this kind of link, you should take a snapshot of the cursor's data and construct ranges for each field.

### Method packInternals

    public container packInternals()

#### Return Value

### Method queryFilter

    public QueryFilter queryFilter(int count, [QueryBuildDataSource rootDataSource])

#### Parameters

count  

<!-- -->

rootDataSource  

#### Return Value

### Method queryFilterCount

    public int queryFilterCount([QueryBuildDataSource rootDataSource])

#### Parameters

rootDataSource  

#### Return Value

### Method queryType

    public int queryType([int value])

#### Parameters

value  

#### Return Value

### Method quickFilterValue

    public str quickFilterValue()

#### Return Value

### Method quickFilterControlId

    public int quickFilterControlId()

#### Return Value

### Method recordLevelSecurity

    public boolean recordLevelSecurity([boolean value])

#### Parameters

value  

#### Return Value

### Method report

Returns the report in which the query is defined, if the report exists.

    public Report report()

#### Return Value

The report in which the query is defined under the data sources node.

#### Remarks

A query is not necessarily defined in the context of a report. To determine whether a query is defined in the context of a report, you can use the inReport method.

### Method saved

Indicates whether the query has been saved to disk.

    public boolean saved()

#### Return Value

true if the query has been saved to disk; otherwise, false.

### Method searchable

    public boolean searchable([boolean value])

#### Parameters

value  

#### Return Value

### Method importSession

    public Guid importSession([Guid value])

#### Parameters

value  

#### Return Value

### Method title

    public str title([str value])

#### Parameters

value  

#### Return Value

### Method topRows

    public int topRows([int value])

#### Parameters

value  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. However, the method can be overridden in a derived class so that it returns values that are meaningful for that type.For example, an instance of the SysMethodInfo class returns the method name, and the type of method, such as Instance or Static.

### Method userUpdate

Gets or sets a value that indicates whether the query can update the records that it fetches.

    public boolean userUpdate([boolean value])

#### Parameters

value  
A Boolean value that indicates whether the query can update the records that it fetches; optional.

#### Return Value

true if the query can currently update records that it fetches; otherwise false.

### Method validTimeStateAsOfDate

    public Date validTimeStateAsOfDate([Date asOfDate])

#### Parameters

asOfDate  

#### Return Value

### Method validTimeStateAsOfDateTime

    public DateTime validTimeStateAsOfDateTime([DateTime asOfDateTime])

#### Parameters

asOfDateTime  

#### Return Value

### Method validTimeStateFlags

    public int validTimeStateFlags([int value])

#### Parameters

value  

#### Return Value

### Method version

    public int version([int value])

#### Parameters

value  

#### Return Value

### Method xml

Returns an XML string that represents the current object.

    public str xml([int indent])

#### Parameters

indent  
The amount of indentation for the returned XML string; optional.

#### Return Value

An XML string that represents the current object.

#### Remarks

This method can be overridden to return values that are meaningful for that type.

### Method clearBaseQueries

    public void clearBaseQueries()

### Method addCompanyRange

    public void addCompanyRange(str companyName)

#### Parameters

companyName  

### Method checkRangeParsingErrors

    public void checkRangeParsingErrors(boolean setCheckRangeParsingErrors)

#### Parameters

setCheckRangeParsingErrors  

### Method clearCompanyRange

    public void clearCompanyRange()

### Method unpackInternals

    public void unpackInternals(container internalData)

#### Parameters

internalData  

### Method new

Creates a query object.

    public void new([AnyType source])

#### Parameters

source  
The source to base the query object on; optional.

#### Remarks

If no arguments are supplied when this method is called, a temporary query is created that is not stored in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT) for subsequent use.

### Method checkFieldAccess

    public void checkFieldAccess(boolean setCheckFieldAccess)

#### Parameters

setCheckFieldAccess  

### Method useDbCacheOnGeneratedCursors

    public void useDbCacheOnGeneratedCursors([int fetchsize])

#### Parameters

fetchsize  

### Method setValidTimeStateQueryType

    public void setValidTimeStateQueryType([ValidTimeStateQueryType type])

#### Parameters

type  

### Method validTimeStateDateRange

    public void validTimeStateDateRange([Date fromDate], [Date toDate])

#### Parameters

fromDate  

<!-- -->

toDate  

### Method clearHavingFilters

    public void clearHavingFilters([QueryBuildDataSource dataSource], [str fieldName], [int occurence], [int arrayIndex])

#### Parameters

dataSource  

<!-- -->

fieldName  

<!-- -->

occurence  

<!-- -->

arrayIndex  

### Method quickFilter

    public void quickFilter([str dataSourceName], [int tableId], [int fieldId], [str filterValue], [int controlId], [boolean useEqualityComparisonForStrings])

#### Parameters

dataSourceName  

<!-- -->

tableId  

<!-- -->

fieldId  

<!-- -->

filterValue  

<!-- -->

controlId  

<!-- -->

useEqualityComparisonForStrings  

### Method finalize

    public void finalize()

### Method clearQueryFilters

    public void clearQueryFilters([QueryBuildDataSource dataSource], [str fieldName], [int occurence], [int arrayIndex])

#### Parameters

dataSource  

<!-- -->

fieldName  

<!-- -->

occurence  

<!-- -->

arrayIndex  

### Method clearOrderBy

    public void clearOrderBy()

### Method clearAllFields

    public void clearAllFields()

### Method clearGroupBy

    public void clearGroupBy()

### Method autoAuthzMode

    public void autoAuthzMode(AutoAuthzMode mode)

#### Parameters

mode  

### Method insert\_recordset

    public static void insert_recordset(Common targetCursor, Map targetToSourceMap, Query sourceQuery)

#### Parameters

targetCursor  

<!-- -->

targetToSourceMap  

<!-- -->

sourceQuery  

### Method generateCursors

    public void generateCursors()

### Method checkAuthorizationOnOpenRanges

    public void checkAuthorizationOnOpenRanges(boolean setCheckAuthorizationOnOpenRanges)

#### Parameters

setCheckAuthorizationOnOpenRanges  

### Method addContains

    public void addContains(str containsValue, [boolean prefixSearch])

#### Parameters

containsValue  

<!-- -->

prefixSearch  

### Method resetValidTimeStateQueryType

    public void resetValidTimeStateQueryType()

### Method validTimeStateDateTimeRange

    public void validTimeStateDateTimeRange([DateTime fromDateTime], [DateTime toDateTime])

#### Parameters

fromDateTime  

<!-- -->

toDateTime  

## Class QueryBuildDataSource
    class QueryBuildDataSource extends TreeNode

The QueryBuildDataSource class provides the building blocks that queries are made of.

### Remarks

Data sources are arranged in hierarchies that define the sequence in which records are fetched from the tables that are assigned to the data sources. Each data source defines the order in which the records are fetched, and also the criteria that must be met by the selected records. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

    {    QueryBuildDataSource ds;    Query q = new Query();        ds = q.addDataSource(        TableNum(CustTable));}

### Methods

| Method                                                                                                                                                       | Description                                                                                                                               |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int addAllFields(TableName tableName)                                                                                                                 |                                                                                                                                           |
| public QueryBuildDataSource addDataSource(AnyType arg, \[str name\], \[boolean emptyFieldList\])                                                             | Adds a data source that is embedded in this data source.                                                                                  |
| public QueryBuildDynalink addDynalink(FieldId field, Common dynamicFile, FieldId dynamicField, \[int fieldArrayIndex\], \[int dynamicFieldArrayIndex\])      |                                                                                                                                           |
| public QueryBuildLink addForeignkeyRelation(str relatedTableRole, \[str parentDatasourceName\])                                                              |                                                                                                                                           |
| public QueryGroupByField addGroupByField(FieldId fieldID, \[int arrayIndex\])                                                                                |                                                                                                                                           |
| public QueryBuildLink addLink(FieldId parentField, FieldId thisField, \[str parentDatasourceName\])                                                          |                                                                                                                                           |
| public QueryOrderByField addOrderByAggregateField(SelectionField fieldType, FieldId fieldID, \[SortOrder direction\], \[int arrayIndex\])                    |                                                                                                                                           |
| public QueryOrderByField addOrderByCalculationField(Microsoft.Dynamics.AX.Analytics.CalculationModel.NumericExpression calculation, \[SortOrder direction\]) |                                                                                                                                           |
| public QueryOrderByField addOrderByField(FieldId fieldID, \[SortOrder direction\], \[int arrayIndex\])                                                       |                                                                                                                                           |
| public QueryBuildRange addRange(FieldId field, \[int arrayIndex\], \[QueryRangeType rangeType\])                                                             | Adds a range to the data source.                                                                                                          |
| public int addSortField(FieldId sortField, \[SortOrder direction\], \[int arrayIndex\])                                                                      |                                                                                                                                           |
| public int addSortIndex(IndexId index)                                                                                                                       |                                                                                                                                           |
| public int allowAdd(\[int value\])                                                                                                                           |                                                                                                                                           |
| public boolean applyFilter(FilterValue filterValue)                                                                                                          |                                                                                                                                           |
| public boolean autoHeader(FieldId field, \[boolean orderNo\])                                                                                                |                                                                                                                                           |
| public int autoHeaderDetailLevel(FieldId field, \[int orderNo\])                                                                                             |                                                                                                                                           |
| public boolean autoSum(FieldId field, \[boolean orderNo\])                                                                                                   |                                                                                                                                           |
| public int autoSumDetailLevel(FieldId field, \[int orderNo\])                                                                                                |                                                                                                                                           |
| public boolean changedNo()                                                                                                                                   |                                                                                                                                           |
| public int childDataSourceCount()                                                                                                                            |                                                                                                                                           |
| public QueryBuildDataSource childDataSourceNo(int dataSourceNo)                                                                                              |                                                                                                                                           |
| public str company(\[str value\])                                                                                                                            |                                                                                                                                           |
| public int concurrencyModel(\[int value\])                                                                                                                   |                                                                                                                                           |
| public QueryBuildDynalink dynalink(int dynalinkNo)                                                                                                           |                                                                                                                                           |
| public int dynalinkCount()                                                                                                                                   |                                                                                                                                           |
| public boolean embedded()                                                                                                                                    |                                                                                                                                           |
| public boolean enabled(\[boolean value\])                                                                                                                    | Determines whether to enable or disable the object.                                                                                       |
| public boolean existsMeanOrExists(\[boolean value\])                                                                                                         |                                                                                                                                           |
| public int fetchMode(\[int value\])                                                                                                                          |                                                                                                                                           |
| public QueryBuildFieldList fields()                                                                                                                          |                                                                                                                                           |
| public TableId file()                                                                                                                                        |                                                                                                                                           |
| public QueryBuildRange findRange(FieldId field, \[int occurrence\], \[int arrayIndex\])                                                                      |                                                                                                                                           |
| public boolean firstFast(\[boolean value\])                                                                                                                  | Determines whether to retrieve the first record from the query before the other records.                                                  |
| public boolean firstOnly(\[boolean value\])                                                                                                                  |                                                                                                                                           |
| public int getMostRestrictedQueryBuildRangeStatus(FieldId field, \[int occurrence\], \[int arrayIndex\])                                                     |                                                                                                                                           |
| public Common getNo()                                                                                                                                        |                                                                                                                                           |
| public int id()                                                                                                                                              |                                                                                                                                           |
| public boolean indexIsHint(boolean arg)                                                                                                                      |                                                                                                                                           |
| public boolean isPartOfSubQueryInBaseQuery()                                                                                                                 |                                                                                                                                           |
| public boolean joined()                                                                                                                                      |                                                                                                                                           |
| public container joinedDataSources()                                                                                                                         |                                                                                                                                           |
| public int joinMode(\[int value\])                                                                                                                           |                                                                                                                                           |
| public str label(\[str value\])                                                                                                                              | Gets or sets the label for a control.                                                                                                     |
| public int level()                                                                                                                                           |                                                                                                                                           |
| public QueryBuildLink link(int associationNo)                                                                                                                |                                                                                                                                           |
| public int linkCount()                                                                                                                                       |                                                                                                                                           |
| public str name(\[str value\])                                                                                                                               | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public container oneToOneDataSources()                                                                                                                       |                                                                                                                                           |
| public int orderMode(\[int value\])                                                                                                                          |                                                                                                                                           |
| public QueryBuildDataSource parentDataSource()                                                                                                               |                                                                                                                                           |
| public str policyContext(\[str value\])                                                                                                                      |                                                                                                                                           |
| public QueryBuildRange range(int rangeNo)                                                                                                                    |                                                                                                                                           |
| public int rangeCount()                                                                                                                                      |                                                                                                                                           |
| public QueryBuildRange rangeField(FieldId field, \[int occurrence\])                                                                                         |                                                                                                                                           |
| public boolean relations(\[boolean value\])                                                                                                                  |                                                                                                                                           |
| public int selectionCount()                                                                                                                                  |                                                                                                                                           |
| public boolean selectWithRepeatableRead(\[boolean value\])                                                                                                   |                                                                                                                                           |
| public SortOrder sortDirection(FieldId field, \[SortOrder direction\])                                                                                       |                                                                                                                                           |
| public FieldId sortField(FieldId field)                                                                                                                      |                                                                                                                                           |
| public int sortFieldCount()                                                                                                                                  |                                                                                                                                           |
| public IndexId sortIndex(int indexNo)                                                                                                                        |                                                                                                                                           |
| public int sortIndexCount()                                                                                                                                  |                                                                                                                                           |
| public QueryBuildStaticlink staticlink(int staticlinkNo)                                                                                                     | Returns a static Link object on the query’s data source.                                                                                  |
| public int staticlinkCount()                                                                                                                                 | Gives the number of static links that are defined on the QueryBuildDataSource object.                                                     |
| public TableId table(\[TableId value\])                                                                                                                      | Gets or sets the table ID that is associated with the object.                                                                             |
| public str toString()                                                                                                                                        | Returns a string that represents the current object.                                                                                      |
| public int unionType(\[int value\])                                                                                                                          |                                                                                                                                           |
| public int uniqueId()                                                                                                                                        |                                                                                                                                           |
| public boolean update(\[boolean value\])                                                                                                                     | Determines whether the records fetched by this data source can be updated.                                                                |
| public void clearLinks()                                                                                                                                     |                                                                                                                                           |
| public void clearDynalinks()                                                                                                                                 |                                                                                                                                           |
| public void clearRange(FieldId field, \[int occurrence\])                                                                                                    |                                                                                                                                           |
| public void sortClear()                                                                                                                                      |                                                                                                                                           |
| public void finalize()                                                                                                                                       |                                                                                                                                           |
| public void addSelectionFieldWithAlias(str alias, FieldId field, \[SelectionField fieldType\])                                                               |                                                                                                                                           |
| public void addCalculationField(Microsoft.Dynamics.AX.Analytics.CalculationModel.NumericExpression calculation, str alias)                                   |                                                                                                                                           |
| public void addForeignKeyDynalink(Common dynamicFile, str relatedRole)                                                                                       |                                                                                                                                           |
| public void addRelation(DictRelation relation, \[TableScope tableScope\])                                                                                    |                                                                                                                                           |
| public void clearSortIndex()                                                                                                                                 |                                                                                                                                           |
| public void clearRanges()                                                                                                                                    | Deletes all ranges that are associated with the data source.                                                                              |
| public void linkFields(str parentField, str thisField, \[str parentDatasourceName\])                                                                         |                                                                                                                                           |
| public void addSelectionField(FieldId field, \[SelectionField fieldType\], \[int arrayIndex\])                                                               |                                                                                                                                           |

### Method addAllFields

    public int addAllFields(TableName tableName)

#### Parameters

tableName  

#### Return Value

### Method addDataSource

Adds a data source that is embedded in this data source.

    public QueryBuildDataSource addDataSource(AnyType arg, [str name], [boolean emptyFieldList])

#### Parameters

arg  

<!-- -->

name  

<!-- -->

emptyFieldList  

#### Return Value

The new data source.

#### Remarks

Top-level data sources are created by using the addDataSource method.

### Method addDynalink

    public QueryBuildDynalink addDynalink(FieldId field, Common dynamicFile, FieldId dynamicField, [int fieldArrayIndex], [int dynamicFieldArrayIndex])

#### Parameters

field  

<!-- -->

dynamicFile  

<!-- -->

dynamicField  

<!-- -->

fieldArrayIndex  

<!-- -->

dynamicFieldArrayIndex  

#### Return Value

### Method addForeignkeyRelation

    public QueryBuildLink addForeignkeyRelation(str relatedTableRole, [str parentDatasourceName])

#### Parameters

relatedTableRole  

<!-- -->

parentDatasourceName  

#### Return Value

### Method addGroupByField

    public QueryGroupByField addGroupByField(FieldId fieldID, [int arrayIndex])

#### Parameters

fieldID  

<!-- -->

arrayIndex  

#### Return Value

### Method addLink

    public QueryBuildLink addLink(FieldId parentField, FieldId thisField, [str parentDatasourceName])

#### Parameters

parentField  

<!-- -->

thisField  

<!-- -->

parentDatasourceName  

#### Return Value

### Method addOrderByAggregateField

    public QueryOrderByField addOrderByAggregateField(SelectionField fieldType, FieldId fieldID, [SortOrder direction], [int arrayIndex])

#### Parameters

fieldType  

<!-- -->

fieldID  

<!-- -->

direction  

<!-- -->

arrayIndex  

#### Return Value

### Method addOrderByCalculationField

    public QueryOrderByField addOrderByCalculationField(Microsoft.Dynamics.AX.Analytics.CalculationModel.NumericExpression calculation, [SortOrder direction])

#### Parameters

calculation  

<!-- -->

direction  

#### Return Value

### Method addOrderByField

    public QueryOrderByField addOrderByField(FieldId fieldID, [SortOrder direction], [int arrayIndex])

#### Parameters

fieldID  

<!-- -->

direction  

<!-- -->

arrayIndex  

#### Return Value

### Method addRange

Adds a range to the data source.

    public QueryBuildRange addRange(FieldId field, [int arrayIndex], [QueryRangeType rangeType])

#### Parameters

field  

<!-- -->

arrayIndex  

<!-- -->

rangeType  

#### Return Value

A new range for the data source.

#### Remarks

Ranges define the values that records from the data source's table must satisfy. Several range values can exist for the same field in a particular data source. In this case, the values are included in the query if the record qualifies for any of the values that are supplied. When ranges are included for multiple fields, only records that satisfy the constraints that are supplied by both criteria are included. The constraints are specified in the value method.

### Method addSortField

    public int addSortField(FieldId sortField, [SortOrder direction], [int arrayIndex])

#### Parameters

sortField  

<!-- -->

direction  

<!-- -->

arrayIndex  

#### Return Value

### Method addSortIndex

    public int addSortIndex(IndexId index)

#### Parameters

index  

#### Return Value

### Method allowAdd

    public int allowAdd([int value])

#### Parameters

value  

#### Return Value

### Method applyFilter

    public boolean applyFilter(FilterValue filterValue)

#### Parameters

filterValue  

#### Return Value

### Method autoHeader

    public boolean autoHeader(FieldId field, [boolean orderNo])

#### Parameters

field  

<!-- -->

orderNo  

#### Return Value

### Method autoHeaderDetailLevel

    public int autoHeaderDetailLevel(FieldId field, [int orderNo])

#### Parameters

field  

<!-- -->

orderNo  

#### Return Value

### Method autoSum

    public boolean autoSum(FieldId field, [boolean orderNo])

#### Parameters

field  

<!-- -->

orderNo  

#### Return Value

### Method autoSumDetailLevel

    public int autoSumDetailLevel(FieldId field, [int orderNo])

#### Parameters

field  

<!-- -->

orderNo  

#### Return Value

### Method changedNo

    public boolean changedNo()

#### Return Value

### Method childDataSourceCount

    public int childDataSourceCount()

#### Return Value

### Method childDataSourceNo

    public QueryBuildDataSource childDataSourceNo(int dataSourceNo)

#### Parameters

dataSourceNo  

#### Return Value

### Method company

    public str company([str value])

#### Parameters

value  

#### Return Value

### Method concurrencyModel

    public int concurrencyModel([int value])

#### Parameters

value  

#### Return Value

### Method dynalink

    public QueryBuildDynalink dynalink(int dynalinkNo)

#### Parameters

dynalinkNo  

#### Return Value

### Method dynalinkCount

    public int dynalinkCount()

#### Return Value

### Method embedded

    public boolean embedded()

#### Return Value

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property enables controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method existsMeanOrExists

    public boolean existsMeanOrExists([boolean value])

#### Parameters

value  

#### Return Value

### Method fetchMode

    public int fetchMode([int value])

#### Parameters

value  

#### Return Value

### Method fields

    public QueryBuildFieldList fields()

#### Return Value

### Method file

    public TableId file()

#### Return Value

### Method findRange

    public QueryBuildRange findRange(FieldId field, [int occurrence], [int arrayIndex])

#### Parameters

field  

<!-- -->

occurrence  

<!-- -->

arrayIndex  

#### Return Value

### Method firstFast

Determines whether to retrieve the first record from the query before the other records.

    public boolean firstFast([boolean value])

#### Parameters

value  

#### Return Value

true if the first record is retrieved first; otherwise, false.

#### Remarks

The firstFast property enables some database systems to optimize record retrieval, which improves performance. If the database does not support this property, it is ignored.

### Method firstOnly

    public boolean firstOnly([boolean value])

#### Parameters

value  

#### Return Value

### Method getMostRestrictedQueryBuildRangeStatus

    public int getMostRestrictedQueryBuildRangeStatus(FieldId field, [int occurrence], [int arrayIndex])

#### Parameters

field  

<!-- -->

occurrence  

<!-- -->

arrayIndex  

#### Return Value

### Method getNo

    public Common getNo()

#### Return Value

### Method id

    public int id()

#### Return Value

### Method indexIsHint

    public boolean indexIsHint(boolean arg)

#### Parameters

arg  

#### Return Value

### Method isPartOfSubQueryInBaseQuery

    public boolean isPartOfSubQueryInBaseQuery()

#### Return Value

### Method joined

    public boolean joined()

#### Return Value

### Method joinedDataSources

    public container joinedDataSources()

#### Return Value

### Method joinMode

    public int joinMode([int value])

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

### Method level

    public int level()

#### Return Value

### Method link

    public QueryBuildLink link(int associationNo)

#### Parameters

associationNo  

#### Return Value

### Method linkCount

    public int linkCount()

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method oneToOneDataSources

    public container oneToOneDataSources()

#### Return Value

### Method orderMode

    public int orderMode([int value])

#### Parameters

value  

#### Return Value

### Method parentDataSource

    public QueryBuildDataSource parentDataSource()

#### Return Value

### Method policyContext

    public str policyContext([str value])

#### Parameters

value  

#### Return Value

### Method range

    public QueryBuildRange range(int rangeNo)

#### Parameters

rangeNo  

#### Return Value

### Method rangeCount

    public int rangeCount()

#### Return Value

### Method rangeField

    public QueryBuildRange rangeField(FieldId field, [int occurrence])

#### Parameters

field  

<!-- -->

occurrence  

#### Return Value

### Method relations

    public boolean relations([boolean value])

#### Parameters

value  

#### Return Value

### Method selectionCount

    public int selectionCount()

#### Return Value

### Method selectWithRepeatableRead

    public boolean selectWithRepeatableRead([boolean value])

#### Parameters

value  

#### Return Value

### Method sortDirection

    public SortOrder sortDirection(FieldId field, [SortOrder direction])

#### Parameters

field  

<!-- -->

direction  

#### Return Value

### Method sortField

    public FieldId sortField(FieldId field)

#### Parameters

field  

#### Return Value

### Method sortFieldCount

    public int sortFieldCount()

#### Return Value

### Method sortIndex

    public IndexId sortIndex(int indexNo)

#### Parameters

indexNo  

#### Return Value

### Method sortIndexCount

    public int sortIndexCount()

#### Return Value

### Method staticlink

Returns a static Link object on the query’s data source.

    public QueryBuildStaticlink staticlink(int staticlinkNo)

#### Parameters

staticlinkNo  

#### Return Value

The static Link object at the \_staticLinkNo index.

### Method staticlinkCount

Gives the number of static links that are defined on the QueryBuildDataSource object.

    public int staticlinkCount()

#### Return Value

The number of static links that are defined on the QueryBuildDataSource object.

### Method table

Gets or sets the table ID that is associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID that is associated with the object.

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method unionType

    public int unionType([int value])

#### Parameters

value  

#### Return Value

### Method uniqueId

    public int uniqueId()

#### Return Value

### Method update

Determines whether the records fetched by this data source can be updated.

    public boolean update([boolean value])

#### Parameters

value  

#### Return Value

true if the records can be updated; otherwise, false.

#### Remarks

To update the records, start a separate transaction by using the ttsBegin and ttsCommit methods.

### Method clearLinks

    public void clearLinks()

### Method clearDynalinks

    public void clearDynalinks()

### Method clearRange

    public void clearRange(FieldId field, [int occurrence])

#### Parameters

field  

<!-- -->

occurrence  

### Method sortClear

    public void sortClear()

### Method finalize

    public void finalize()

### Method addSelectionFieldWithAlias

    public void addSelectionFieldWithAlias(str alias, FieldId field, [SelectionField fieldType])

#### Parameters

alias  

<!-- -->

field  

<!-- -->

fieldType  

### Method addCalculationField

    public void addCalculationField(Microsoft.Dynamics.AX.Analytics.CalculationModel.NumericExpression calculation, str alias)

#### Parameters

calculation  

<!-- -->

alias  

### Method addForeignKeyDynalink

    public void addForeignKeyDynalink(Common dynamicFile, str relatedRole)

#### Parameters

dynamicFile  

<!-- -->

relatedRole  

### Method addRelation

    public void addRelation(DictRelation relation, [TableScope tableScope])

#### Parameters

relation  

<!-- -->

tableScope  

### Method clearSortIndex

    public void clearSortIndex()

### Method clearRanges

Deletes all ranges that are associated with the data source.

    public void clearRanges()

#### Examples

The following example adds ranges and then removes them from a data source.

    Query Q = new Query(); 
    QueryBuildDataSource ds = q.addDataSource(TableNum(CustTable)); 
    QueryBuildRange r = ds.addRange(FieldNum(CustTable, recId)); 
    print ds.rangeCount(); 
    ds.clearRanges(); 
    print ds.rangeCount(); 
    pause;

### Method linkFields

    public void linkFields(str parentField, str thisField, [str parentDatasourceName])

#### Parameters

parentField  

<!-- -->

thisField  

<!-- -->

parentDatasourceName  

### Method addSelectionField

    public void addSelectionField(FieldId field, [SelectionField fieldType], [int arrayIndex])

#### Parameters

field  

<!-- -->

fieldType  

<!-- -->

arrayIndex  

## Class QueryBuildDynalink
    class QueryBuildDynalink extends Object

### Remarks

### Examples

### Methods

| Method                                                | Description |
|-------------------------------------------------------|-------------|
| public Common cursor(\[Common cursor\])               |             |
| public QueryBuildDataSource dataSource()              |             |
| public FieldId dynamicField(\[FieldId dynamicField\]) |             |
| public FieldId field(\[FieldId fieldId\])             |             |
| public int fieldArrayIndex()                          |             |
| public FieldName fieldName()                          |             |
| public void finalize()                                |             |

### Method cursor

    public Common cursor([Common cursor])

#### Parameters

cursor  

#### Return Value

### Method dataSource

    public QueryBuildDataSource dataSource()

#### Return Value

### Method dynamicField

    public FieldId dynamicField([FieldId dynamicField])

#### Parameters

dynamicField  

#### Return Value

### Method field

    public FieldId field([FieldId fieldId])

#### Parameters

fieldId  

#### Return Value

### Method fieldArrayIndex

    public int fieldArrayIndex()

#### Return Value

### Method fieldName

    public FieldName fieldName()

#### Return Value

### Method finalize

    public void finalize()

## Class QueryBuildFieldList
    class QueryBuildFieldList extends TreeNode

The QueryBuildFieldList class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                 | Description |
|--------------------------------------------------------------------------------------------------------|-------------|
| public int addAllFields(TableName tableName)                                                           |             |
| public QueryBuildFieldList addField(FieldId fieldId, \[SelectionField fieldType\], \[int arrayIndex\]) |             |
| public int dynamic(\[int value\])                                                                      |             |
| public FieldId field(int index)                                                                        |             |
| public int fieldCount()                                                                                |             |
| public SelectionField fieldKind(int index)                                                             |             |
| public TableId tableSelector(int index)                                                                |             |
| public void clearFieldList()                                                                           |             |

### Method addAllFields

    public int addAllFields(TableName tableName)

#### Parameters

tableName  

#### Return Value

### Method addField

    public QueryBuildFieldList addField(FieldId fieldId, [SelectionField fieldType], [int arrayIndex])

#### Parameters

fieldId  

<!-- -->

fieldType  

<!-- -->

arrayIndex  

#### Return Value

### Method dynamic

    public int dynamic([int value])

#### Parameters

value  

#### Return Value

### Method field

    public FieldId field(int index)

#### Parameters

index  

#### Return Value

### Method fieldCount

    public int fieldCount()

#### Return Value

### Method fieldKind

    public SelectionField fieldKind(int index)

#### Parameters

index  

#### Return Value

### Method tableSelector

    public TableId tableSelector(int index)

#### Parameters

index  

#### Return Value

### Method clearFieldList

    public void clearFieldList()

## Class QueryBuildLink
    class QueryBuildLink extends TreeNode

The QueryBuildLink class enables for the creating, reading, updating, and deleting of X++ code and metadata.

### Remarks

### Examples

### Methods

| Method                      | Description |
|-----------------------------|-------------|
| public int delete()         |             |
| public int field()          |             |
| public boolean incomplete() |             |
| public str joinRelation()   |             |
| public int relatedField()   |             |
| public int relatedTable()   |             |
| public int table()          |             |
| public void finalize()      |             |

### Method delete

    public int delete()

#### Return Value

### Method field

    public int field()

#### Return Value

### Method incomplete

    public boolean incomplete()

#### Return Value

### Method joinRelation

    public str joinRelation()

#### Return Value

### Method relatedField

    public int relatedField()

#### Return Value

### Method relatedTable

    public int relatedTable()

#### Return Value

### Method table

    public int table()

#### Return Value

### Method finalize

    public void finalize()

## Class QueryBuildRange
    class QueryBuildRange extends TreeNode

The QueryBuildRange class represents the ranges that define which records should be fetched from the data source in which the QueryBuildRange class is associated.

### Remarks

The value property can be used to set the string that defines the range. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. A particular data source can have any number of ranges. Multiple ranges are valid for the same data source field.

### Examples

The following basic example shows how to use the QueryBuildRange class to specify the range of interest for a specific data field.

    Query                   query; 
    QueryRun                queryRun; 
    QueryBuildDataSource    queryBuildDataSource; 
    QueryBuildRange         queryBuildRange; 
    CustTable               custTable; 
    query = new Query(); 
    queryBuildDataSource = query.addDataSource( 
       TableNum(CustTable)); 
    queryBuildRange = queryBuildDataSource.addRange( 
        FieldNum(CustTable,AccountNum)); 
    queryBuildRange.value("4000..5000"); 
    queryRun = new queryRun(query); 
    if (queryRun.prompt()) 
    { 
        while (queryRun.next()) 
        { 
            custTable = queryRun.get(TableNum(CustTable)); 
            print custTable.AccountNum; 
        } 
    }

### Methods

| Method                                                        | Description                                                                                                                               |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public QueryBuildDataSource dataSource()                      | Returns the data source that was used to instantiate the QueryBuildRange object.                                                          |
| public boolean doesRangeNodeBelongToCompositeQuery()          |                                                                                                                                           |
| public boolean enabled(\[boolean value\])                     | Determines whether to enable or disable the object.                                                                                       |
| public FieldId field(\[FieldId value\])                       | Gets or sets the field ID associated with the object.                                                                                     |
| public int fieldArrayIndex()                                  |                                                                                                                                           |
| public FieldName fieldName()                                  |                                                                                                                                           |
| public str label(\[str value\])                               | Gets or sets the label for a control.                                                                                                     |
| public str name(\[str value\])                                | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public str prompt()                                           |                                                                                                                                           |
| public QueryRangeType rangeType(\[QueryRangeType rangeType\]) |                                                                                                                                           |
| public int status(\[int value\])                              | Gets or sets the status of an object.                                                                                                     |
| public TableId table(\[TableId value\])                       | Gets or sets the table ID that is associated with the object.                                                                             |
| public TableId tableSelector(\[TableId value\])               |                                                                                                                                           |
| public str toString()                                         | Returns a string that represents the current object.                                                                                      |
| public int typeof()                                           |                                                                                                                                           |
| public boolean valid()                                        |                                                                                                                                           |
| public str value(\[str value\])                               | Gets or sets the value that queried records must match to be retrieved.                                                                   |
| public void associateRangeNodeToCompositeQuery()              |                                                                                                                                           |
| public void finalize()                                        |                                                                                                                                           |

### Method dataSource

Returns the data source that was used to instantiate the QueryBuildRange object.

    public QueryBuildDataSource dataSource()

#### Return Value

The data source that was used to instantiate the QueryBuildRange class object.

### Method doesRangeNodeBelongToCompositeQuery

    public boolean doesRangeNodeBelongToCompositeQuery()

#### Return Value

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property enables controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method field

Gets or sets the field ID associated with the object.

    public FieldId field([FieldId value])

#### Parameters

value  

#### Return Value

The current value of the field ID associated with the object.

### Method fieldArrayIndex

    public int fieldArrayIndex()

#### Return Value

### Method fieldName

    public FieldName fieldName()

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

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method prompt

    public str prompt()

#### Return Value

### Method rangeType

    public QueryRangeType rangeType([QueryRangeType rangeType])

#### Parameters

rangeType  

#### Return Value

### Method status

Gets or sets the status of an object.

    public int status([int value])

#### Parameters

value  

#### Return Value

The current status of the object.

#### Remarks

The following values are possible for the status:

-   0 – Status Open.
-   1 – Status Lock.
-   2 – Status Hide.

### Method table

Gets or sets the table ID that is associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID that is associated with the object.

### Method tableSelector

    public TableId tableSelector([TableId value])

#### Parameters

value  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method typeof

    public int typeof()

#### Return Value

### Method valid

    public boolean valid()

#### Return Value

### Method value

Gets or sets the value that queried records must match to be retrieved.

    public str value([str value])

#### Parameters

value  

#### Return Value

The string value for the range.

### Method associateRangeNodeToCompositeQuery

    public void associateRangeNodeToCompositeQuery()

### Method finalize

    public void finalize()

## Class QueryBuildStaticlink
    class QueryBuildStaticlink extends Object

The QueryBuildStaticLink class provides the information about the static links that are defined on a QueryBuildDataSource class.

### Remarks

### Examples

### Methods

| Method                 | Description                                                         |
|------------------------|---------------------------------------------------------------------|
| public FieldId field() | Provides the field information on which the static link is defined/ |
| public AnyType value() | Gets the value of the field on which the static link is defined.    |
| public void finalize() |                                                                     |

### Method field

Provides the field information on which the static link is defined/

    public FieldId field()

#### Return Value

The FieldId value of the field on which the static link is defined.

### Method value

Gets the value of the field on which the static link is defined.

    public AnyType value()

#### Return Value

The value of the static link.

### Method finalize

    public void finalize()

## Class QueryFilter
    class QueryFilter extends Object

### Remarks

### Examples

### Methods

| Method                                                        | Description                                          |
|---------------------------------------------------------------|------------------------------------------------------|
| public QueryBuildDataSource dataSource()                      |                                                      |
| public FieldName field()                                      |                                                      |
| public QueryRangeType rangeType(\[QueryRangeType rangeType\]) |                                                      |
| public int status(\[int status\])                             |                                                      |
| public str toString()                                         | Returns a string that represents the current object. |
| public str value(\[str value\])                               |                                                      |
| public void finalize()                                        |                                                      |

### Method dataSource

    public QueryBuildDataSource dataSource()

#### Return Value

### Method field

    public FieldName field()

#### Return Value

### Method rangeType

    public QueryRangeType rangeType([QueryRangeType rangeType])

#### Parameters

rangeType  

#### Return Value

### Method status

    public int status([int status])

#### Parameters

status  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method value

    public str value([str value])

#### Parameters

value  

#### Return Value

### Method finalize

    public void finalize()

## Class QueryGroupByField
    class QueryGroupByField extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                  | Description |
|---------------------------------------------------------|-------------|
| public boolean autoHeader(\[boolean value\])            |             |
| public int autoHeaderDetailLevel(\[int value\])         |             |
| public boolean autoSum(\[boolean value\])               |             |
| public int autoSumDetailLevel(\[int value\])            |             |
| public QueryBuildDataSource dataSource()                |             |
| public int fieldID()                                    |             |
| public TableId tableSelector(\[TableId tableSelector\]) |             |
| public void finalize()                                  |             |

### Method autoHeader

    public boolean autoHeader([boolean value])

#### Parameters

value  

#### Return Value

### Method autoHeaderDetailLevel

    public int autoHeaderDetailLevel([int value])

#### Parameters

value  

#### Return Value

### Method autoSum

    public boolean autoSum([boolean value])

#### Parameters

value  

#### Return Value

### Method autoSumDetailLevel

    public int autoSumDetailLevel([int value])

#### Parameters

value  

#### Return Value

### Method dataSource

    public QueryBuildDataSource dataSource()

#### Return Value

### Method fieldID

    public int fieldID()

#### Return Value

### Method tableSelector

    public TableId tableSelector([TableId tableSelector])

#### Parameters

tableSelector  

#### Return Value

### Method finalize

    public void finalize()

## Class QueryHavingFilter
    class QueryHavingFilter extends TreeNode

### Remarks

### Examples

### Methods

| Method                                          | Description                                                                                                                               |
|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public AggregateFunction aggregateFunction()    |                                                                                                                                           |
| public QueryBuildDataSource dataSource()        |                                                                                                                                           |
| public boolean enabled(\[boolean value\])       | Determines whether to enable or disable the object.                                                                                       |
| public FieldId field(\[FieldId value\])         | Gets or sets the field ID associated with the object.                                                                                     |
| public int fieldArrayIndex()                    |                                                                                                                                           |
| public FieldName fieldName()                    |                                                                                                                                           |
| public str label(\[str value\])                 | Gets or sets the label for a control.                                                                                                     |
| public str name(\[str value\])                  | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public str prompt()                             |                                                                                                                                           |
| public int status(\[int value\])                | Gets or sets the status of an object.                                                                                                     |
| public TableId table(\[TableId value\])         | Gets or sets the table ID that is associated with the object.                                                                             |
| public TableId tableSelector(\[TableId value\]) |                                                                                                                                           |
| public str toString()                           | Returns a string that represents the current object.                                                                                      |
| public int typeof()                             |                                                                                                                                           |
| public boolean valid()                          |                                                                                                                                           |
| public str value(\[str value\])                 |                                                                                                                                           |
| public void finalize()                          |                                                                                                                                           |

### Method aggregateFunction

    public AggregateFunction aggregateFunction()

#### Return Value

### Method dataSource

    public QueryBuildDataSource dataSource()

#### Return Value

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property enables controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method field

Gets or sets the field ID associated with the object.

    public FieldId field([FieldId value])

#### Parameters

value  

#### Return Value

The current value of the field ID associated with the object.

### Method fieldArrayIndex

    public int fieldArrayIndex()

#### Return Value

### Method fieldName

    public FieldName fieldName()

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

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method prompt

    public str prompt()

#### Return Value

### Method status

Gets or sets the status of an object.

    public int status([int value])

#### Parameters

value  

#### Return Value

The current value of the status of the object.

### Method table

Gets or sets the table ID that is associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID that is associated with the object.

### Method tableSelector

    public TableId tableSelector([TableId value])

#### Parameters

value  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method typeof

    public int typeof()

#### Return Value

### Method valid

    public boolean valid()

#### Return Value

### Method value

    public str value([str value])

#### Parameters

value  

#### Return Value

### Method finalize

    public void finalize()

## Class QueryOrderByField
    class QueryOrderByField extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                  | Description |
|---------------------------------------------------------|-------------|
| public boolean autoHeader(\[boolean value\])            |             |
| public int autoHeaderDetailLevel(\[int value\])         |             |
| public boolean autoSum(\[boolean value\])               |             |
| public int autoSumDetailLevel(\[int value\])            |             |
| public QueryBuildDataSource dataSource()                |             |
| public SortOrder direction()                            |             |
| public int fieldID()                                    |             |
| public TableId tableSelector(\[TableId tableSelector\]) |             |
| public void finalize()                                  |             |

### Method autoHeader

    public boolean autoHeader([boolean value])

#### Parameters

value  

#### Return Value

### Method autoHeaderDetailLevel

    public int autoHeaderDetailLevel([int value])

#### Parameters

value  

#### Return Value

### Method autoSum

    public boolean autoSum([boolean value])

#### Parameters

value  

#### Return Value

### Method autoSumDetailLevel

    public int autoSumDetailLevel([int value])

#### Parameters

value  

#### Return Value

### Method dataSource

    public QueryBuildDataSource dataSource()

#### Return Value

### Method direction

    public SortOrder direction()

#### Return Value

### Method fieldID

    public int fieldID()

#### Return Value

### Method tableSelector

    public TableId tableSelector([TableId tableSelector])

#### Parameters

tableSelector  

#### Return Value

### Method finalize

    public void finalize()

## Class QueryRun
    class QueryRun extends ObjectRun

The QueryRun class traverses tables in the database, fetches records that satisfy constraints that are given by the user, and helps to gather such constraints from user input.

### Remarks

QueryRun objects are used to traverse tables in the database and fetch records that satisfy the constraints that are given by the user. A QueryRun object may interact with the user to let the user enter such constraints. Queries are used internally by reports to delineate and fetch the data to be presented in the report. A QueryRun object relies on a Query object to define the structure of the query (for example, which tables are searched and how the records are sorted). A QueryRun object defines the dynamic behavior of the query, whereas a Query object defines the static characteristics of the query.

### Examples

In the following example, it is assumed that there is a query named Customer in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT), and that it has one data source, the CustTable table.

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

### Methods

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
| public str name(\[str value\])                                                                                 | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
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

### Method allowCheck

    public boolean allowCheck([boolean value])

#### Parameters

value  

#### Return Value

### Method allowCrossCompany

    public boolean allowCrossCompany([boolean value])

#### Parameters

value  

#### Return Value

### Method canPage

    public boolean canPage([boolean skipOrderByCheck], [boolean throwIfNotPagable], [boolean isValuePaging])

#### Parameters

skipOrderByCheck  

<!-- -->

throwIfNotPagable  

<!-- -->

isValuePaging  

#### Return Value

### Method changed

Determines whether the specified data source has fetched a new value since the last call to the QueryRun.next method.

    public boolean changed(TableId table, [int occurrence])

#### Parameters

table  
The data source to check; optional. If more than one data source is assigned to a given table, this argument can be used to determine which data source to check.

<!-- -->

occurrence  
The data source to check; optional. If more than one data source is assigned to a given table, this argument can be used to determine which data source to check.

#### Return Value

true if the specified data source has changed since the last call to QueryRun.next; otherwise, false.

#### Remarks

This method is useful when data sources are hierarchically structured. A more embedded data source may change many times (such as the customer transactions). This occurs every time that a less embedded data source (such as the customer table) fetches a new record (another customer). The changedNo method can be used instead of this function.

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

### Method changedNo

    public boolean changedNo(int dataSourceNo)

#### Parameters

dataSourceNo  

#### Return Value

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

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

### Method description

    public str description([str value])

#### Parameters

value  

#### Return Value

### Method equal

Determines whether the specified object is equal to the current object.

    public boolean equal(Object obj)

#### Parameters

obj  

#### Return Value

true if the specified object is equal to the current object; otherwise, false.

#### Remarks

The default implementation of the Object::equal method supports only reference equality. However, derived classes can override the Object::equal method to support value equality.

### Method form

    public str form([str value])

#### Parameters

value  

#### Return Value

### Method get

Retrieves the record fetched by the previous call to next method.

    public Common get(TableId table, [int occurrence])

#### Parameters

table  
The data source to be addressed; optional. The number of the data source with the given table; 1-based. If more than one data source has the same table assigned to it, this (optional) parameter can be used to specify which one is to be addressed. It specifies the number of the data source with the given table. Thus, if the CustTable table is assigned to two data sources, and the second data source is required, this argument should have the value 2.

<!-- -->

occurrence  
The data source to be addressed; optional. The number of the data source with the given table; 1-based. If more than one data source has the same table assigned to it, this (optional) parameter can be used to specify which one is to be addressed. It specifies the number of the data source with the given table. Thus, if the CustTable table is assigned to two data sources, and the second data source is required, this argument should have the value 2.

#### Return Value

Returns the record fetched from the data source identified by the arguments.

#### Remarks

The data source from which to retrieve the record is specified by the table assigned to the data source and by an optional parameter. Instead of supplying the table (and optional parameter), you can use the getNo method, which takes the data source number as an argument.

### Method getImpExpDataContractType

    public System.Type getImpExpDataContractType()

#### Return Value

### Method getNo

Retrieves the record fetched by the previous call to QueryRun.next Method.

    public Common getNo(int dataSourceNo)

#### Parameters

dataSourceNo  
The number of the data source from which to get the currently selected record.

#### Return Value

Returns the record fetched for the data source identified by the argument.

#### Remarks

The data source from which to retrieve the record is specified by the number of the data source. The data sources are counted consecutively, starting from 1. The QueryRun.get Method method can be used instead; that method is supplied with the table (and an optional parameter), that defines the data source.

#### Examples

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

### Method importable

    public boolean importable()

#### Return Value

### Method interactive

    public boolean interactive([boolean value])

#### Parameters

value  

#### Return Value

### Method isPositionPagingEnabled

    public boolean isPositionPagingEnabled()

#### Return Value

### Method isQueryTimedout

    public boolean isQueryTimedout()

#### Return Value

### Method isValueBasedPagingEnabled

    public boolean isValueBasedPagingEnabled()

#### Return Value

### Method literals

    public int literals([int value])

#### Parameters

value  

#### Return Value

### Method loadCsv

    public Guid loadCsv(str fileName)

#### Parameters

fileName  

#### Return Value

### Method loadXml

    public Guid loadXml(str fileName)

#### Parameters

fileName  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, or classes.

### Method newObject

    public QueryRun newObject(AnyType source)

#### Parameters

source  

#### Return Value

### Method next

Retrieves the next record from the query.

    public boolean next()

#### Return Value

true if the next record is available and can be fetched with the getNo method or get method; false if no there are no more records that satisfy the constraint set up in the query.

#### Remarks

The changed method or changedNo method can be used to check whether the record from the given data source has changed since the previous call to the next method.

#### Examples

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

### Method nextUniqueId

    public int nextUniqueId([int value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method pack

    public container pack([boolean doCheck])

#### Parameters

doCheck  

#### Return Value

### Method prompt

Presents, to the user, the options for defining the records to be fetched by the query.

    public boolean prompt()

#### Return Value

true if the user clicked OK and the search is to continue; false if the user clicked Cancel to stop the search.

#### Remarks

The user is presented with a form to give ranges that define constraints to be fulfilled by the fetched records. Or the user may add new fields to delimit, change the sorting, and so on. This method can be overloaded to prompt the user in an application-defined way instead of in through the predefined query form. Or this method can be overloaded to avoid giving the user control over which records are fetched. To produce these results, do not call the inherited method. In any case, the function should return true if the query is to continue, and false otherwise.

#### Examples

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

### Method query

    public Query query([Query query])

#### Parameters

query  

#### Return Value

### Method queryType

    public int queryType([int value])

#### Parameters

value  

#### Return Value

### Method recordLevelSecurity

    public boolean recordLevelSecurity([boolean value])

#### Parameters

value  

#### Return Value

### Method report

    public ReportRun report()

#### Return Value

### Method reportRun

    public ReportRun reportRun()

#### Return Value

### Method saved

    public boolean saved()

#### Return Value

### Method saveUserSetup

Saves the user setup.

    public boolean saveUserSetup([boolean saveIt])

#### Parameters

saveIt  

#### Return Value

true if the setup was successfully saved; otherwise false.

### Method searchable

    public boolean searchable([boolean value])

#### Parameters

value  

#### Return Value

### Method setCursor

    public boolean setCursor(Common record, [int occurrence])

#### Parameters

record  

<!-- -->

occurrence  

#### Return Value

### Method setRecord

    public boolean setRecord(Common record, [int occurrence])

#### Parameters

record  

<!-- -->

occurrence  

#### Return Value

### Method title

    public str title([str value])

#### Parameters

value  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method userUpdate

    public boolean userUpdate([boolean value])

#### Parameters

value  

#### Return Value

### Method version

    public int version([int value])

#### Parameters

value  

#### Return Value

### Method getQueryRowCount

    public static int getQueryRowCount(Query query, int maxRows)

#### Parameters

query  

<!-- -->

maxRows  

#### Return Value

### Method runAndPopulate

    public static int runAndPopulate(Query sourceRuery, Common targetTable, Map queryAliasesAndTargetColumnsMap)

#### Parameters

sourceRuery  

<!-- -->

targetTable  

<!-- -->

queryAliasesAndTargetColumnsMap  

#### Return Value

### Method run

Opens a form used to obtain information about the query from the user, and fetches the matching records.

    public void run()

#### Remarks

Running the query will find the records that satisfy the constraints entered by the user. However, running the query in this manner has no side effects. In order to be useful, one or more of the inherited methods must be overloaded.

### Method new

Initializes a new instance of the Object class.

    public void new(AnyType source)

#### Parameters

source  

#### Remarks

When you pass an instance of the Query class into this constructor of the QueryRun class, a copy of the Query object is created. Changes that are made to this copy of the Query object do not affect the original Query object.

### Method addPageRange

    public void addPageRange([Int64 startingPosition], [Int64 numberOfRecordsToFetch])

#### Parameters

startingPosition  

<!-- -->

numberOfRecordsToFetch  

### Method reset

    public void reset()

### Method setImportSession

    public void setImportSession(Guid importSession)

#### Parameters

importSession  

### Method setQuerytimeout

    public void setQuerytimeout(int seconds, [boolean raiseException])

#### Parameters

seconds  

<!-- -->

raiseException  

### Method init

    public void init()

### Method enablePositionPaging

    public void enablePositionPaging([boolean enabled])

#### Parameters

enabled  

### Method shred

    public void shred(Guid importSession)

#### Parameters

importSession  

### Method enableValueBasedPaging

    public void enableValueBasedPaging([boolean enable])

#### Parameters

enable  

### Method bulkNext

    public void bulkNext([boolean fetchAllData])

#### Parameters

fetchAllData  

### Method applyValueBasedPaging

    public void applyValueBasedPaging([Common sourceCursor], [boolean isForward])

#### Parameters

sourceCursor  

<!-- -->

isForward  



