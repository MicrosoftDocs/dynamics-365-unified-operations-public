---
title: CryptoAPI class
description: This topic describes the CryptoAPI class.
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

# Class CryptoAPI

[!include [banner](../../includes/banner.md)]

```xpp
class CryptoAPI extends Object
```

## Remarks

## Examples

## Methods

| Method                                   | Description                                     |
|------------------------------------------|-------------------------------------------------|
| public container decrypt(container blob) |                                                 |
| public container encrypt(container blob) |                                                 |
| public container getKey()                |                                                 |
| public Int64 salt()                      |                                                 |
| public void new(Int64 salt)              | Initializes a new instance of the Object class. |
| ::public static void resetKey()          |                                                 |

## Method decrypt

```xpp
public container decrypt(container blob)
```

### Parameters - decrypt

blob  

### Return Value - decrypt

## Method encrypt

```xpp
public container encrypt(container blob)
```

### Parameters - encrypt

blob  

### Return Value - encrypt

## Method getKey

```xpp
public container getKey()
```

### Return Value - getKey

## Method salt

```xpp
public Int64 salt()
```

### Return Value - salt

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(Int64 salt)
```

### Parameters - new

salt  

## Method resetKey

```xpp
public static void resetKey()
```

