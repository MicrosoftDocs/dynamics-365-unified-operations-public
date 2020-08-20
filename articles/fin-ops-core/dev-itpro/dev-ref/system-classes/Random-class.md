---
title: Random class
description: This topic describes the Random class.
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

# Class Random

[!include [banner](../../includes/banner.md)]


```xpp
class Random extends Object
```

The Random class generates random numbers.

## Remarks

Because this class operates on a global random generator, the individual random objects will interfere with each other. Therefore, it is not possible to predict the sequence of numbers for a specific random object.

## Examples

The following example prints 100 random numbers.

```xpp
static void example() 
{ 
    Random myRand = new Random(); 
    int i; 
    for(i=0;i<100;i++) 
    { 
        print myRand.nextInt(); 
    } 
}
```

## Methods

| Method               | Description                                               |
|----------------------|-----------------------------------------------------------|
| public int nextInt() | Returns the next random number from the random generator. |
| public void new()    | Initializes a new instance of the Random class.           |

## Method nextInt

Returns the next random number from the random generator.

```xpp
public int nextInt()
```

### Return Value - nextInt

The next random integer number from the random generator.

### Remarks - nextInt

The value will be in the range from 0 to 32767 (0x7FFF).

## Method new

Initializes a new instance of the Random class.

```xpp
public void new()
```

