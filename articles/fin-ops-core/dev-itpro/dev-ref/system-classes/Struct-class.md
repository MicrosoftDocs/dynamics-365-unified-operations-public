---
title: Struct class
description: This topic describes the Struct class.
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

# Class Struct

[!include [banner](../../includes/banner.md)]

```xpp
class Struct extends Object
```

A struct holds several values of any X++ type, to group the information about a specific entity.

## Remarks

A struct (short for structure) is an entity that can hold several values of any X++ type. Structs are used to group information about a specific entity. For example, you might want to store information about a customer's name, age and address and then treat this compound information as one item. The items in a struct are specified by a data type and a name. Items are added when the struct is created by using the new method, or they are created after the struct has been created by using the add method. If you add an item by using the add method, you specify the value for the item at the same time, and the data type is inferred from this value. If you add an item during the instantiation of the struct, you need to use the value or the valueIndex method to assign a value to it. The items in a struct can be of any of the data types found in the Types system enum, including: string, integer, real, date, container, record, and class. The items in a struct are arranged in alphabetical order of the item names. The fields in a struct can be traversed by using the fields, fieldName, and fieldType methods. Structs can be packed into containers and later restored by using the Struct::create method. Structs have some similarities to X++ containers. However, a container is a value type and is built into the X++ language. You can create nested containers, but you cannot create nested structs. X++ classes can store information in much the same way as structs. But although classes can supply methods to manipulate the data, no such facility is provided for structs, and there is no concept of overriding or extension. Classes can only be created in the AOT, but structs exist solely in the context of the code in which they are created. Class member variables are private to the class, so accessor functions must be coded for them for the values to be used from outside the class. The items within a struct are publicly accessible.

## Examples

The following example creates a struct with two items and then assigns values to those items. A new item is then added by using the Struct.add method; the data type of the item is inferred from the value assigned to it. The struct is then packed into a container and used to create a new struct, a copy of the original struct.

```xpp
{ 
    Struct s = new struct ("int age; str name"); 
    Struct copy; 
    container c; 
    int i; 
    // Add values to the items 
    s.value("age", 25); 
    s.value("name", "Jane Dow"); 
  // Add a new item; data type is inferred from value 
    s.add("Shoesize", 45); 
    // Print the definition of the struct 
    print s.definitionString(); 
    // Prints the type and name of all items in the struct 
    for (i =  1;   i <= s.fields();i++) 
    { 
         print s.fieldType(i), " ", s.fieldName(i); 
    }  
    // Pack the struct into a container and restore it into copy 
    c = s.pack(); 
    copy = Struct::create(c); 
    print copy.definitionString(); 
    pause; 
}
```

## Methods

| Method                                                        | Description                                                                                   |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| public boolean add(str fieldName, AnyType value)              | Adds a new item to the struct and assigns the specified value to it.                          |
| public str definitionString()                                 | Returns a description of the names and types of the elements in the struct.                   |
| public boolean exists(str fieldName)                          | Determines whether a particular item exists in a struct.                                      |
| public str fieldName(int index)                               | Returns the name of the item in the struct at the specified position.                         |
| public int fields()                                           | Returns the number of items in the struct.                                                    |
| public Types fieldType(int index)                             | Returns the data type of the item in the struct at the specified position.                    |
| public int index(str fieldName)                               | Calculates the position of an item in the struct based on its name.                           |
| public container pack()                                       | Serializes the current instance of the Struct class.                                          |
| public boolean remove(str fieldName)                          | Removes an item from a struct.                                                                |
| public str toString()                                         | Returns a string that describes the contents of the struct.                                   |
| public AnyType value(str fieldName, \[AnyType value\])        | Gets or sets the value for a specified item in a struct.                                      |
| public str valueImage(int index)                              | Returns a string that describes the value of the item at a particular position in the struct. |
| public AnyType valueIndex(int index, \[AnyType value\])       | Gets or sets the value of the item at a specified position in a struct.                       |
| public str xml(\[int indent\])                                | Returns an XML string that represents the current object.                                     |
| ::public static Struct create(container container)            | Creates a struct from a container that is obtained from a prior call to Struct.pack.          |
| ::public static Struct createFromXML(Object xmlnode)          |                                                                                               |
| ::public static boolean equal(Struct struct1, Struct struct2) | Determines whether two structs are equal.                                                     |
| ::public static Struct merge(Struct struct1, Struct struct2)  | Combines two structs to create a new struct.                                                  |
| public void new(VarArg specifier)                             | Creates a struct.                                                                             |

## Method add

Adds a new item to the struct and assigns the specified value to it.

```xpp
public boolean add(str fieldName, AnyType value)
```

### Parameters - add

fieldName  
The value to assign to the new item. This value defines the type of the item.

<!-- -->

