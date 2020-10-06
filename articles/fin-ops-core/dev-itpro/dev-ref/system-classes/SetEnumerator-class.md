---
title: SetEnumerator class
description: This topic describes the SetEnumerator class.
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

# Class SetEnumerator

[!include [banner](../../includes/banner.md)]

```xpp
class SetEnumerator extends Object
```

The SetEnumerator class lets you traverse the elements in a set.

## Remarks

Set enumerators start before the first element in the set. You must call the SetEnumerator.moveNext method to make it point to the first element in the set. As a best practice, use the SetEnumerator class instead of the SetIterator class, because enumerators are automatically created on the same tier as the set when the set.getEnumerator method is called. This helps you avoid a potential problem in code that is marked as Called from, where the iterator and set can be on separate tiers. In addition, set enumerators require less code than set iterators and therefore perform slightly better.

## Examples

## Methods

| Method                        | Description                                                                                                |
|-------------------------------|------------------------------------------------------------------------------------------------------------|
| public AnyType current()      | Retrieves the value that is pointed to by the enumerator.                                                  |
| public str definitionString() | Returns a description of the enumerator.                                                                   |
| public boolean moveNext()     | Determines whether the enumerator denotes a valid set element.                                             |
| public str toString()         | Retrieves a description of the contents of the element in the set that the enumerator currently points to. |
| public void reset()           | Moves the enumerator to the start of the set.                                                              |

## Method current

Retrieves the value that is pointed to by the enumerator.

```xpp
public AnyType current()
```

### Return Value - current

The value that is currently pointed to in the set.

### Remarks - current

The type of the return value is determined by the type of items in the set. You must call the SetEnumerator.moveNext method before you call the current method.

## Method definitionString

Returns a description of the enumerator.

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that contains a description of the enumerator.

### Remarks - definitionString

For example, an enumerator for a set of integers would return "int set enumerator".

### Examples - definitionString

The following example creates a set and an enumerator for the set. The definitionString method is used to print a description of the enumerator.

```xpp
{ 
    Set mySet = new Set(Types::Integer); 
    SetEnumerator enumerator; 
    int i; 
    // Add some elements to the set. 
   for (i = 0; i < 10; i++) 
    { 
        mySet.add(i); 
    } 
    // Set the enumerator. 
    enumerator = mySet.getEnumerator(); 
    print enumerator.definitionString(); 
    pause; 
}
```

## Method moveNext

Determines whether the enumerator denotes a valid set element.

```xpp
public boolean moveNext()
```

### Return Value - moveNext

true if the current position in the set holds a valid element; otherwise, false.

### Remarks - moveNext

Set enumerators start before the first element in the set. You must call the moveNext method to make it point to the first element in the set.

## Method toString

Retrieves a description of the contents of the element in the set that the enumerator currently points to.

```xpp
public str toString()
```

### Return Value - toString

A string that contains a description of the current element in the set.

### Examples - toString

The following example creates a set of integers, and then prints the content of the first and second elements in the set.

```xpp
{ 
    Set mySet = new Set(Types::Integer); 
    SetEnumerator  enumerator; 
    int i; 
     // Add some elements to the set. 
    for (i = 0; i < 10; i++) 
    { 
        mySet.add(i); 
    } 
    // Set the enumerator. 
    enumerator = mySet.getEnumerator(); 
    // Go to the beginning of the enumerator. 
    enumerator.reset(); 
    // Go to the first element in the set. 
    enumerator.moveNext(); 
    // Print the first item in the set. 
    print enumerator.toString(); 
    pause; 
    enumerator.moveNext(); 
    // Print the second element in the set. 
    print enumerator.toString(); 
    pause; 
}
```

## Method reset

Moves the enumerator to the start of the set.

```xpp
public void reset()
```

### Remarks - reset

The reset method moves the enumerator to the start of the set, in front of the first element in the set. You must call the SetEnumerator.moveNext method to make it point to the first element in the set.

### Examples - reset

The following example creates a set and then creates an enumerator for the set. It uses the reset method to move to the start of the set and then uses the moveNext method to move to the first element in the set.

```xpp
{ 
    Set mySet = new Set(Types::Integer); 
    SetEnumerator  enumerator; 
    int i; 
     // Add some elements to the set. 
    for (i = 0; i < 10; i++) 
    { 
        mySet.add(i); 
    } 
    // Set the enumerator. 
    enumerator = mySet.getEnumerator(); 
    // Go to beginning of enumerator. 
    enumerator.reset(); 
    // Go to the first element in the set. 
    enumerator.moveNext(); 
    // Print the first item in the set. 
    print enumerator.toString(); 
    pause; 
}
```

