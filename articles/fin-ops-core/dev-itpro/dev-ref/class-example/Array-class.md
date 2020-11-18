---
title: Array class
description: This topic describes the Array class.
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

# Class Array
    class Array extends Object

## Remarks

Arrays can hold values of any single type, such as objects and records (contrary to the array data type that is built into the X++ language). Objects of this type can be transferred to functions and methods. The values are stored sequentially. The arrays expand as required. Therefore, no specific dimension of the array is supplied.

## Examples

The following example creates an array of classes and adds three query objects to the array.

    { 
        Array oarray = new Array (Types::Class); 

        oarray.value(1, new query()); 
        oarray.value(2, new query()); 
        oarray.value(4, new query());  
        print oarray.toString(); 
        print oarray.definitionString(); 
        pause; 
    }

## Methods

| Method                                              | Description                                                                                         |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| public str definitionString()                       | Returns a string that contains the definition of the array.                                         |
| public boolean exists(int index)                    | Determines whether a particular array element is valid.                                             |
| public int lastIndex()                              | Retrieves the highest index that is used to store a value in the array.                             |
| public container pack()                             | Serializes the current instance of the Array class.                                                 |
| public str toString()                               | Returns a string that describes the contents of the array.                                          |
| public Types typeId()                               | Returns the data type of the values in the array.                                                   |
| public AnyType value(int index, \[AnyType arg\])    | Gets or sets the value of the array element that is stored at the specified index.                  |
| public str xml(\[int indent\])                      | Returns an XML string that represents the current object.                                           |
| ::public static Array create(container container)   | Creates an array from the container that is obtained from a previous call to the Array.pack method. |
| ::public static Array createFromXML(Object xmlnode) |                                                                                                     |
| public void new(Types Type)                         | Creates an array in which each element has the specified type.                                      |

## Method definitionString

Returns a string that contains the definition of the array.

    public str definitionString()

### Return Value

A string that contains the definition of the array.

### Examples

The following example creates an array of classes and then adds three query objects to the array. It uses the definitionString method to print a definition of the array.

    { 
        Array oarray = new Array (Types::Class); 

        oarray.value(1, new query()); 
        oarray.value(2, new query()); 
        oarray.value(4, new query());  
        print oarray.definitionString(); 
        pause; 
    }

## Method exists

Determines whether a particular array element is valid.

    public boolean exists(int index)

### Parameters

index  
The array element to test.

### Return Value

true if the array element that is pointed to by the index is valid; otherwise, false.

### Examples

The following example uses the exists method to test whether various elements in an array are valid.

    { 
        array a = new array(types::Integer); 

        a.value(1, 23); 

        print a.value(1); 
        pause; 
        if (a.exists(7)) // No, only element 1 is initialized 
        { 
            print a.value(7); 

        } 
        else  
        { 
            print "Value does not exist"; 
        } 
        pause; 

        //Array positions 2 to 9 padded with default values 
        a.value(10, 55); 

        if (a.exists(7)) // Yes, elements 1..10 now initialized 
        { 
            print a.value(7); 
        } 
        else  
        { 
            print "Value does not exist"; 
        } 
        pause; 
    }

## Method lastIndex

Retrieves the highest index that is used to store a value in the array.

    public int lastIndex()

### Return Value

An integer that represents the highest index that is used to store a value.

### Examples

The following example uses the lastIndex method to find the last element in the array and then add a new value after this element.

    { 
        Array myArray = new Array(Types::Integer); 
        int newValue; 

        // Other code - values are added to myArray 
        // and a value is assigned to newValue 

        myArray.value(myArray.lastIndex()+1, newValue); 
    }

## Method pack

Serializes the current instance of the Array class.

    public container pack()

### Return Value

A container that contains the current instance of the Array class.

### Remarks

The container created by this method contains three elements before the first element from the array:

-   A version number for the container.
-   An integer that identifies the data type of the array elements.
-   The number of elements in the array.

If the values of the array are objects, the pack method is called on each object to yield a subcontainer.

### Examples

The following example creates an array of integers and adds some values to it. The pack method is used to pack the array into a container, and the container is then used to create a new array.

    { 
        int i; 
        container packedArray; 
        // Create an integer array 
        Array ia = new Array (Types::Integer); 
        Array iacopy; 

        // Write some elements in it 
        for (i = 1; i< 10; i++) 
        { 
            ia.value(i, i*2); 
        } 

        // Pack the array 
        packedArray = ia.pack(); 

        // Unpack the array  
        iacopy = Array::create(packedArray); 

        // Check the values 
        for (i = 1; i< 10; i++) 
        { 
            if (iacopy.value(i) != 2*i) 
            { 
                print "Error!"; 
            } 
        } 
        pause; 
    }

