---
title: MapiFileDesc class
description: This topic describes the MapiFileDesc class.
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

# Class MapiFileDesc

[!include [banner](../../includes/banner.md)]

```xpp
class MapiFileDesc extends Object
```

The MapiFileDesc class gets and sets the files that are attached to messages.

## Remarks

The file description consists of two types of information for the file:

-   A path method, which points to a file on disk
-   A fileName method, which contains the file name as it will be presented to the user.

## Examples

```xpp
static void example() 
{ 
    MapiMessage msg = New MapiMessage(); 
    MapiFileDesc attach = new MapiFileDesc(); 
    attach.Path("C:\\files\\myfile.txt"); 
}
```

## Methods

| Method                                | Description                                           |
|---------------------------------------|-------------------------------------------------------|
| public str fileName(\[str filename\]) |                                                       |
| public str path(\[str thePath\])      |                                                       |
| public void new()                     | Initializes a new instance of the MapiFileDesc class. |
| public void finalize()                |                                                       |

## Method fileName

```xpp
public str fileName([str filename])
```

### Parameters - fileName

filename  

### Return Value - fileName

## Method path

```xpp
public str path([str thePath])
```

### Parameters - path

thePath  

### Return Value - path

## Method new

Initializes a new instance of the MapiFileDesc class.

```xpp
public void new()
```

## Method finalize

```xpp
public void finalize()
```

