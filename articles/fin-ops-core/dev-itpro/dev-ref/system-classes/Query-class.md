---
title: Query class
description: This topic describes the Query class.
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

# Class Query

[!include [banner](../../includes/banner.md)]


```xpp
class Query extends TreeNode
```

The Query class embodies the structure of a query.

## Remarks

Objects of this kind are not used to fetch records from the database. Instead, use a QueryRun object that can be assigned a query object. The dynamic behavior of a query is defined by the QueryRun class. The static behavior is defined by the Query class. Queries contain one or more data sources that correspond to tables in the database. The data sources are specified by using QueryBuildDataSource objects. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. Queries are used when the user wants to modify the records that are fetched by, for example, a form. One or more ranges are often added to an existing data source. Ranges are specified by using queryBuildRange objects.

## Examples

The following example creates a query object that is used to create a QueryRun object.

```xpp
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
```

## Methods

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
| public str name(\[str value\])                                                                                                                                         | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
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
| public boolean skipAutoOrderBy(\[boolean value\])                                                                                                                           | Allows to skip the generation of an automatic Order By clause in case no Order By field was specified explicitly.                                             |

## Method addBaseQuery

```xpp
public Query addBaseQuery(str queryName)
```

### Parameters - addBaseQuery

queryName  

### Return Value - addBaseQuery

## Method addDataSource

Adds a data source to the top level of the query.

```xpp
public QueryBuildDataSource addDataSource(TableId table, [str name], [UnionType unionType], [boolean emptyFieldList])
```

### Parameters - addDataSource

table  

<!-- -->

name  

<!-- -->

unionType  

<!-- -->

emptyFieldList  

### Return Value - addDataSource

The data source object that is created.

### Remarks - addDataSource

A name value can be specified for documentation purposes. You can use the name to fetch the data source by using the dataSourceName method.

## Method addHavingFilter

```xpp
public QueryHavingFilter addHavingFilter(QueryBuildDataSource dataSource, str fieldName, AggregateFunction aggregateFunction, [int arrayIndex])
```

### Parameters - addHavingFilter

dataSource  

<!-- -->

fieldName  

<!-- -->

aggregateFunction  

<!-- -->

arrayIndex  

### Return Value - addHavingFilter

## Method addQueryFilter

```xpp
public QueryFilter addQueryFilter(QueryBuildDataSource dataSource, str fieldName, [int arrayIndex])
```

### Parameters - addQueryFilter

dataSource  

<!-- -->

fieldName  

<!-- -->

arrayIndex  

### Return Value - addQueryFilter

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

## Method allowHavingFilters

```xpp
public boolean allowHavingFilters(QueryBuildDataSource dataSource, FieldName fieldName, AggregateFunction aggregateFunction)
```

### Parameters - allowHavingFilters

dataSource  

<!-- -->

fieldName  

<!-- -->

aggregateFunction  

### Return Value - allowHavingFilters

## Method allowQueryFilters

```xpp
public boolean allowQueryFilters(QueryBuildDataSource dataSource)
```

### Parameters - allowQueryFilters

dataSource  

### Return Value - allowQueryFilters

## Method changedBy

Gets or sets the name of the user who last changed the Query object.

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  
The name of the user who last changed the Query object; optional.

### Return Value - changedBy

The name of the user who last changed the Query object.

## Method changedDate

Gets or sets the date an application object was last changed.

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  

### Return Value - changedDate

The date an application object was last changed.

## Method changedTime

Gets or sets the time an application object was last changed.

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  

### Return Value - changedTime

The time an application object was last changed.

## Method childDataSourceCount

Counts the number of data sources that are related to the query.

```xpp
public int childDataSourceCount()
```

### Return Value - childDataSourceCount

The number of data sources that are related to the query.

### Remarks - childDataSourceCount

This method is used for the top-level query. To determine the number of data sources that are embedded in another data source, use the childDataSourceCount method.

## Method childDataSourceNo

Returns the child data source that corresponds to the specified number.

```xpp
public QueryBuildDataSource childDataSourceNo(int dataSourceNo)
```

### Parameters - childDataSourceNo

dataSourceNo  
The number of the child data source.

### Return Value - childDataSourceNo

The child data source that has the specified number.

### Remarks - childDataSourceNo

The number that is specified must represent a data source that is immediately underneath the query. Typically, there is only one such data source.

## Method containsAggregateFields

```xpp
public boolean containsAggregateFields()
```

### Return Value - containsAggregateFields

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

