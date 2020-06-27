---
title: Map class
description: This topic describes the Map class.
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

# Class Map

[!include [banner](../../includes/banner.md)]

```xpp
class Map extends Object
```

The Map class lets to associate one value (the key) with another value.

## Remarks

Both the key and the value can be any valid X++ type, including objects. The types of the key and the value are specified in the declaration of the map. The way in which maps are implemented means that access to the values is very fast. Multiple keys can map to the same value, but one key can map to only one value at a time. If you add a (key, value) pair that has an existing key value, it replaces the existing pair with that key value. The (key, value) pairs in a map can be traversed by using the MapEnumerator class.

## Examples

The following example illustrates how to invert a map. A map can be inverted only if no value is mapped to by two different keys. The number of elements in the Map.keySet method and the Map.valueSet method is compared to check this. Otherwise, the elements are traversed in the incoming map and inserted into the result map. The function that performs the inversion, the invertMap method, works regardless of the types of the keys and values.

```xpp
{ 
    Map example; 
    Map invertMap(map _mapToInvert) 
    { 
        MapEnumerator en; 
        Map result =  new Map( 
            _mapToInvert.valueType(), 
            _mapToInvert.keyType()); 
        if (_mapToInvert.keySet().elements()  
            != _mapToInvert.valueSet().elements()) 
        { 
            return null; 
        } 
        en = new MapEnumerator(_mapToInvert); 
        while (en.moveNext()) 
        { 
            result.insert(en.currentValue(), en.currentKey()); 
        } 
        return result; 
    } 
    ; 
    // Fill in a few values. 
    example = new Map(Types::Integer, Types::String); 
    example.insert (1, "one"); 
    example.insert (2, "two"); 
    print invertMap(example).toString(); 
    pause; 
    // Now two keys (2 and 3) map to the same value 
    // so can't create inverse map 
    example.insert (3, "two"); 
    if (!invertMap(example)) 
    { 
        print "Could not create the map"; 
    } 
    pause; 
}
```

## Methods

| Method                                                      | Description                                                                                     |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| public str definitionString()                               | Returns a string that contains a definition of the map.                                         |
| public Set domainSet()                                      | Creates a set of the key (domain) values in a map.                                              |
| public Types domainType()                                   | Determines the type of the key (domain) values in a map.                                        |
| public int elements()                                       | Returns the number of elements in the map.                                                      |
| public boolean empty()                                      | Determines whether the map contains any (key, value) pairs.                                     |
| public boolean exists(AnyType keyValue)                     | Determines whether a particular value exists as a key in the map.                               |
| public MapEnumerator getEnumerator()                        | Creates an enumerator for the map, which lets you traverse the map.                             |
| public boolean insert(AnyType keyValue, AnyType valueValue) | Inserts an element (keyValue, valueValue pair) into the map.                                    |
| public Set keySet()                                         | Returns a set that contains the key values from a map.                                          |
| public Types keyType()                                      | Returns the type of the key values in a map.                                                    |
| public AnyType lookup(AnyType keyValue)                     | Returns the value that is mapped to by a specified key value.                                   |
| public container pack()                                     | Serializes the current instance of the Map class.                                               |
| public Set rangeSet()                                       | Returns a set that contains the values (ranges) that are mapped to by the keys in a map.        |
| public Types rangeType()                                    | Determines the type of the values (ranges) that are mapped to by the keys in a map.             |
| public boolean remove(AnyType keyValue)                     | Removes a (key, value) pair from a map.                                                         |
| public str toString()                                       | Returns a description of the (key, value) pairs in the map.                                     |
| public Set valueSet()                                       | Returns a set that contains the values that are mapped to by the keys in a map.                 |
| public Types valueType()                                    | Returns the type of the values that are mapped to by the keys in a map.                         |
| public str xml(\[int indent\])                              | Returns an XML string that represents the current object.                                       |
| ::public static Map create(container container)             | Creates a map from the container that was obtained from a previous call to the Map.pack method. |
| ::public static Map createFromXML(Object xmlnode)           |                                                                                                 |
| ::public static boolean equal(Map map1, Map map2)           | Determines whether two maps are equal.                                                          |
| public void new(Types key, Types value)                     | Creates a new map.                                                                              |

## Method definitionString

Returns a string that contains a definition of the map.

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that contains the definition of the map.

### Remarks - definitionString

The definition of the map.

### Examples - definitionString

The following example creates a map and then prints the definition of the map.

```xpp
{ 
    Map myMap = new Map(Types::Integer, Types::String); 
    print myMap.definitionString(); 
    pause; 
}
```

