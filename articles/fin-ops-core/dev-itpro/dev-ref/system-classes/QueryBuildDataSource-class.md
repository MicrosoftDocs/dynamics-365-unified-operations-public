---
title: QueryBuildDataSource class
description: This topic describes the QueryBuildDataSource class.
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

# Class QueryBuildDataSource

[!include [banner](../../includes/banner.md)]

```xpp
class QueryBuildDataSource extends TreeNode
```

The QueryBuildDataSource class provides the building blocks that queries are made of.

## Remarks

Data sources are arranged in hierarchies that define the sequence in which records are fetched from the tables that are assigned to the data sources. Each data source defines the order in which the records are fetched, and also the criteria that must be met by the selected records. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

```xpp
{    QueryBuildDataSource ds;    Query q = new Query();        ds = q.addDataSource(        TableNum(CustTable));}
```

## Methods

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
| public str name(\[str value\])                                                                                                                               | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
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
| public QueryBuildStaticlink staticlink(int staticlinkNo)                                                                                                     | Returns a static Link object on the query�s data source.                                                                                  |
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

## Method addAllFields

```xpp
public int addAllFields(TableName tableName)
```

### Parameters - addAllFields

tableName  

### Return Value - addAllFields

## Method addDataSource

Adds a data source that is embedded in this data source.

```xpp
public QueryBuildDataSource addDataSource(AnyType arg, [str name], [boolean emptyFieldList])
```

### Parameters - addDataSource

arg  

<!-- -->

name  

<!-- -->

emptyFieldList  

### Return Value - addDataSource

The new data source.

### Remarks - addDataSource

Top-level data sources are created by using the addDataSource method.

## Method addDynalink

```xpp
public QueryBuildDynalink addDynalink(FieldId field, Common dynamicFile, FieldId dynamicField, [int fieldArrayIndex], [int dynamicFieldArrayIndex])
```

### Parameters - addDynalink

field  

<!-- -->

dynamicFile  

<!-- -->

dynamicField  

<!-- -->

fieldArrayIndex  

<!-- -->

dynamicFieldArrayIndex  

### Return Value - addDynalink

## Method addForeignkeyRelation

```xpp
public QueryBuildLink addForeignkeyRelation(str relatedTableRole, [str parentDatasourceName])
```

### Parameters - addForeignkeyRelation

relatedTableRole  

<!-- -->

parentDatasourceName  

### Return Value - addForeignkeyRelation

## Method addGroupByField

```xpp
public QueryGroupByField addGroupByField(FieldId fieldID, [int arrayIndex])
```

### Parameters - addGroupByField

fieldID  

<!-- -->

arrayIndex  

### Return Value - addGroupByField

## Method addLink

```xpp
public QueryBuildLink addLink(FieldId parentField, FieldId thisField, [str parentDatasourceName])
```

### Parameters - addLink

parentField  

<!-- -->

thisField  

<!-- -->

parentDatasourceName  

### Return Value - addLink

## Method addOrderByAggregateField

```xpp
public QueryOrderByField addOrderByAggregateField(SelectionField fieldType, FieldId fieldID, [SortOrder direction], [int arrayIndex])
```

### Parameters - addOrderByAggregateField

fieldType  

<!-- -->

fieldID  

<!-- -->

direction  

<!-- -->

arrayIndex  

### Return Value - addOrderByAggregateField

## Method addOrderByCalculationField

```xpp
public QueryOrderByField addOrderByCalculationField(Microsoft.Dynamics.AX.Analytics.CalculationModel.NumericExpression calculation, [SortOrder direction])
```

### Parameters - addOrderByCalculationField

calculation  

<!-- -->

direction  

### Return Value - addOrderByCalculationField

## Method addOrderByField

```xpp
public QueryOrderByField addOrderByField(FieldId fieldID, [SortOrder direction], [int arrayIndex])
```

### Parameters - addOrderByField

fieldID  

<!-- -->

direction  

<!-- -->

arrayIndex  

### Return Value - addOrderByField

## Method addRange

