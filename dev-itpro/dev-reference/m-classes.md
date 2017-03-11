---
# required metadata

title: M Classes
description: System API classes that start with the letter M.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-24 14 - 27 - 00
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 52321
ms.assetid: 954d2067-ef47-4714-ae75-23e7a5d539db
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# M Classes

System API classes that start with the letter M.

Class ManagedEventArgs
----------------------

    class ManagedEventArgs extends Object

### Remarks

### Examples

### Methods

| Method            | Description                                               |
|-------------------|-----------------------------------------------------------|
| public void new() | Initializes a new instance of the ManagedEventArgs class. |

### Method new

Initializes a new instance of the ManagedEventArgs class.

    public void new()

## Class ManagedEventDelegate
    class ManagedEventDelegate extends Object

### Remarks

### Examples

### Methods

| Method                                                                    | Description                                                   |
|---------------------------------------------------------------------------|---------------------------------------------------------------|
| public boolean marshalExceptionsToXPP(\[boolean marshalExceptionsToXPP\]) |                                                               |
| private void new()                                                        | Initializes a new instance of the ManagedEventDelegate class. |
| public void invoke(Object sender, ManagedEventArgs args)                  |                                                               |

### Method marshalExceptionsToXPP

    public boolean marshalExceptionsToXPP([boolean marshalExceptionsToXPP])

#### Parameters

marshalExceptionsToXPP  

#### Return Value

### Method new

Initializes a new instance of the ManagedEventDelegate class.

    private void new()

### Method invoke

    public void invoke(Object sender, ManagedEventArgs args)

#### Parameters

sender  

<!-- -->

args  

## Class ManagedEventHandler
    class ManagedEventHandler extends Object

### Remarks

### Examples

### Methods

| Method                                     | Description                                     |
|--------------------------------------------|-------------------------------------------------|
| public void finalize()                     |                                                 |
| public void new(Object object, str method) | Initializes a new instance of the Object class. |

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the Object class.

    public void new(Object object, str method)

#### Parameters

object  

<!-- -->

method  

## Class Map
    class Map extends Object

The Map class lets to associate one value (the key) with another value.

### Remarks

Both the key and the value can be any valid X++ type, including objects. The types of the key and the value are specified in the declaration of the map. The way in which maps are implemented means that access to the values is very fast. Multiple keys can map to the same value, but one key can map to only one value at a time. If you add a (key, value) pair that has an existing key value, it replaces the existing pair with that key value. The (key, value) pairs in a map can be traversed by using the MapEnumerator class.

### Examples

The following example illustrates how to invert a map. A map can be inverted only if no value is mapped to by two different keys. The number of elements in the Map.keySet method and the Map.valueSet method is compared to check this. Otherwise, the elements are traversed in the incoming map and inserted into the result map. The function that performs the inversion, the invertMap method, works regardless of the types of the keys and values.

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

### Methods

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

### Method definitionString

Returns a string that contains a definition of the map.

    public str definitionString()

#### Return Value

A string that contains the definition of the map.

#### Remarks

The definition of the map.

#### Examples

The following example creates a map and then prints the definition of the map.

    { 
        Map myMap = new Map(Types::Integer, Types::String); 
        print myMap.definitionString(); 
        pause; 
    }

### Method domainSet

Creates a set of the key (domain) values in a map.

    public Set domainSet()

#### Return Value

#### Remarks

This method is obsolete; use the Map.keySet method instead.

### Method domainType

Determines the type of the key (domain) values in a map.

    public Types domainType()

#### Return Value

#### Remarks

This method is obsolete; use the Map.keyType method instead.

### Method elements

Returns the number of elements in the map.

    public int elements()

#### Return Value

The number of elements in the map.

#### Remarks

The number of elements in the map is equal to the number of different key values in the map.

#### Examples

The following example uses the elements method to check whether a map has any elements. If the \_from map exists and has some elements, the values from the \_from map are inserted into the \_to map.

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

### Method empty

Determines whether the map contains any (key, value) pairs.

    public boolean empty()

#### Return Value

true if the map does not contain any elements; otherwise, false.

#### Remarks

This method is equivalent to (elements() == 0).

### Method exists

Determines whether a particular value exists as a key in the map.

    public boolean exists(AnyType keyValue)

#### Parameters

keyValue  
The value to check for.

#### Return Value

true if the specified key value exists in the map; otherwise, false.

#### Remarks

Use this method to guard calls to the Map.lookup method. If the Map.lookup method does not find the value that it is looking for, it throws an exception.

#### Examples

The following example checks whether a particular style exists in a map of styles in a style sheet. If it does, a new name is substituted for the body style.

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

### Method getEnumerator

Creates an enumerator for the map, which lets you traverse the map.

    public MapEnumerator getEnumerator()

#### Return Value

A MapEnumerator object for the map.

#### Examples

The following example checks whether the \_from map has any elements and creates an enumerator for the map if it has any elements. The map is then traversed, and the elements in it are inserted into the \_to map.

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

### Method insert

Inserts an element (keyValue, valueValue pair) into the map.

    public boolean insert(AnyType keyValue, AnyType valueValue)

#### Parameters

keyValue  
The value that is mapped to by the key.

<!-- -->

valueValue  
The value that is mapped to by the key.

#### Return Value

true if the key did not already exist in the map and has been inserted; otherwise, false.

#### Remarks

If the key already exists in the map, the value is updated.

#### Examples

The following example checks whether the \_from map has any elements and creates an enumerator for the map if it has any elements. The map is traversed, and the insert method is used to insert the elements from the \_from map into the \_to map.

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

### Method keySet

Returns a set that contains the key values from a map.

    public Set keySet()

#### Return Value

A set that contains the key values.

#### Examples

The following example deletes all elements from a map that have key values that are not found as elements in a set.

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

### Method keyType

Returns the type of the key values in a map.

    public Types keyType()

#### Return Value

The type of the key values.

#### Remarks

The possible return values are outlined by the Types system enum. The type of the key values is determined when the map is constructed. It is supplied as the first parameter to the Map.new method.

### Method lookup

Returns the value that is mapped to by a specified key value.

    public AnyType lookup(AnyType keyValue)

#### Parameters

keyValue  
The key to find.

#### Return Value

The value that is mapped to by the specified key.

#### Remarks

An exception is thrown if the key is not found in the map, so check whether the value that you want to retrieve exists by using the Map.exists method.

#### Examples

The following example checks whether a particular style exists in a map of styles in a style sheet. If it does, a new name is substituted for the body style.

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

### Method pack

Serializes the current instance of the Map class.

    public container pack()

#### Return Value

A container that contains the current instance of the Map class.

#### Remarks

The container created by this method contains 4 elements before the first element from the map:

-   A version number for the container
-   An integer that identifies the data type of the keys in the map
-   An integer that identifies the data type of the values in the map
-   The number of elements in the map

If the keys or the values are objects, packing is performed by calling the pack method successively on each object to yield a subcontainer. The pack and unpack methods cannot preserve X++ anytype values. One option is to put the anytype values into objects or structs, and have the structs be the values in the Map object. Use of Microsoft .NET System.Collections classes is another option. The map can be retrieved from the packed container by using the Map.create method.

#### Examples

The following example creates a map from a container that is passed into the method (conprojItemTransSalesAmount), adds some values to it, and then uses MapEnumerator.pack to pack the map into a container. The new container is then returned by the method.

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

### Method rangeSet

Returns a set that contains the values (ranges) that are mapped to by the keys in a map.

    public Set rangeSet()

#### Return Value

#### Remarks

This method is obsolete; use the Map.valueSet method instead.

### Method rangeType

Determines the type of the values (ranges) that are mapped to by the keys in a map.

    public Types rangeType()

#### Return Value

#### Remarks

This method is obsolete; use the valueType method instead.

### Method remove

Removes a (key, value) pair from a map.

    public boolean remove(AnyType keyValue)

#### Parameters

keyValue  
The value of the key to delete.

#### Return Value

true if the key was found in the map and the element has been deleted; otherwise, false.

#### Examples

The following example checks whether a particular key value exists in a map. If the value exists, the method deletes the key and its corresponding value. The method returns true if the value was found and false if the key did not exist in the map.

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

### Method toString

Returns a description of the (key, value) pairs in the map.

    public str toString()

#### Return Value

