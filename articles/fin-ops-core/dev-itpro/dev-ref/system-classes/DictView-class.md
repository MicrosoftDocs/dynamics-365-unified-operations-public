---
title: DictView class
description: This topic describes the DictView class.
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

# Class DictView

[!include [banner](../../includes/banner.md)]

```xpp
class DictView extends DictTable
```

The DictView class provides access to information about a particular view.

## Remarks

## Examples

## Methods

| Method                                                                                                                               | Description                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public str computedColumnString(str dataSourceName, str fieldName, \[FieldNameGenerationMode generationMode\], \[boolean needTrim\]) | Retrieves the table alias.                                                                                  |
| public int datasourceCnt()                                                                                                           | Counts data sources in the view.                                                                            |
| public str datasourceDataareaIdName(int cnt)                                                                                         | Retrieves the SQL name that is used in the view definition to identify the legal entity of the data source. |
| public TableId datasourceID2TableId(TableId dataSourceId)                                                                            | Gets the table ID of the given data source.                                                                 |
| public TableId datasourceTableId(int cnt)                                                                                            | Retrieves the table ID of the indexed data source.                                                          |
| public SelectionField fieldAggregation(FieldId fieldId)                                                                              | Retrieves the type of aggregation that a given field performs.                                              |
| public int fieldDatasource(FieldId fieldId)                                                                                          | Retrieves the ID of the data source that the given field originates from.                                   |
| public TableId fieldDatasourceID(FieldId fieldId)                                                                                    | Retrieves the ID of the data source in the view that the given field maps to.                               |
| public FieldId fieldId(FieldId fieldId)                                                                                              | Retrieves the field ID from the underlying table.                                                           |
| public boolean isAggregatedView()                                                                                                    | Checks whether the view is aggregated.                                                                      |
| public Query query()                                                                                                                 |                                                                                                             |
| public boolean isDataEntity()                                                                                                        |                                                                                                             |
| public boolean isUpdatable()                                                                                                         |                                                                                                             |
| public boolean isPublic()                                                                                                            |                                                                                                             |
| public str collectionName()                                                                                                          |                                                                                                             |
| public boolean isVirtualField(str fieldName)                                                                                         |                                                                                                             |
| public FieldAccessModifier getFieldAccessModifier(str fieldName)                                                                     |                                                                                                             |
| public boolean isStaged()                                                                                                            |                                                                                                             |
| public str version()                                                                                                                 |                                                                                                             |
| public MessagingRole messagingRole()                                                                                                 |                                                                                                             |
| public void new(TableId tableId)                                                                                                     | Initializes a new instance of the Object class.                                                             |

## Method computedColumnString

Retrieves the table alias.

```xpp
public str computedColumnString(str dataSourceName, str fieldName, [FieldNameGenerationMode generationMode], [boolean needTrim])
```

### Parameters - computedColumnString

dataSourceName  

<!-- -->

fieldName  

<!-- -->

generationMode  

<!-- -->

needTrim  

### Return Value - computedColumnString

The formatted field name string.

### Remarks - computedColumnString

The table alias is an SQL field name in a database-style format that can be used together with a computed column definition.

## Method datasourceCnt

Counts data sources in the view.

```xpp
public int datasourceCnt()
```

### Return Value - datasourceCnt

The number of data sources in the view.

## Method datasourceDataareaIdName

Retrieves the SQL name that is used in the view definition to identify the legal entity of the data source.

```xpp
public str datasourceDataareaIdName(int cnt)
```

### Parameters - datasourceDataareaIdName

cnt  

### Return Value - datasourceDataareaIdName

The SQL name that is used in the view definition to identify the legal entity of the data source; an empty string if an error occurs.

## Method datasourceID2TableId

Gets the table ID of the given data source.

```xpp
public TableId datasourceID2TableId(TableId dataSourceId)
```

### Parameters - datasourceID2TableId

dataSourceId  

### Return Value - datasourceID2TableId

The table ID of the given data source.

## Method datasourceTableId

Retrieves the table ID of the indexed data source.

```xpp
public TableId datasourceTableId(int cnt)
```

### Parameters - datasourceTableId

cnt  

### Return Value - datasourceTableId

The table ID of the given data source; 0 (zero) if an error occurs.

## Method fieldAggregation

Retrieves the type of aggregation that a given field performs.

```xpp
public SelectionField fieldAggregation(FieldId fieldId)
```

### Parameters - fieldAggregation

fieldId  

### Return Value - fieldAggregation

The type of aggregation.

## Method fieldDatasource

Retrieves the ID of the data source that the given field originates from.

```xpp
public int fieldDatasource(FieldId fieldId)
```

### Parameters - fieldDatasource

fieldId  

### Return Value - fieldDatasource

The data source ID.

## Method fieldDatasourceID

Retrieves the ID of the data source in the view that the given field maps to.

```xpp
public TableId fieldDatasourceID(FieldId fieldId)
```

### Parameters - fieldDatasourceID

fieldId  

### Return Value - fieldDatasourceID

The data source ID.

## Method fieldId

Retrieves the field ID from the underlying table.

```xpp
public FieldId fieldId(FieldId fieldId)
```

### Parameters - fieldId

fieldId  

### Return Value - fieldId

The field ID from the underlying table.

## Method isAggregatedView

Checks whether the view is aggregated.

```xpp
public boolean isAggregatedView()
```

### Return Value - isAggregatedView

true if the view is aggregated; otherwise, false.

## Method query

```xpp
public Query query()
```

### Return Value - query

## Method isDataEntity

```xpp
public boolean isDataEntity()
```

### Return Value - isDataEntity

## Method isUpdatable

```xpp
public boolean isUpdatable()
```

### Return Value - isUpdatable

## Method isPublic

```xpp
public boolean isPublic()
```

### Return Value - isPublic

## Method collectionName

```xpp
public str collectionName()
```

### Return Value - collectionName

## Method isVirtualField

```xpp
public boolean isVirtualField(str fieldName)
```

### Parameters - isVirtualField

fieldName  

### Return Value - isVirtualField

## Method getFieldAccessModifier

```xpp
public FieldAccessModifier getFieldAccessModifier(str fieldName)
```

### Parameters - getFieldAccessModifier

fieldName  

### Return Value - getFieldAccessModifier

## Method isStaged

```xpp
public boolean isStaged()
```

### Return Value - isStaged

## Method version

```xpp
public str version()
```

### Return Value - version

## Method messagingRole

```xpp
public MessagingRole messagingRole()
```

### Return Value - messagingRole

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(TableId tableId)
```

### Parameters - new

tableId  
The table ID to use to create the class instance.