value  
The value to assign to the new item. This value defines the type of the item.

### Return Value - add

true if the value has been added to the struct; false if the value could not be added (if it already existed in the struct).

### Remarks - add

The type of the value is inferred from content of the value. The items in a struct are arranged in alphabetical order according to the item names. The value of an item in a struct can be changed by using the Struct.value or the Struct.valueIndex method.

### Examples - add

The following example creates a struct with two items name and age fields and assigns values to those items. The add method is then used to create an additional item the shoeSize variable, with a value of 43. The type of the value determines the type of the new item, int.

```xpp
{ 
    Struct s = new Struct ("str name; int age"); 
    // Prints number of items (2) 
    print s.fields(); 
    // Values are assigned to the two items 
    s.value("name", "John"); 
    s.value("age", 34); 
    //Another item is added to the struct 
    s.add("shoeSize", 43); 
    // Prints number of item (3) 
    print s.fields(); 
    // Prints a description of the items in the struct 
    print s.definitionString(); 
    pause; 
}
```

## Method definitionString

Returns a description of the names and types of the elements in the struct.

```xpp
public str definitionString()
```

### Return Value - definitionString

A string that contains a definition of the struct.

### Remarks - definitionString

You can use the definitionString method to create a copy of a struct by using the syntax: newStruct = new struct(oldStruct.definitionString());

## Method exists

Determines whether a particular item exists in a struct.

```xpp
public boolean exists(str fieldName)
```

### Parameters - exists

fieldName  
The name of the item to check for.

### Return Value - exists

true if the item exists in the struct; otherwise, false.

### Examples - exists

The following example tests whether a particular item exists in a struct, and if not, it adds the item and assigns a value to it using the Struct.add method.

```xpp
client server static void setProp( 
    Struct     properties, 
    str        name, 
    anytype   value 
    ) 
{ 
    if (! properties.exists(name)) 
    { 
        properties.add(name,nullValue(value)); 
    } 
    properties.value(name,value); 
}
```

## Method fieldName

Returns the name of the item in the struct at the specified position.

```xpp
public str fieldName(int index)
```

### Parameters - fieldName

index  
The position in the struct at which you want to retrieve the item name.

### Return Value - fieldName

The name of the item at the position specified by index.

### Remarks - fieldName

If index is not found, an empty string is returned.

### Examples - fieldName

The following example creates a struct from a container and then uses the Struct.fields method to iterate through the contents of the container. The fieldName method is used to test the name of each item in the struct, and a specific action is run depending on the value of this name.

```xpp
boolean unpack(container packed) 
{ 
    Struct      unpackedProperties; 
    container   structCon; 
    Counter     i; 
    [#currentList,structCon] = packed; 
    unpackedProperties = Struct::create(structCon); 
    for (i=1;i<=unpackedProperties.fields();i++) 
    { 
        switch (unpackedProperties.fieldName(i)) 
        { 
            case #closedOk: 
                break; 
            case #PropertyCaption: 
                if (! dialogForm  
                    || dialogForm  
                    && ! dialogForm.form().design().caption()) 
                    this.caption(unpackedProperties.valueIndex(i)); 
                break; 
            case #dialogFormname: 
                // Do nothing 
                break; 
            case #PropertyAlwaysOnTop: 
                this.alwaysOnTop(unpackedProperties.valueIndex(i)); 
                break; 
            case #PropertyWindowType: 
                this.windowType(unpackedProperties.valueIndex(i)); 
                break; 
            case #defaultButton: 
                this.defaultButton(unpackedProperties.valueIndex(i)); 
                break; 
            default: 
                throw error(strfmt( 
                    "@SYS67326",unpackedProperties.fieldName(i), 
                     classId2Name(classidget(this)))); 
        } 
    } 
    return true; 
}
```

## Method fields

Returns the number of items in the struct.

```xpp
public int fields()
```

### Return Value - fields

The number of items in the struct.

### Remarks - fields

To find the position of an item in a struct, use the Struct.index method.

### Examples - fields

The following example creates a struct from a container and then uses the fields method to iterate through the contents of the container.

```xpp
boolean unpack(container packed) 
{ 
    Struct      unpackedProperties; 
    container   structCon; 
    Counter     i; 
    [#currentList,structCon] = packed; 
    unpackedProperties = Struct::create(structCon); 
    for (i=1;i<=unpackedProperties.fields();i++) 
    { 
        switch (unpackedProperties.fieldName(i)) 
        { 
            case #closedOk: 
                break; 
            case #PropertyCaption: 
                if (! dialogForm  
                    || dialogForm  
                    && ! dialogForm.form().design().caption()) 
                    this.caption(unpackedProperties.valueIndex(i)); 
                break; 
            case #dialogFormname: 
                // Do nothing 
                break; 
            case #PropertyAlwaysOnTop: 
                this.alwaysOnTop(unpackedProperties.valueIndex(i)); 
                break; 
            case #PropertyWindowType: 
                this.windowType(unpackedProperties.valueIndex(i)); 
                break; 
            case #defaultButton: 
                this.defaultButton(unpackedProperties.valueIndex(i)); 
                break; 
            default: 
                throw error(strfmt( 
                    "@SYS67326",unpackedProperties.fieldName(i), 
                     classId2Name(classidget(this)))); 
        } 
    } 
    return true; 
}
```