A string that contains a description of the elements in the map.

#### Examples

The following example creates a map, adds some elements to it, and then prints a description of these elements.

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

### Method valueSet

Returns a set that contains the values that are mapped to by the keys in a map.

    public Set valueSet()

#### Return Value

A set that contains the values from the map.

#### Remarks

If all the keys map to different values, the number of elements in the set is equal to the number of elements in the map.

### Method valueType

Returns the type of the values that are mapped to by the keys in a map.

    public Types valueType()

#### Return Value

The type of the values that are mapped to by the keys.

#### Remarks

The type of the key values is determined when the map is constructed. It is supplied as the first parameter to the Map.new method.

### Method xml

Returns an XML string that represents the current object.

    public str xml([int indent])

#### Parameters

indent  
The amount of indentation of the XML string that is returned; optional.

#### Return Value

An XML string that represents the current object.

#### Remarks

This method can be overridden to return values that are meaningful for that type.

### Method create

Creates a map from the container that was obtained from a previous call to the Map.pack method.

    public static Map create(container container)

#### Parameters

container  

#### Return Value

A map that is equal to the map that was packed into the container by the Map.pack method.

#### Remarks

If the keys or values are objects, the objects must have an unpack method that is called to re-establish their internal state from the container.

#### Examples

The following example creates a map from a container that is passed into the method (conprojItemTransSalesAmount), adds some values to the container, and then packs the map and returns it as a new container.

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

### Method createFromXML

    public static Map createFromXML(Object xmlnode)

#### Parameters

xmlnode  

#### Return Value

### Method equal

Determines whether two maps are equal.

    public static boolean equal(Map map1, Map map2)

#### Parameters

map1  
The second map to compare.

<!-- -->

map2  
The second map to compare.

#### Return Value

true if the two maps are equal; otherwise, false.

#### Remarks

Two maps are equal if they contain the same number of elements, their key sets are the same, and each key in the key set maps to the same value in both maps.

### Method new

Creates a new map.

    public void new(Types key, Types value)

#### Parameters

key  
The type of the values.

<!-- -->

value  
The type of the values.

#### Examples

The following example creates a map that maps string keys to integer values.

    Map myMap = new Map(Types::String, Types::Integer);

## Class MapEnumerator
    class MapEnumerator extends Object

The MapEnumerator class lets you traverse through the elements in a map.

### Remarks

Map enumerators start before the first element in the list. You must call the MapEnumerator.moveNext method to make it point to the first element in the list. It is a best practice to use the MapEnumerator class instead of the MapIterator class because enumerators are automatically created on the same tier as the map when you call the Map.getEnumerator method. Using the MapEnumerator class avoids a potential problem in code marked as Called from, where the iterator and map can end up on separate tiers. In addition, because map enumerators require less code than map iterators, they perform slightly better. The only situation where you have to use a map iterator, is when you want to delete items from a list by using the MapIterator.delete method.

### Examples

### Methods

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

### Method current

This method is obsolete; use MapEnumerator.currentKey instead.

    public AnyType current()

#### Return Value

### Method currentKey

Returns the key from the (key, value) pair that is currently pointed to by the enumerator.

    public AnyType currentKey()

#### Return Value

The key from the map element that is currently pointed to by the enumerator.

#### Remarks

You must call the MapEnumerator.moveNext method before you call the currentKey method.

#### Examples

The following example searches for a particular table ID in a map and then returns the key value of that map element.

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

### Method currentValue

Returns the value from the (key, value) pair that is currently pointed to by the enumerator.

    public AnyType currentValue()

#### Return Value

The value from the map element that is currently pointed to by the enumerator.

#### Remarks

You must call the MapEnumerator.moveNext method before you call this method.

#### Examples

The following example searches through a map to find an element that has a value equal to that passed in as a parameter. The MapEnumerator.moveNext method is used to iterate through the map, and the currentValue method is used to test each value to see whether it matches the parameter.

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

### Method definitionString

Returns a description of the enumerator. For example, an enumerator for a map of integers to strings would return "\[int -&gt; str\] enumerator".

    public str definitionString()

#### Return Value

A string that contains a description of the enumerator.

#### Examples

The following example creates a map and an enumerator for it, and then it prints out a definition of the enumerator.

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

### Method moveNext

Determines whether the enumerator points to a valid map element.

    public boolean moveNext()

#### Return Value

true if the current position in the map holds a valid element; otherwise false.

#### Remarks

Map enumerators start before the first element in the map. You must call the moveNext method to make it point to the first element in the map.

#### Examples

The following example uses the moveNext method to iterate over the tables that are contained in a project and adds them to a new map that contains a DictTable object for each table. (DictTable lets you access information about a table.)

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

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

#### Examples

The following example creates a map, and then prints the content of the first and second elements in the map.

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

### Method new

Initializes a new instance of the Object class.

    public void new(Map map)

#### Parameters

map  
The map for which to create an enumerator.

#### Remarks

This method is obsolete. Use the Map.getEnumerator method instead.

### Method reset

Moves the enumerator to point to just before the first element in the map.

    public void reset()

#### Remarks

The reset method moves the enumerator to the start of the set, before the first element in the set. You must call the MapEnumerator.moveNext method to make it point to the first element in the set.

## Class Mapi
    class Mapi extends Object

The Mapi class enables email to be sent, received, and managed in most major mail systems, such as Microsoft Exchange–based systems, Microsoft Outlook Express, and Lotus CCMail.

### Remarks

Together with the other Mapi classes, MapiMessage, MapiRecipDesc, and MapiFileDesc, this class lets you specify multiple recipients, file attachments, message text, and a subject. The easiest approach is to set up a working mail client on the machine, and make sure that this works correctly order by sending and receiving a few email messages. Flags for the Mapi methods are located in the Mapi macro. You include this macro in code where you use the Mapi classes together with the \#MAPI statement.

### Examples

