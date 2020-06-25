---
title: SearchParm class
description: This topic describes the SearchParm class.
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

# Class SearchParm

[!include [banner](../../includes/banner.md)]

```xpp
class SearchParm extends Object
```

The SearchParm class serves as an interface between the kernel and the sysTreeSearch class, and enables searches in the  Application Object Tree (AOT).

## Remarks

## Examples

## Methods

| Method                                          | Description |
|-------------------------------------------------|-------------|
| public str nodeName(\[str name\])               |             |
| public int nodeType(\[int type\])               |             |
| public str nodeTypeArray()                      |             |
| public str propertyName(\[str name\])           |             |
| public str propertyValue(\[str value\])         |             |
| public str replaceString(\[str replaceString\]) |             |
| public int searchFlag(\[int flag\])             |             |
| public str searchString(\[str searchString\])   |             |
| public int searchType(\[int type\])             |             |
| public boolean startSearch()                    |             |
| public TreeNode topNode(\[TreeNode node\])      |             |
| public str topNodeName(\[str name\])            |             |
| public int topNodeType(\[int type\])            |             |
| public void preSearch()                         |             |
| public void killSearch()                        |             |

## Method nodeName

```xpp
public str nodeName([str name])
```

### Parameters - nodeName

name  

### Return Value - nodeName

## Method nodeType

```xpp
public int nodeType([int type])
```

### Parameters - nodeType

type  

### Return Value - nodeType

## Method nodeTypeArray

```xpp
public str nodeTypeArray()
```

### Return Value - nodeTypeArray

## Method propertyName

```xpp
public str propertyName([str name])
```

### Parameters - propertyName

name  

### Return Value - propertyName

## Method propertyValue

```xpp
public str propertyValue([str value])
```

### Parameters - propertyValue

value  

### Return Value - propertyValue

## Method replaceString

```xpp
public str replaceString([str replaceString])
```

### Parameters - replaceString

replaceString  

### Return Value - replaceString

## Method searchFlag

```xpp
public int searchFlag([int flag])
```

### Parameters - searchFlag

flag  

### Return Value - searchFlag

## Method searchString

```xpp
public str searchString([str searchString])
```

### Parameters - searchString

searchString  

### Return Value - searchString

## Method searchType

```xpp
public int searchType([int type])
```

### Parameters - searchType

type  

### Return Value - searchType

## Method startSearch

```xpp
public boolean startSearch()
```

### Return Value - startSearch

## Method topNode

```xpp
public TreeNode topNode([TreeNode node])
```

### Parameters - topNode

node  

### Return Value - topNode

## Method topNodeName

```xpp
public str topNodeName([str name])
```

### Parameters - topNodeName

name  

### Return Value - topNodeName

## Method topNodeType

```xpp
public int topNodeType([int type])
```

### Parameters - topNodeType

type  

### Return Value - topNodeType

## Method preSearch

```xpp
public void preSearch()
```

## Method killSearch

```xpp
public void killSearch()
```

