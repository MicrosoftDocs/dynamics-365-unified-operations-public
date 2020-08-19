---
title: ListPage class
description: This topic describes the ListPage class.
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

# Class ListPage

[!include [banner](../../includes/banner.md)]

```xpp
class ListPage extends Page
```

## Remarks

## Examples

## Methods

| Method                                                                      | Description                                       |
|-----------------------------------------------------------------------------|---------------------------------------------------|
| public str actionPaneControlParameters(str controlName, \[str parameters\]) |                                                   |
| public Array activeActionPaneTabNames()                                     | Gets the name of the specified active tab.        |
| public str caption(\[str value\])                                           |                                                   |
| public ListPageArgs listPageArgs()                                          |                                                   |
| public int listPageFieldDataField(str fieldName)                            |                                                   |
| public Array listPageFieldNames()                                           |                                                   |
| public int listPageFieldTableId(str fieldName)                              |                                                   |
| public boolean listPageFieldVisible(str fieldName, \[boolean visible\])     |                                                   |
| public str modeledQueryName(\[str value\])                                  |                                                   |
| public void new()                                                           | Initializes a new instance of the ListPage class. |

## Method actionPaneControlParameters

```xpp
public str actionPaneControlParameters(str controlName, [str parameters])
```

### Parameters - actionPaneControlParameters

controlName  

<!-- -->

parameters  

### Return Value - actionPaneControlParameters

## Method activeActionPaneTabNames

Gets the name of the specified active tab.

```xpp
public Array activeActionPaneTabNames()
```

### Return Value - activeActionPaneTabNames

An array that contains the names of the active tabs.

## Method caption

```xpp
public str caption([str value])
```

### Parameters - caption

value  

### Return Value - caption

## Method listPageArgs

```xpp
public ListPageArgs listPageArgs()
```

### Return Value - listPageArgs

## Method listPageFieldDataField

```xpp
public int listPageFieldDataField(str fieldName)
```

### Parameters - listPageFieldDataField

fieldName  

### Return Value - listPageFieldDataField

## Method listPageFieldNames

```xpp
public Array listPageFieldNames()
```

### Return Value - listPageFieldNames

## Method listPageFieldTableId

```xpp
public int listPageFieldTableId(str fieldName)
```

### Parameters - listPageFieldTableId

fieldName  

### Return Value - listPageFieldTableId

## Method listPageFieldVisible

```xpp
public boolean listPageFieldVisible(str fieldName, [boolean visible])
```

### Parameters - listPageFieldVisible

fieldName  

<!-- -->

visible  

### Return Value - listPageFieldVisible

## Method modeledQueryName

```xpp
public str modeledQueryName([str value])
```

### Parameters - modeledQueryName

value  

### Return Value - modeledQueryName

## Method new

Initializes a new instance of the ListPage class.

```xpp
public void new()
```