The following example shows how to send an email message by using this class.

    static void example() 
    { 
        #Mapi 
        Mapi m = new Mapi(); 
        MapiMessage msg = new MapiMessage(); 
        MapiRecipDesc recip = new MapiRecipDesc(); 
        // Set up the recipient. 
        recip.Name("someone"); 
        recip.RecipClass(#MAPI_TO); 
        msg.setRecipNo(1,recip); 
        // Log on using default profile. 
        m.Logon("","",#MAPI_USE_DEFAULT); 
        // Send the mail, and allow the user to modify the 
        // Subject, Text and Recipients in the Send Mail Dialog. 
        m.SendMail(msg,#MAPI_DIALOG); 
        // Log off. 
        m.Logoff(); 
    }

### Methods

| Method                                                                         | Description                                                                                          |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| public int deleteMail(str messageID)                                           | Removes the specified message from the message store.                                                |
| public str findNext(\[str messageType\], \[str seedMessageID\], \[int flags\]) | Finds the first or next message in the message store.                                                |
| public int logoff()                                                            | Lets you log off the mail system.                                                                    |
| public int logon(str profileName, str password, int flags)                     | Logs on to the mail system by using the specified profile and password.                              |
| public MapiMessage readMail(str messageID, \[int flags\])                      | Retrieves a message from the message store.                                                          |
| public MapiRecipDesc resolveName(str mame, int flags)                          | Transforms the message recipient's name, as entered by a user, to an unambiguous address list entry. |
| public int saveMail(MapiMessage message, int flags, str messageId)             | Saves a message to the message store.                                                                |
| public int sendMail(MapiMessage message, \[int flags\])                        | Sends a message to the specified recipients.                                                         |
| public int status()                                                            | Retrieves the status of the last Mapi operation.                                                     |
| public void new()                                                              | Initializes an instance of the Mapi class.                                                           |
| public void finalize()                                                         |                                                                                                      |

### Method deleteMail

Removes the specified message from the message store.

    public int deleteMail(str messageID)

#### Parameters

messageID  
The unique message ID for the message to delete.

#### Return Value

The status \#SUCCESS\_SUCCES or an error code, which can be found in the \#MAPI macro.

#### Remarks

The message ID can be retrieved by using the findNext method.

### Method findNext

Finds the first or next message in the message store.

    public str findNext([str messageType], [str seedMessageID], [int flags])

#### Parameters

messageType  
Flags that indicate first in, first out (FIFO) or unread; optional. This parameter has two possible values:

<!-- -->

seedMessageID  
Flags that indicate first in, first out (FIFO) or unread; optional. This parameter has two possible values:

<!-- -->

flags  
Flags that indicate first in, first out (FIFO) or unread; optional. This parameter has two possible values:

#### Return Value

The message ID of the message that is found; an empty string if no message is found.

#### Remarks

Call this method to find the first message, and then issue subsequent calls to obtain the following messages. Use the status method to check for Mapi errors after you call this method.

### Method logoff

Lets you log off the mail system.

    public int logoff()

#### Return Value

The status \#SUCCESS\_SUCCESS or an error code, which can be found in the \#MAPI macro.

### Method logon

Logs on to the mail system by using the specified profile and password.

    public int logon(str profileName, str password, int flags)

#### Parameters

profileName  
A list of flags. The valid flags are as follows:

<!-- -->

password  
A list of flags. The valid flags are as follows:

<!-- -->

flags  
A list of flags. The valid flags are as follows:

#### Return Value

The status \#SUCCESS\_SUCCESS if the logon succeeded; otherwise, an error code, which can be found in the \#MAPI macro.

#### Remarks

An easy and common way to log on is to specify the \#MAPI\_USE\_DEFAULT flag, which logs on by using the default profile.

### Method readMail

Retrieves a message from the message store.

    public MapiMessage readMail(str messageID, [int flags])

#### Parameters

messageID  
A list of flags; optional. The valid flags are as follows:

<!-- -->

flags  
A list of flags; optional. The valid flags are as follows:

#### Return Value

The MapiMessage object that is retrieved or nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Method resolveName

Transforms the message recipient's name, as entered by a user, to an unambiguous address list entry.

    public MapiRecipDesc resolveName(str mame, int flags)

#### Parameters

mame  
A list of flags. The valid flags are as follows:

<!-- -->

flags  
A list of flags. The valid flags are as follows:

#### Return Value

A MapiRecipDesc class object that has an unambiguous address list entry.

### Method saveMail

Saves a message to the message store.

    public int saveMail(MapiMessage message, int flags, str messageId)

#### Parameters

message  
The unique ID of the message to retrieve.

<!-- -->

flags  
The unique ID of the message to retrieve.

<!-- -->

messageId  
The unique ID of the message to retrieve.

#### Return Value

The status \#SUCCESS\_SUCCESS or an error code from the \#MAPI macro.

### Method sendMail

Sends a message to the specified recipients.

    public int sendMail(MapiMessage message, [int flags])

#### Parameters

message  
A list of flags; optional. The valid flags are as follows:

<!-- -->

flags  
A list of flags; optional. The valid flags are as follows:

#### Return Value

The status \#SUCCESS\_SUCCESS or an error code from the \#MAPI macro.

### Method status

Retrieves the status of the last Mapi operation.

    public int status()

#### Return Value

The status code of the last Mapi operation.

#### Remarks

The status codes can be found in the \#MAPI macro.

### Method new

Initializes an instance of the Mapi class.

    public void new()

### Method finalize

    public void finalize()

## Class MapiEx
    class MapiEx extends Object

### Remarks

### Examples

### Methods

| Method                                                          | Description                                     |
|-----------------------------------------------------------------|-------------------------------------------------|
| public MapiExAppointment getAppointmentFromEntryId(str entryID) |                                                 |
| public MapiExContact getContactFromEntryId(str entryID)         |                                                 |
| public int getCurrentUser()                                     |                                                 |
| public str getCurrentUserEmail()                                |                                                 |
| public str getCurrentUserEntryId()                              |                                                 |
| public str getCurrentUserName()                                 |                                                 |
| public MapiExMail getMailFromEntryId(str entryID)               |                                                 |
| public MapiExTask getTaskFromEntryId(str entryID)               |                                                 |
| public int logon(str profileName, str password, int flags)      |                                                 |
| public boolean mapiInitialised()                                |                                                 |
| public boolean openMessageStore(str str)                        |                                                 |
| public void finalize()                                          |                                                 |
| public void new()                                               | Initializes a new instance of the MapiEx class. |
| public void logout()                                            |                                                 |

### Method getAppointmentFromEntryId

    public MapiExAppointment getAppointmentFromEntryId(str entryID)

#### Parameters

entryID  

#### Return Value

### Method getContactFromEntryId

    public MapiExContact getContactFromEntryId(str entryID)

#### Parameters

entryID  

#### Return Value

### Method getCurrentUser

    public int getCurrentUser()

#### Return Value

### Method getCurrentUserEmail

    public str getCurrentUserEmail()

#### Return Value

### Method getCurrentUserEntryId

    public str getCurrentUserEntryId()

#### Return Value

### Method getCurrentUserName

    public str getCurrentUserName()

#### Return Value

### Method getMailFromEntryId

    public MapiExMail getMailFromEntryId(str entryID)

#### Parameters

entryID  

#### Return Value

### Method getTaskFromEntryId

    public MapiExTask getTaskFromEntryId(str entryID)

#### Parameters

entryID  

#### Return Value

### Method logon

    public int logon(str profileName, str password, int flags)

#### Parameters

profileName  

<!-- -->

password  

<!-- -->

flags  

#### Return Value

### Method mapiInitialised

    public boolean mapiInitialised()

#### Return Value

### Method openMessageStore

    public boolean openMessageStore(str str)

#### Parameters

str  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the MapiEx class.

    public void new()

### Method logout

    public void logout()

## Class MapiExAppointment
    class MapiExAppointment extends MapiExMessage

### Remarks

### Examples

### Methods

| Method                                                 | Description                                                |
|--------------------------------------------------------|------------------------------------------------------------|
| public str addRecipient(str email, str name, int type) |                                                            |
| public str entryId()                                   |                                                            |
| public str getGlobalObjectId()                         |                                                            |
| public boolean getRecipient(int index)                 |                                                            |
| public int getRecipientCount()                         |                                                            |
| public str getRecipientDisplayName()                   |                                                            |
| public str getRecipientEmailAddress()                  |                                                            |
| public str getRecipientEntryId()                       |                                                            |
| public boolean getRecipients()                         |                                                            |
| public str getRecipientSMTPAddress()                   |                                                            |
| public int getRecipientType()                          |                                                            |
| public str getSenderEmail()                            |                                                            |
| public str getSenderName()                             |                                                            |
| public str removeRecipient(str email, int type)        |                                                            |
| public boolean save()                                  |                                                            |
| public boolean setBody(str body)                       |                                                            |
| public void new()                                      | Initializes a new instance of the MapiExAppointment class. |
| public void close()                                    |                                                            |
| public void finalize()                                 |                                                            |

### Method addRecipient

    public str addRecipient(str email, str name, int type)

#### Parameters

email  

<!-- -->

name  

<!-- -->

type  

#### Return Value

### Method entryId

    public str entryId()

#### Return Value

### Method getGlobalObjectId

    public str getGlobalObjectId()

#### Return Value

### Method getRecipient

    public boolean getRecipient(int index)

#### Parameters

index  

#### Return Value

### Method getRecipientCount

    public int getRecipientCount()

#### Return Value

### Method getRecipientDisplayName

    public str getRecipientDisplayName()

#### Return Value

### Method getRecipientEmailAddress

    public str getRecipientEmailAddress()

#### Return Value

### Method getRecipientEntryId

    public str getRecipientEntryId()

#### Return Value

### Method getRecipients

    public boolean getRecipients()

#### Return Value

### Method getRecipientSMTPAddress

    public str getRecipientSMTPAddress()

#### Return Value

### Method getRecipientType

    public int getRecipientType()

#### Return Value

### Method getSenderEmail

    public str getSenderEmail()

#### Return Value

### Method getSenderName

    public str getSenderName()

#### Return Value

### Method removeRecipient

    public str removeRecipient(str email, int type)

#### Parameters

email  

<!-- -->

type  

#### Return Value

### Method save

    public boolean save()

#### Return Value

### Method setBody

    public boolean setBody(str body)

#### Parameters

body  

#### Return Value

### Method new

Initializes a new instance of the MapiExAppointment class.

    public void new()

### Method close

    public void close()

### Method finalize

    public void finalize()

## Class MapiExContact
    class MapiExContact extends MapiExMessage

### Remarks

### Examples

### Methods

| Method                            | Description                                            |
|-----------------------------------|--------------------------------------------------------|
| public str entryId()              |                                                        |
| public str getBody()              |                                                        |
| public str getEmail1()            |                                                        |
| public str getEmail1DisplayName() |                                                        |
| public str getEmail1Type()        |                                                        |
| public str getEmail2()            |                                                        |
| public str getEmail2DisplayName() |                                                        |
| public str getEmail2Type()        |                                                        |
| public str getEmail3()            |                                                        |
| public str getEmail3DisplayName() |                                                        |
| public str getEmail3Type()        |                                                        |
| public str getIMAddress()         |                                                        |
| public boolean save()             |                                                        |
| public boolean setBody(str body)  |                                                        |
| public void close()               |                                                        |
| public void finalize()            |                                                        |
| public void new()                 | Initializes a new instance of the MapiExContact class. |

### Method entryId

    public str entryId()

#### Return Value

### Method getBody

    public str getBody()

#### Return Value

### Method getEmail1

    public str getEmail1()

#### Return Value

### Method getEmail1DisplayName

    public str getEmail1DisplayName()

#### Return Value

### Method getEmail1Type

    public str getEmail1Type()

#### Return Value

### Method getEmail2

    public str getEmail2()

#### Return Value

### Method getEmail2DisplayName

    public str getEmail2DisplayName()

#### Return Value

### Method getEmail2Type

    public str getEmail2Type()

#### Return Value

### Method getEmail3

    public str getEmail3()

#### Return Value

### Method getEmail3DisplayName

    public str getEmail3DisplayName()

#### Return Value

### Method getEmail3Type

    public str getEmail3Type()

#### Return Value

### Method getIMAddress

    public str getIMAddress()

#### Return Value

### Method save

    public boolean save()

#### Return Value

### Method setBody

    public boolean setBody(str body)

#### Parameters

body  

#### Return Value

### Method close

    public void close()

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the MapiExContact class.

    public void new()

## Class MapiExMail
    class MapiExMail extends MapiExMessage

### Remarks

### Examples

### Methods

| Method                                                 | Description                                         |
|--------------------------------------------------------|-----------------------------------------------------|
| public str addRecipient(str email, str name, int type) |                                                     |
| public str entryId()                                   |                                                     |
| public boolean getRecipient(int index)                 |                                                     |
| public int getRecipientCount()                         |                                                     |
| public str getRecipientDisplayName()                   |                                                     |
| public str getRecipientEmailAddress()                  |                                                     |
| public str getRecipientEntryId()                       |                                                     |
| public boolean getRecipients()                         |                                                     |
| public str getRecipientSMTPAddress()                   |                                                     |
| public int getRecipientType()                          |                                                     |
| public str getSenderEmail()                            |                                                     |
| public str getSenderName()                             |                                                     |
| public str removeRecipient(str email, int type)        |                                                     |
| public boolean save()                                  |                                                     |
| public boolean saveMsgToFile(str fileName)             |                                                     |
| public boolean send()                                  |                                                     |
| public boolean setBody(str body)                       |                                                     |
| public void finalize()                                 |                                                     |
| public void close()                                    |                                                     |
| public void new()                                      | Initializes a new instance of the MapiExMail class. |

### Method addRecipient

    public str addRecipient(str email, str name, int type)

#### Parameters

email  

<!-- -->

name  

<!-- -->

type  

#### Return Value

### Method entryId

    public str entryId()

#### Return Value

### Method getRecipient

    public boolean getRecipient(int index)

#### Parameters

index  

#### Return Value

### Method getRecipientCount

    public int getRecipientCount()

#### Return Value

### Method getRecipientDisplayName

    public str getRecipientDisplayName()

#### Return Value

### Method getRecipientEmailAddress

    public str getRecipientEmailAddress()

#### Return Value

### Method getRecipientEntryId

    public str getRecipientEntryId()

#### Return Value

### Method getRecipients

    public boolean getRecipients()

#### Return Value

### Method getRecipientSMTPAddress

    public str getRecipientSMTPAddress()

#### Return Value

### Method getRecipientType

    public int getRecipientType()

#### Return Value

### Method getSenderEmail

    public str getSenderEmail()

#### Return Value

### Method getSenderName

    public str getSenderName()

#### Return Value

### Method removeRecipient

    public str removeRecipient(str email, int type)

#### Parameters

email  

<!-- -->

type  

#### Return Value

### Method save

    public boolean save()

#### Return Value

### Method saveMsgToFile

    public boolean saveMsgToFile(str fileName)

#### Parameters

fileName  

#### Return Value

### Method send

    public boolean send()

#### Return Value

### Method setBody

    public boolean setBody(str body)

#### Parameters

body  

#### Return Value

### Method finalize

    public void finalize()

### Method close

    public void close()

### Method new

Initializes a new instance of the MapiExMail class.

    public void new()

## Class MapiExMessage
    class MapiExMessage extends Object

### Remarks

### Examples

### Methods

| Method                           | Description                                            |
|----------------------------------|--------------------------------------------------------|
| public str entryId()             |                                                        |
| public str getBody()             |                                                        |
| public boolean save()            |                                                        |
| public boolean setBody(str body) |                                                        |
| public void new()                | Initializes a new instance of the MapiExMessage class. |
| public void finalize()           |                                                        |
| public void close()              |                                                        |

### Method entryId

    public str entryId()

#### Return Value

### Method getBody

    public str getBody()

#### Return Value

### Method save

    public boolean save()

#### Return Value

### Method setBody

    public boolean setBody(str body)

#### Parameters

body  

#### Return Value

### Method new

Initializes a new instance of the MapiExMessage class.

    public void new()

### Method finalize

    public void finalize()

### Method close

    public void close()

## Class MapiExTask
    class MapiExTask extends MapiExMessage

### Remarks

### Examples

### Methods

| Method                           | Description                                         |
|----------------------------------|-----------------------------------------------------|
| public str entryId()             |                                                     |
| public str getBody()             |                                                     |
| public boolean save()            |                                                     |
| public boolean setBody(str body) |                                                     |
| public void finalize()           |                                                     |
| public void close()              |                                                     |
| public void new()                | Initializes a new instance of the MapiExTask class. |

### Method entryId

    public str entryId()

#### Return Value

### Method getBody

    public str getBody()

#### Return Value

### Method save

    public boolean save()

#### Return Value

### Method setBody

    public boolean setBody(str body)

#### Parameters

body  

#### Return Value

### Method finalize

    public void finalize()

### Method close

    public void close()

### Method new

Initializes a new instance of the MapiExTask class.

    public void new()

## Class MapiFileDesc
    class MapiFileDesc extends Object

The MapiFileDesc class gets and sets the files that are attached to messages.

### Remarks

The file description consists of two types of information for the file:

-   A path method, which points to a file on disk
-   A fileName method, which contains the file name as it will be presented to the user.

### Examples

    static void example() 
    { 
        MapiMessage msg = New MapiMessage(); 
        MapiFileDesc attach = new MapiFileDesc(); 
        attach.Path("C:\\files\\myfile.txt"); 
    }

### Methods

| Method                                | Description                                           |
|---------------------------------------|-------------------------------------------------------|
| public str fileName(\[str filename\]) |                                                       |
| public str path(\[str thePath\])      |                                                       |
| public void new()                     | Initializes a new instance of the MapiFileDesc class. |
| public void finalize()                |                                                       |

### Method fileName

    public str fileName([str filename])

#### Parameters

filename  

#### Return Value

### Method path

    public str path([str thePath])

#### Parameters

thePath  

#### Return Value

### Method new

Initializes a new instance of the MapiFileDesc class.

    public void new()

### Method finalize

    public void finalize()

## Class MapiMessage
    class MapiMessage extends Object

The MapiMessage class contains a message that is sent to or received from the MAPI system. The message includes a subject, text, recipient information, and attachment information.

### Remarks

When you send or receive a message, the message is passed to and from the MAPI system as a MapiMessage object.

### Examples

### Methods

| Method                                                        | Description                                                                                             |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| public str conversationID(\[str conversationId\])             | Gets or sets the string that identifies the conversation thread to which the message belongs.           |
| public str dateReceived(\[Date theDate\])                     | Returns the date when the message was received.                                                         |
| public int flags(\[int flags\])                               | Set or get a bitmask of the message status flags.                                                       |
| public MapiFileDesc getFileNo(int fileNo)                     | Gets a file attachment from a message.                                                                  |
| public MapiRecipDesc getRecipNo(int recipentNo)               | Retrieves information about a message recipient in a MapiRecipDesc object.                              |
| public str messageType(\[str messageType\])                   | Gets or sets the string that indicates that the message is not of the IPM (interpersonal message) type. |
| public int numFiles(\[int numFiles\])                         |                                                                                                         |
| public int numRecips(\[int numRecips\])                       |                                                                                                         |
| public MapiRecipDesc originator(\[MapiRecipDesc originator\]) |                                                                                                         |
| public str subject(\[str subject\])                           |                                                                                                         |
| public str text(\[str text\])                                 |                                                                                                         |
| public void new()                                             | Initializes an instance of the MapiMessage class.                                                       |
| public void finalize()                                        |                                                                                                         |
| public void setRecipNo(int recipNo, MapiRecipDesc recipient)  | Adds a recipient to the message.                                                                        |
| public void setFileNo(int fileNo, MapiFileDesc file)          | Sets a file attachment for the message.                                                                 |

### Method conversationID

Gets or sets the string that identifies the conversation thread to which the message belongs.

    public str conversationID([str conversationId])

#### Parameters

conversationId  
The ID of the conversation thread; optional.

#### Return Value

A string that identifies the conversation thread to which the message belongs.

#### Remarks

Some messaging systems might ignore and not return this member.

### Method dateReceived

Returns the date when the message was received.

    public str dateReceived([Date theDate])

#### Parameters

theDate  
The date when the message was received; optional.

#### Return Value

A string that indicates the date when the message was received.

#### Remarks

The format of the string that is returned is YYYY/MM/DD HH:MM and uses a 24-hour clock.

### Method flags

Set or get a bitmask of the message status flags.

    public int flags([int flags])

#### Parameters

flags  
The message status flags; optional.

#### Return Value

A bitmask of the message status flags.

#### Remarks

The following flags can be set:

-   \#MAPI\_RECEIPT\_REQUESTED – Receipt notification is requested. Client applications set this bit when they send a message.
-   \#MAPI\_SENT – The message has been sent.
-   \#MAPI\_UNREAD – The message has not been read.

### Method getFileNo

Gets a file attachment from a message.

    public MapiFileDesc getFileNo(int fileNo)

#### Parameters

fileNo  
The index of the attachment to retrieve. The index starts at 1, and the total number of attachments can be retrieved using the numFiles method.

#### Return Value

Returns a MapiFileDesc object that contains information about the attachment.

#### Remarks

The attached file is returned in a MapiFileDesc object.

#### Examples

    { 
        MapiFileDesc attachment; 
        MapiMessage message; 
        // Retrieve message. 
        // ...  
        if (message.NumFiles() >= 1) 
        { 
            attachment = message.GetFileNo(1); 
        } 
    }

### Method getRecipNo

Retrieves information about a message recipient in a MapiRecipDesc object.

    public MapiRecipDesc getRecipNo(int recipentNo)

#### Parameters

recipentNo  
The number of the recipient to retrieve. The numbering starts at 1, and the total number of recipients can be read by using the numRecips method.

#### Return Value

A MapiRecipDesc object that describes the recipient or nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Method messageType

Gets or sets the string that indicates that the message is not of the IPM (interpersonal message) type.

    public str messageType([str messageType])

#### Parameters

messageType  
The messageType value to set for the message; optional.

#### Return Value

A messagetype string.

#### Remarks

Applications can select message types for messages that are not IPMs. Clients that support only IPMs can ignore the MessageType member when they read messages and set it to empty when they send messages.

### Method numFiles

    public int numFiles([int numFiles])

#### Parameters

numFiles  

#### Return Value

### Method numRecips

    public int numRecips([int numRecips])

#### Parameters

numRecips  

#### Return Value

### Method originator

    public MapiRecipDesc originator([MapiRecipDesc originator])

#### Parameters

originator  

#### Return Value

### Method subject

    public str subject([str subject])

#### Parameters

subject  

#### Return Value

### Method text

    public str text([str text])

#### Parameters

text  

#### Return Value

### Method new

Initializes an instance of the MapiMessage class.

    public void new()

### Method finalize

    public void finalize()

### Method setRecipNo

Adds a recipient to the message.

    public void setRecipNo(int recipNo, MapiRecipDesc recipient)

#### Parameters

recipNo  
The MapiRecipDesc object that describes the recipient.

<!-- -->

recipient  
The MapiRecipDesc object that describes the recipient.

#### Remarks

If you have to get a correct MapiRecipDesc object from a name that a user entered, use the resolveName method.

### Method setFileNo

Sets a file attachment for the message.

    public void setFileNo(int fileNo, MapiFileDesc file)

#### Parameters

fileNo  
The MapiFileDesc object that describes the attachment.

<!-- -->

file  
The MapiFileDesc object that describes the attachment.

#### Remarks

The attachments are numbered from 1. Therefore, the first attachment should be numbered 1. You can call the numFiles method to retrieve the number of attachments.

#### Examples

    { 
        MapiMessage msg = new MapiMessage(); 
        MapiFileDesc attachment = new MapiFileDesc(); 
        attachment.Path("C:\\files\\info.txt"); 
        msg.SetFileNo(1,attachment); 
    }

## Class MapiRecipDesc
    class MapiRecipDesc extends Object

### Remarks

### Examples

### Methods

| Method                                    | Description                                                                                                                                   |
|-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str address(\[str Address\])       |                                                                                                                                               |
| public str name(\[str Name\])             | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int recipClass(\[int RecipClass\]) |                                                                                                                                               |
| public void new()                         | Initializes a new instance of the MapiRecipDesc class.                                                                                        |
| public void finalize()                    |                                                                                                                                               |

### Method address

    public str address([str Address])

#### Parameters

Address  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str Name])

#### Parameters

Name  

#### Return Value

The name that is used in thte code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method recipClass

    public int recipClass([int RecipClass])

#### Parameters

RecipClass  

#### Return Value

### Method new

Initializes a new instance of the MapiRecipDesc class.

    public void new()

### Method finalize

    public void finalize()

## Class MapIterator
    class MapIterator extends Object

The MapIterator class is used to iterate over the elements in a map.

### Remarks

Map iterators are used to iterate over the elements in a map. They can be viewed as simple pointers into the maps over which they iterate. Functionality is available to start the iteration, determine whether more (key, value) pairs are available, and fetch the element that is pointed to by the iterator. It is better to use the MapEnumerator class than the MapIterator class. Map iterators and the maps over which they iterate must be on the same client/server side. If you use the MapIterator class and code is marked as Called from, the map and the iterator could end up on different tiers, and the code will fail. If you use the MapEnumerator class, the enumerator is automatically created on the same tier as the map. Additionally, if you use the MapIterator class, you must explicitly call the more and next methods to move to the next item in a map. If you use the MapEnumerator class, you only have to call the moveNext method. The sequence in which the elements are inserted does not determine the order in which they occur. The order is defined by the ordering of the elements. Elements that have lower keys appear before elements that have higher keys. The usual ordering for the types is used. However, if the keys are objects, the addresses of the objects are used to supply the ordering, and therefore no specific ordering can be inferred. The addresses of the objects are transient by nature.

### Examples

The following example creates a map and adds three (key, value) pairs. It then iterates through the map and prints information about each map element.

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

### Methods

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

### Method definitionString

Retrieves a textual representation of the iterator type, such as "\[int -&gt; str\] iterator".

    public str definitionString()

#### Return Value

A string that describes the iterator.

### Method domainValue

Returns the value of the key in the (key, value) pair that is referred to by the iterator.

    public AnyType domainValue()

#### Return Value

The value of the first item in the map element that is currently referred to by the iterator.

### Method find

Searches for the specified key value.

    public boolean find(AnyType value)

#### Parameters

value  
The value to search for.

#### Return Value

true if the value is found; otherwise, false.

#### Remarks

If true is returned, the method positions the iterator at the element; otherwise, the MapIterator.more method returns false.

### Method key

Returns the key from the (key, value) pair that is referred to by the iterator.

    public AnyType key()

#### Return Value

The key value of the map entry that is denoted by the iterator.

#### Remarks

Use the SetIterator.more method to test whether an element exists before you try to retrieve the key value of the map element.

#### Examples

The following example iterates through a map and returns a description of all the elements in the map.

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

### Method more

Determines whether the iterator finds a valid (key, value) pair.

    public boolean more()

#### Return Value

true if more (key, value) pairs are available in the map; otherwise, false.

#### Remarks

If you try to access an element that is pointed to by an iterator when the more method returns false, you receive an error. The more method only tests whether the iterator points to a valid element. It does not test whether there are more elements in the map.

#### Examples

The following example iterates through a map by using the more method to check whether there are still elements in the map. It then returns a description of all the elements in the map.

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

### Method rangeValue

Returns the value of the value in the (key, value) pair that is referred to by the iterator.

    public AnyType rangeValue()

#### Return Value

The value of the second item in the map element that is currently referred to by the iterator.

#### Remarks

The rangeValue method has the same functionality as the MapIterator.value method, but it is available as a counterpart to the domainValue method.

### Method toString

Retrieves a textual representation of the iterator.

    public str toString()

#### Return Value

The string that describes the iterator.

#### Remarks

If the iterator points to the first element in the set, the string will contain an indication of this, in the form: "(begin)\[ *value*\]". If the iterator does not point to an element (that is, if the MapIterator.more method returns false), the string that is returned is "(end)". If the iterator points to a value, the string is "\[ *value*\]", where *value* is a string representation of the element value.

#### Examples

The following example iterates through an integer or class map, and prints information about each map element. It uses the MapIterator.toString method to return a textual representation of the class in each map element.

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

### Method value

Returns the value from the (key, value) pair that is referred to by the iterator.

    public AnyType value()

#### Return Value

The value from the map element that is denoted by the map iterator.

#### Remarks

Use the MapIterator.more method to test whether an element exists before you try to retrieve the key value of the map element.

#### Examples

The following example iterates through a map and returns a list of all the elements in the map.

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

### Method valuePair

Retrieves a container that holds the key and the value.

    public container valuePair()

#### Return Value

A container that holds the key and the value.

#### Remarks

Objects cannot reside in containers. Therefore, an exception is raised if either the key or the value is an object.

### Method next

Moves the iterator to the next (key, value) pair.

    public void next()

#### Remarks

You can use the MapIterator.more method to determine whether there are any more elements in the map.

#### Examples

The following example uses the next method to iterate through a map and returns a list of all the elements in the map.

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

### Method new

Creates a new iterator for a map that lets you traverse through the elements in the map.

    public void new(Map map)

#### Parameters

map  
The map for which to create an iterator.

#### Remarks

The iterator is positioned at the first value in the map if the map is not empty.

#### Examples

The following example creates a map of (integer, class) pairs and then creates an iterator to traverse the map.

    Map iim = new Map(Types::Integer, Types::Class); 
    MapIterator it; 
    it = new MapIterator (iim);

### Method begin

Moves the iterator to the start of the map.

    public void begin()

#### Remarks

Newly created map iterators are positioned at the first element in the map, so you do not have to call the begin method before you iterate through the set. You must call the begin method if you want to reset the pointer.

### Method end

Moves the iterator past the last element in the map.

    public void end()

#### Remarks

After this method runs, the MapIterator.more method will return false.

### Method delete

Removes from the map the element that is pointed to by the iterator.

    public void delete()

#### Remarks

The iterator points to the next element after the delete method is invoked.

## Class MemberFunction
    class MemberFunction extends TreeNode

The MemberFunction class provides information about a specified node in the Microsoft Dynamics AX Application Object Tree (AOT), such as a form, report, or class.

### Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. You can use the ::findNode method to assign a node to an instance of the MemberFunction class.

### Examples

The following example uses the TreeNode::findNode method to assign the node for the AddressSelectForm.callerDataSource method to an instance of the MemberFunction class. The MemberFunction.AOTgetSource Method method returns the method source code.

    void getMemberFunction() 
    { 
        MemberFunction memberFunction; 
        str name; 
        boolean isStatic; 
        str source; 
        try 
        { 
            memberFunction = TreeNode::findNode( 
               '\\Classes\\AddressSelectForm\\callerDataSource'); 
            if(!memberFunction) 
            { 
                throw exception::Error; 
            } 
            source = memberFunction.AOTgetSource(); 
            print source; 
            pause; 
        } 
        catch (exception::Error) 
        { 
            print "The specified node does not exist."; 
            pause; 
            } 
        } 
    }

