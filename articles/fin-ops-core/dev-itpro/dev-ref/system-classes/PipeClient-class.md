---
title: PipeClient class
description: This topic describes the PipeClient class.
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

# Class PipeClient

[!include [banner](../../includes/banner.md)]

```xpp
class PipeClient extends Object
```

## Remarks

## Examples

## Methods

| Method                                                              | Description                                         |
|---------------------------------------------------------------------|-----------------------------------------------------|
| public boolean blockingMode(\[boolean block\])                      |                                                     |
| public int errorCode()                                              |                                                     |
| public str read()                                                   |                                                     |
| public boolean write(str buffer)                                    |                                                     |
| public void new(str servername, str pipename, \[boolean blocking\]) | Initializes a new instance of the PipeClient class. |

## Method blockingMode

```xpp
public boolean blockingMode([boolean block])
```

### Parameters - blockingMode

block  

### Return Value - blockingMode

## Method errorCode

```xpp
public int errorCode()
```

### Return Value - errorCode

## Method read

```xpp
public str read()
```

### Return Value - read

## Method write

```xpp
public boolean write(str buffer)
```

### Parameters - write

buffer  

### Return Value - write

## Method new

Initializes a new instance of the PipeClient class.

```xpp
public void new(str servername, str pipename, [boolean blocking])
```

### Parameters - new

servername  

<!-- -->

pipename  

<!-- -->

blocking  

