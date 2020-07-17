---
title: RelationPath class
description: This topic describes the RelationPath class.
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

# Class RelationPath

[!include [banner](../../includes/banner.md)]

```xpp
class RelationPath extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                        | Description                                           |
|-----------------------------------------------------------------------------------------------|-------------------------------------------------------|
| public boolean isEqualTo(RelationPath otherRelationPath)                                      |                                                       |
| public boolean isPathCyclical(boolean excludePathRootTable)                                   |                                                       |
| public boolean isPathValid()                                                                  |                                                       |
| public List pathAsList()                                                                      |                                                       |
| public str pathAsString(\[str delimiter\])                                                    |                                                       |
| public str pathRelativeTable()                                                                |                                                       |
| public str pathRootTable()                                                                    |                                                       |
| ::public static RelationPath construct(RelationPath sourceRelationPath)                       |                                                       |
| ::public static RelationPath constructFromPathList(str pathRootTableName, List relationPath)  |                                                       |
| ::public static RelationPath constructFromPathString(str pathRootTableName, str relationPath) |                                                       |
| private void new()                                                                            | Initializes a new instance of the RelationPath class. |
| public void trimPathAtFront()                                                                 |                                                       |
| public void trimPathAtEnd()                                                                   |                                                       |

## Method isEqualTo

```xpp
public boolean isEqualTo(RelationPath otherRelationPath)
```

### Parameters - isEqualTo

otherRelationPath  

### Return Value - isEqualTo

## Method isPathCyclical

```xpp
public boolean isPathCyclical(boolean excludePathRootTable)
```

### Parameters - isPathCyclical

excludePathRootTable  

### Return Value - isPathCyclical

## Method isPathValid

```xpp
public boolean isPathValid()
```

### Return Value - isPathValid

## Method pathAsList

```xpp
public List pathAsList()
```

### Return Value - pathAsList

## Method pathAsString

```xpp
public str pathAsString([str delimiter])
```

### Parameters - pathAsString

delimiter  

### Return Value - pathAsString

## Method pathRelativeTable

```xpp
public str pathRelativeTable()
```

### Return Value - pathRelativeTable

## Method pathRootTable

```xpp
public str pathRootTable()
```

### Return Value - pathRootTable

## Method construct

```xpp
public static RelationPath construct(RelationPath sourceRelationPath)
```

### Parameters - construct

sourceRelationPath  

### Return Value - construct

## Method constructFromPathList

```xpp
public static RelationPath constructFromPathList(str pathRootTableName, List relationPath)
```

### Parameters - constructFromPathList

pathRootTableName  

<!-- -->

relationPath  

### Return Value - constructFromPathList

## Method constructFromPathString

```xpp
public static RelationPath constructFromPathString(str pathRootTableName, str relationPath)
```

### Parameters - constructFromPathString

pathRootTableName  

<!-- -->

relationPath  

### Return Value - constructFromPathString

## Method new

Initializes a new instance of the RelationPath class.

```xpp
private void new()
```

## Method trimPathAtFront

```xpp
public void trimPathAtFront()
```

## Method trimPathAtEnd

```xpp
public void trimPathAtEnd()
```