## Method dataSourceCount

Returns the total number of data sources for the query, including any embedded data sources.

```xpp
public int dataSourceCount()
```

### Return Value - dataSourceCount

The number of data sources for this query.

### Remarks - dataSourceCount

The number is the transitive number of data sources and includes any embedded data sources.

## Method dataSourceName

Returns the data source that has the specified name.

```xpp
public QueryBuildDataSource dataSourceName(str name)
```

### Parameters - dataSourceName

name  
The string that contains the name of the data source to return.

### Return Value - dataSourceName

The data source that has the specified name; an uninitialized object if the specified data source does not exist.

## Method dataSourceNo

Returns the data source that is specified by the data source number.

```xpp
public QueryBuildDataSource dataSourceNo(int dataSourceNo)
```

### Parameters - dataSourceNo

dataSourceNo  
The number of the data source.

### Return Value - dataSourceNo

The data source that has the specified number; an uninitialized object if the specified data source does not exist.

## Method dataSourceTable

Returns the data source that the specified table is assigned to.

```xpp
public QueryBuildDataSource dataSourceTable(TableId table, [int occurrence])
```

### Parameters - dataSourceTable

table  
An integer that is used when more than one data source uses the specified table ID; optional. The default value is 1, which specifies the first (and typically only) instance.

<!-- -->

occurrence  
An integer that is used when more than one data source uses the specified table ID; optional. The default value is 1, which specifies the first (and typically only) instance.

### Return Value - dataSourceTable

The data source that the specified table is assigned to.

### Remarks - dataSourceTable

The data source can also be retrieved by calling the dataSourceNo method or the dataSourceName method.

## Method dataSourceUniqueId

```xpp
public QueryBuildDataSource dataSourceUniqueId(int uniqueId)
```

### Parameters - dataSourceUniqueId

uniqueId  

### Return Value - dataSourceUniqueId

## Method description

```xpp
public str description([str value])
```

### Parameters - description

value  

### Return Value - description

## Method equal

Evaluates whether one query is equal to another.

```xpp
public boolean equal(Object record)
```

### Parameters - equal

record  
The query to use as a comparison.

### Return Value - equal

true if the queries are equal; otherwise, false.

### Remarks - equal

"Equal" in this case means that the query is structurally identical to the query that it is compared to. The query has the same number of data sources assigned to the same files, and it has the same number of ranges.

## Method exportXML

```xpp
public str exportXML()
```

### Return Value - exportXML

## Method findHavingFilterByField

```xpp
public QueryHavingFilter findHavingFilterByField(QueryBuildDataSource dataSource, FieldName fieldName, [int occurrence], [int arrayIndex])
```

### Parameters - findHavingFilterByField

dataSource  

<!-- -->

fieldName  

<!-- -->

occurrence  

<!-- -->

arrayIndex  

### Return Value - findHavingFilterByField

## Method findQueryFilter

```xpp
public QueryFilter findQueryFilter(QueryBuildDataSource dataSource, FieldName fieldName, [int occurrence], [int arrayIndex])
```

### Parameters - findQueryFilter

dataSource  

<!-- -->

fieldName  

<!-- -->

occurrence  

<!-- -->

arrayIndex  

### Return Value - findQueryFilter

## Method firstTopLevelDataSource

```xpp
public QueryBuildDataSource firstTopLevelDataSource()
```

### Return Value - firstTopLevelDataSource

## Method forceNestedLoop

```xpp
public boolean forceNestedLoop(boolean arg)
```

### Parameters - forceNestedLoop

arg  

### Return Value - forceNestedLoop

## Method forceSelectOrder

```xpp
public boolean forceSelectOrder(boolean arg)
```

### Parameters - forceSelectOrder

arg  

### Return Value - forceSelectOrder

## Method form

```xpp
public str form([str value])
```

### Parameters - form

value  

### Return Value - form

## Method getCompanyRange

```xpp
public container getCompanyRange()
```

### Return Value - getCompanyRange

## Method getMostRestrictedQueryFilterStatus

```xpp
public int getMostRestrictedQueryFilterStatus(QueryBuildDataSource dataSource, FieldName fieldName, [int fieldId])
```

### Parameters - getMostRestrictedQueryFilterStatus

dataSource  

<!-- -->

fieldName  

<!-- -->

fieldId  

### Return Value - getMostRestrictedQueryFilterStatus

## Method getNextUniqueId

```xpp
public int getNextUniqueId()
```

### Return Value - getNextUniqueId