### Methods

| Method                                                     | Description                                                                                                                             |
|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                  | Provides the source code for a specified node in the AOT, such as a class or method.                                                    |
| public boolean canAddEventHandler()                        |                                                                                                                                         |
| public boolean isEvent()                                   |                                                                                                                                         |
| public boolean isStatic()                                  | Indicates whether a method is static.                                                                                                   |
| public str name(\[str value\])                             | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object. |
| public void AOTedit(\[int Line\], \[int Column\])          | Opens the appropriate editor for a specified node in the AOT.                                                                           |
| public void new()                                          | Initializes a new instance of the MemberFunction class.                                                                                 |
| public void AOTsetSource(str source, \[boolean isStatic\]) | Sets the source code for a specified node in the AOT, such as a class or method.                                                        |

### Method AOTgetSource

Provides the source code for a specified node in the AOT, such as a class or method.

    public str AOTgetSource()

#### Return Value

A string value for the source code; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the node does not contain source code.

### Method canAddEventHandler

    public boolean canAddEventHandler()

#### Return Value

### Method isEvent

    public boolean isEvent()

#### Return Value

### Method isStatic

Indicates whether a method is static.

    public boolean isStatic()

#### Return Value

true if the method is static; otherwise, false.

#### Remarks

This method is associated with a specified node in the AOT, such as a form, report, or class. This method is used primarily in conjunction with the MemberFunction::AOTsetSource method.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
A string that specifies a node; optional.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It starts with a letter.
-   It doesn't exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, and classes.

