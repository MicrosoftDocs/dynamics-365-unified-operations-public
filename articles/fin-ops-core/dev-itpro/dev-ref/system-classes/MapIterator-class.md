---
title: MapIterator class
description: This topic describes the MapIterator class.
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

# Class MapIterator

[!include [banner](../../includes/banner.md)]

```xpp
class MapIterator extends Object
```

The MapIterator class is used to iterate over the elements in a map.

## Remarks

Map iterators are used to iterate over the elements in a map. They can be viewed as simple pointers into the maps over which they iterate. Functionality is available to start the iteration, determine whether more (key, value) pairs are available, and fetch the element that is pointed to by the iterator. It is better to use the MapEnumerator class than the MapIterator class. Map iterators and the maps over which they iterate must be on the same client/server side. If you use the MapIterator class and code is marked as Called from, the map and the iterator could end up on different tiers, and the code will fail. If you use the MapEnumerator class, the enumerator is automatically created on the same tier as the map. Additionally, if you use the MapIterator class, you must explicitly call the more and next methods to move to the next item in a map. If you use the MapEnumerator class, you only have to call the moveNext method. The sequence in which the elements are inserted does not determine the order in which they occur. The order is defined by the ordering of the elements. Elements that have lower keys appear before elements that have higher keys. The usual ordering for the types is used. However, if the keys are objects, the addresses of the objects are used to supply the ordering, and therefore no specific ordering can be inferred. The addresses of the objects are transient by nature.

## Examples

The following example creates a map and adds three (key, value) pairs. It then iterates through the map and prints information about each map element.

```xpp
{ 
    Map iim = new Map(Types::Integer, Types::Class); 
    MapIterator it; 
    // Add some elements into the map 
    iim.insert(1, new query()); 
    iim.insert(2, new query()); 
    iim.insert(4, new query()); 
    // Create a map iterator 
    it = new MapIterator (iim); 
    // Print "[int -> class] iterator" 
    print it.definitionString();     
    // Go on for as long as elements are found in the map 
    while (it.more()) 
    { 
        // Print each key (1, 2, 4) 
        print it.key();  
        // Print text representation of each value 
        print it.value().toString();  
        // Fetch next element in map 
        it.next(); 
    } 
    pause; 
}
```

## Methods

| Method                             | Description                                                                                    |
|------------------------------------|------------------------------------------------------------------------------------------------|
| public str definitionString()      | Retrieves a textual representation of the iterator type, such as "\[int -&gt; str\] iterator". |
| public AnyType domainValue()       | Returns the value of the key in the (key, value) pair that is referred to by the iterator.     |
| public boolean find(AnyType value) | Searches for the specified key value.                                                          |
| public AnyType key()               | Returns the key from the (key, value) pair that is referred to by the iterator.                |
| public boolean more()              | Determines whether the iterator finds a valid (key, value) pair.                               |
| public AnyType rangeValue()        | Returns the value of the value in the (key, value) pair that is referred to by the iterator.   |
| public str toString()              | Retrieves a textual representation of the iterator.                                            |
| public AnyType value()             | Returns the value from the (key, value) pair that is referred to by the iterator.              |
| public container valuePair()       | Retrieves a container that holds the key and the value.                                        |
| public void next()                 | Moves the iterator to the next (key, value) pair.                                              |
| public void new(Map map)           | Creates a new iterator for a map that lets you traverse through the elements in the map.       |
| public void begin()                | Moves the iterator to the start of the map.                                                    |
| public void end()                  | Moves the iterator past the last element in the map.                                           |
| public void delete()               | Removes from the map the element that is pointed to by the iterator.                           |

## Method definitionString

Retrieves a textual representation of the iterator type, such as "\[int -&gt; str\] iterator".

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that describes the iterator.

## Method domainValue

Returns the value of the key in the (key, value) pair that is referred to by the iterator.

```xpp
public AnyType domainValue()
```

### Return Value - domainValue

The value of the first item in the map element that is currently referred to by the iterator.

## Method find

Searches for the specified key value.

```xpp
public boolean find(AnyType value)
```

### Parameters - find

value  
The value to search for.

### Return Value - find

true if the value is found; otherwise, false.

### Remarks - find

If true is returned, the method positions the iterator at the element; otherwise, the MapIterator.more method returns false.

## Method key

Returns the key from the (key, value) pair that is referred to by the iterator.

```xpp
public AnyType key()
```

### Return Value - key

The key value of the map entry that is denoted by the iterator.

### Remarks - key

Use the SetIterator.more method to test whether an element exists before you try to retrieve the key value of the map element.

### Examples - key

The following example iterates through a map and returns a description of all the elements in the map.

```xpp
static str writeMap (Map m) 
{ 
    MapIterator it = new MapIterator(m); 
    str result; 
    while (it.more()) 
    { 
        result += it.key() + '\n' + it.value() + '\n'; 
        it.next(); 
    } 
    return result; 
}
```