## Method getSQLStatement

```xpp
public str getSQLStatement([boolean noRuntimeOptimization])
```

### Parameters - getSQLStatement

noRuntimeOptimization  

### Return Value - getSQLStatement

## Method getValidTimeStateDateRange

```xpp
public container getValidTimeStateDateRange()
```

### Return Value - getValidTimeStateDateRange

## Method getValidTimeStateDateTimeRange

```xpp
public container getValidTimeStateDateTimeRange()
```

### Return Value - getValidTimeStateDateTimeRange

## Method getValidTimeStateQueryType

```xpp
public ValidTimeStateQueryType getValidTimeStateQueryType()
```

### Return Value - getValidTimeStateQueryType

## Method groupByField

```xpp
public QueryGroupByField groupByField(int index, [QueryBuildDataSource dataSource])
```

### Parameters - groupByField

index  

<!-- -->

dataSource  

### Return Value - groupByField

## Method groupByFieldCount

```xpp
public int groupByFieldCount([QueryBuildDataSource dataSource])
```

### Parameters - groupByFieldCount

dataSource  

### Return Value - groupByFieldCount

## Method hasMultipleTopLevelDataSource

```xpp
public boolean hasMultipleTopLevelDataSource()
```

### Return Value - hasMultipleTopLevelDataSource

## Method hasRangeOrFilter

```xpp
public boolean hasRangeOrFilter(QueryBuildDataSource dataSource)
```

### Parameters - hasRangeOrFilter

dataSource  

### Return Value - hasRangeOrFilter

## Method havingFilter

```xpp
public QueryHavingFilter havingFilter(int count, [QueryBuildDataSource dataSource])
```

### Parameters - havingFilter

count  

<!-- -->

dataSource  

### Return Value - havingFilter

## Method havingFilterCount

```xpp
public int havingFilterCount([QueryBuildDataSource dataSource])
```

### Parameters - havingFilterCount

dataSource  

### Return Value - havingFilterCount

## Method inReport

Determines whether the query is part of a report.

```xpp
public boolean inReport()
```

### Return Value - inReport

