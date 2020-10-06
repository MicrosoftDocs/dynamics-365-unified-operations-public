---
title: SurrogateFKReplacementHelper class
description: This topic describes the SurrogateFKReplacementHelper class.
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

# Class SurrogateFKReplacementHelper

[!include [banner](../../includes/banner.md)]

```xpp
class SurrogateFKReplacementHelper extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                                                             | Description                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public Map addDefaultRequiredJoins(QueryBuildDataSource foreignKeyQueryBuildDataSource, str replacementFieldGroupName)                                                                                             |                                                 |
| public Map addRequiredJoins(List requiredJoinsAsRelationPathList, QueryBuildDataSource foreignKeyQueryBuildDataSource, str replacementFieldGroupName)                                                              |                                                 |
| public List displayBindings(str replacementFieldGroupName, \[boolean distinctBindingsOnly\])                                                                                                                       |                                                 |
| public List displayValuesFromQueryRun(QueryRun queryRun, str replacementFieldGroupName, \[boolean isRootPrimaryKeyDataSource\], \[boolean trimSecuredValues\], \[boolean distinctBindingsOnly\])                   |                                                 |
| public List displayValuesFromRecID(Int64 recIDValue, str replacementFieldGroupName, \[boolean trimSecuredValues\], \[boolean distinctBindingsOnly\])                                                               |                                                 |
| public List displayValuesFromRootDS(QueryBuildDataSource rootQueryBuildDataSource, boolean isPrimaryKeyDataSource, str replacementFieldGroupName, \[boolean trimSecuredValues\], \[boolean distinctBindingsOnly\]) |                                                 |
| public FilterValue displayValue(Common resolvedCursor, FieldBinding displayBinding, \[boolean isRootPrimaryKeyDataSource\])                                                                                        |                                                 |
| public str extendedDataType()                                                                                                                                                                                      |                                                 |
| public Query generateResolveReferenceQuery(List requiredJoinsAsRelationPathList, List filterValuesAsFilterValueList)                                                                                               |                                                 |
| public boolean isResolvedReferenceAmbiguous(Query query)                                                                                                                                                           |                                                 |
| public str primaryKeyTableName()                                                                                                                                                                                   |                                                 |
| public Map queryBuildDataSourceBindingsForQuery(Query query, str replacementFieldGroupName, \[boolean isRootPrimaryKeyDataSource\])                                                                                |                                                 |
| public Map queryBuildDataSourceBindingsForRootDS(QueryBuildDataSource rootQueryBuildDataSource, boolean isPrimaryKeyDataSource, str replacementFieldGroupName)                                                     |                                                 |
| public Common resolveReference(Query query, \[boolean ignoreAmbiguousReference\])                                                                                                                                  |                                                 |
| public FieldBinding surrogateForeignKeyFieldBinding()                                                                                                                                                              |                                                 |
| ::public static SurrogateFKReplacementHelper construct(FieldBinding surrogateForeignKeyBinding)                                                                                                                    |                                                 |
| ::public static SurrogateFKReplacementHelper constructForEDT(str edtName)                                                                                                                                          |                                                 |
| ::public static SurrogateFKReplacementHelper constructForPKTable(str pkTableName)                                                                                                                                  |                                                 |
| ::public static str defaultPrimaryKeyQueryDataSourceName()                                                                                                                                                         |                                                 |
| ::public static str DEPRECATED\_WorkflowCaption(str tableName, str fieldName, Int64 recIDValue)                                                                                                                    |                                                 |
| ::public static str implicitReplacementFieldGroupName()                                                                                                                                                            |                                                 |
| private void new(FieldBinding surrogateForeignKeyBinding)                                                                                                                                                          | Initializes a new instance of the Object class. |

## Method addDefaultRequiredJoins

```xpp
public Map addDefaultRequiredJoins(QueryBuildDataSource foreignKeyQueryBuildDataSource, str replacementFieldGroupName)
```

### Parameters - addDefaultRequiredJoins

foreignKeyQueryBuildDataSource  

<!-- -->

replacementFieldGroupName  

### Return Value - addDefaultRequiredJoins

## Method addRequiredJoins

```xpp
public Map addRequiredJoins(List requiredJoinsAsRelationPathList, QueryBuildDataSource foreignKeyQueryBuildDataSource, str replacementFieldGroupName)
```

### Parameters - addRequiredJoins

requiredJoinsAsRelationPathList  

<!-- -->

foreignKeyQueryBuildDataSource  

<!-- -->

replacementFieldGroupName  

### Return Value - addRequiredJoins

## Method displayBindings

```xpp
public List displayBindings(str replacementFieldGroupName, [boolean distinctBindingsOnly])
```

### Parameters - displayBindings

replacementFieldGroupName  

<!-- -->

distinctBindingsOnly  

### Return Value - displayBindings

## Method displayValuesFromQueryRun

```xpp
public List displayValuesFromQueryRun(QueryRun queryRun, str replacementFieldGroupName, [boolean isRootPrimaryKeyDataSource], [boolean trimSecuredValues], [boolean distinctBindingsOnly])
```

### Parameters - displayValuesFromQueryRun

queryRun  

<!-- -->

replacementFieldGroupName  

<!-- -->

isRootPrimaryKeyDataSource  

<!-- -->

trimSecuredValues  

<!-- -->

distinctBindingsOnly  

### Return Value - displayValuesFromQueryRun

## Method displayValuesFromRecID

```xpp
public List displayValuesFromRecID(Int64 recIDValue, str replacementFieldGroupName, [boolean trimSecuredValues], [boolean distinctBindingsOnly])
```

### Parameters - displayValuesFromRecID

recIDValue  

<!-- -->

replacementFieldGroupName  

<!-- -->

trimSecuredValues  

<!-- -->

distinctBindingsOnly  

### Return Value - displayValuesFromRecID

## Method displayValuesFromRootDS

```xpp
public List displayValuesFromRootDS(QueryBuildDataSource rootQueryBuildDataSource, boolean isPrimaryKeyDataSource, str replacementFieldGroupName, [boolean trimSecuredValues], [boolean distinctBindingsOnly])
```

### Parameters - displayValuesFromRootDS

rootQueryBuildDataSource  

<!-- -->

isPrimaryKeyDataSource  

<!-- -->

replacementFieldGroupName  

<!-- -->

trimSecuredValues  

<!-- -->

distinctBindingsOnly  

### Return Value - displayValuesFromRootDS

## Method displayValue

```xpp
public FilterValue displayValue(Common resolvedCursor, FieldBinding displayBinding, [boolean isRootPrimaryKeyDataSource])
```

### Parameters - displayValue

resolvedCursor  

<!-- -->

displayBinding  

<!-- -->

isRootPrimaryKeyDataSource  

### Return Value - displayValue

## Method extendedDataType

```xpp
public str extendedDataType()
```

### Return Value - extendedDataType

## Method generateResolveReferenceQuery

```xpp
public Query generateResolveReferenceQuery(List requiredJoinsAsRelationPathList, List filterValuesAsFilterValueList)
```

### Parameters - generateResolveReferenceQuery

requiredJoinsAsRelationPathList  

<!-- -->

filterValuesAsFilterValueList  

### Return Value - generateResolveReferenceQuery

## Method isResolvedReferenceAmbiguous

```xpp
public boolean isResolvedReferenceAmbiguous(Query query)
```

### Parameters - isResolvedReferenceAmbiguous

query  

### Return Value - isResolvedReferenceAmbiguous

## Method primaryKeyTableName

```xpp
public str primaryKeyTableName()
```

### Return Value - primaryKeyTableName

## Method queryBuildDataSourceBindingsForQuery

```xpp
public Map queryBuildDataSourceBindingsForQuery(Query query, str replacementFieldGroupName, [boolean isRootPrimaryKeyDataSource])
```

### Parameters - queryBuildDataSourceBindingsForQuery

query  

<!-- -->

replacementFieldGroupName  

<!-- -->

isRootPrimaryKeyDataSource  

### Return Value - queryBuildDataSourceBindingsForQuery

## Method queryBuildDataSourceBindingsForRootDS

```xpp
public Map queryBuildDataSourceBindingsForRootDS(QueryBuildDataSource rootQueryBuildDataSource, boolean isPrimaryKeyDataSource, str replacementFieldGroupName)
```

### Parameters - queryBuildDataSourceBindingsForRootDS

rootQueryBuildDataSource  

<!-- -->

isPrimaryKeyDataSource  

<!-- -->

replacementFieldGroupName  

### Return Value - queryBuildDataSourceBindingsForRootDS

## Method resolveReference

```xpp
public Common resolveReference(Query query, [boolean ignoreAmbiguousReference])
```

### Parameters - resolveReference

query  

<!-- -->

ignoreAmbiguousReference  

### Return Value - resolveReference

## Method surrogateForeignKeyFieldBinding

```xpp
public FieldBinding surrogateForeignKeyFieldBinding()
```

### Return Value - surrogateForeignKeyFieldBinding

## Method construct

```xpp
public static SurrogateFKReplacementHelper construct(FieldBinding surrogateForeignKeyBinding)
```

### Parameters - construct

surrogateForeignKeyBinding  

### Return Value - construct

## Method constructForEDT

```xpp
public static SurrogateFKReplacementHelper constructForEDT(str edtName)
```

### Parameters - constructForEDT

edtName  

### Return Value - constructForEDT

## Method constructForPKTable

```xpp
public static SurrogateFKReplacementHelper constructForPKTable(str pkTableName)
```

### Parameters - constructForPKTable

pkTableName  

### Return Value - constructForPKTable

## Method defaultPrimaryKeyQueryDataSourceName

```xpp
public static str defaultPrimaryKeyQueryDataSourceName()
```

### Return Value - defaultPrimaryKeyQueryDataSourceName

## Method DEPRECATED\_WorkflowCaption

```xpp
public static str DEPRECATED_WorkflowCaption(str tableName, str fieldName, Int64 recIDValue)
```

### Parameters - DEPRECATED\_WorkflowCaption

tableName  

<!-- -->

fieldName  

<!-- -->

recIDValue  

### Return Value - DEPRECATED\_WorkflowCaption

## Method implicitReplacementFieldGroupName

```xpp
public static str implicitReplacementFieldGroupName()
```

### Return Value - implicitReplacementFieldGroupName

## Method new

Initializes a new instance of the Object class.

```xpp
private void new(FieldBinding surrogateForeignKeyBinding)
```

### Parameters - new

surrogateForeignKeyBinding  

