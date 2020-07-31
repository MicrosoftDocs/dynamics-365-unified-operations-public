---
title: Sequence class
description: This topic describes the Sequence class.
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

# Class Sequence

[!include [banner](../../includes/banner.md)]

```xpp
class Sequence extends Object
```

The Sequence class lets you perform transactions outside the main transaction scope, typically for some kind of sequence, or voucher number generation.

## Remarks

There are three kinds of connections: The main user connection, an auxiliary system connection, and user connections. The first is used for the application logic. The second is used for internal sequence number generation (specifically the built-in field RecId). The third is used for the application maintained separate connections. This class provides an interface to the auxiliary system connection for number generation. However, it may be a better solution to use the UserConnection class, as this is the method the application uses or flexibility, and to avoid concurrency problems with the kernel's sequence number generation.

## Examples

```xpp
static void example() 
{ 
    Sequence S = new Sequence("mySequence",1,100,10000); 
    print S.nextval(10);           // 100 in current company (the subkey) 
    print S.nextval(10);           // 110 in current company (the subkey) 
    print S.nextval(1,"MMM");      // 100 in subkey "MMM" 
    print S.nextval(1,"MMM");      // 101 in subkey "MMM" 
}
```

## Methods

| Method                                                                                                        | Description                                                                                 |
|---------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| public Int64 currval(\[str Subkey1\], \[int Subkey2\])                                                        | Gets the current sequence number from the sequence, without incrementing the counter value. |
| public Int64 nextval(Int64 Increment, \[str Subkey1\], \[int Subkey2\])                                       | Returns the next sequence number from the sequence and then increments the counter value.   |
| public void new(str Name, int Id, Int64 InitialValue, Int64 MaxValue, \[boolean Cycle\], \[Int64 CacheSize\]) | Initializes a new instance of the Object class.                                             |

## Method currval

Gets the current sequence number from the sequence, without incrementing the counter value.

```xpp
public Int64 currval([str Subkey1], [int Subkey2])
```

### Parameters - currval

Subkey1  

<!-- -->

Subkey2  

### Return Value - currval

The current sequence number from the sequence.

## Method nextval

Returns the next sequence number from the sequence and then increments the counter value.

```xpp
public Int64 nextval(Int64 Increment, [str Subkey1], [int Subkey2])
```

### Parameters - nextval

Increment  

<!-- -->

Subkey1  

<!-- -->

Subkey2  

### Return Value - nextval

The next sequence number available.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(str Name, int Id, Int64 InitialValue, Int64 MaxValue, [boolean Cycle], [Int64 CacheSize])
```

### Parameters - new

Name  

<!-- -->

Id  

<!-- -->

InitialValue  

<!-- -->

MaxValue  

<!-- -->

Cycle  

<!-- -->

CacheSize  