### Method AOTedit

Opens the appropriate editor for a specified node in the AOT.

    public void AOTedit([int Line], [int Column])

#### Parameters

Line  
An integer that specifies the column position for the cursor; optional.

<!-- -->

Column  
An integer that specifies the column position for the cursor; optional.

### Method new

Initializes a new instance of the MemberFunction class.

    public void new()

### Method AOTsetSource

Sets the source code for a specified node in the AOT, such as a class or method.

    public void AOTsetSource(str source, [boolean isStatic])

#### Parameters

source  
A Boolean value: true for a static method or false for an instance method; optional.

<!-- -->

isStatic  
A Boolean value: true for a static method or false for an instance method; optional.

## Class Menu
    class Menu extends TreeNode

The Menu system class lets you configure and run any of the Microsoft Dynamics AXMenu objects from code.

### Remarks

The TreeNode system class serves as a more general approach to the menus in the Microsoft Dynamics AX Application Object Tree (AOT). You use the Menu class to create or manipulate the menus contents, such as submenus and menu items. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                               |
|--------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                      | Gets or sets the name of the user who last changed the application object.                                                |
| public Date changedDate(\[Date value\])                                  | Gets or sets the date an application object was last changed.                                                             |
| public str changedTime(\[str value\])                                    | Gets or sets the time an application object was last changed.                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                       |
| public str countryRegionCodes(\[str value\])                             |                                                                                                                           |
| public str createdBy(\[str value\])                                      | Gets or sets the name of the user who created the application object.                                                     |
| public Date creationDate(\[Date value\])                                 | Gets or sets the date an application object was created.                                                                  |
| public str creationTime(\[str value\])                                   |                                                                                                                           |
| public str disabledImage(\[str value\])                                  | Gets or sets the disabled image of the button.                                                                            |
| public int disabledImageLocation(\[int value\])                          |                                                                                                                           |
| public int disabledResource(\[int value\])                               | Gets or sets the resource ID of the image to use as the disabled button image.                                            |
| public int imageLocation(\[int value\])                                  |                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                     |
| public str menuFunctionName(\[str name\])                                |                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                           |
| public str menuName()                                                    |                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, rable, query, or another MSDAX application object. |
| public int neededAccessLevel(\[int value\])                              | Gets or sets the neededAccessLevel property for the MenuFunction class.                                                   |
| public str normalImage(\[str value\])                                    |                                                                                                                           |
| public int normalResource(\[int value\])                                 |                                                                                                                           |
| public Guid origin(\[Guid value\])                                       |                                                                                                                           |
| public str parameter(\[str parameter\])                                  |                                                                                                                           |
| public str parameters(\[str value\])                                     | Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.                    |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                           |
| public boolean setCompany(\[boolean value\])                             |                                                                                                                           |
| public str shortCut(\[str value\])                                       |                                                                                                                           |
| public boolean showParentModule(\[boolean value\])                       |                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                           |
| public void save()                                                       |                                                                                                                           |
| public void new(str Name)                                                | Initializes a new instance of the TreeNode class.                                                                         |
| public void makeWebMenu(Object outputClass)                              |                                                                                                                           |
| public void addMenuitem(xMenuFunction menuFunction)                      | Adds a menu item to the menu.                                                                                             |
| public void setTreeNodeName(str name)                                    |                                                                                                                           |
| public void addMenuReference(Menu menu)                                  |                                                                                                                           |
| public void addSubmenu(str name)                                         | Adds a submenu to the menu.                                                                                               |
| public void addSeparator()                                               | Adds a menu separator to the menu.                                                                                        |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method disabledImage