## Method domainSet

Creates a set of the key (domain) values in a map.

```xpp
public Set domainSet()
```

### Return Value - domainSet

### Remarks - domainSet

This method is obsolete; use the Map.keySet method instead.

## Method domainType

Determines the type of the key (domain) values in a map.

```xpp
public Types domainType()
```

### Return Value - domainType

### Remarks - domainType

This method is obsolete; use the Map.keyType method instead.

## Method elements

Returns the number of elements in the map.

```xpp
public int elements()
```

### Return Value - elements

The number of elements in the map.

### Remarks - elements

The number of elements in the map is equal to the number of different key values in the map.

### Examples - elements

The following example uses the elements method to check whether a map has any elements. If the \_from map exists and has some elements, the values from the \_from map are inserted into the \_to map.

```xpp
static void mergeRecsPrim( 
    Map _from, 
    Map _to 
    ) 
{ 
    MapEnumerator   me; 
    if (! _from) 
    { 
        return; 
    } 
    if (! _from.elements()) 
    { 
        return; 
    } 
    me = _from.getEnumerator(); 
    while (me.moveNext()) 
    { 
        _to.insert(me.currentKey(),me.currentValue()); 
    } 
}
```

## Method empty

Determines whether the map contains any (key, value) pairs.

```xpp
public boolean empty()
```

### Return Value - empty

true if the map does not contain any elements; otherwise, false.

### Remarks - empty

This method is equivalent to (elements() == 0).

## Method exists

Determines whether a particular value exists as a key in the map.

```xpp
public boolean exists(AnyType keyValue)
```

### Parameters - exists

keyValue  
The value to check for.

### Return Value - exists

true if the specified key value exists in the map; otherwise, false.

### Remarks - exists

Use this method to guard calls to the Map.lookup method. If the Map.lookup method does not find the value that it is looking for, it throws an exception.

### Examples - exists

The following example checks whether a particular style exists in a map of styles in a style sheet. If it does, a new name is substituted for the body style.

```xpp
static void renameStyle(Map stylesheet, str fromName, str toName) 
{ 
    str body; 
    if (stylesheet.exists(fromName)) 
    { 
        body = stylesheet.lookup (fromName); 
        stylesheet.remove (fromName); 
        stylesheet.insert (toName, body); 
    } 
    else 
    { 
        info (fromName); 
    } 
}
```

## Method getEnumerator

Creates an enumerator for the map, which lets you traverse the map.

```xpp
public MapEnumerator getEnumerator()
```

### Return Value - getEnumerator

A MapEnumerator object for the map.

### Examples - getEnumerator

The following example checks whether the \_from map has any elements and creates an enumerator for the map if it has any elements. The map is then traversed, and the elements in it are inserted into the \_to map.

```xpp
static void mergeRecsPrim( 
    Map _from, 
    Map _to 
    ) 
{ 
    MapEnumerator   me; 
    if (! _from) 
    { 
        return; 
    } 
    if (! _from.elements()) 
    { 
        return; 
    } 
    me = _from.getEnumerator(); 
    while (me.moveNext()) 
    { 
        _to.insert(me.currentKey(),me.currentValue()); 
    } 
}
```

## Method insert

Inserts an element (keyValue, valueValue pair) into the map.

```xpp
public boolean insert(AnyType keyValue, AnyType valueValue)
```

### Parameters - insert

keyValue  
The value that is mapped to by the key.

<!-- -->

valueValue  
The value that is mapped to by the key.

### Return Value - insert

true if the key did not already exist in the map and has been inserted; otherwise, false.

### Remarks - insert

If the key already exists in the map, the value is updated.

### Examples - insert

The following example checks whether the \_from map has any elements and creates an enumerator for the map if it has any elements. The map is traversed, and the insert method is used to insert the elements from the \_from map into the \_to map.

```xpp
static void mergeRecsPrim( 
    Map _from, 
    Map _to 
    ) 
{ 
    MapEnumerator   me; 
    if (! _from) 
    { 
        return; 
    } 
    if (! _from.elements()) 
    { 
        return; 
    } 
    me = _from.getEnumerator(); 
    while (me.moveNext()) 
    { 
        _to.insert(me.currentKey(),me.currentValue()); 
    } 
}
```

## Method keySet

Returns a set that contains the key values from a map.

```xpp
public Set keySet()
```

### Return Value - keySet

A set that contains the key values.

### Examples - keySet

The following example deletes all elements from a map that have key values that are not found as elements in a set.

