---
title: DictIndex class
description: This topic describes the DictIndex class.
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

# Class DictIndex

[!include [banner](../../includes/banner.md)]

```xpp
class DictIndex extends Object
```

The DictIndex class returns metadata about a table index.

## Remarks

## Examples

The following example creates an instance of the DictIndex class.

```xpp
Dictionary dict; 
DictTable  table; 
DictIndex  idx; 
dict = new Dictionary(); 
table = new DictTable(dict.tableName2Id("Address")); 
idx = new DictIndex(table.id(), table.indexName2Id("AddrIdx"));
```

## Methods

| Method                                                                                                                          | Description                                                           |
|---------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| public boolean allowDuplicates()                                                                                                | Returns the value of the allowDuplicates property for the index.      |
| public ConfigurationKeyId configurationKeyId()                                                                                  | Returns the ID of the configuration key for the index.                |
| public boolean enabled()                                                                                                        | Returns a value that indicates whether the index is enabled.          |
| public FieldId field(int fieldNumber)                                                                                           | Returns the ID of the specified field in the index.                   |
| public ValidTimeStateMode getValidTimeStateMode()                                                                               |                                                                       |
| public IndexId id()                                                                                                             | Returns the ID of the index.                                          |
| public FieldId includedColumn(int fieldNumber)                                                                                  |                                                                       |
| public boolean isAlternateKey()                                                                                                 |                                                                       |
| public boolean isSql()                                                                                                          | Gets a value that indicates whether the index is in the SQL database. |
| public boolean isValidTimeStateKey()                                                                                            |                                                                       |
| public boolean modify(boolean enabled, boolean allowDuplicates, boolean saveInLoadedLayer)                                      | Modifies the index.                                                   |
| public str name(\[DbBackend db\])                                                                                               | Returns the name of the index.                                        |
| public int numberOfFields()                                                                                                     | Returns the number of fields in the index definition.                 |
| public int numberOfIncludedColumns()                                                                                            |                                                                       |
| public boolean setAlternateKey(boolean alternateKey, boolean saveInLoadedLayer)                                                 |                                                                       |
| public boolean setValidTimeStateKey(boolean setValidTimeStateKey, ValidTimeStateMode validTimeState, boolean saveInLoadedLayer) |                                                                       |
| public TableId tableid()                                                                                                        | Returns the ID of the table that contains the index.                  |
| public void new(TableId tableId, IndexId indexId)                                                                               | Initializes a new instance of the Object class.                       |

## Method allowDuplicates

Returns the value of the allowDuplicates property for the index.

```xpp
public boolean allowDuplicates()
```

### Return Value - allowDuplicates

true if the index allows duplicates; otherwise, false.

## Method configurationKeyId

Returns the ID of the configuration key for the index.

```xpp
public ConfigurationKeyId configurationKeyId()
```

### Return Value - configurationKeyId

The ID of the configuration key for the index; 0 (zero) if the index does not have a configuration key.

## Method enabled

Returns a value that indicates whether the index is enabled.

```xpp
public boolean enabled()
```

### Return Value - enabled

true if the index is enabled; otherwise, false.

## Method field

Returns the ID of the specified field in the index.

```xpp
public FieldId field(int fieldNumber)
```

### Parameters - field

fieldNumber  
The one-based index of the field in the index.

### Return Value - field

The ID of the field that is specified by fieldNumber; 0 (zero) if fieldNumber does not represent a valid field.

### Examples - field

The following example shows the retrieval of each field in an index. The name of each field is displayed by using a loop.

```xpp
Dictionary dict; 
DictTable  table; 
DictIndex  idx; 
DictField  field; 
int i; 
dict = new Dictionary(); 
table = new DictTable(dict.tableName2Id("Address")); 
idx = new DictIndex(table.id(), table.indexName2Id("AddrIdx")); 
for (i=1; i <= idx.numberOfFields(); i++) 
{ 
    field = new DictField(table.id(), idx.field(i)); 
    print field.name(); 
}
```