Adds a range to the data source.

```xpp
public QueryBuildRange addRange(FieldId field, [int arrayIndex], [QueryRangeType rangeType])
```

### Parameters - addRange

field  

<!-- -->

arrayIndex  

<!-- -->

rangeType  

### Return Value - addRange

A new range for the data source.

### Remarks - addRange

Ranges define the values that records from the data source's table must satisfy. Several range values can exist for the same field in a particular data source. In this case, the values are included in the query if the record qualifies for any of the values that are supplied. When ranges are included for multiple fields, only records that satisfy the constraints that are supplied by both criteria are included. The constraints are specified in the value method.

## Method addSortField

```xpp
public int addSortField(FieldId sortField, [SortOrder direction], [int arrayIndex])
```

### Parameters - addSortField

sortField  

<!-- -->

direction  

<!-- -->

arrayIndex  

### Return Value - addSortField

## Method addSortIndex

```xpp
public int addSortIndex(IndexId index)
```

### Parameters - addSortIndex

index  

### Return Value - addSortIndex

## Method allowAdd

```xpp
public int allowAdd([int value])
```

### Parameters - allowAdd

value  

### Return Value - allowAdd

## Method applyFilter

```xpp
public boolean applyFilter(FilterValue filterValue)
```

### Parameters - applyFilter

filterValue  

### Return Value - applyFilter

## Method autoHeader

```xpp
public boolean autoHeader(FieldId field, [boolean orderNo])
```

### Parameters - autoHeader

field  

<!-- -->

orderNo  

### Return Value - autoHeader

## Method autoHeaderDetailLevel

```xpp
public int autoHeaderDetailLevel(FieldId field, [int orderNo])
```

### Parameters - autoHeaderDetailLevel

field  

<!-- -->

orderNo  

### Return Value - autoHeaderDetailLevel

## Method autoSum

```xpp
public boolean autoSum(FieldId field, [boolean orderNo])
```

### Parameters - autoSum

field  

<!-- -->

orderNo  

### Return Value - autoSum

## Method autoSumDetailLevel

```xpp
public int autoSumDetailLevel(FieldId field, [int orderNo])
```

### Parameters - autoSumDetailLevel

field  

<!-- -->

orderNo  

### Return Value - autoSumDetailLevel

## Method changedNo

```xpp
public boolean changedNo()
```

### Return Value - changedNo

## Method childDataSourceCount

```xpp
public int childDataSourceCount()
```

### Return Value - childDataSourceCount

## Method childDataSourceNo

```xpp
public QueryBuildDataSource childDataSourceNo(int dataSourceNo)
```

### Parameters - childDataSourceNo

dataSourceNo  

### Return Value - childDataSourceNo

## Method company

```xpp
public str company([str value])
```

### Parameters - company

value  

### Return Value - company

## Method concurrencyModel

```xpp
public int concurrencyModel([int value])
```

### Parameters - concurrencyModel

value  

### Return Value - concurrencyModel

## Method dynalink

```xpp
public QueryBuildDynalink dynalink(int dynalinkNo)
```

### Parameters - dynalink

dynalinkNo  

### Return Value - dynalink

## Method dynalinkCount

```xpp
public int dynalinkCount()
```

### Return Value - dynalinkCount

## Method embedded

```xpp
public boolean embedded()
```

### Return Value - embedded

## Method enabled

Determines whether to enable or disable the object.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property enables controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

## Method existsMeanOrExists

```xpp
public boolean existsMeanOrExists([boolean value])
```

### Parameters - existsMeanOrExists

value  

### Return Value - existsMeanOrExists

## Method fetchMode

```xpp
public int fetchMode([int value])
```

### Parameters - fetchMode

value  

### Return Value - fetchMode

## Method fields

```xpp
public QueryBuildFieldList fields()
```

### Return Value - fields

## Method file

```xpp
public TableId file()
```

### Return Value - file

## Method findRange

```xpp
public QueryBuildRange findRange(FieldId field, [int occurrence], [int arrayIndex])
```

