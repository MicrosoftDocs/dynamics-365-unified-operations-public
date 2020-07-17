---
title: Set class
description: This topic describes the Set class.
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

# Class Set

[!include [banner](../../includes/banner.md)]

```xpp
class Set extends Object
```

The Set class is used for the storage and retrieval of data from a collection in which the values of the elements contained are unique and serve as the key values according to which the data is automatically ordered.

## Remarks

The values may be of any X++ type. All values in the set must have the same type. When a value that is already stored in the set is added, it is ignored and does not increase the number of elements in the set. The values stored in the set can be traversed by using objects of type SetEnumerator. The contents of a set are stored in a way that facilitates efficient look up of the elements.

## Examples

The following example checks whether any of the values in one set, the noConfigs set, are found in a second set, the yesConfigs set. If they are, they are removed from the yesConfigs set.

```xpp
Set             noConfigs; 
Set             yesConfigs; 
ConfigId        configId; 
SetEnumerator   se; 
; 
se = noConfigs.getEnumerator(); 
while (se.moveNext()) 
{ 
    configId    = se.current(); 
    if (yesConfigs.in(configId)) 
    { 
        yesConfigs.remove(configId); 
    } 
}
```

## Methods

| Method                                               | Description                                                                                                                       |
|------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public boolean add(AnyType arg)                      | Adds an element to the set.                                                                                                       |
| public str definitionString()                        | Returns a description of the type of the elements in the set.                                                                     |
| public int elements()                                | Returns the number of elements in the set.                                                                                        |
| public boolean empty()                               | Determines whether the set is empty.                                                                                              |
| public boolean equal(Set set)                        | Determines whether a set is identical to the current set.                                                                         |
| public SetEnumerator getEnumerator()                 | Creates an enumerator for a set, which allows you to traverse the set.                                                            |
| public boolean in(AnyType arg)                       | Determines whether a specified element is a member of the set.                                                                    |
| public container pack()                              | Serializes the current instance of the Set class.                                                                                 |
| public boolean remove(AnyType arg)                   | Removes an element from the set.                                                                                                  |
| public str toString()                                | Returns a string describing the contents of the set.                                                                              |
| public Types typeId()                                | Returns the type of the values in the set.                                                                                        |
| public str xml(\[int indent\])                       | Returns an XML string that represents the current object.                                                                         |
| ::public static Set create(container container)      | Creates a set from the container obtained from a prior call to the Set.pack method.                                               |
| ::public static Set createFromXML(Object xmlnode)    |                                                                                                                                   |
| ::public static Set difference(Set set1, Set set2)   | Calculates and retrieves the set containing the elements from set1 that are not found in set2.                                    |
| ::public static Set intersection(Set set1, Set set2) | Calculates and returns the identical values found in two sets.                                                                    |
| ::public static Set union(Set set1, Set set2)        | Calculates and retrieves the union of two given sets. This is the set that contains the values found in at least one of the sets. |
| public void new(Types Type)                          | Creates a set that can contain elements of the specified type.                                                                    |

## Method add

Adds an element to the set.

```xpp
public boolean add(AnyType arg)
```

### Parameters - add

arg  
The element to add to the set.

### Return Value - add

true if the element is added to the set; otherwise, false.

### Remarks - add

The element added to a set must be of the same type as the type assigned to the set when it was created. An element will not be added if it already exists in the set.

### Examples - add

The following example creates a set, adds some integers to it, and then prints out the contents of the set.

```xpp
{ 
    // Create a set of integers 
    Set is = new Set (Types::Integer); 
    int i; 
    ;  
    // Add values 0 to 9 to the set 
    for (i = 0; i < 10; i++) 
    { 
        is.add(i); 
    } 
    print is.toString(); 
    pause; 
}
```

## Method definitionString

Returns a description of the type of the elements in the set.

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that contains a definition of the set.

### Remarks - definitionString

To print a list of the values within the set, use Set.toString.

