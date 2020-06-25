---
title: SetIterator class
description: This topic describes the SetIterator class.
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

# Class SetIterator

[!include [banner](../../includes/banner.md)]

```xpp
class SetIterator extends Object
```

The SetIterator class allows you to iterate over the elements in a set.

## Remarks

Set iterators may be viewed as pointers into the sets over which they iterate. Functionality is available to start the iteration, to determine whether more elements are available, and to fetch the element pointed to by the iterator. Newly created set iterators are positioned at the first element in the set. The order in which the elements occur during iteration is defined not by the sequence in which the elements are inserted, but by the ordering of the elements. Elements with lower values appear before elements with higher values. The usual ordering for the types is used. If the constituent elements are objects; however, the addresses of the objects are used to supply the ordering. No specific ordering may consequently be inferred. The addresses of the objects are transient by nature. It is best practice to use the class instead of the SetIterator class. This avoids problems if you are accessing the set on one tier with an iterator on another tier. Set iterators and the sets over which they iterate must be on the same client/server side. If you use SetIterator and code is marked as Called from, it is possible that the set and the iterator will end up on different tiers, and the code will fail. If you use SetEnumerator, the enumerator is automatically created on the same tier as the set. Also, to move to the next item in a set, you must explicitly call the more and next methods if you are using a set iterator. If you use SetEnumerator, you only have to call moveNext method.

## Examples

The following example creates a set of integers and then adds four values to it. It then iterates through the set that is printing out information about each set element.

```xpp
    Set s1 = new Set (Types::Integer); 
    int theElement; 
    SetIterator it; 
    ; 
    // Add some elements. 
    s1.add(3); 
    s1.add(4); 
    s1.add(13); 
    s1.add(1); 
    // Start a traversal of the elements in the set. 
    it = new SetIterator(s1); 
    // Prints "(begin)[1]". 
    print it.toString(); 
    // The elements are fetched in the order: 1, 3, 4, 13. 
    while (it.more()) 
    { 
        theElement = it.value(); 
        print theElement; 
         // Fetch the next element. 
        it.next(); 
    } 
    pause; 
}
```

## Methods

| Method                        | Description                                                                                            |
|-------------------------------|--------------------------------------------------------------------------------------------------------|
| public str definitionString() | Returns a textual representation of the type of the iterator.                                          |
| public boolean more()         | Determines whether the iterator denotes a valid set element.                                           |
| public str toString()         | Returns a textual representation of the current element in the set that is pointed to by the iterator. |
| public AnyType value()        | Retrieves the value that the iterator is pointing to.                                                  |
| public void next()            | Moves the iterator to the next element.                                                                |
| public void new(Set set)      | Creates a new iterator for a set.                                                                      |
| public void begin()           | Moves the iterator to the start of the set.                                                            |
| public void delete()          | Removes the element that is pointed to by the iterator of the set.                                     |
| public void end()             | Moves the iterator past the last element in the set.                                                   |

## Method definitionString

Returns a textual representation of the type of the iterator.

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that indicates the type of the iterator.

## Method more

Determines whether the iterator denotes a valid set element.

```xpp
public boolean more()
```

### Return Value - more

true if the iterator denotes a valid element; otherwise, false.

### Remarks - more

Attempting to access an element that is pointed to by an iterator when this method returns false will result in an error. This method will check only whether the iterator points to a valid element. It will not check whether there are more elements in the set.

### Examples - more

The following example uses the SetIterator.more method to check whether there are more elements in the set before it runs through the while loop, which deletes all the odd elements from the set.

```xpp
{ 
    Set iset = new Set (Types::Integer); 
    SetIterator it; 
    int i; 
    ; 
    for (i = 1; i <= 10; i++) 
    { 
        iset.add(i); 
    } 
    // Delete all odd elements 
    it = new SetIterator(iset); 
    while (it.more()) 
    { 
        if (it.value() mod 2 != 0) 
        { 
            // The value is odd. Delete and skip to next element. 
            it.delete(); 
        } 
        else 
        { 
            it.next(); 
        } 
    } 
    print iset.toString(); 
    pause; 
}
```

## Method toString

Returns a textual representation of the current element in the set that is pointed to by the iterator.

```xpp
public str toString()
```

### Return Value - toString

A string that is the textual representation of the current element in the set.

### Remarks - toString

If the iterator points to the first element in the set, the string will contain an indication of this, in the following format: "(begin)\[value\]" If the iterator does not point to an element (that is, if more() returns false), the string returned is: "(end)" If the iterator points to a value the string is: "\[value\]" where value is a string representation of the element value.

### Examples - toString

The following example uses the SetIterator.toString method to print a description of the value in the set that the iterator points to before it starts traversing the set.

```xpp
{ 
    Set s1 = new Set (Types::Integer); 
    int theElement; 
    SetIterator it; 
    // Add some elements 
    s1.add(3); 
    s1.add(4); 
    s1.add(13); 
    s1.add(1);  
    // Start a traversal of the elements in the set 
    it = new SetIterator(s1); 
    // The elements are fetched in the order: 1, 3, 4, 13 
    print it.toString(); // Prints "(begin)[1]" 
    while (it.more()) 
    { 
        theElement = it.value(); 
        print theElement; 
        // Fetch the next element 
        it.next(); 
    } 
    pause; 
}
```

