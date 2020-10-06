---
title: ListIterator class
description: This topic describes the ListIterator class.
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

# Class ListIterator

[!include [banner](../../includes/banner.md)]

```xpp
class ListIterator extends Object
```

The ListIterator class is used to iterate over the elements in a list.

## Remarks

List iterators can be viewed as pointers into the lists over which they iterate. Functionality is available to start the iteration, determine whether more elements are available, and fetch the element that is pointed to by the iterator. The order in which the elements occur during iteration is defined by the sequence in which the elements are inserted. Elements can be inserted by using the List.addStart, List.addEnd, or ListIterator.insert method. It is better to use the ListEnumerator class than the ListIterator class. List iterators and the maps over which they iterate must be on the same client/server side. If you use the ListIterator class, and code is marked as Called from, it is possible that the list and the iterator will be on different tiers. In this case, the code will fail. If you use the ListEnumerator class, the enumerator is automatically created on the same tier as the list. Additionally, to move to the next item in a list, you must explicitly call the more and next methods if you are using a list iterator. If you use the ListEnumerator class, you only have to call the moveNext method. The only situation where you cannot use a list enumerator is where you need to delete elements from a list. For more information, see the delete method.

## Examples

The following example creates a list and an iterator to point to it. It then uses various methods on the ListIterator class to print a description of the list, and the items in the list.

```xpp
{ 
    List il = new List(types::Integer); 
    ListIterator it; 
    // Add some elements into the list. 
    il.addStart(1); 
    il.addStart(2); 
    il.addStart(4);  
    // Create a list iterator to traverse the values. 
    it = new ListIterator (il);  
    // Prints "int list iterator". 
    print it.definitionString();  
    // Prints "(begin)[4]". 
    print it.toString();  
    // Go on for as long as elements are found in the list. 
    // Prints 4, 2, 1. 
    while (it.more()) 
    { 
        print it.value(); 
        it.next(); 
    } 
    // Prints (end). 
    print it.toString(); 
    pause; 
}
```

## Methods

| Method                               | Description                                                                                    |
|--------------------------------------|------------------------------------------------------------------------------------------------|
| public str definitionString()        | Returns a textual representation of the type of the iterator.                                  |
| public AnyType insert(AnyType value) | Inserts a new value at the position in the list that the iterator currently points to.         |
| public boolean more()                | Determines whether the list iterator points to a valid element.                                |
| public str toString()                | Returns a textual representation of the current list value that is pointed to by the iterator. |
| public AnyType value()               | Retrieves the value that is pointed to by the iterator.                                        |
| public void begin()                  | Moves the iterator to the start of the list.                                                   |
| public void next()                   | Moves the iterator to the next element in the list.                                            |
| public void end()                    | Moves the iterator past the last element in the list.                                          |
| public void delete()                 | Removes the element that is pointed to by the iterator from the list.                          |
| public void new(List list)           | Creates a new iterator for a particular list.                                                  |

## Method definitionString

Returns a textual representation of the type of the iterator.

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that contains the type of the iterator.

### Remarks - definitionString

For example: int list iterator.

## Method insert

Inserts a new value at the position in the list that the iterator currently points to.

```xpp
public AnyType insert(AnyType value)
```

### Parameters - insert

value  
The value of the item to insert into the list.

### Return Value - insert

The value that was inserted into the list.

### Remarks - insert

The value parameter must be the same type as the list.

### Examples - insert

The following example creates a list that has ten items and then uses the ListIterator.insert method to insert a new value as the third item in the list.

```xpp
{ 
    List il = new List(Types::Integer); 
    ListIterator it; 
    int i; 
    int j = 25; 
    // Insert values 1 to 10 into the list 
    for (i = 1; i <= 10; i++) 
    { 
        il.addEnd(i); 
    } 
    // Go to the 3rd element in the list 
    it = new ListIterator(il); 
    it.begin(); 
    it.next(); 
    it.next(); 
    // Insert a new value (25) 
    it.insert(j); 
  it.begin(); 
    // Print all values in the list. 
    // 25 is the third value in the list 
    while (it.more()) 
    { 
        print it.value(); 
        it.next();  
    } 
    pause; 
}
```

