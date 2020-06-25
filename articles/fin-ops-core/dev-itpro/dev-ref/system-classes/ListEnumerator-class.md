---
title: ListEnumerator class
description: This topic describes the ListEnumerator class.
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

# Class ListEnumerator

[!include [banner](../../includes/banner.md)]

```xpp
class ListEnumerator extends Object
```

The ListEnumerator class lets you traverse the elements in a list.

## Remarks

List enumerators start before the first element in the list. You must call the ListEnumerator.moveNext method to make it point to the first element in the list. It is best practice to use the ListEnumerator class instead of the ListIterator class, because enumerators are automatically created on the same tier as the list (when the list.getEnumerator method is called). This avoids a potential problem in code that is marked as Called from, where the iterator and list can be on separate tiers. In addition, list enumerators require less code than list iterators and therefore perform slightly better. The only situation where you have to use a list iterator is if you want to delete items from a list (use the ListIterator.delete method).

## Examples

The following example creates a list of integers and puts some values into it. It then creates an enumerator, and then sets the enumerator to the first element in the list and then the second element in the list.

```xpp
{ 
    List list = new List(Types::Integer); 
    ListEnumerator enumerator; 
    // Add some elements to the list 
    list.addEnd(1); 
    list.addEnd(2); 
    list.addStart(3); 
    // Set the enumerator 
    enumerator = list.getEnumerator(); 
    // Print a description of the list 
    print enumerator.definitionString(); 
    // Go to beginning of enumerator 
    enumerator.reset(); 
    //Go to the first element in the List 
    enumerator.moveNext(); 
    // Print contents of first and second elements 
    // First element is 3 as this was added to start of list 
    print enumerator.toString(); 
    enumerator.moveNext(); 
    print enumerator.toString(); 
    pause; 
}
```

## Methods

| Method                        | Description                                                                                                   |
|-------------------------------|---------------------------------------------------------------------------------------------------------------|
| public AnyType current()      | Retrieves the value that is pointed to by the enumerator.                                                     |
| public str definitionString() | Returns a description of the enumerator.                                                                      |
| public boolean moveNext()     | Determines whether the enumerator denotes a valid list element.                                               |
| public str toString()         | Returns a description of the content of the element in the list that the enumerator is currently pointing to. |
| public void reset()           | Moves the enumerator to the start of the list.                                                                |

## Method current

Retrieves the value that is pointed to by the enumerator.

```xpp
public AnyType current()
```

### Return Value - current

The value that is currently pointed to in the list. The type of the return value is determined by the type of the items in the list.

### Examples - current

The following example iterates through the list and sets the dimensionTopic variable to the value of the current list element.

```xpp
public DimensionTopic firstDimensionTopic() 
{ 
    DimensionTopic  dimensionTopic; 
    ListEnumerator  enumerator; 
    enumerator = this.getTopicsEnumerator(); 
    if (enumerator.moveNext()) 
    { 
        dimensionTopic = enumerator.current(); 
    } 
    return dimensionTopic; 
}
```

## Method definitionString

Returns a description of the enumerator.

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that contains a description of the enumerator.

### Remarks - definitionString

For example, an enumerator for a list of integers would return int list enumerator.

### Examples - definitionString

The following example creates a list and an enumerator for the list. It uses the definitionString method to print a description of the enumerator.

```xpp
{ 
    List list = new List(Types::Integer); 
    ListEnumerator  enumerator; 
    ; 
    // Add some elements to the list 
    list.addEnd(1); 
    list.addEnd(2); 
    list.addStart(3); 
    // Set the enumerator 
    enumerator = list.getEnumerator(); 
    print enumerator.definitionString(); 
    pause; 
}
```

## Method moveNext

Determines whether the enumerator denotes a valid list element.

```xpp
public boolean moveNext()
```

### Return Value - moveNext

true if the current position in the list holds a valid element; otherwise, false.

### Remarks - moveNext

List enumerators start before the first element in the list. You must call the moveNext method to make it point to the first element in the list.

### Examples - moveNext

The following example uses the moveNext method to check whether there is another element in the list and then sets the dimensionTopic variable to the value of the current list element.

```xpp
public DimensionTopic firstDimensionTopic() 
{ 
    DimensionTopic  dimensionTopic; 
    ListEnumerator  enumerator; 
    enumerator = this.getTopicsEnumerator(); 
    if (enumerator.moveNext()) 
    { 
        dimensionTopic = enumerator.current(); 
    } 
    return dimensionTopic; 
}
```

## Method toString

Returns a description of the content of the element in the list that the enumerator is currently pointing to.

```xpp
public str toString()
```

### Return Value - toString

A string that contains a description of the current list element.

### Examples - toString

The following example creates a list, and then prints the content of the first and second elements in the list.

```xpp
{ 
    List list = new List(Types::Integer); 
    ListEnumerator  enumerator; 
    // Add some elements to the list 
    list.addEnd(1); 
    list.addEnd(2); 
    list.addStart(3); 
    // Set the enumerator 
    enumerator = list.getEnumerator(); 
    // Go to beginning of enumerator 
    enumerator.reset(); 
    //Go to the first element in the List 
    enumerator.moveNext(); 
    // First element is 3 as this was added to start of list 
    print enumerator.toString(); 
    pause; 
    enumerator.moveNext(); 
    //Print second element in list (1) 
    print enumerator.toString(); 
    pause; 
}
```

## Method reset

Moves the enumerator to the start of the list.

```xpp
public void reset()
```

### Remarks - reset

The reset method moves the enumerator to the start of the list, before the first element in the list. You must call the ListEnumerator.moveNext method to make it point to the first element in the list.

### Examples - reset

The following example creates a list and then an enumerator for the list. It uses the reset method to move to the start of the list and then uses the moveNext method to move to the first element in the list.

```xpp
{ 
    List list = new List(Types::Integer); 
    ListEnumerator  enumerator; 
    // Add some elements to the list 
    list.addEnd(1); 
    list.addEnd(2); 
    list.addStart(3); 
    // Set the enumerator 
    enumerator = list.getEnumerator(); 
    // Go to beginning of enumerator 
    enumerator.reset(); 
    //Go to the first element in the List 
    enumerator.moveNext(); 
    // First element is 3 as this was added to start of list 
    print enumerator.toString(); 
    pause; 
}
```

