---
title: List class
description: This topic describes the List class.
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

# Class List

[!include [banner](../../includes/banner.md)]

```xpp
class List extends Object
```

Contains any number of elements that are accessed sequentially. Lists are structures that can contain values of any X++ type. All the values in the list must be of the same type.

## Remarks

The type of the values in the list is specified when the list is created and cannot be changed afterwards. The implementation of lists makes traversal of the list elements very fast. Lists can be traversed by using the ListEnumerator class. To create a ListEnumerator object, use List.getEnumerator.

## Examples

The following example creates a list of integers and prints out a description of the list and the values that it contains.

```xpp
{ 
    // Create a list of integers 
    List il = new List(Types::Integer); 
    // Add some elements to the list 
    il.addEnd(1); 
    il.addEnd(2); 
    il.addStart(3); 
    // Print a description of the list 
    print il.definitionString(); 
    print il.toString(); 
    pause; 
}
```

## Methods

| Method                                                | Description                                                                           |
|-------------------------------------------------------|---------------------------------------------------------------------------------------|
| public AnyType addEnd(AnyType element)                | Adds a value to the end of the list.                                                  |
| public AnyType addStart(AnyType element)              | Adds a value to the start of the list.                                                |
| public str definitionString()                         | Returns a description of the type of the elements in the list.                        |
| public int elements()                                 | Specifies the number of elements in a list.                                           |
| public boolean empty()                                | Determines whether a list is empty.                                                   |
| public boolean equalTo(List l)                        | Determines whether a list is the same as the current list.                            |
| public ListEnumerator getEnumerator()                 | Creates an enumerator for a list which allows you to traverse the list.               |
| public container pack()                               | Serializes the current instance of the List class.                                    |
| public str toString()                                 | Returns a description of the values in the list.                                      |
| public Types typeId()                                 | Returns the type of the values in a list.                                             |
| public str xml(\[int indent\])                        | Returns an XML string that represents the current object.                             |
| ::public static List create(container container)      | Creates a list from the container obtained from a prior call to the List.pack method. |
| ::public static List createFromXML(Object xmlnode)    |                                                                                       |
| ::public static boolean equal(List list1, List list2) | Determines whether two lists are identical.                                           |
| ::public static List merge(List list1, List list2)    | Combines two lists to create a new list.                                              |
| public void appendList(List list)                     |                                                                                       |
| public void new(Types Type)                           | Creates a list.                                                                       |

## Method addEnd

Adds a value to the end of the list.

```xpp
public AnyType addEnd(AnyType element)
```

### Parameters - addEnd

element  
The value to add to the end of the list.

### Return Value - addEnd

The value that is added to the list.

## Method addStart

Adds a value to the start of the list.

```xpp
public AnyType addStart(AnyType element)
```

### Parameters - addStart

element  
The value to add to the start of the list.

### Return Value - addStart

The value added to the list.

### Remarks - addStart

Elements can be added to the end of the list by using the List.addEnd method.

### Examples - addStart

The following example creates a list of integers, adds the values 1 and 2 to the end of the list, and then adds the value 3 to the start of the list. The values that are returned by the List.toString method are {3, 1, 2}.

```xpp
{ 
    // Create a list of integers 
    list il = new List(Types::Integer); 
    // Add some elements to the list 
    il.addEnd(1); 
    il.addEnd(2); 
    il.addStart(3); 
    // Print a description of the list. 
    print il.definitionString(); 
    print il.toString(); 
    pause; 
}
```

## Method definitionString

Returns a description of the type of the elements in the list.

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that contains a definition of the list.

### Remarks - definitionString

For example, this method could return "list of int". To print a list of the values within the list, use the List.toString method.

### Examples - definitionString

The following example creates a list of integers. The definitionString method is used to print a description of the list.

```xpp
{ 
    // Create a list of integers 
    List il = new List(Types::Integer); 
    // Add some elements to the list 
    il.addEnd(1); 
    il.addEnd(2); 
    il.addStart(3); 
    // Print a description ofvthe list 
    print il.definitionString(); 
    print il.toString(); 
    pause; 
}
```

## Method elements

Specifies the number of elements in a list.

```xpp
public int elements()
```

### Return Value - elements

The number of elements in the list.

### Examples - elements

The following example creates a list of integers and adds some elements to it. The elements method is used to test whether there are three elements in the list.

```xpp
{ 
    List il = new List(Types::Integer); 
    il.addStart(1); 
    il.addStart(2); 
    il.addStart(3); 
    if (il.elements() != 3) 
    { 
        print "Something is wrong..."; 
    } 
}
```

## Method empty

Determines whether a list is empty.

```xpp
public boolean empty()
```

### Return Value - empty

true if the list is empty; otherwise, false.

## Method equalTo

Determines whether a list is the same as the current list.

```xpp
public boolean equalTo(List l)
```

### Parameters - equalTo

l  
The list to be compared with the current list.

### Return Value - equalTo

true if the specified list is identical to the list on which the method is called; otherwise, false.

### Remarks - equalTo