### Parameters - findRange

field  

<!-- -->

occurrence  

<!-- -->

arrayIndex  

### Return Value - findRange

## Method firstFast

Determines whether to retrieve the first record from the query before the other records.

```xpp
public boolean firstFast([boolean value])
```

### Parameters - firstFast

value  

### Return Value - firstFast

true if the first record is retrieved first; otherwise, false.

### Remarks - firstFast

The firstFast property enables some database systems to optimize record retrieval, which improves performance. If the database does not support this property, it is ignored.

## Method firstOnly

```xpp
public boolean firstOnly([boolean value])
```

### Parameters - firstOnly

value  

### Return Value - firstOnly

## Method getMostRestrictedQueryBuildRangeStatus

```xpp
public int getMostRestrictedQueryBuildRangeStatus(FieldId field, [int occurrence], [int arrayIndex])
```

### Parameters - getMostRestrictedQueryBuildRangeStatus

field  

<!-- -->

occurrence  

<!-- -->

arrayIndex  

### Return Value - getMostRestrictedQueryBuildRangeStatus

## Method getNo

```xpp
public Common getNo()
```

### Return Value - getNo

## Method id

```xpp
public int id()
```

### Return Value - id

## Method indexIsHint

```xpp
public boolean indexIsHint(boolean arg)
```

### Parameters - indexIsHint

arg  

### Return Value - indexIsHint

## Method isPartOfSubQueryInBaseQuery

```xpp
public boolean isPartOfSubQueryInBaseQuery()
```

### Return Value - isPartOfSubQueryInBaseQuery

## Method joined

```xpp
public boolean joined()
```

### Return Value - joined

## Method joinedDataSources

```xpp
public container joinedDataSources()
```

### Return Value - joinedDataSources

## Method joinMode

```xpp
public int joinMode([int value])
```

### Parameters - joinMode

value  

### Return Value - joinMode

## Method label

Gets or sets the label for a control.

```xpp
public str label([str value])
```

### Parameters - label

value  

### Return Value - label

The current value of the label string.

### Remarks - label

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

## Method level

```xpp
public int level()
```

### Return Value - level

## Method link

```xpp
public QueryBuildLink link(int associationNo)
```

### Parameters - link

associationNo  

### Return Value - link

## Method linkCount

```xpp
public int linkCount()
```

### Return Value - linkCount

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

## Method oneToOneDataSources

```xpp
public container oneToOneDataSources()
```

### Return Value - oneToOneDataSources

## Method orderMode

```xpp
public int orderMode([int value])
```

### Parameters - orderMode

value  

### Return Value - orderMode

## Method parentDataSource

```xpp
public QueryBuildDataSource parentDataSource()
```

### Return Value - parentDataSource

## Method policyContext

```xpp
public str policyContext([str value])
```

### Parameters - policyContext

value  

### Return Value - policyContext

## Method range

```xpp
public QueryBuildRange range(int rangeNo)
```

### Parameters - range

rangeNo  

### Return Value - range

## Method rangeCount

```xpp
public int rangeCount()
```

### Return Value - rangeCount

## Method rangeField

```xpp
public QueryBuildRange rangeField(FieldId field, [int occurrence])
```

### Parameters - rangeField

field  

<!-- -->

occurrence  

### Return Value - rangeField

## Method relations

```xpp
public boolean relations([boolean value])
```

### Parameters - relations

value  

### Return Value - relations

## Method selectionCount

```xpp
public int selectionCount()
```

### Return Value - selectionCount

## Method selectWithRepeatableRead

```xpp
public boolean selectWithRepeatableRead([boolean value])
```

### Parameters - selectWithRepeatableRead

value  

### Return Value - selectWithRepeatableRead

## Method sortDirection

```xpp
public SortOrder sortDirection(FieldId field, [SortOrder direction])
```

### Parameters - sortDirection

field  

<!-- -->

direction  

### Return Value - sortDirection

## Method sortField

```xpp
public FieldId sortField(FieldId field)
```

### Parameters - sortField

field  