### Examples - definitionString

The following example creates a set of integers. The definitionString method is used to print a description of the set.

```xpp
{ 
    // Declare a set of integers 
    Set is = new Set (Types::Integer);  
    ; 
    // Add some integers to the set 
    print is.add(1); 
    print is.add(2); 
    print is.add(1); 
    // Print a description of the set 
    print is.definitionString(); 
    // Print a description of the set elements 
    print is.toString(); 
    pause; 
}
```

## Method elements

Returns the number of elements in the set.

```xpp
public int elements()
```

### Return Value - elements

The number of elements in the set.

### Examples - elements

The following example packs the contents of a set into a container. The elements method is used to test whether the set has any contents. If there are no contents, a nullNothingnullptrunita null reference (Nothing in Visual Basic) container is returned.

```xpp
public static container intSet2Con(Set _intSet) 
{ 
    SetEnumerator se; 
    container     intCon; 
    ; 
    if (!_intSet || !_intSet.elements()) 
    { 
        return conNull(); 
    } 
    se = _intSet.getEnumerator(); 
    while (se.moveNext()) 
    { 
        intCon += se.current(); 
    } 
    return intCon; 
}
```

## Method empty

Determines whether the set is empty.

```xpp
public boolean empty()
```

### Return Value - empty

true if the set is empty; otherwise, false.

### Remarks - empty

This is equivalent to (elements() == 0).

### Examples - empty

The following example tests whether there are any elements in a set.

```xpp
{ 
    Set mySet = new Set(Types::Integer); 
    ; 
    // ... 
    if (mySet.empty()) 
    { 
        print "There are no values in the set"; 
    } 
}
```

## Method equal

Determines whether a set is identical to the current set.

```xpp
public boolean equal(Set set)
```

### Parameters - equal

set  
The set to be compared with the current set.

### Return Value - equal

true if the set is the same as the current set; otherwise, false.

### Remarks - equal

For two sets to be equal, they must have the same type and the same number of elements, and all elements must be the same.

### Examples - equal

The following example creates two sets of integers, adds some values to them, and then compares them to see whether the sets are the same.

```xpp
{ 
    Set is1 = new Set (Types::Integer); 
    Set is2 = new Set (Types::Integer); 
    ; 
    is1.add(1); 
    is1.add(2); 
    is1.add(3); 
    is2.add(2); 
    is2.add(4); 
    if (is1.equal(is2)) 
    { 
        print "The sets are equal"; 
        pause; 
    } 
    else 
    { 
         print "The sets are not equal"; 
         pause; 
     } 
}
```

## Method getEnumerator

Creates an enumerator for a set, which allows you to traverse the set.

```xpp
public SetEnumerator getEnumerator()
```

### Return Value - getEnumerator

A SetEnumerator object for the current set.

### Examples - getEnumerator

The following example packs the contents of a set into a container. The getEnumerator method is used to create an enumerator for the set. Therefore, that the elements in the set can be traversed and added to the container.

```xpp
public static container intSet2Con(Set _intSet) 
{ 
    SetEnumerator se; 
    container     intCon; 
    ; 
    if (!_intSet || !_intSet.elements()) 
    { 
        return conNull(); 
    } 
    se = _intSet.getEnumerator(); 
    while (se.moveNext()) 
    { 
        intCon += se.current(); 
    } 
    return intCon; 
}
```

## Method in

Determines whether a specified element is a member of the set.

```xpp
public boolean in(AnyType arg)
```

### Parameters - in

arg  
The element to check. The type of the element must be the same as the type that was specified for the set.

### Return Value - in

true if the specified element is found in the set; otherwise, false.

### Examples - in

The following example loads the contents a particular change list in the version control system, if the in method returns false. The changeSet set contains a list of the change list numbers that already have the content loaded.