A list is equal to another list if the two lists are the same type, contain the same number of elements, and the elements occur in the same order. The equalTo method is a shortcut for using the List.equal method: equal(this, l).

## Method getEnumerator

Creates an enumerator for a list which allows you to traverse the list.

```xpp
public ListEnumerator getEnumerator()
```

### Return Value - getEnumerator

A listEnumerator object for the current list.

## Method pack

Serializes the current instance of the List class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the List class.

### Remarks - pack

The container created by this method contains 3 elements before the first element from the list:

-   A version number for the container
-   An integer that identifies the data type of the list elements
-   The number of elements in the list

If the elements in the list are objects, packing is performed by calling the pack method successively on each object to yield a subcontainer. The list can be retrieved from the packed container by using the List.create method.

### Examples - pack

The following example creates a list of records and passes in the packed list as a parameter for creating a new projReverseMarking object.

```xpp
public boolean canClose() 
{ 
    ProjReverseMarking      projReverseMarking; 
    boolean                 canClose; 
    List                    list; 
    canClose = super(); 
    if (element.closedOk() && canClose) 
    { 
        List = new List(Types::Record); 
        while select tmpFrmVirtualLines 
        { 
            list.addEnd(tmpFrmVirtualLines); 
        } 
        projReverseMarking = new ProjReverseMarking(list.pack()); 
        projReverseMarking.run(); 
    } 
    return canClose; 
}
```

## Method toString

Returns a description of the values in the list.

```xpp
public str toString()
```

### Return Value - toString

A string that describes the values of the elements in the list.

### Remarks - toString

To print a description of the type of the elements in the list, use the List.definitionString method.

### Examples - toString

The following example creates a list of integers. The toString method is used to print a description of the values in the list.

```xpp
{ 
    // Create a list of integers 
    List il = new List(Types::Integer); 
    // Add some elements to the list 
    il.addEnd(1); 
    il.addEnd(2); 
    il.addStart(3); 
    // Print a description of the list 
    print il.definitionString(); 
    print il.toString(); 
    pause; 
}
```

## Method typeId

Returns the type of the values in a list.

```xpp
public Types typeId()
```

### Return Value - typeId

The type of the list elements.

### Remarks - typeId

The type of the list is specified when the list is created, and remains the same throughout the life of the list.

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

Creates a list from the container obtained from a prior call to the List.pack method.

```xpp
public static List create(container container)
```

### Parameters - create

container  
The container that holds the packed list.

### Return Value - create

A list identical to the one that was packed into the container.

### Examples - create

The following example creates a list and packs it into a container. The create method is then used to unpack the container and create a list identical to the original one.

```xpp
{ 
    List il = new List(Types::Integer); 
    List newList; 
    container packedList; 
    // Add some elements 
    il.addEnd(1); 
    il.addEnd(2); 
    il.addEnd(3); 
    // Pack the list into a container 
    packedList = il.pack(); 
    newList = list::create(packedList); 
    // Prints <1, 2, 3> 
    print newList.toString(); 
    pause; 
}
```

## Method createFromXML

```xpp
public static List createFromXML(Object xmlnode)
```

### Parameters - createFromXML

xmlnode  

### Return Value - createFromXML

## Method equal

Determines whether two lists are identical.

```xpp
public static boolean equal(List list1, List list2)
```

### Parameters - equal

list1  
The second list to be compared.

<!-- -->

list2  
The second list to be compared.

### Return Value - equal

true if the two lists are identical; otherwise, false.

### Remarks - equal

A list is equal to another list if the two lists are the same type, contain the same number of elements, and the elements occur in the same order.

## Method merge

Combines two lists to create a new list.

```xpp
public static List merge(List list1, List list2)
```

### Parameters - merge

list1  
The list that will be added to the end of the first to create the new list.

<!-- -->

list2  
The list that will be added to the end of the first to create the new list.

### Return Value - merge

The new list.

### Remarks - merge

The types of the lists must be the same.

### Examples - merge

The following example creates two lists of integer values, merges them to create a new list, and then prints out the values in the new combined list.

```xpp
{ 
    List list1  = new List(Types::Integer); 
    List list2  = new List(Types::Integer); 
    List combinedList  = new List(Types::Integer); 
    int  i; 
    for(i=1; i<6; i++) 
    { 
        List1.addEnd(i); 
    } 
     for(i=6; i<11; i++) 
    { 
        List2.addEnd(i); 
    } 
    combinedList = List::merge(list1, list2); 
    print combinedList.toString(); 
    pause; 
}
```

## Method appendList

```xpp
public void appendList(List list)
```

### Parameters - appendList

list  

## Method new

Creates a list.

```xpp
public void new(Types Type)
```

### Parameters - new

Type  
The type that the elements in the list should have.

### Remarks - new

The possible values for the Type parameter are supplied by the Types system enum. After you have created a list, you cannot change the type of the elements it contains.

### Examples - new

The following example creates a list of strings.

```xpp
{ 
    // Creates a list of integers. 
    List il = new List(Types::String); 
}
```