## Method fieldType

Returns the data type of the item in the struct at the specified position.

```xpp
public Types fieldType(int index)
```

### Parameters - fieldType

index  
The position in the struct that you want to retrieve the data type for.

### Return Value - fieldType

The data type of the item at the position specified by index.

### Remarks - fieldType

The possible values are supplied by the system enum. If index is not found, the return value is Types::void. You can determine the position of a particular item in a struct by using the Struct.index method

## Method index

Calculates the position of an item in the struct based on its name.

```xpp
public int index(str fieldName)
```

### Parameters - index

fieldName  
The name of the item for which to return the position.

### Return Value - index

The position of the item.

### Remarks - index

The items in a struct are arranged in alphabetical order according to the item names. If there is no item with the name fieldName, 0 is returned.

## Method pack

Serializes the current instance of the Struct class.

```xpp
public container pack()
```

### Return Value - pack

A container that contains the current instance of the Struct class.

### Remarks - pack

The pack method is called on each field that holds an object, to yield a (sub) container. The struct may be recreated from the container by using the Struct.create method.

### Examples - pack

The following example creates a struct with two items in it (name and age), and then adds values to the items. The struct is packed into a container, and this container is then used to create a new struct.

```xpp
{  
    container packedStruct;  
    Struct s1, s = new Struct ("str name; int age"); 
    s.value ("name", "Jane Dow");  
    s.value ("age", 34); 
    // Struct is packed into a container 
    packedStruct = s.pack();  
    // A new struct is created from the container 
    s1 = Struct::create(packedStruct); 
    // Both structs have the same contents 
    print s.toString();  
    print s1.toString();  
    pause;  
}
```

## Method remove

Removes an item from a struct.

```xpp
public boolean remove(str fieldName)
```

### Parameters - remove

fieldName  
The name of the item you want to remove.

### Return Value - remove

true if the item was found (and removed); otherwise, false.

### Remarks - remove

The name you specify for the fieldName parameter must be the name of the item as it was specified in the instantiation of the struct or the name of the item as it was added using the Struct.add method. The name must be enclosed in quotes (" ").

### Examples - remove

The following example creates a struct with two items in it and prints a description of these items. One of the items is then removed by using the remove method.

```xpp
{ 
    Struct s = new Struct ("str name; int age"); 
    // Values are assigned to the two items 
    s.value("name", "John"); 
    s.value("age", 34); 
    // Prints a description of the items in the struct 
    print s.definitionString(); 
    pause; 
    // Removes the name field 
    s.remove("name"); 
    // Describes remaining items in the struct 
    print s.definitionString(); 
    pause; 
}
```

## Method toString

Returns a string that describes the contents of the struct.

```xpp
public str toString()
```

### Return Value - toString

A string that describes the contents of the struct.

## Method value

Gets or sets the value for a specified item in a struct.

```xpp
public AnyType value(str fieldName, [AnyType value])
```

### Parameters - value

fieldName  
The value to assign to the item; optional.

<!-- -->

value  
The value to assign to the item; optional.

### Return Value - value

The value of the specified item.

### Remarks - value

An exception is raised if there is no item with the specified name in the struct. The name of an item in a struct may be retrieved by using the Struct.fieldName method. You can add a new item to a struct and assign a value to it at the same time by using the Struct.add method. To assign a new value to an item based on its position in the struct, use the Struct.valueIndex method.

### Examples - value

The following example creates a struct with two items in it and then uses the value method to assign values to those two items.

```xpp
{ 
    Struct s = new Struct ("str name; int age"); 
    // Set the values 
    s.value("name", "Jane Dow"); 
    s.value("age", 34); 
    // Print the values 
    print s.value("name"); 
    print s.value("age"); 
    pause; 
}
```

## Method valueImage

Returns a string that describes the value of the item at a particular position in the struct.

```xpp
public str valueImage(int index)
```

### Parameters - valueImage

index  
The position of the item that you want to return a description for.

### Return Value - valueImage

A string that describes the value of the item.

### Remarks - valueImage

The items in a struct are in alphabetical order according to the names of the items. If there is no item at the position specified by index, an exception is raised.

## Method valueIndex

