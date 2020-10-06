---
title: DataSetRun class
description: This topic describes the DataSetRun class.
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

# Class DataSetRun

[!include [banner](../../includes/banner.md)]

```xpp
class DataSetRun extends ObjectRun
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                              | Description                                                                   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| public FormDataSource addDataSource(TableId tableId, \[str joinDataSourceName\], \[DataSourceLinkTypePropertyValues linkType\], \[FieldId joinFieldId\], \[str newDataSourceName\]) | Adds a new data source to the dataSetRun class.                               |
| public DataSet dataSet()                                                                                                                                                            |                                                                               |
| public FormObjectSet dataSource(\[AnyType objectSet\])                                                                                                                              |                                                                               |
| public FormObjectSet dataSourceById(int id)                                                                                                                                         |                                                                               |
| public int dataSourceCount()                                                                                                                                                        |                                                                               |
| public Array getActiveFields(int dataSourceId)                                                                                                                                      |                                                                               |
| public container getChildrenById(str dataSourceName, \[AnyType parentId\])                                                                                                          | Gets the children of a data source by using the parent ID.                    |
| public container getChildrenByIndex(str dataSourceName, \[int parentIndex\])                                                                                                        | Gets the children of a data source by using the parent index.                 |
| public DataSetError getLastError()                                                                                                                                                  |                                                                               |
| public AnyType getParentById(str dataSourceName, AnyType childId)                                                                                                                   | Gets the parent of a data source by using the child ID.                       |
| public int getParentByIndex(str dataSourceName, int childIndex)                                                                                                                     | Gets the parent of a data source by using the child index.                    |
| public int getRowIndexFromRowHierarchyId(str dataSourceName, AnyType id)                                                                                                            | Gets the row index on a data source by using a row hierarchy ID.              |
| public boolean initComplete()                                                                                                                                                       |                                                                               |
| public str name()                                                                                                                                                                   |                                                                               |
| public FormObjectSet objectSet(\[AnyType objectSet\])                                                                                                                               |                                                                               |
| public container pack()                                                                                                                                                             | Serializes the current instance of the DataSetRun class.                      |
| public boolean runCalled()                                                                                                                                                          |                                                                               |
| public boolean unpack(container pack)                                                                                                                                               | Deserializes the pack parameter value to an instance of the DataSetRun class. |
| ::public static DataSetRun create(str name, container pack)                                                                                                                         |                                                                               |
| ::public static DataSetRun createRunTime(container pack)                                                                                                                            |                                                                               |
| public void setLastError(DataSetError error)                                                                                                                                        |                                                                               |
| public void run()                                                                                                                                                                   |                                                                               |
| public void setLookupMode()                                                                                                                                                         | Puts the dataset into lookup mode.                                            |
| public void new(xArgs args)                                                                                                                                                         | Initializes a new instance of the Object class.                               |
| public void finalize()                                                                                                                                                              |                                                                               |
| public void createRecord(str formDataSourceName, \[boolean append\])                                                                                                                | Creates a new record.                                                         |
| public void setActiveFields(int dataSourceId, Array fieldIds)                                                                                                                       |                                                                               |
| public void setExternalContext(\[Common externalContext\])                                                                                                                          | Sets the external context on the dataSetRun object.                           |
| public void init()                                                                                                                                                                  |                                                                               |
| public void enableHierarchicalDataBrowsing(str hierarchyPKDataSourceName, FieldId hierarchyPKfieldId, str hierarchyFKDataSourceName, FieldId hierarchyFKfieldId)                    | Enables hierarchical data browsing.                                           |
| public void disableHierarchicalDataBrowsing(str dataSourceName)                                                                                                                     | Disables hierarchical data browsing.                                          |

## Method addDataSource

Adds a new data source to the dataSetRun class.

```xpp
public FormDataSource addDataSource(TableId tableId, [str joinDataSourceName], [DataSourceLinkTypePropertyValues linkType], [FieldId joinFieldId], [str newDataSourceName])
```

### Parameters - addDataSource

tableId  
The name of the new data source.

<!-- -->

joinDataSourceName  
The name of the new data source.

<!-- -->

linkType  
The name of the new data source.

<!-- -->

joinFieldId  
The name of the new data source.

<!-- -->

newDataSourceName  
The name of the new data source.

### Return Value - addDataSource

The new data source.

## Method dataSet

```xpp
public DataSet dataSet()
```

### Return Value - dataSet

## Method dataSource

```xpp
public FormObjectSet dataSource([AnyType objectSet])
```

### Parameters - dataSource

objectSet  

### Return Value - dataSource

## Method dataSourceById

```xpp
public FormObjectSet dataSourceById(int id)
```

### Parameters - dataSourceById

id  

### Return Value - dataSourceById

## Method dataSourceCount

```xpp
public int dataSourceCount()
```

### Return Value - dataSourceCount

## Method getActiveFields

```xpp
public Array getActiveFields(int dataSourceId)
```

### Parameters - getActiveFields

dataSourceId  

### Return Value - getActiveFields

## Method getChildrenById

Gets the children of a data source by using the parent ID.

```xpp
public container getChildrenById(str dataSourceName, [AnyType parentId])
```

### Parameters - getChildrenById

dataSourceName  
The parent ID.

<!-- -->

parentId  
The parent ID.

### Return Value - getChildrenById

A container for the children.

## Method getChildrenByIndex

Gets the children of a data source by using the parent index.

```xpp
public container getChildrenByIndex(str dataSourceName, [int parentIndex])
```

### Parameters - getChildrenByIndex

dataSourceName  
The parent index.

<!-- -->

parentIndex  
The parent index.

### Return Value - getChildrenByIndex

A container for the children.

## Method getLastError

```xpp
public DataSetError getLastError()
```

### Return Value - getLastError

## Method getParentById

Gets the parent of a data source by using the child ID.

```xpp
public AnyType getParentById(str dataSourceName, AnyType childId)
```

### Parameters - getParentById

dataSourceName  
The child ID.

<!-- -->

childId  
The child ID.

### Return Value - getParentById

The parent ID.

## Method getParentByIndex

Gets the parent of a data source by using the child index.

```xpp
public int getParentByIndex(str dataSourceName, int childIndex)
```

### Parameters - getParentByIndex

dataSourceName  
The child index.

<!-- -->

childIndex  
The child index.

### Return Value - getParentByIndex

The parent ID.

## Method getRowIndexFromRowHierarchyId

Gets the row index on a data source by using a row hierarchy ID.

```xpp
public int getRowIndexFromRowHierarchyId(str dataSourceName, AnyType id)
```

### Parameters - getRowIndexFromRowHierarchyId

dataSourceName  
The row hierarchy ID.

<!-- -->

id  
The row hierarchy ID.

### Return Value - getRowIndexFromRowHierarchyId

The row index.

## Method initComplete

```xpp
public boolean initComplete()
```

### Return Value - initComplete

## Method name

```xpp
public str name()
```

### Return Value - name

## Method objectSet

```xpp
public FormObjectSet objectSet([AnyType objectSet])
```

### Parameters - objectSet

objectSet  

### Return Value - objectSet

## Method pack

Serializes the current instance of the DataSetRun class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the DataSetRun class.

## Method runCalled

```xpp
public boolean runCalled()
```

### Return Value - runCalled

## Method unpack

Deserializes the pack parameter value to an instance of the DataSetRun class.

```xpp
public boolean unpack(container pack)
```

### Parameters - unpack

pack  
The container from which to deserialize the instance.

### Return Value - unpack

true if deserialization was successful; otherwise, false.

## Method create

```xpp
public static DataSetRun create(str name, container pack)
```

### Parameters - create

name  

<!-- -->

pack  

### Return Value - create

## Method createRunTime

```xpp
public static DataSetRun createRunTime(container pack)
```

### Parameters - createRunTime

pack  

### Return Value - createRunTime

## Method setLastError

```xpp
public void setLastError(DataSetError error)
```

### Parameters - setLastError

error  

## Method run

```xpp
public void run()
```

## Method setLookupMode

Puts the dataset into lookup mode.

```xpp
public void setLookupMode()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(xArgs args)
```

### Parameters - new

args  

## Method finalize

```xpp
public void finalize()
```

## Method createRecord

Creates a new record.

```xpp
public void createRecord(str formDataSourceName, [boolean append])
```

### Parameters - createRecord

formDataSourceName  
The record to append.

<!-- -->

append  
The record to append.

## Method setActiveFields

```xpp
public void setActiveFields(int dataSourceId, Array fieldIds)
```

### Parameters - setActiveFields

dataSourceId  

<!-- -->

fieldIds  

## Method setExternalContext

Sets the external context on the dataSetRun object.

```xpp
public void setExternalContext([Common externalContext])
```

### Parameters - setExternalContext

externalContext  
The external context.

## Method init

```xpp
public void init()
```

## Method enableHierarchicalDataBrowsing

Enables hierarchical data browsing.

```xpp
public void enableHierarchicalDataBrowsing(str hierarchyPKDataSourceName, FieldId hierarchyPKfieldId, str hierarchyFKDataSourceName, FieldId hierarchyFKfieldId)
```

### Parameters - enableHierarchicalDataBrowsing

hierarchyPKDataSourceName  
The ID of the foreign key field in the hierarchy.

<!-- -->

hierarchyPKfieldId  
The ID of the foreign key field in the hierarchy.

<!-- -->

hierarchyFKDataSourceName  
The ID of the foreign key field in the hierarchy.

<!-- -->

hierarchyFKfieldId  
The ID of the foreign key field in the hierarchy.

## Method disableHierarchicalDataBrowsing

Disables hierarchical data browsing.

```xpp
public void disableHierarchicalDataBrowsing(str dataSourceName)
```

### Parameters - disableHierarchicalDataBrowsing

dataSourceName  
The name of the data source to disable hierarchical data browsing on.