```xpp
public void deleteItems(Set _set, Map _map) 
{ 
    Set             deletedSet; 
    SetEnumerator   enumerator; 
    // deletedSet contains all key values from 
    // _map that are not values in _set 
    deletedSet = Set::difference(_map.keySet(), _set); 
    enumerator = deletedSet.getEnumerator(); 
    while (enumerator.moveNext()) 
    { 
        // Deletes elements from map with key 
        // values matching values in deletedSet 
        _map.remove(enumerator.current()); 
    } 
}
```

## Method keyType

Returns the type of the key values in a map.

```xpp
public Types keyType()
```

### Return Value - keyType

The type of the key values.

### Remarks - keyType

The possible return values are outlined by the Types system enum. The type of the key values is determined when the map is constructed. It is supplied as the first parameter to the Map.new method.

## Method lookup

Returns the value that is mapped to by a specified key value.

```xpp
public AnyType lookup(AnyType keyValue)
```

### Parameters - lookup

keyValue  
The key to find.

### Return Value - lookup

The value that is mapped to by the specified key.

### Remarks - lookup

An exception is thrown if the key is not found in the map, so check whether the value that you want to retrieve exists by using the Map.exists method.

### Examples - lookup

The following example checks whether a particular style exists in a map of styles in a style sheet. If it does, a new name is substituted for the body style.

```xpp
static void renameStyle(Map stylesheet, str fromName, str toName) 
{ 
    str body; 
    if (stylesheet.exists(fromName)) 
    { 
        body = stylesheet.lookup (fromName); 
        stylesheet.remove (fromName); 
        stylesheet.insert (toName, body); 
    } 
    else 
    { 
        info (fromName); 
    } 
}
```

## Method pack

Serializes the current instance of the Map class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the Map class.

### Remarks - pack

The container created by this method contains 4 elements before the first element from the map:

-   A version number for the container
-   An integer that identifies the data type of the keys in the map
-   An integer that identifies the data type of the values in the map
-   The number of elements in the map

If the keys or the values are objects, packing is performed by calling the pack method successively on each object to yield a subcontainer. The pack and unpack methods cannot preserve X++ anytype values. One option is to put the anytype values into objects or structs, and have the structs be the values in the Map object. Use of Microsoft .NET System.Collections classes is another option. The map can be retrieved from the packed container by using the Map.create method.

### Examples - pack

The following example creates a map from a container that is passed into the method (conprojItemTransSalesAmount), adds some values to it, and then uses MapEnumerator.pack to pack the map into a container. The new container is then returned by the method.

```xpp
server static container salesAmountDisplayCache( 
    container   _conprojItemTrans, 
    container   _conprojItemTransSalesAmount, 
    TransDate   _ledgerFromDate, 
    TransDate   _ledgerToDate) 
{ 
    ProjItemTrans    projItemTrans; 
    Set              setprojItemTrans; 
    Map              mapprojItemTransSalesAmount; 
    SetIterator      si; 
    if(_conprojItemTrans) 
    { 
        setprojItemTrans = Set::create(_conprojItemTrans); 
    } 
    if(_conprojItemTransSalesAmount) 
    { 
        mapprojItemTransSalesAmount = Map::create( 
            _conprojItemTransSalesAmount); 
    } 
    si = new SetIterator(setprojItemTrans); 
    si.begin(); 
    while (si.more()) 
    { 
        projItemTrans = ProjItemTrans::find(si.value()); 
        mapprojItemTransSalesAmount.insert( 
            si.value(),  
            projItemTrans.salesAmount( 
                projItemTrans, 
               _ledgerFromDate, 
               _ledgerToDate)); 
        si.next(); 
    } 
    return mapprojItemTransSalesAmount.pack(); 
}
```

## Method rangeSet

Returns a set that contains the values (ranges) that are mapped to by the keys in a map.

```xpp
public Set rangeSet()
```

### Return Value - rangeSet

### Remarks - rangeSet

This method is obsolete; use the Map.valueSet method instead.

## Method rangeType

Determines the type of the values (ranges) that are mapped to by the keys in a map.

```xpp
public Types rangeType()
```

### Return Value - rangeType

### Remarks - rangeType

This method is obsolete; use the valueType method instead.

## Method remove

Removes a (key, value) pair from a map.

```xpp
public boolean remove(AnyType keyValue)
```

### Parameters - remove

keyValue  
The value of the key to delete.

### Return Value - remove

true if the key was found in the map and the element has been deleted; otherwise, false.