## Method more

Determines whether the iterator finds a valid (key, value) pair.

```xpp
public boolean more()
```

### Return Value - more

true if more (key, value) pairs are available in the map; otherwise, false.

### Remarks - more

If you try to access an element that is pointed to by an iterator when the more method returns false, you receive an error. The more method only tests whether the iterator points to a valid element. It does not test whether there are more elements in the map.

### Examples - more

The following example iterates through a map by using the more method to check whether there are still elements in the map. It then returns a description of all the elements in the map.

```xpp
static str writeMap (Map m) 
{ 
    MapIterator it = new MapIterator(m); 
    str result; 
    while (it.more()) 
    { 
        result += it.key() + '\n' + it.value() + '\n'; 
        it.next(); 
    } 
    return result; 
}
```

## Method rangeValue

Returns the value of the value in the (key, value) pair that is referred to by the iterator.

```xpp
public AnyType rangeValue()
```

### Return Value - rangeValue

The value of the second item in the map element that is currently referred to by the iterator.

### Remarks - rangeValue

The rangeValue method has the same functionality as the MapIterator.value method, but it is available as a counterpart to the domainValue method.

## Method toString

Retrieves a textual representation of the iterator.

```xpp
public str toString()
```

### Return Value - toString

The string that describes the iterator.

### Remarks - toString

If the iterator points to the first element in the set, the string will contain an indication of this, in the form: "(begin)\[ *value*\]". If the iterator does not point to an element (that is, if the MapIterator.more method returns false), the string that is returned is "(end)". If the iterator points to a value, the string is "\[ *value*\]", where *value* is a string representation of the element value.

### Examples - toString

The following example iterates through an integer or class map, and prints information about each map element. It uses the MapIterator.toString method to return a textual representation of the class in each map element.

```xpp
{ 
    Map iim = new Map(Types::Integer, Types::Class); 
    MapIterator it; 
    // Add some elements into the map 
    iim.insert(1, new query()); 
    iim.insert(2, new query()); 
    iim.insert(4, new query()); 
    // Create a map iterator 
    it = new MapIterator (iim); 
    // Go on for as long as elements are found in the map 
    while (it.more()) 
    { 
        // Print each key (1, 2, 4) 
        print it.key();  
        // Print text representation of each value 
        print it.value().toString();  
        // Fetch next element in map 
        it.next(); 
    } 
    pause; 
}
```

## Method value

Returns the value from the (key, value) pair that is referred to by the iterator.

```xpp
public AnyType value()
```

### Return Value - value

The value from the map element that is denoted by the map iterator.

### Remarks - value

Use the MapIterator.more method to test whether an element exists before you try to retrieve the key value of the map element.

### Examples - value

The following example iterates through a map and returns a list of all the elements in the map.

```xpp
static str writeMap (Map m) 
{ 
    MapIterator it = new MapIterator(m); 
    str result; 
    while (it.more()) 
    { 
        result += it.key() + '\n' + it.value() + '\n'; 
        it.next(); 
    } 
    return result; 
}
```

## Method valuePair

Retrieves a container that holds the key and the value.

```xpp
public container valuePair()
```

### Return Value - valuePair

A container that holds the key and the value.

### Remarks - valuePair

Objects cannot reside in containers. Therefore, an exception is raised if either the key or the value is an object.

## Method next

Moves the iterator to the next (key, value) pair.

```xpp
public void next()
```

### Remarks - next

You can use the MapIterator.more method to determine whether there are any more elements in the map.

### Examples - next

The following example uses the next method to iterate through a map and returns a list of all the elements in the map.

```xpp
static str writeMap (Map m) 
{ 
    MapIterator it = new MapIterator(m); 
    str result; 
    while (it.more()) 
    { 
        result += it.key() + '\n' + it.value() + '\n'; 
        it.next(); 
    } 
    return result; 
}
```

## Method new

Creates a new iterator for a map that lets you traverse through the elements in the map.

```xpp
public void new(Map map)
```

### Parameters - new

map  
The map for which to create an iterator.

### Remarks - new

The iterator is positioned at the first value in the map if the map is not empty.

### Examples - new

The following example creates a map of (integer, class) pairs and then creates an iterator to traverse the map.

```xpp
Map iim = new Map(Types::Integer, Types::Class); 
MapIterator it; 
it = new MapIterator (iim);
```

## Method begin

Moves the iterator to the start of the map.

```xpp
public void begin()
```

### Remarks - begin

Newly created map iterators are positioned at the first element in the map, so you do not have to call the begin method before you iterate through the set. You must call the begin method if you want to reset the pointer.

## Method end

Moves the iterator past the last element in the map.

```xpp
public void end()
```

### Remarks - end

After this method runs, the MapIterator.more method will return false.

## Method delete

Removes from the map the element that is pointed to by the iterator.

```xpp
public void delete()
```

### Remarks - delete

The iterator points to the next element after the delete method is invoked.

