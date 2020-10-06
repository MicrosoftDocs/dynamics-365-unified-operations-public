---
title: MapEnumerator class
description: This topic describes the MapEnumerator class.
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

# Class MapEnumerator

[!include [banner](../../includes/banner.md)]

```xpp
class MapEnumerator extends Object
```

The MapEnumerator class lets you traverse through the elements in a map.

## Remarks

Map enumerators start before the first element in the list. You must call the MapEnumerator.moveNext method to make it point to the first element in the list. It is a best practice to use the MapEnumerator class instead of the MapIterator class because enumerators are automatically created on the same tier as the map when you call the Map.getEnumerator method. Using the MapEnumerator class avoids a potential problem in code marked as Called from, where the iterator and map can end up on separate tiers. In addition, because map enumerators require less code than map iterators, they perform slightly better. The only situation where you have to use a map iterator, is when you want to delete items from a list by using the MapIterator.delete method.

## Examples

## Methods

| Method                        | Description                                                                                                                                       |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| public AnyType current()      | This method is obsolete; use MapEnumerator.currentKey instead.                                                                                    |
| public AnyType currentKey()   | Returns the key from the (key, value) pair that is currently pointed to by the enumerator.                                                        |
| public AnyType currentValue() | Returns the value from the (key, value) pair that is currently pointed to by the enumerator.                                                      |
| public str definitionString() | Returns a description of the enumerator. For example, an enumerator for a map of integers to strings would return "\[int -&gt; str\] enumerator". |
| public boolean moveNext()     | Determines whether the enumerator points to a valid map element.                                                                                  |
| public str toString()         | Returns a string that represents the current object.                                                                                              |
| public void new(Map map)      | Initializes a new instance of the Object class.                                                                                                   |
| public void reset()           | Moves the enumerator to point to just before the first element in the map.                                                                        |

## Method current

This method is obsolete; use MapEnumerator.currentKey instead.

```xpp
public AnyType current()
```

### Return Value - current

## Method currentKey

Returns the key from the (key, value) pair that is currently pointed to by the enumerator.

```xpp
public AnyType currentKey()
```

### Return Value - currentKey

The key from the map element that is currently pointed to by the enumerator.

### Remarks - currentKey

You must call the MapEnumerator.moveNext method before you call the currentKey method.

### Examples - currentKey

The following example searches for a particular table ID in a map and then returns the key value of that map element.

```xpp
private LabelType tableLabel(tableId _tableId) 
{ 
    LabelType     labelType; 
    MapEnumerator mapEnum; 
    mapEnum = tableAllMap.getEnumerator(); 
    while (mapEnum.moveNext()) 
    { 
        if (_tableId == mapEnum.currentValue()) 
        { 
            labelType = mapEnum.currentKey(); 
            break; 
        } 
    } 
    return labelType; 
}
```

## Method currentValue

Returns the value from the (key, value) pair that is currently pointed to by the enumerator.

```xpp
public AnyType currentValue()
```

### Return Value - currentValue

The value from the map element that is currently pointed to by the enumerator.

### Remarks - currentValue

You must call the MapEnumerator.moveNext method before you call this method.

### Examples - currentValue

The following example searches through a map to find an element that has a value equal to that passed in as a parameter. The MapEnumerator.moveNext method is used to iterate through the map, and the currentValue method is used to test each value to see whether it matches the parameter.

```xpp
private LabelType tableLabel(tableId _tableId) 
{ 
    LabelType     labelType; 
    MapEnumerator mapEnum; 
    mapEnum = tableAllMap.getEnumerator(); 
    while (mapEnum.moveNext()) 
    { 
        if (_tableId == mapEnum.currentValue()) 
        { 
            labelType = mapEnum.currentKey(); 
            break; 
        } 
    } 
    return labelType; 
}
```

## Method definitionString

Returns a description of the enumerator. For example, an enumerator for a map of integers to strings would return "\[int -&gt; str\] enumerator".

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that contains a description of the enumerator.

### Examples - definitionString

The following example creates a map and an enumerator for it, and then it prints out a definition of the enumerator.

```xpp
{ 
    Map myMap = new Map(Types::Integer, Types::String); 
    MapEnumerator  enumerator; 
    int i; 
    // Add some elements to the map 
    myMap.insert(1, "Element one"); 
    myMap.insert(2, "Element two"); 
    myMap.insert(3, "Element three"); 
    myMap.insert(4, "Element Four"); 
    // Set the enumerator 
    enumerator = myMap.getEnumerator(); 
    print enumerator.definitionString(); 
    pause; 
}
```

## Method moveNext

Determines whether the enumerator points to a valid map element.

```xpp
public boolean moveNext()
```

### Return Value - moveNext

true if the current position in the map holds a valid element; otherwise false.

### Remarks - moveNext

Map enumerators start before the first element in the map. You must call the moveNext method to make it point to the first element in the map.

### Examples - moveNext

The following example uses the moveNext method to iterate over the tables that are contained in a project and adds them to a new map that contains a DictTable object for each table. (DictTable lets you access information about a table.)

```xpp
{ 
    Map map = Map::create( 
        SysUmlDataModel::getProjectTablesClient(projectNode)); 
    MapEnumerator enum = map.getEnumerator(); 
    TableName tableName; 
    while (enum.moveNext()) 
    { 
        tableName = enum.currentKey(); 
        map.insert(tableName, new DictTable(tablename2id(tableName))); 
    } 
    return map; 
}
```

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Examples - toString

The following example creates a map, and then prints the content of the first and second elements in the map.

```xpp
{ 
    Map myMap = new Map(Types::Integer, Types::String); 
    MapEnumerator  enumerator; 
    int i; 
     // Add some elements to the map 
    myMap.insert(1, "Element one"); 
    myMap.insert(2, "Element two"); 
    myMap.insert(3, "Element three"); 
    myMap.insert(4, "Element Four"); 
    // Set the enumerator 
    enumerator = myMap.getEnumerator(); 
    // Go to beginning of enumerator 
    enumerator.reset(); 
    // Go to the first element in the map 
    enumerator.moveNext(); 
    // Print first item in the map 
    print enumerator.toString(); 
    // go to second element 
     enumerator.moveNext(); 
    // Print second element in map 
    print enumerator.toString(); 
    pause; 
}
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(Map map)
```

### Parameters - new

map  
The map for which to create an enumerator.

### Remarks - new

This method is obsolete. Use the Map.getEnumerator method instead.

## Method reset

Moves the enumerator to point to just before the first element in the map.

```xpp
public void reset()
```

### Remarks - reset

The reset method moves the enumerator to the start of the set, before the first element in the set. You must call the MapEnumerator.moveNext method to make it point to the first element in the set.