true if the query is part of a report (is found under a report's data sources node); otherwise, false.

### Remarks - inReport

This function is not typically used by application code. If the method returns true, the report method can be used to access the report in which the query is defined.

## Method interactive

Specifies whether the query is interactive.

```xpp
public boolean interactive([boolean value])
```

### Parameters - interactive

value  
A value that indicates whether the query is interactive; optional.

### Return Value - interactive

true if the query is interactive; otherwise, false.

### Remarks - interactive

In an interactive query, the query can, for example, present the user with a dialog box when the prompt method is called. This functionality is used when code will be submitted to a batch and in other situations where code must run unattended.

## Method isCompositeQuery

```xpp
public boolean isCompositeQuery()
```

### Return Value - isCompositeQuery

## Method isExplicitlyOrdered

```xpp
public boolean isExplicitlyOrdered()
```

### Return Value - isExplicitlyOrdered

## Method isExplicitlyGrouped

```xpp
public boolean isExplicitlyGrouped()
```

### Return Value - isExplicitlyGrouped

## Method isPureUnionAll

```xpp
public boolean isPureUnionAll()
```

### Return Value - isPureUnionAll

## Method isUnionType

```xpp
public boolean isUnionType()
```

### Return Value - isUnionType

## Method levelNo

Determines the level of indentation of the specified data source.

```xpp
public int levelNo(int dataSourceNo)
```

### Parameters - levelNo

dataSourceNo  
The data source number to determine the level for.

### Return Value - levelNo

The level number of the specified data source.

### Remarks - levelNo

The data sources are numbered consecutively, starting at 1.

## Method levelTable

Determines the tree level, in the hierarchy of data sources, of the data source that is assigned to the specified table.

```xpp
public int levelTable(TableId table, [int occurrence])
```

### Parameters - levelTable

table  
The integer that is used if more than one data source is assigned to the same table; optional.

<!-- -->

occurrence  
The integer that is used if more than one data source is assigned to the same table; optional.

### Return Value - levelTable

The level number of the query's specified data source.

## Method literals

```xpp
public int literals([int value])
```

### Parameters - literals

value  

### Return Value - literals

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method newObject

Creates a query that exists on the same client side or server side as the source query.

```xpp
public Query newObject(AnyType source)
```

### Parameters - newObject

source  
The source query.

### Return Value - newObject

The new query.

## Method nextUniqueId

```xpp
public int nextUniqueId([int value])
```

### Parameters - nextUniqueId

value  

### Return Value - nextUniqueId

## Method orderByField

```xpp
public QueryOrderByField orderByField(int index, [QueryBuildDataSource dataSource])
```

### Parameters - orderByField

index  

<!-- -->

dataSource  

### Return Value - orderByField

## Method orderByFieldCount

```xpp
public int orderByFieldCount([QueryBuildDataSource dataSource])
```

### Parameters - orderByFieldCount

dataSource  

### Return Value - orderByFieldCount

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method pack

Packs the query into a container and returns that container, so that it can be used when you create a query.

```xpp
public container pack([boolean doCheck])
```

### Parameters - pack

doCheck  
A Boolean value that indicates whether to flag an error when a data source in the query references an outside cursor, such as a link to a cursor that is foreign to the query's data source; optional. The default value is true, which enforces the constraint.

### Return Value - pack

The container that holds the query.

### Remarks - pack

The container that is created by this method can serve as input when you instantiate a query or queryRun object by using either the new method or the newObject method. Links to cursors that are foreign to the query's data source are not packed into the container. If you must pack this kind of link, you should take a snapshot of the cursor's data and construct ranges for each field.

## Method packInternals

```xpp
public container packInternals()
```

### Return Value - packInternals

## Method queryFilter

```xpp
public QueryFilter queryFilter(int count, [QueryBuildDataSource rootDataSource])
```

### Parameters - queryFilter

count  

<!-- -->

rootDataSource  

### Return Value - queryFilter

## Method queryFilterCount

```xpp
public int queryFilterCount([QueryBuildDataSource rootDataSource])
```

### Parameters - queryFilterCount

rootDataSource  

### Return Value - queryFilterCount

## Method queryType

```xpp
public int queryType([int value])
```

### Parameters - queryType

value  

### Return Value - queryType

## Method quickFilterValue

```xpp
public str quickFilterValue()
```

### Return Value - quickFilterValue

## Method quickFilterControlId

```xpp
public int quickFilterControlId()
```

### Return Value - quickFilterControlId

## Method recordLevelSecurity

```xpp
public boolean recordLevelSecurity([boolean value])
```

### Parameters - recordLevelSecurity

value  

### Return Value - recordLevelSecurity

## Method report

Returns the report in which the query is defined, if the report exists.

```xpp
public Report report()
```

### Return Value - report

The report in which the query is defined under the data sources node.

### Remarks - report

A query is not necessarily defined in the context of a report. To determine whether a query is defined in the context of a report, you can use the inReport method.

## Method saved

Indicates whether the query has been saved to disk.

```xpp
public boolean saved()
```

### Return Value - saved

true if the query has been saved to disk; otherwise, false.

## Method searchable

```xpp
public boolean searchable([boolean value])
```

### Parameters - searchable

value  

### Return Value - searchable

## Method importSession

```xpp
public Guid importSession([Guid value])
```

### Parameters - importSession

value  

### Return Value - importSession

## Method title

```xpp
public str title([str value])
```

### Parameters - title

value  

### Return Value - title

## Method topRows

```xpp
public int topRows([int value])
```

### Parameters - topRows

value  

### Return Value - topRows

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. However, the method can be overridden in a derived class so that it returns values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name, and the type of method, such as Instance or Static.

## Method userUpdate

Gets or sets a value that indicates whether the query can update the records that it fetches.

```xpp
public boolean userUpdate([boolean value])
```

### Parameters - userUpdate

value  
A Boolean value that indicates whether the query can update the records that it fetches; optional.

### Return Value - userUpdate

true if the query can currently update records that it fetches; otherwise false.

## Method validTimeStateAsOfDate

```xpp
public Date validTimeStateAsOfDate([Date asOfDate])
```

### Parameters - validTimeStateAsOfDate

asOfDate  

### Return Value - validTimeStateAsOfDate

## Method validTimeStateAsOfDateTime

```xpp
public DateTime validTimeStateAsOfDateTime([DateTime asOfDateTime])
```

### Parameters - validTimeStateAsOfDateTime

asOfDateTime  

### Return Value - validTimeStateAsOfDateTime

## Method validTimeStateFlags

```xpp
public int validTimeStateFlags([int value])
```

### Parameters - validTimeStateFlags

value  

### Return Value - validTimeStateFlags

## Method version

```xpp
public int version([int value])
```

### Parameters - version

value  

### Return Value - version

## Method xml

Returns an XML string that represents the current object.

```xpp
public str xml([int indent])
```

### Parameters - xml

indent  
The amount of indentation for the returned XML string; optional.

### Return Value - xml

An XML string that represents the current object.

### Remarks - xml

This method can be overridden to return values that are meaningful for that type.

## Method clearBaseQueries

```xpp
public void clearBaseQueries()
```

## Method addCompanyRange

```xpp
public void addCompanyRange(str companyName)
```

### Parameters - addCompanyRange

companyName  

## Method checkRangeParsingErrors

```xpp
public void checkRangeParsingErrors(boolean setCheckRangeParsingErrors)
```

### Parameters - checkRangeParsingErrors

setCheckRangeParsingErrors  

## Method clearCompanyRange

```xpp
public void clearCompanyRange()
```

## Method unpackInternals

```xpp
public void unpackInternals(container internalData)
```

### Parameters - unpackInternals

internalData  

## Method new

Creates a query object.

```xpp
public void new([AnyType source])
```

### Parameters - new

source  
The source to base the query object on; optional.

### Remarks - new

If no arguments are supplied when this method is called, a temporary query is created that is not stored in the Application Object Tree (AOT) for subsequent use.

## Method checkFieldAccess

```xpp
public void checkFieldAccess(boolean setCheckFieldAccess)
```

### Parameters - checkFieldAccess

setCheckFieldAccess  

## Method useDbCacheOnGeneratedCursors

```xpp
public void useDbCacheOnGeneratedCursors([int fetchsize])
```

### Parameters - useDbCacheOnGeneratedCursors

fetchsize  

## Method setValidTimeStateQueryType

```xpp
public void setValidTimeStateQueryType([ValidTimeStateQueryType type])
```

### Parameters - setValidTimeStateQueryType

type  

## Method validTimeStateDateRange

```xpp
public void validTimeStateDateRange([Date fromDate], [Date toDate])
```

### Parameters - validTimeStateDateRange

fromDate  

<!-- -->

toDate  

## Method clearHavingFilters

```xpp
public void clearHavingFilters([QueryBuildDataSource dataSource], [str fieldName], [int occurence], [int arrayIndex])
```

### Parameters - clearHavingFilters

dataSource  

<!-- -->

fieldName  

<!-- -->

occurence  

<!-- -->

arrayIndex  

## Method quickFilter

```xpp
public void quickFilter([str dataSourceName], [int tableId], [int fieldId], [str filterValue], [int controlId], [boolean useEqualityComparisonForStrings])
```

### Parameters - quickFilter

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

## Method finalize

```xpp
public void finalize()
```

## Method clearQueryFilters

```xpp
public void clearQueryFilters([QueryBuildDataSource dataSource], [str fieldName], [int occurence], [int arrayIndex])
```

### Parameters - clearQueryFilters

dataSource  

<!-- -->

fieldName  

<!-- -->

occurence  

<!-- -->

arrayIndex  

## Method clearOrderBy

```xpp
public void clearOrderBy()
```

## Method clearAllFields

```xpp
public void clearAllFields()
```

## Method clearGroupBy

```xpp
public void clearGroupBy()
```

## Method autoAuthzMode

```xpp
public void autoAuthzMode(AutoAuthzMode mode)
```

### Parameters - autoAuthzMode

mode  

## Method insert\_recordset

```xpp
public static void insert_recordset(Common targetCursor, Map targetToSourceMap, Query sourceQuery)
```

### Parameters - insert\_recordset

targetCursor  

<!-- -->

targetToSourceMap  

<!-- -->

sourceQuery  

## Method generateCursors

```xpp
public void generateCursors()
```

## Method checkAuthorizationOnOpenRanges

```xpp
public void checkAuthorizationOnOpenRanges(boolean setCheckAuthorizationOnOpenRanges)
```

### Parameters - checkAuthorizationOnOpenRanges

setCheckAuthorizationOnOpenRanges  

## Method addContains

```xpp
public void addContains(str containsValue, [boolean prefixSearch])
```

### Parameters - addContains

containsValue  

<!-- -->

prefixSearch  

## Method resetValidTimeStateQueryType

```xpp
public void resetValidTimeStateQueryType()
```

## Method validTimeStateDateTimeRange

```xpp
public void validTimeStateDateTimeRange([DateTime fromDateTime], [DateTime toDateTime])
```

### Parameters - validTimeStateDateTimeRange

fromDateTime  

<!-- -->

toDateTime  

