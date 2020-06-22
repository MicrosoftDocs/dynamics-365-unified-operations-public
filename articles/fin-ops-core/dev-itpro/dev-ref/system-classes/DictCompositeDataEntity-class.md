---
title: DictCompositeDataEntity class
description: This topic describes the DictCompositeDataEntity class.
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

# Class DictCompositeDataEntity

[!include [banner](../../includes/banner.md)]

```xpp
class DictCompositeDataEntity extends Object
```

## Remarks

## Examples

## Methods

| Method                                                       | Description |
|--------------------------------------------------------------|-------------|
| ::public static List listOfCompositeDataEntities()           |             |
| public str label()                                           |             |
| public boolean isReadOnly()                                  |             |
| public str modules()                                         |             |
| public str configurationKey()                                |             |
| public str countryRegionCodes()                              |             |
| public str countryRegionContextField()                       |             |
| public str developerDocumentation()                          |             |
| public EntityCategory entityCategory()                       |             |
| public str formRef()                                         |             |
| public str singularLabel()                                   |             |
| public str tags()                                            |             |
| public str publicCollectionName()                            |             |
| public str publicEntityName()                                |             |
| public int dataEntityCount()                                 |             |
| public DictCompositeChildDataEntity childDataEntityNo(int n) |             |
| public void new(str compositeDataEntityName)                 |             |

## Method listOfCompositeDataEntities

```xpp
public static List listOfCompositeDataEntities()
```

### Return Value - listOfCompositeDataEntities

## Method label

```xpp
public str label()
```

### Return Value - label

## Method isReadOnly

```xpp
public boolean isReadOnly()
```

### Return Value - isReadOnly

## Method modules

```xpp
public str modules()
```

### Return Value - modules

## Method configurationKey

```xpp
public str configurationKey()
```

### Return Value - configurationKey

## Method countryRegionCodes

```xpp
public str countryRegionCodes()
```

### Return Value - countryRegionCodes

## Method countryRegionContextField

```xpp
public str countryRegionContextField()
```

### Return Value - countryRegionContextField

## Method developerDocumentation

```xpp
public str developerDocumentation()
```

### Return Value - developerDocumentation

## Method entityCategory

```xpp
public EntityCategory entityCategory()
```

### Return Value - entityCategory

## Method formRef

```xpp
public str formRef()
```

### Return Value - formRef

## Method singularLabel

```xpp
public str singularLabel()
```

### Return Value - singularLabel

## Method tags

```xpp
public str tags()
```

### Return Value - tags

## Method publicCollectionName

```xpp
public str publicCollectionName()
```

### Return Value - publicCollectionName

## Method publicEntityName

```xpp
public str publicEntityName()
```

### Return Value - publicEntityName

## Method dataEntityCount

```xpp
public int dataEntityCount()
```

### Return Value - dataEntityCount

## Method childDataEntityNo

```xpp
public DictCompositeChildDataEntity childDataEntityNo(int n)
```

### Parameters - childDataEntityNo

n  

### Return Value - childDataEntityNo

## Method new

```xpp
public void new(str compositeDataEntityName)
```

### Parameters - new

compositeDataEntityName  