Gets or sets the disabled image of the button.

    public str disabledImage([str value])

#### Parameters

value  

#### Return Value

The full name of an image file. The system supports all of the GDI-supported image formats.

#### Remarks

This property has precedence over the disabledResource property . It is used if both of these properties are set.

### Method disabledImageLocation

    public int disabledImageLocation([int value])

#### Parameters

value  

#### Return Value

### Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

    public int disabledResource([int value])

#### Parameters

value  

#### Return Value

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method menuFunctionName

    public str menuFunctionName([str name])

#### Parameters

name  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method menuName

    public str menuName()

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another MSDAX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method neededAccessLevel

Gets or sets the neededAccessLevel property for the MenuFunction class.

    public int neededAccessLevel([int value])

#### Parameters

value  

#### Return Value

The current value of the neededAccessLevel property.

#### Remarks

The possible values for the AccessType system enumuration value are as follows:

-   AccessType::NoAccess.
-   AccessType::View.
-   AccessType::Edit.
-   AccessType::Add.
-   AccessType::Delete.

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method parameter

    public str parameter([str parameter])

#### Parameters

parameter  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on.cts ignore passed, unrecognized parameters.

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setCompany

    public boolean setCompany([boolean value])

#### Parameters

value  

#### Return Value

### Method shortCut

    public str shortCut([str value])