```xpp
public void pageActivated() 
{ 
    SysVersionControlTmpItem contentsAddition; 
    if (!changeSet.in(changes.ChangeNumber)) 
    { 
        startLengthyOperation(); 
        contentsAddition = versioncontrol.getChangeNumberContents( 
            changes.ChangeNumber); 
        while select contentsAddition 
        { 
            contentsItem.data(contentsAddition); 
            contentsItem.insert(); 
        } 
        contents_ds.executeQuery(); 
        changeSet.add(changes.ChangeNumber); 
    } 
    super(); 
}
```

## Method pack

Serializes the current instance of the Set class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the Set class.

### Remarks - pack

The container created by this method contains 3 elements before the first element from the set:

-   A version number for the container
-   An integer that identifies the data type of the set elements
-   The number of elements in the set

If the keys or the values are objects, the pack method is called on each object to create a subcontainer. You can create a new set from the resulting container by using the Set::create method.

### Examples - pack

The following example creates a set of 10 integers, packs it into a container, and then creates a new set with contents identical to the original one.

```xpp
{ 
    Set is1, is = new Set (Types::Integer); 
    int i; 
    container packedSet; 
    ; 
    // Create a set containing the first 10 integers. 
    for (i = 1; i <= 10; i++) 
    { 
        is.add(i); 
    } 
    // Pack it down in a container... 
    packedSet = is.pack(); 
    // ... and restore it 
    is1 = Set::create(packedSet); 
    print is1.toString(); 
    pause; 
}
```

## Method remove

Removes an element from the set.

```xpp
public boolean remove(AnyType arg)
```

### Parameters - remove

arg  
The element to remove.

### Return Value - remove

true if the element was found and removed; otherwise, false.

### Examples - remove

The following example checks whether any of the values in one set, the noConfigs set, are found in a second set, the yesConfigs set. If they are found, they are removed from the yesConfigs set.

```xpp
Set             noConfigs; 
Set             yesConfigs; 
ConfigId        configId; 
SetEnumerator   se; 
; 
se = noConfigs.getEnumerator(); 
while (se.moveNext()) 
{ 
    configId    = se.current(); 
    if (yesConfigs.in(configId)) 
    { 
        yesConfigs.remove(configId); 
    } 
}
```

## Method toString

Returns a string describing the contents of the set.

```xpp
public str toString()
```

### Return Value - toString

A string that describes the contents of the set.

### Remarks - toString

Use the to get the description of a single element within a set.

### Examples - toString

The following example creates a set of strings, and then prints out a description of the set and a description of the set contents.

```xpp
{ 
    // Declare a set of strings 
    Set names = new Set (Types::String); 
    ; 
    // Add some values to the set. 
    names.add("Peter"); 
    names.add("Paul"); 
    names.add("Mary"); 
    print names.definitionString(); 
    print names.toString(); 
    pause; 
}
```

## Method typeId

Returns the type of the values in the set.

```xpp
public Types typeId()
```

### Return Value - typeId

The type of the values in the set.

### Remarks - typeId

The type of the constituent elements is determined when the set is created.

### Examples - typeId

The following example instantiates a new set with the same type as an existing set.

```xpp
{ 
    Set set1 = new Set(Types::Integer); 
    Set set2; 
   ; 
    set2 = new Set(set1.typeId()); 
    print set2.typeId(); 
    pause; 
}
```

## Method xml

Returns an XML string that represents the current object.

```xpp
public str xml([int indent])
```

### Parameters - xml

indent  
The amount of indentation of the returned XML string; optional.

### Return Value - xml

An XML string that represents the current object.

### Remarks - xml

This method can be overridden to return values that are meaningful for that type.

## Method create

Creates a set from the container obtained from a prior call to the Set.pack method.

```xpp
public static Set create(container container)
```

### Parameters - create

container  
The container that holds the packed set.

### Return Value - create

A set equal to the one that was packed into the container.

### Remarks - create

If the values are objects, the objects must have an unpack method that is called to reestablish their internal state from the container.

### Examples - create

