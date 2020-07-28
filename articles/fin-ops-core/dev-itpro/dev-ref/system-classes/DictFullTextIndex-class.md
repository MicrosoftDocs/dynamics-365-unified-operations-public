---
title: DictFullTextIndex class
description: This topic describes the DictFullTextIndex class.
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

# Class DictFullTextIndex

[!include [banner](../../includes/banner.md)]

```xpp
class DictFullTextIndex extends Object
```

The DictFullTextIndex class returns metadata about a full text index.

## Remarks

## Examples

## Methods

| Method                                                  | Description                                            |
|---------------------------------------------------------|--------------------------------------------------------|
| public FullTextIndexChangeTracking changeTrackingMode() | Gets the change tracking mode of the full text index.  |
| public ConfigurationKeyId configurationKeyId()          | Returns the ID of the configuration key for the index. |
| public IndexId id()                                     | Gets the ID of the full text index.                    |
| public str name()                                       | Gets the name of the full text index.                  |
| public TableId tableid()                                | Returns the ID of the table that contains the index.   |
| public void new(TableId tableId, IndexId indexId)       | Initializes a new instance of the Object class.        |

## Method changeTrackingMode

Gets the change tracking mode of the full text index.

```xpp
public FullTextIndexChangeTracking changeTrackingMode()
```

### Return Value - changeTrackingMode

## Method configurationKeyId

Returns the ID of the configuration key for the index.

```xpp
public ConfigurationKeyId configurationKeyId()
```

### Return Value - configurationKeyId

The ID of the configuration key for the index; 0 (zero) if the index does not have a configuration key.

## Method id

Gets the ID of the full text index.

```xpp
public IndexId id()
```

### Return Value - id

The ID of the index.

## Method name

Gets the name of the full text index.

```xpp
public str name()
```

### Return Value - name

The name of the index.

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

<!-- -->

indexId  