#### Parameters

value  

#### Return Value

### Method showParentModule

    public boolean showParentModule([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method save

    public void save()

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str Name)

#### Parameters

Name  

### Method makeWebMenu

    public void makeWebMenu(Object outputClass)

#### Parameters

outputClass  

### Method addMenuitem

Adds a menu item to the menu.

    public void addMenuitem(xMenuFunction menuFunction)

#### Parameters

menuFunction  
The menu item to add.

### Method setTreeNodeName

    public void setTreeNodeName(str name)

#### Parameters

name  

### Method addMenuReference

    public void addMenuReference(Menu menu)

#### Parameters

menu  

### Method addSubmenu

Adds a submenu to the menu.

    public void addSubmenu(str name)

#### Parameters

name  
A string expression that evaluates to the name of the submenu to add to the menu.

### Method addSeparator

Adds a menu separator to the menu.

    public void addSeparator()

## Class MenuItem
    class MenuItem extends TreeNode

The MenuItem class lets you create, read, update, and delete X++ code and metadata.

### Remarks

A menu item represents the user interface of a menu function. Menu items are linked to a MenuFunction object, which runs when the user selects the menu item. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                     | Description                                                                                                                                   |
|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str allowRootNavigation(\[str value\])              |                                                                                                                                               |
| public boolean isDisplayedInContentArea(\[boolean value\]) |                                                                                                                                               |
| public str label(\[str name\])                             |                                                                                                                                               |
| public str menuFunctionName(\[str name\])                  |                                                                                                                                               |
| public str menuItemName(\[str value\])                     |                                                                                                                                               |
| public MenuItemType menuItemType(\[MenuItemType value\])   |                                                                                                                                               |
| public str name(\[str value\])                             | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public str parameter(\[str parameter\])                    |                                                                                                                                               |
| public str parameters(\[str value\])                       | Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.                                        |
| public str shortCut(\[str value\])                         |                                                                                                                                               |
| public boolean showParentModule(\[boolean value\])         |                                                                                                                                               |
| public boolean visible(\[boolean value\])                  |                                                                                                                                               |
| public str webTarget(\[str value\])                        |                                                                                                                                               |

### Method allowRootNavigation

    public str allowRootNavigation([str value])

#### Parameters

value  

#### Return Value

### Method isDisplayedInContentArea

    public boolean isDisplayedInContentArea([boolean value])

#### Parameters

value  

#### Return Value

### Method label

    public str label([str name])

#### Parameters

name  

#### Return Value

### Method menuFunctionName

    public str menuFunctionName([str name])

#### Parameters

name  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method parameter

    public str parameter([str parameter])

#### Parameters

parameter  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on.cts ignore passed, unrecognized parameters.

### Method shortCut

    public str shortCut([str value])

#### Parameters

value  

#### Return Value

### Method showParentModule

    public boolean showParentModule([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

## Class MenuReference
    class MenuReference extends TreeNode

The MenuReference class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

### Examples

### Methods

| Method                | Description |
|-----------------------|-------------|
| public str menuName() |             |

### Method menuName

    public str menuName()

#### Return Value

## Class MessageWin
    class MessageWin extends Object

The MessageWin class gives access to the messageWindow class of the Microsoft Dynamics AX development environment.

### Remarks

Although you can instantiate more MessageWin objects, they will all refer to the same message window on the screen.

### Examples

### Methods

| Method                        | Description                                           |
|-------------------------------|-------------------------------------------------------|
| public void clear()           | Clears the message window.                            |
| public void activate()        | Makes the message window the currently active window. |
| public void addLine(str line) | Writes a line to the message window.                  |

### Method clear

Clears the message window.

    public void clear()

### Method activate

Makes the message window the currently active window.

    public void activate()

#### Remarks

Before version 2.11, the message window would get focus when lines were added or contents were cleared. Starting in version 2.11, the developer must call this method to make the message window the top window.

### Method addLine

Writes a line to the message window.

    public void addLine(str line)

#### Parameters

line  
A string that contains the line to write to the message window.

## Class MethodInfo
    class MethodInfo extends Object

Provides information about a specified method.

### Remarks

Assign a table method to MethodInfo by using the SysDictTable class. Assign a class method by using the SysDictClass class. The following classes extend MethodInfo:

-   SysMethodInfo
-   DictMethod

### Examples

The following example uses the SysDictClass::ObjectMethodObject method to assign a method of a FormBuildDataSource Class object to an instance of the MethodInfo class. An integer value specifies the method. The MethodInfo.name Method method returns the method name.

    void getMethodInfo() 
    { 
        MethodInfo methodInfo; 
        SysDictClass sysDictClass; 
        str name; 
        try 
        { 
            sysDictClass = new SysDictClass(classnum(FormBuildDataSource)); 
            methodInfo = sysDictClass.objectMethodObject(1); 
            if(!methodInfo) 
            { 
                throw exception::Error; 
            } 
            name = methodInfo.name(); 
            print name; 
            pause; 
         } 
         catch (exception::Error) 
         { 
            print "The specified method does not exist"; 
            pause; 
         } 
    }

### Methods

| Method                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public AccessSpecifier accessSpecifier()                    | Specifies whether the method is public, protected, or private.                                                                                |
| public boolean compiledOk()                                 | Specifies whether the method has compiled.                                                                                                    |
| public TableId displayTableId()                             |                                                                                                                                               |
| public DisplayFunctionType displayType()                    | Specifies the display function type of a method.                                                                                              |
| public Array getAllAttributes()                             | Gets the full set of attributes for the method.                                                                                               |
| public Object getAttribute(str attribute)                   | Gets the first matching attribute from the class header metadata, creates an instance of the Object class that represents it, and returns it. |
| public Array getAttributes(str attribute)                   |                                                                                                                                               |
| public boolean isAbstract()                                 | Indicates whether the method is abstract.                                                                                                     |
| public boolean isStatic()                                   | Specifies whether the method is static.                                                                                                       |
| public str name()                                           | Specifies the name of a method.                                                                                                               |
| public int noParms()                                        | Specifies the number of parameters in a method.                                                                                               |
| public int noVars()                                         | Specifies the number of variables in a method.                                                                                                |
| public int parentId()                                       | Specifies the table ID for a table method or the class ID for a class method.                                                                 |
| public str propertyHelp()                                   | Specifies the Help text that a method sets or returns for a control.                                                                          |
| public NoYes PropertyMethod()                               | Specifies whether a method is a property method.                                                                                              |
| public int returnId()                                       | Specifies the ID for certain return data types, such as extended data types and classes, for a method that returns a value.                   |
| public Types returnType()                                   | Specifies a method return type.                                                                                                               |
| public ClassRunMode runMode()                               | Specifies where a method is executed.                                                                                                         |
| public int varId(int variableNumber)                        | Specifies the ID for certain variable data types, such as extended data types and enums, for a method that contains variables.                |
| public int varIdOld(int variableNumber)                     |                                                                                                                                               |
| public Types varType(int variableNumber)                    | Specifies a variable data type by using values from the Types enumeration.                                                                    |
| public void new(UtilElementType utilType, int Id, str Name) | Creates a new instance of the MethodInfo class.                                                                                               |
| public void setMethod(MemberFunction method)                | Specifies the application object type of a node in the Application Object Tree (AOT) by using an instance of the .                            |

### Method accessSpecifier

Specifies whether the method is public, protected, or private.

    public AccessSpecifier accessSpecifier()

#### Return Value

An AccessSpecifier enum value that specifies whether the method is public, proctected, or private.

### Method compiledOk

Specifies whether the method has compiled.

    public boolean compiledOk()

#### Return Value

true if the method has compiled; otherwise, false.

### Method displayTableId

    public TableId displayTableId()

#### Return Value

### Method displayType

Specifies the display function type of a method.

    public DisplayFunctionType displayType()

#### Return Value

A DisplayFunctionType enumeration value that indicates the display function type of a method.

#### Remarks

The following table lists the possible values returned by the displayType method.

|           |                                             |
|-----------|---------------------------------------------|
| Get       | The method is a display method.             |
| None      | The method is not a display or edit method. |
| RecordGet | The method gets a record.                   |
| RecordSet | The method sets a record.                   |
| Set       | The method is an edit method.               |

### Method getAllAttributes

Gets the full set of attributes for the method.

    public Array getAllAttributes()

#### Return Value

The Array of SysAttribute objects for the method.

### Method getAttribute

Gets the first matching attribute from the class header metadata, creates an instance of the Object class that represents it, and returns it.

    public Object getAttribute(str attribute)

#### Parameters

attribute  
The attribute for which to search.

#### Return Value

The attribute as an instance of the Object class.

### Method getAttributes

    public Array getAttributes(str attribute)

#### Parameters

attribute  

#### Return Value

### Method isAbstract

Indicates whether the method is abstract.

    public boolean isAbstract()

#### Return Value

true if the method is abstract; otherwise, false.

#### Remarks

An abstract method is declared but not implemented in a parent class. For more information, see Method Modifiers.

### Method isStatic

Specifies whether the method is static.

    public boolean isStatic()

#### Return Value

true if the method is static; otherwise, false.

#### Remarks

For more information, see Static Methods.

### Method name

Specifies the name of a method.

    public str name()

#### Return Value

A string that indicates the method name.

### Method noParms

Specifies the number of parameters in a method.

    public int noParms()

#### Return Value

An integer value that indicates the number of parameters in a method.

### Method noVars

Specifies the number of variables in a method.

    public int noVars()

#### Return Value

An integer value that indicates the number of variables in a method.

### Method parentId

Specifies the table ID for a table method or the class ID for a class method.

    public int parentId()

#### Return Value

An integer value that indicates a table ID or a class ID.

### Method propertyHelp

Specifies the Help text that a method sets or returns for a control.

    public str propertyHelp()

#### Return Value

A string that contains the Help text.

### Method PropertyMethod

Specifies whether a method is a property method.

    public NoYes PropertyMethod()

#### Return Value

1 if the method is a property method; otherwise, 0.

#### Remarks

A property method sets or returns a property.

### Method returnId

Specifies the ID for certain return data types, such as extended data types and classes, for a method that returns a value.

    public int returnId()

#### Return Value

An integer value that indicates the ID for the return data type.

#### Remarks

The return value is 0 if the data type does not have an ID or if a method does not return a value.

### Method returnType

Specifies a method return type.

    public Types returnType()

#### Return Value

A Types enumeration value that indicates a method return type.

#### Remarks

The following list indicates the possible values. :

-   AnyType
-   BLOB
-   Class
-   Container
-   Date
-   DateTime
-   Enum
-   Grid
-   Int64
-   Integer
-   Real
-   Record
-   RString
-   String
-   UserType
-   VarString
-   void

### Method runMode

Specifies where a method is executed.

    public ClassRunMode runMode()

#### Return Value

A ClassRunMode enumeration value that indicates where a method is executed.

#### Remarks

The following list indicates the possible values.

-   Called
-   Client
-   ClientorServer
-   Server

### Method varId

Specifies the ID for certain variable data types, such as extended data types and enums, for a method that contains variables.

    public int varId(int variableNumber)

#### Parameters

variableNumber  
An integer value that specifies a method variable based on the order of the variables listed in the method.

#### Return Value

An integer value that indicates the variable data type ID.

#### Remarks

The return value is 0 if the data type does not have an ID or if a method does not have variables.

### Method varIdOld

    public int varIdOld(int variableNumber)

#### Parameters

variableNumber  

#### Return Value

### Method varType

Specifies a variable data type by using values from the Types enumeration.

    public Types varType(int variableNumber)

#### Parameters

variableNumber  
An integer that specifies a method variable based on the order of the variables listed in the method.

#### Return Value

A Types enumeration value that indicates the variable data type.

#### Remarks

Following are the possible values:

-   AnyType
-   BLOB
-   Class
-   Container
-   Date
-   DateTime
-   Enum
-   Grid
-   Int64
-   Integer
-   Real
-   Record
-   RString
-   String
-   UserType
-   VarString
-   void

### Method new

Creates a new instance of the MethodInfo class.

    public void new(UtilElementType utilType, int Id, str Name)

#### Parameters

utilType  
A string that specifies the name of the element.

<!-- -->

Id  
A string that specifies the name of the element.

<!-- -->

Name  
A string that specifies the name of the element.

### Method setMethod

Specifies the application object type of a node in the Application Object Tree (AOT).

    public void setMethod(MemberFunction method)

#### Parameters

method  
An instance of the MemberFunction class that represents a node in the AOT.

## Class ModifyFieldEventArgs
    class ModifyFieldEventArgs extends DataEventArgs

### Remarks

### Examples

### Methods

| Method                       | Description |
|------------------------------|-------------|
| public int parmFieldId()     |             |
| public void new(int fieldId) |             |

### Method parmFieldId

    public int parmFieldId()

#### Return Value

### Method new

    public void new(int fieldId)

#### Parameters

fieldId  

## Class ModifyFieldValueEventArgs
    class ModifyFieldValueEventArgs extends DataEventArgs

### Remarks

### Examples

### Methods

| Method                                         | Description |
|------------------------------------------------|-------------|
| public str parmFieldName()                     |             |
| public int parmArrayIndex()                    |             |
| public void new(str fieldName, int arrayIndex) |             |

### Method parmFieldName

    public str parmFieldName()

#### Return Value

### Method parmArrayIndex

    public int parmArrayIndex()

#### Return Value

### Method new

    public void new(str fieldName, int arrayIndex)

#### Parameters

fieldName  

<!-- -->

arrayIndex  

## Class MultiSelectionContext
    class MultiSelectionContext extends Object

### Remarks

### Examples

### Methods

| Method                   | Description                                                    |
|--------------------------|----------------------------------------------------------------|
| public Common getFirst() |                                                                |
| public Common getNext()  |                                                                |
| private void new()       | Initializes a new instance of the MultiSelectionContext class. |

### Method getFirst

    public Common getFirst()

#### Return Value

### Method getNext

    public Common getNext()

#### Return Value

### Method new

Initializes a new instance of the MultiSelectionContext class.

    private void new()