## Method more

Determines whether the list iterator points to a valid element.

```xpp
public boolean more()
```

### Return Value - more

true if the list iterator points to a valid element; otherwise, false.

### Remarks - more

Attempting to access an element when this method returns false will cause an error.

### Examples - more

The following example uses the ListIterator.more method to check whether there are more elements in the list and then runs through the while loop, which prints the values of all the elements in the list.

```xpp
{ 
    List il = new List(Types::Integer); 
    ListIterator it; 
    int i; 
    // Add some elements 
    for (i = 1; i <= 10; i++) 
    { 
        il.addEnd(i); 
    } 
    // Traverse the list 
    it = new ListIterator(il); 
    while (it.more()) 
    { 
        print it.value(); 
        it.next(); // Skip to the next element 
    } 
    pause; 
}
```

## Method toString

Returns a textual representation of the current list value that is pointed to by the iterator.

```xpp
public str toString()
```

### Return Value - toString

A string that contains a description of the current value.

### Remarks - toString

If the iterator points to the first element in the list, the string will contain an indication of this, in the form "(begin)\[value\]" If the iterator does not point to an element (that is, the more() method returns false), the following string returned is: (end). If the iterator points to a value, the string is "\[value\]", where value is a string representation of the element value.

### Examples - toString

The following example prints the following description of the values of the two values in a list:

1.  (begin) \[2\]
2.  \[1\]

<!-- -->

```xpp
{ 
    List li = new List(Types::Integer); 
    ListIterator it = new ListIterator(li); 
    li.addStart(1); 
    li.addStart(2); // This is now the first value 
    it.begin(); 
    print it.toString(); 
    it.next(); 
    print it.toString(); 
    pause; 
}
```

## Method value

Retrieves the value that is pointed to by the iterator.

```xpp
public AnyType value()
```

### Return Value - value

The value that is pointed to by the iterator.

### Remarks - value

Before you try to retrieve the value of a list element, use the ListIterator.more method to test whether an element exists.

## Method begin

Moves the iterator to the start of the list.

```xpp
public void begin()
```

## Method next

Moves the iterator to the next element in the list.

```xpp
public void next()
```

### Remarks - next

Use the ListIterator.more method to determine whether the iterator points to a valid element.

### Examples - next

The following example uses the ListIterator.next method to traverse a list as the value of each element is printed.

```xpp
{ 
    List il = new List(Types::Integer); 
    ListIterator it; 
    int i; 
    // Add some elements 
    for (i = 1; i <= 10; i++) 
    { 
        il.addEnd(i); 
    } 
    // Traverse the list 
    it = new ListIterator(il); 
    while (it.more()) 
    { 
        print it.value(); 
        // Move to the next element 
        it.next();  
    } 
    pause; 
}
```

## Method end

Moves the iterator past the last element in the list.

```xpp
public void end()
```

### Remarks - end

After this method runs, the ListIterator.more method will return false.

## Method delete

Removes the element that is pointed to by the iterator from the list.

```xpp
public void delete()
```

### Remarks - delete

The iterator will point to the next element after the deletion.

### Examples - delete

The following example creates a list that contains three elements and prints a description of the elements in the list. It then deletes the first element in the list and prints a description of the remaining elements.

```xpp
{ 
    List li = new List(Types::Integer); 
    ListIterator it; 
    li.addStart(1); 
    li.addStart(2); 
    li.addStart(3); 
    print li.toString(); 
    it = new ListIterator(li); 
    it.delete(); 
    print li.toString(); 
    pause; 
}
```

## Method new

Creates a new iterator for a particular list.

```xpp
public void new(List list)
```

### Parameters - new

list  
The list for which to create an iterator.

### Remarks - new

The iterator is positioned at the first value in the list, if the list is not empty. Iterators and the lists that they iterate over must be on the same client/server side.

### Examples - new

The following example creates an iterator for a list of integers.

```xpp
List il = new List(types::Integer); 
ListIterator it; 
it = new ListIterator (il);
```