Gets or sets the value of the item at a specified position in a struct.

```xpp
public AnyType valueIndex(int index, [AnyType value])
```

### Parameters - valueIndex

index  
The value to assign to the item at the position specified by index; optional.

<!-- -->

value  
The value to assign to the item at the position specified by index; optional.

### Return Value - valueIndex

The value of the item at the position specified by index.

### Remarks - valueIndex

An exception is raised if there is no item at the position specified by index. The position of an item in a struct can be retrieved by using the Struct.index method.

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

Creates a struct from a container that is obtained from a prior call to Struct.pack.

```xpp
public static Struct create(container container)
```

### Parameters - create

container  
A container that contains the packed struct.

### Return Value - create

A struct equal to the one that was packed into the specified container.

### Remarks - create

If the struct contains objects, these objects must have an unpack method that is called to re-establish their internal state from the container.

### Examples - create

The following example creates a struct with two items in it (name and age), and then adds values to the items. The struct is packed into a container, and this container is then unpacked to create a new struct.

```xpp
{  
    container packedStruct;  
    Struct s1, s = new Struct ("str name; int age"); 
    s.value ("name", "Jane Dow");  
    s.value ("age", 34); 
    // Struct is packed into a container 
    packedStruct = s.pack();  
    // A new struct is created from the container 
    s1 = Struct::create(packedStruct); 
    // Both structs have the same contents 
    print s.toString();  
    print s1.toString();  
    pause;  
}
```

## Method createFromXML

```xpp
public static Struct createFromXML(Object xmlnode)
```

### Parameters - createFromXML

xmlnode  

### Return Value - createFromXML

## Method equal

Determines whether two structs are equal.

```xpp
public static boolean equal(Struct struct1, Struct struct2)
```

### Parameters - equal

struct1  
The second of the two structs to be compared.

<!-- -->

struct2  
The second of the two structs to be compared.

### Return Value - equal

true if the structs are equal; otherwise, false.

### Remarks - equal

Two structs are equal if they have the same number of fields, the field names are the same, and each field is the same type and has the same value.

## Method merge

Combines two structs to create a new struct.

```xpp
public static Struct merge(Struct struct1, Struct struct2)
```

### Parameters - merge

struct1  
The struct that will be added to the end of the first struct to create a new struct.

<!-- -->

struct2  
The struct that will be added to the end of the first struct to create a new struct.

### Return Value - merge

The new struct.

### Remarks - merge

struct2 is added to the end of struct1. This means that the order of the items in the new struct will be: all the items in struct1, arranged in alphabetical order of the item names, followed by all the items in struct2, arranged in alphabetical order of the item names. If both structs contain an item with the same name, only the item from the first struct will be included.

### Examples - merge

The following example creates two structs called person and address, and then merges them into a new struct called allInfo.

```xpp
{ 
    container packedStruct; 
    Struct person = new Struct ("str name; int age"); 
    Struct address = new Struct ("str street; str city; str country"); 
    Struct allInfo; 
    person.value ("name", "Jane Dow"); 
    person.value ("age", 34); 
    address.value ("street", "Downing street 10"); 
    address.value ("country", "Great Britain"); 
    address.value ("city", " London"); 
    allInfo = Struct::merge(person, address); 
    print allInfo.toString(); 
    pause; 
}
```

## Method new

Creates a struct.

```xpp
public void new(VarArg specifier)
```

### Parameters - new

specifier  
One or more pairs that specify the data type of an item followed by the name of the item as a string.

### Remarks - new

The data type of the item can be specified using the name of a primitive data type or by using the system enum. The items in a struct can be of any of the data types found in the Types system enum, including: string, integer, real, date, container, record, and class. You can create a copy of a struct by using the Struct.definitionString method to create a new struct, as illustrated in the example below. After you have created a struct, you can add new items using the Struct.add method and set the value of items in the struct by using the Struct.value or Struct.valueIndex method.

### Examples - new

The following example creates two structs with the same definition and then adds 2 values and an additional item and value to one of them (s1). This struct is then copied to create a new struct by using the Struct.definitionString method.

```xpp
{ 
    Struct s1, s2, s3; 
    // The two constructors below create the same struct 
    s1 = new Struct(Types::Integer, "age", Types::String, "name"); 
    s2 = new Struct ("int age; str name"); 
    // Print the definitions 
    print s1.definitionString(); 
    print s2.definitionString(); 
    s1.value("age", 25); 
    s1.value("name", "Jane Dow"); 
    // Add a field at runtime 
    s1.add("Shoesize", 45); 
    print s1.definitionString(); 
    print s1.toString(); 
    // Create a container with age, name and shoesize, 
    // using definitionString 
    s3 = new struct(s1.definitionString()); 
    print s3.definitionString(); 
    pause; 
}
```