### Return Value - sortField

## Method sortFieldCount

```xpp
public int sortFieldCount()
```

### Return Value - sortFieldCount

## Method sortIndex

```xpp
public IndexId sortIndex(int indexNo)
```

### Parameters - sortIndex

indexNo  

### Return Value - sortIndex

## Method sortIndexCount

```xpp
public int sortIndexCount()
```

### Return Value - sortIndexCount

## Method staticlink

Returns a static Link object on the query�s data source.

```xpp
public QueryBuildStaticlink staticlink(int staticlinkNo)
```

### Parameters - staticlink

staticlinkNo  

### Return Value - staticlink

The static Link object at the \_staticLinkNo index.

## Method staticlinkCount

Gives the number of static links that are defined on the QueryBuildDataSource object.

```xpp
public int staticlinkCount()
```

### Return Value - staticlinkCount

The number of static links that are defined on the QueryBuildDataSource object.

## Method table

Gets or sets the table ID that is associated with the object.

```xpp
public TableId table([TableId value])
```

### Parameters - table

value  

### Return Value - table

The current value of the table ID that is associated with the object.

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method unionType

```xpp
public int unionType([int value])
```

### Parameters - unionType

value  

### Return Value - unionType

## Method uniqueId

```xpp
public int uniqueId()
```

### Return Value - uniqueId

## Method update

Determines whether the records fetched by this data source can be updated.

```xpp
public boolean update([boolean value])
```

### Parameters - update

value  

### Return Value - update

true if the records can be updated; otherwise, false.

### Remarks - update

To update the records, start a separate transaction by using the ttsBegin and ttsCommit methods.

## Method clearLinks

```xpp
public void clearLinks()
```

## Method clearDynalinks

```xpp
public void clearDynalinks()
```

## Method clearRange

```xpp
public void clearRange(FieldId field, [int occurrence])
```

### Parameters - clearRange

field  

<!-- -->

occurrence  

## Method sortClear

```xpp
public void sortClear()
```

## Method finalize

```xpp
public void finalize()
```

## Method addSelectionFieldWithAlias

```xpp
public void addSelectionFieldWithAlias(str alias, FieldId field, [SelectionField fieldType])
```

### Parameters - addSelectionFieldWithAlias

alias  

<!-- -->

field  

<!-- -->

fieldType  

## Method addCalculationField

```xpp
public void addCalculationField(Microsoft.Dynamics.AX.Analytics.CalculationModel.NumericExpression calculation, str alias)
```

### Parameters - addCalculationField

calculation  

<!-- -->

alias  

## Method addForeignKeyDynalink

```xpp
public void addForeignKeyDynalink(Common dynamicFile, str relatedRole)
```

### Parameters - addForeignKeyDynalink

dynamicFile  

<!-- -->

relatedRole  

## Method addRelation

```xpp
public void addRelation(DictRelation relation, [TableScope tableScope])
```

### Parameters - addRelation

relation  

<!-- -->

tableScope  

## Method clearSortIndex

```xpp
public void clearSortIndex()
```

## Method clearRanges

Deletes all ranges that are associated with the data source.

```xpp
public void clearRanges()
```

### Examples - clearRanges

The following example adds ranges and then removes them from a data source.

```xpp
Query Q = new Query(); 
QueryBuildDataSource ds = q.addDataSource(TableNum(CustTable)); 
QueryBuildRange r = ds.addRange(FieldNum(CustTable, recId)); 
print ds.rangeCount(); 
ds.clearRanges(); 
print ds.rangeCount(); 
pause;
```

## Method linkFields

```xpp
public void linkFields(str parentField, str thisField, [str parentDatasourceName])
```

### Parameters - linkFields

parentField  

<!-- -->

thisField  

<!-- -->

parentDatasourceName  

## Method addSelectionField

```xpp
public void addSelectionField(FieldId field, [SelectionField fieldType], [int arrayIndex])
```

### Parameters - addSelectionField

field  

<!-- -->

fieldType  

<!-- -->

arrayIndex  