### Examples - remove

The following example checks whether a particular key value exists in a map. If the value exists, the method deletes the key and its corresponding value. The method returns true if the value was found and false if the key did not exist in the map.

```xpp
public boolean clear(str owner) 
{ 
    // maps is a class variable 
    if (maps.exists(owner)) 
    { 
        maps.remove(owner); 
    } 
    else 
    { 
        return false; 
    } 
    return true; 
}
```

## Method toString

Returns a description of the (key, value) pairs in the map.

```xpp
public str toString()
```

### Return Value - toString

A string that contains a description of the elements in the map.

### Examples - toString

The following example creates a map, adds some elements to it, and then prints a description of these elements.

```xpp
{ 
    Map myMap = new Map(Types::Integer, Types::String); 
    // Add some elements to the map 
    myMap.insert(1, "Element one"); 
    myMap.insert(2, "Element two"); 
    myMap.insert(3, "Element three"); 
    myMap.insert(4, "Element Four"); 
    print myMap.toString(); 
    pause; 
}
```

## Method valueSet

Returns a set that contains the values that are mapped to by the keys in a map.

```xpp
public Set valueSet()
```

### Return Value - valueSet

A set that contains the values from the map.

### Remarks - valueSet

If all the keys map to different values, the number of elements in the set is equal to the number of elements in the map.

## Method valueType

Returns the type of the values that are mapped to by the keys in a map.

```xpp
public Types valueType()
```

### Return Value - valueType

The type of the values that are mapped to by the keys.

### Remarks - valueType

The type of the key values is determined when the map is constructed. It is supplied as the first parameter to the Map.new method.

## Method xml

Returns an XML string that represents the current object.

```xpp
public str xml([int indent])
```

### Parameters - xml

indent  
The amount of indentation of the XML string that is returned; optional.

### Return Value - xml

An XML string that represents the current object.

### Remarks - xml

This method can be overridden to return values that are meaningful for that type.

## Method create

Creates a map from the container that was obtained from a previous call to the Map.pack method.

```xpp
public static Map create(container container)
```

### Parameters - create

container  

### Return Value - create

A map that is equal to the map that was packed into the container by the Map.pack method.

### Remarks - create

If the keys or values are objects, the objects must have an unpack method that is called to re-establish their internal state from the container.

### Examples - create

The following example creates a map from a container that is passed into the method (conprojItemTransSalesAmount), adds some values to the container, and then packs the map and returns it as a new container.

```xpp
server static container salesAmountDisplayCache( 
    container   _conprojItemTrans, 
    container   _conprojItemTransSalesAmount, 
    TransDate   _ledgerFromDate, 
    TransDate   _ledgerToDate) 
{ 
    ProjItemTrans    projItemTrans; 
    Set              setprojItemTrans; 
    Map              mapprojItemTransSalesAmount; 
    SetIterator      si; 
    if(_conprojItemTrans) 
    { 
        setprojItemTrans = Set::create(_conprojItemTrans); 
    } 
    if(_conprojItemTransSalesAmount) 
    { 
        mapprojItemTransSalesAmount = Map::create( 
            _conprojItemTransSalesAmount); 
    } 
    si = new SetIterator(setprojItemTrans); 
    si.begin(); 
    while (si.more()) 
    { 
        projItemTrans = ProjItemTrans::find(si.value()); 
        mapprojItemTransSalesAmount.insert( 
            si.value(),  
            projItemTrans.salesAmount( 
                projItemTrans, 
               _ledgerFromDate, 
               _ledgerToDate)); 
        si.next(); 
    } 
    return mapprojItemTransSalesAmount.pack(); 
}
```

## Method createFromXML

```xpp
public static Map createFromXML(Object xmlnode)
```

### Parameters - createFromXML

xmlnode  

### Return Value - createFromXML

## Method equal

Determines whether two maps are equal.

```xpp
public static boolean equal(Map map1, Map map2)
```

### Parameters - equal

map1  
The second map to compare.

<!-- -->

map2  
The second map to compare.

### Return Value - equal

true if the two maps are equal; otherwise, false.

### Remarks - equal

Two maps are equal if they contain the same number of elements, their key sets are the same, and each key in the key set maps to the same value in both maps.

## Method new

Creates a new map.

```xpp
public void new(Types key, Types value)
```

### Parameters - new

key  
The type of the values.

<!-- -->

value  
The type of the values.

### Examples - new

The following example creates a map that maps string keys to integer values.

```xpp
Map myMap = new Map(Types::String, Types::Integer);
```