## Method toString

Returns a string that describes the contents of the array.

    public str toString()

### Return Value

A string that describes the contents of the array.

### Examples

The following example creates an array of integers and adds some values to it. The toString method is used to print the values that the array holds.

    { 
        Array     myArray; 

        Set set1 = new Set(Types::Integer); 
        Set set2 = new Set(Types::Integer); 
        int i; 


        myArray = new Array(Types::Integer); 

        // Add some values to the array. 
        for (i = 1; i< 10; i++) 
        { 
            myArray.value(i, i*2); 
        } 

        // Print out the values in the array. 
        print myArray.toString(); 
        pause; 
    }

## Method typeId

Returns the data type of the values in the array.

    public Types typeId()

### Return Value

The data type of the elements in the array.

### Remarks

The type remains the same throughout the life of the array. The type is specified when the array is created.

### Examples

The following example tests whether a particular array element exists. If it does not exist, the typeId method is used to specify the type of the new value that should be added to the array.

    public anytype getArrayValue(Array a, int _index) 
    { 
        if (! a.exists(_index)) 
        { 
            a.value(_index,nullValueFromType(a.typeId())); 
        } 

        return a.value(_index); 
    }

## Method value

Gets or sets the value of the array element that is stored at the specified index.

    public AnyType value(int index, [AnyType arg])

### Parameters

index  
The value to assign to the array element at the specified offset; optional.

<!-- -->

arg  
The value to assign to the array element at the specified offset; optional.

### Return Value

The value that is stored at the specified offset.

### Remarks

The return type is the same as the type of the array. If an attempt is made to read a value at an index that is beyond the last index that has a value, an exception is thrown. If a value is written to a nonexistent location, all locations between the previous element and the nonexistent location are filled with default values, and the array is expanded.

### Examples

The following example creates an array of integers and then uses the value method to add some values to the array. It then uses the value method to get the values that are stored in the array and test them.

    { 
         int i; 
        // Create an integer array 
        Array ia = new Array (Types::Integer); 

        // Write some elements in it 
        for (i = 1; i< 10; i++) 
        { 
            ia.value(i, i*2); 
        } 

        // Check the values 
        for (i = 1; i< 10; i++) 
        { 
            if (ia.value(i) != 2*i) 
            { 
                print "Error!"; 
            } 
        } 
        pause; 
    }

## Method xml

Returns an XML string that represents the current object.

    public str xml([int indent])

### Parameters

indent  
The amount of indentation of the returned XML string; optional.

### Return Value

An XML string that represents the current object.

### Remarks

This method can be overridden to return values that are meaningful for a particular type.

### Method create

Creates an array from the container that is obtained from a previous call to the Array.pack method.

    public static Array create(container container)

### Parameters

container  
A container that is created by using the Array.pack method. The container is unpacked to create an array.

### Return Value

An array that holds the contents of the specified container.

### Remarks

If the values in the array are objects, the objects must have an Array.unpack method that is called to reestablish their internal state from a container.

### Examples

The following example creates an array and adds two sets to it. The array is packed and then used to create a new array.

    { 
        Array     myArray; 
        Array     newArray; 
        container packedArray; 

        Set set1 = new Set(Types::Integer); 
        Set set2 = new Set(Types::Integer); 
        int i; 
        int j; 

        myArray = new Array(Types::Class); 

        // Add some values to the set1 and set2 
        for (i = 0; i < 10; i++) 
        { 
            set1.add(i); 
            j = i+3; 
            set2.add(j); 
        } 

        // Add set1 and set2 to myArray 
        myArray.value(1, set1); 
        myArray.value(2, set2); 

        // Pack the myArray into a container 
        packedArray = myArray.pack(); 

        // Create a new array from the container 
        if(packedArray != connull()) 
        { 
            newArray = Array::create(packedArray); 
        } 

        // Test that newArray has same contents as myArray 
        print newArray.definitionString(); 
        print newArray.toString(); 
        pause; 
    }

## Method createFromXML

    public static Array createFromXML(Object xmlnode)

### Parameters

xmlnode  

### Return Value

## Method new

Creates an array in which each element has the specified type.

    public void new(Types Type)

### Parameters

Type  
The data type of the array elements.

### Remarks

The possible values are those that are available for the Types system enumeration:

-   AnyType
-   BLOB
-   Class
-   Container
-   Date
-   DateTime
-   Enum
-   Guid
-   Int64
-   Integer

### Examples

The following example creates an array of integers.

    Array intArray = new Array(Types::Integer);