The following example creates a set and packs it into a container. The create method is then used to unpack the container and create a set identical to the original one.

```xpp
{ 
    Set is1, is = new Set (Types::Integer); 
    int i; 
    container packedSet; 
    ; 
    // Add 10 integers (0 - 9) to the set 
    for (i = 1; i <= 10; i++) 
    { 
        is.add(i); 
    } 
    // Pack the set into a container... 
    packedSet = is.pack(); 
    // ... and restore it 
    is1 = Set::create(packedSet); 
    print is1.toString(); 
    pause; 
}
```

## Method createFromXML

```xpp
public static Set createFromXML(Object xmlnode)
```

### Parameters - createFromXML

xmlnode  

### Return Value - createFromXML

## Method difference

Calculates and retrieves the set containing the elements from set1 that are not found in set2.

```xpp
public static Set difference(Set set1, Set set2)
```

### Parameters - difference

set1  
The set to check.

<!-- -->

set2  
The set to check.

### Return Value - difference

A set containing the elements from set1 that are not found in set2.

### Remarks - difference

The two sets to be compared must be of the same type.

### Examples - difference

The following example creates one set that contains the integers 1, 2, and 3, and one set that contains the integers 2 and 4. The difference method is used to create a set that contains the elements in the first set that are not in the second set (1 and 3).

```xpp
{ 
    Set is = new Set (Types::Integer); 
    Set is2, is1 = new Set (Types::Integer); 
    ; 
    is.add(1); 
    is.add(2); 
    is.add(3); 
    is1.add(2); 
    is1.add(4); 
    is2 = Set::difference(is, is1); 
    // prints "{1, 3}" 
    print is2.toString(); 
    pause; 
}
```

## Method intersection

Calculates and returns the identical values found in two sets.

```xpp
public static Set intersection(Set set1, Set set2)
```

### Parameters - intersection

set1  
The second set to be compared.

<!-- -->

set2  
The second set to be compared.

### Return Value - intersection

A set containing the elements found in both sets.

### Examples - intersection

The following example creates two sets of integers and adds some values to them. It then prints a list of the values that are that is contained in both sets.

```xpp
{ 
    Set is = new Set (Types::Integer); 
    Set is2, is1 = new Set (Types::Integer); 
    ; 
    is.add(1); 
    is.add(2); 
    is.add(3); 
    is1.add(2); 
    is1.add(4); 
    is2 = Set::intersection(is, is1); 
    // Prints "{2}" because 2 is contained in both is and is2. 
    print is2.toString(); 
}
```

## Method union

Calculates and retrieves the union of two given sets. This is the set that contains the values found in at least one of the sets.

```xpp
public static Set union(Set set1, Set set2)
```

### Parameters - union

set1  
The second of the two sets that are compared.

<!-- -->

set2  
The second of the two sets that are compared.

### Return Value - union

The set containing elements found in set1 or set2.

### Remarks - union

The two sets that are compared must be of the same type.

### Examples - union

The following example creates two sets of integers and adds some values to them. It then creates a new set that contains all the values that are contained in either of the sets.

```xpp
{ 
    Set is = new Set (Types::Integer); 
    Set is2, is1 = new Set (Types::Integer); 
    ; 
    is.add(1); 
    is.add(2); 
    is.add(3); 
    is1.add(2); 
    is1.add(4); 
    is2 = Set::union(is, is1); 
    // Prints "{1, 2, 3, 4}". 
    print is2.toString(); 
    pause; 
}
```

## Method new

Creates a set that can contain elements of the specified type.

```xpp
public void new(Types Type)
```

### Parameters - new

Type  
The type of the elements within the set.

### Remarks - new

The type of the set cannot be changed after the set has been created.

### Examples - new

The following example creates a set of integers and a set of objects.

```xpp
{ 
    // Create a set of integers. 
    Set is = new Set (Types::Integer); 
    // Create a set of objects. 
    Set os = new Set (Types::Class); 
}
```