## Method value

Retrieves the value that the iterator is pointing to.

```xpp
public AnyType value()
```

### Return Value - value

The value denoted by the iterator.

### Remarks - value

Use SetIterator.more to check whether an element exists before trying to retrieve the key value of the set element.

### Examples - value

The following example uses the SetIterator.value method to print the value of the current item in the set.

```xpp
{ 
    Set s1 = new Set (Types::Integer); 
    SetIterator it; 
    // Add some elements 
    s1.add(3); 
    s1.add(4); 
    s1.add(13); 
    s1.add(1);  
    // Start a traversal of the elements in the set 
    it = new SetIterator(s1); 
    // Prints "(begin)[1]" 
    print it.toString();  
    // The elements are fetched in the order: 1, 3, 4, 13 
    while (it.more()) 
    { 
        print it.value(); 
        // Fetch the next element 
        it.next(); 
    } 
    pause; 
}
```

## Method next

Moves the iterator to the next element.

```xpp
public void next()
```

### Remarks - next

Use SetIterator.more to determine whether the iterator points to a valid element.

### Examples - next

The following example uses the SetIterator.next method to move the iterator to the next element in the set, before testing whether there is another element, and if there is another element, adding the value to a container.

```xpp
static public void saveSequence(classId _classId, Set _sequence) 
{ 
    SysCheckListItemTable sysCheckListItemTable; 
    SetIterator           si; 
    container             con = connull(); 
    if (_sequence) 
    { 
        si = new SetIterator(_sequence); 
        si.begin(); 
        while (si.more()) 
        { 
             con += si.value(); 
             si.next(); 
        } 
    } 
    //... 
}
```

## Method new

Creates a new iterator for a set.

```xpp
public void new(Set set)
```

### Parameters - new

set  
The set to iterate over.

### Remarks - new

The iterator is positioned at the first value in the set, if the set is not empty.

### Examples - new

The following example creates a set of integers and then creates an iterator for that set

```xpp
Set s1 = new Set (Types::Integer); 
SetIterator it; 
it = new SetIterator(s1);
```

## Method begin

Moves the iterator to the start of the set.

```xpp
public void begin()
```

### Remarks - begin

Newly created set iterators are positioned at the first element in the set. Typically, you do not need to call the begin method before you start to iterate through the set; you need to do that only if you want to reset the pointer later on.

### Examples - begin

The following example returns set of class IDs of the classes that implement the specified interface, that is, the \_id class. An iterator is used to remove classes from the set if they are superclasses, and the \_onlyLeafClasses parameter is set to true. The begin method is used to reset the iterator after the superclasses have been removed from the set.

```xpp
public static Set getImplements( 
    classId _id,  
    boolean _onlyLeafClasses = true) 
{ 
    Dictionary dictionary = new Dictionary(); 
    SysDictClass sysDictClass; 
    boolean removed; 
    Set set = new Set(Types::Integer); 
    SetIterator setIterator = new SetIterator(set); 
    int i; 
    for (i=1;i<=dictionary.classCnt();i++) 
    { 
        sysDictClass = new SysDictClass(dictionary.classCnt2Id(i)); 
        if (sysDictClass.isImplementing(_id)) 
        { 
            set.add(sysDictClass.id()); 
        } 
    } 
    //No superclasses included in return set 
    if (_onlyLeafClasses) 
    { 
        // begin method not needed here; only for clarity 
        setIterator.begin();  
        while (setIterator.more()) 
        { 
            removed = false; 
            sysDictClass = new SysDictClass(setIterator.value()); 
            while (sysDictClass.extend()) 
            { 
                removed = removed | set.remove(sysDictClass.extend()); 
                sysDictClass = new SysDictClass(sysDictClass.extend()); 
            } 
            if (removed) 
            { 
                // Restart search 
                setIterator.begin();  
            } 
            else 
            { 
                setIterator.next(); 
            } 
        } 
    } 
    return set; 
}
```

## Method delete

Removes the element that is pointed to by the iterator of the set.

```xpp
public void delete()
```

### Remarks - delete

The iterator will point to the next element after calling this method.

### Examples - delete

The following example deletes all the odd elements from the set.

```xpp
{ 
    Set iset = new Set (Types::Integer); 
    SetIterator it; 
    int i; 
    for (i = 1; i <= 10; i++) 
    { 
        iset.add(i); 
    } 
    // Delete all odd elements 
    it = new SetIterator(iset); 
    while (it.more()) 
    { 
        if (it.value() mod 2 != 0) 
        { 
            // The value is odd. Delete and skip to next element. 
            it.delete(); 
        } 
        else 
        { 
            it.next(); 
        } 
    } 
    print iset.toString(); 
    pause; 
}
```

## Method end

Moves the iterator past the last element in the set.

```xpp
public void end()
```

### Remarks - end

After executing this method, the more method will return false.