## Method getValidTimeStateMode

```xpp
public ValidTimeStateMode getValidTimeStateMode()
```

### Return Value - getValidTimeStateMode

## Method id

Returns the ID of the index.

```xpp
public IndexId id()
```

### Return Value - id

The ID of the index.

## Method includedColumn

```xpp
public FieldId includedColumn(int fieldNumber)
```

### Parameters - includedColumn

fieldNumber  

### Return Value - includedColumn

## Method isAlternateKey

```xpp
public boolean isAlternateKey()
```

### Return Value - isAlternateKey

## Method isSql

Gets a value that indicates whether the index is in the SQL database.

```xpp
public boolean isSql()
```

### Return Value - isSql

true if the index is in the SQL database; otherwise, false.

## Method isValidTimeStateKey

```xpp
public boolean isValidTimeStateKey()
```

### Return Value - isValidTimeStateKey

## Method modify

Modifies the index.

```xpp
public boolean modify(boolean enabled, boolean allowDuplicates, boolean saveInLoadedLayer)
```

### Parameters - modify

enabled  
A Boolean value that indicates whether the modification is saved in the layer that is loaded.

<!-- -->

allowDuplicates  
A Boolean value that indicates whether the modification is saved in the layer that is loaded.

<!-- -->

saveInLoadedLayer  
A Boolean value that indicates whether the modification is saved in the layer that is loaded.

### Return Value - modify

true if the index was successfully modified; otherwise, false.

### Remarks - modify

This method lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Method name

Returns the name of the index.

```xpp
public str name([DbBackend db])
```

### Parameters - name

db  
A DbBackend value that specifies the type of name to return. This can be DbBackend::Native for the native name of the index or DbBackend::Sql for the SQL name of the index. If db is not specified, DbBackend::Native is used.

### Return Value - name

The name of the index in the format that is specified by db.

## Method numberOfFields

Returns the number of fields in the index definition.

```xpp
public int numberOfFields()
```

### Return Value - numberOfFields

The number of fields in the index.

### Examples - numberOfFields

The following example shows the retrieval of the number of fields in the index and lists the names of the fields in the index.

```xpp
Dictionary dict; 
DictTable  table; 
DictIndex  idx; 
DictField  field; 
int i; 
dict = new Dictionary(); 
table = new DictTable(dict.tableName2Id("Address")); 
idx = new DictIndex(table.id(), table.indexName2Id("AddrIdx")); 
for (i=1; i <= idx.numberOfFields(); i++) 
{ 
    field = new DictField(table.id(), idx.field(i)); 
    print field.name(); 
}
```

## Method numberOfIncludedColumns

```xpp
public int numberOfIncludedColumns()
```

### Return Value - numberOfIncludedColumns

## Method setAlternateKey

```xpp
public boolean setAlternateKey(boolean alternateKey, boolean saveInLoadedLayer)
```

### Parameters - setAlternateKey

alternateKey  

<!-- -->

saveInLoadedLayer  

### Return Value - setAlternateKey

## Method setValidTimeStateKey

```xpp
public boolean setValidTimeStateKey(boolean setValidTimeStateKey, ValidTimeStateMode validTimeState, boolean saveInLoadedLayer)
```

### Parameters - setValidTimeStateKey

setValidTimeStateKey  

<!-- -->

validTimeState  

<!-- -->

saveInLoadedLayer  

### Return Value - setValidTimeStateKey

## Method tableid

Returns the ID of the table that contains the index.

```xpp
public TableId tableid()
```

### Return Value - tableid

The ID of the table that contains the index.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(TableId tableId, IndexId indexId)
```

### Parameters - new

tableId  
The ID of the index that is used to create this instance of the DictIndex class.

<!-- -->

indexId  
The ID of the index that is used to create this instance of the DictIndex class.

