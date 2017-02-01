---
# required metadata

title: A Classes | Microsoft Docs
description: System API classes that start with the letter A.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-12 18:13:52
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: a:2:{s:4:"name";s:22:"Robin Reynolds-Haertle";s:2:"id";s:0:"";}
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 47561
ms.assetid: b8e6715d-aa2c-449e-ad9a-34f26cc59090
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# A Classes

System API classes that start with the letter A.

Class AbsoluteFieldBinding
--------------------------

    class AbsoluteFieldBinding extends FieldBinding

### Remarks

### Examples

### Methods

| Method                                                                            | Description                                                   |
|-----------------------------------------------------------------------------------|---------------------------------------------------------------|
| ::public static AbsoluteFieldBinding construct(str fieldName, str tableName)      |                                                               |
| ::public static AbsoluteFieldBinding create(container packedAbsoluteFieldBinding) |                                                               |
| private void new()                                                                | Initializes a new instance of the AbsoluteFieldBinding class. |

### Method construct

    public static AbsoluteFieldBinding construct(str fieldName, str tableName)

#### Parameters

fieldName  

<!-- -->

tableName  

#### Return Value

### Method create

    public static AbsoluteFieldBinding create(container packedAbsoluteFieldBinding)

#### Parameters

packedAbsoluteFieldBinding  

#### Return Value

### Method new

Initializes a new instance of the AbsoluteFieldBinding class.

    private void new()

## Class AdObject
    class AdObject extends Object

### Remarks

### Examples

### Methods

| Method                             | Description                                     |
|------------------------------------|-------------------------------------------------|
| public boolean found()             |                                                 |
| public str getValue(str attribute) |                                                 |
| public void new(str osUserName)    | Initializes a new instance of the Object class. |

### Method found

    public boolean found()

#### Return Value

### Method getValue

    public str getValue(str attribute)

#### Parameters

attribute  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(str osUserName)

#### Parameters

osUserName  

## Class AllowEncryptionKeyRetrievalPermission
    class AllowEncryptionKeyRetrievalPermission extends CodeAccessPermission

### Remarks

### Examples

### Methods

| Method                                                 | Description                                                                                                               |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                                  |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class. |
| public void new()                                      | Initializes a new instance of the AllowEncryptionKeyRetrievalPermission class.                                            |

### Method copy

Creates and returns a copy of a permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the derived class object.

#### Remarks

You can override this method as part of the process of making an API more secure. For more information, see ‘Securing an API that Executes on the Server Tier.’

### Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if a current permission is a subset of a specified permission; otherwise, false.

#### Remarks

You can override the method as part of the process of making an API more secure. For more information, see ‘Securing an API that Executes on the Server Tier.’

### Method new

Initializes a new instance of the AllowEncryptionKeyRetrievalPermission class.

    public void new()

## Class AOSLoadGen
    class AOSLoadGen extends Object

### Remarks

### Examples

### Methods

| Method                                                     | Description                                  |
|------------------------------------------------------------|----------------------------------------------|
| public boolean spawnClass(ClassId classId, str parm)       |                                              |
| public boolean spawnJob(UtilElementName jobName, str parm) |                                              |
| public void new(\[UserId user\], \[ClassId infoClass\])    | Creates an instance of the AOSLoadGen class. |

### Method spawnClass

    public boolean spawnClass(ClassId classId, str parm)

#### Parameters

classId  

<!-- -->

parm  

#### Return Value

### Method spawnJob

    public boolean spawnJob(UtilElementName jobName, str parm)

#### Parameters

jobName  

<!-- -->

parm  

#### Return Value

### Method new

Creates an instance of the AOSLoadGen class.

    public void new([UserId user], [ClassId infoClass])

#### Parameters

user  
The information class that is used to create the instance of the AOSLoadGen class. The default value is info.

<!-- -->

infoClass  
The information class that is used to create the instance of the AOSLoadGen class. The default value is info.

#### Remarks

Control of the input to the new method could be a security risk. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

## Class AOSSessionInfo
    class AOSSessionInfo extends Object

The AOSSessionInfo class is used to provide information about a session for Microsoft Dynamics AX Application Object Server (AOS).

### Remarks

### Examples

### Methods

| Method                             | Description                                                               |
|------------------------------------|---------------------------------------------------------------------------|
| public AOSClientMode clientMode()  | Returns the client mode for the AOS session.                              |
| public int cpuTime()               | Returns the number of milliseconds that the CPU uses for the AOS session. |
| public int idleTicks()             | Returns the number of milliseconds since the last communication with AOS. |
| public int sessionId()             | Returns the ID of the AOS session.                                        |
| public void new(\[int sessionId\]) | Creates an instance of the AOSSessionInfo class.                          |

### Method clientMode

Returns the client mode for the AOS session.

    public AOSClientMode clientMode()

#### Return Value

The client mode for the AOS session.

### Method cpuTime

Returns the number of milliseconds that the CPU uses for the AOS session.

    public int cpuTime()

#### Return Value

The number of milliseconds that the CPU uses for the AOS session.

### Method idleTicks

Returns the number of milliseconds since the last communication with AOS.

    public int idleTicks()

#### Return Value

The number of milliseconds since the last communication with AOS.

### Method sessionId

Returns the ID of the AOS session.

    public int sessionId()

#### Return Value

The ID of the AOS session.

### Method new

Creates an instance of the AOSSessionInfo class.

    public void new([int sessionId])

#### Parameters

sessionId  
The session ID that is used to create the instance of the AOSSessionInfo class. If a session ID is not specified, the current session is used; optional.

## Class AOTTableFieldList
    class AOTTableFieldList extends TreeNode

The AOTTableFieldList class represents the Fields node of a table and is also used to add fields to a table.

### Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. The developer can obtain general information on the node by using other methods.

### Examples

The following example adds a field of the enum type to the TutorialJournalName table.

    { 
        AOTTableFieldList tfl = infolog.findNode( 
            '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
     
         if (!tfl.AOTFindChild('NewEnum')) 
         { 
             tfl.addEnum('NewEnum');  // Adds the field NewEnum. 
         } 
    }

### Methods

| Method                             | Description                                                                         |
|------------------------------------|-------------------------------------------------------------------------------------|
| public void addInteger(str name)   | Adds a new field of the integer type to the list of fields for the current table.   |
| public void addGuid(str name)      |                                                                                     |
| public void addContainer(str name) | Adds a new field of the container type to the list of fields for the current table. |
| public void addInt64(str name)     |                                                                                     |
| public void addDateTime(str name)  |                                                                                     |
| public void addDate(str name)      | Adds a new field of the date type to the list of fields for the current table.      |
| public void addString(str name)    | Adds a new field of the string type to the list of fields for the current table.    |
| public void addReal(str name)      | Adds a new field of the real type to the list of fields for the current table.      |
| public void addTime(str name)      | Adds a new field of the time type to the list of fields for the current table.      |
| public void addEnum(str name)      | Adds a new field of the enum type to the list of fields for the current table.      |

### Method addInteger

Adds a new field of the integer type to the list of fields for the current table.

    public void addInteger(str name)

#### Parameters

name  
The name of the field to add.

#### Remarks

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. The developer must make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

#### Examples

The following code example adds the NewInteger field, which is of the integer type, to the list of fields for the TutorialJournalName table.

    AOTTableFieldList tfl = infolog.findNode( 
        '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
    if (!tfl.AOTFindChild('NewInteger')) 
    { 
        tfl.addInteger('NewInteger'); 
    }

### Method addGuid

    public void addGuid(str name)

#### Parameters

name  

### Method addContainer

Adds a new field of the container type to the list of fields for the current table.

    public void addContainer(str name)

#### Parameters

name  
The name of the field to add.

#### Remarks

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. The developer must make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

#### Examples

The following code example adds the NewContainer and NewContainer1 fields, which are both of the container type, to the list of fields of the TutorialJournalName table.

    AOTTableFieldList tfl = infolog.findNode( 
        '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
     
    // Add a NewContainer field. 
    tfl.addContainer('NewContainer'); 
     
    // Add a NewContainer1 field. 
    tfl.addContainer('NewContainer');

### Method addInt64

    public void addInt64(str name)

#### Parameters

name  

### Method addDateTime

    public void addDateTime(str name)

#### Parameters

name  

### Method addDate

Adds a new field of the date type to the list of fields for the current table.

    public void addDate(str name)

#### Parameters

name  
The name of the field to add.

#### Remarks

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. The developer must make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

#### Examples

The following code example adds the NewDate field, which is of the date type, to the list of fields for the TutorialJournalName table.

    AOTTableFieldList tfl = infolog.findNode( 
        '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
    if (!tfl.AOTFindChild('NewDate')) 
    { 
        tfl.addDate('NewDate'); 
    }

### Method addString

Adds a new field of the string type to the list of fields for the current table.

    public void addString(str name)

#### Parameters

name  
The name of the field to add.

#### Remarks

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. It is up to the developer to make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

#### Examples

The following example adds the NewString field, which is of the string type, to the list of fields for the TutorialJournalName table.

    { 
        AOTTableFieldList tfl = infolog.findNode( 
            '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
        if (!tfl.AOTFindChild('NewString')) 
        { 
            tfl.addString('NewString'); 
        } 
    }

### Method addReal

Adds a new field of the real type to the list of fields for the current table.

    public void addReal(str name)

#### Parameters

name  
The name of the field to add.

#### Remarks

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. It is up to the developer to make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

#### Examples

The following example adds the NewReal and NewReal1 fields, which is of the real type, to the list of fields for the TutorialJournalName table.

    AOTTableFieldList tfl = infolog.findNode( 
        '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
    // Add the field NewReal. 
    tfl.addReal('NewReal'); 
    // Add the field NewReal1. 
    tfl.addReal('NewReal');

### Method addTime

Adds a new field of the time type to the list of fields for the current table.

    public void addTime(str name)

#### Parameters

name  
The name of the field to add.

#### Remarks

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. The developer must make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

#### Examples

The following code example adds the NewTime field, which is of the time type, to the list of fields of the TutorialJournalName table.

    AOTTableFieldList tfl = infolog.findNode( 
        '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
    if (!tfl.AOTFindChild('NewTime')) 
    { 
        tfl.addTime('NewTime'); 
    }

### Method addEnum

Adds a new field of the enum type to the list of fields for the current table.

    public void addEnum(str name)

#### Parameters

name  
The name of the field to add.

#### Remarks

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. It is up to the developer to make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

#### Examples

The following example adds the NewEnum field, which is of the enum type, to the list of fields of the TutorialJournalName table.

    AOTTableFieldList tfl = infolog.findNode( 
        '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
    if (!tfl.AOTFindChild('NewEnum')) 
    { 
        tfl.addEnum('NewEnum');  // adds the field NewEnum 
    }

## Class ApplicationObjectTreeWindow
    class ApplicationObjectTreeWindow extends Object

### Remarks

### Examples

### Methods

| Method                                  | Description                                                          |
|-----------------------------------------|----------------------------------------------------------------------|
| public str getSelectedNodeModelName()   |                                                                      |
| public Set getSelectedNodes()           |                                                                      |
| public Set getSelectedNodesPaths()      |                                                                      |
| public boolean isSelectedNodeExpanded() |                                                                      |
| private void new()                      | Initializes a new instance of the ApplicationObjectTreeWindow class. |

### Method getSelectedNodeModelName

    public str getSelectedNodeModelName()

#### Return Value

### Method getSelectedNodes

    public Set getSelectedNodes()

#### Return Value

### Method getSelectedNodesPaths

    public Set getSelectedNodesPaths()

#### Return Value

### Method isSelectedNodeExpanded

    public boolean isSelectedNodeExpanded()

#### Return Value

### Method new

Initializes a new instance of the ApplicationObjectTreeWindow class.

    private void new()

## Class Array
    class Array extends Object

### Remarks

Arrays can hold values of any single type, such as objects and records (contrary to the array data type that is built into the X++ language). Objects of this type can be transferred to functions and methods. The values are stored sequentially. The arrays expand as required. Therefore, no specific dimension of the array is supplied.

### Examples

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

### Methods

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

### Method definitionString

Returns a string that contains the definition of the array.

    public str definitionString()

#### Return Value

A string that contains the definition of the array.

#### Examples

The following example creates an array of classes and then adds three query objects to the array. It uses the definitionString method to print a definition of the array.

    { 
        Array oarray = new Array (Types::Class); 
     
        oarray.value(1, new query()); 
        oarray.value(2, new query()); 
        oarray.value(4, new query());  
        print oarray.definitionString(); 
        pause; 
    }

### Method exists

Determines whether a particular array element is valid.

    public boolean exists(int index)

#### Parameters

index  
The array element to test.

#### Return Value

true if the array element that is pointed to by the index is valid; otherwise, false.

#### Examples

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

### Method lastIndex

Retrieves the highest index that is used to store a value in the array.

    public int lastIndex()

#### Return Value

An integer that represents the highest index that is used to store a value.

#### Examples

The following example uses the lastIndex method to find the last element in the array and then add a new value after this element.

    { 
        Array myArray = new Array(Types::Integer); 
        int newValue; 
     
        // Other code - values are added to myArray 
        // and a value is assigned to newValue 
      
        myArray.value(myArray.lastIndex()+1, newValue); 
    }

### Method pack

Serializes the current instance of the Array class.

    public container pack()

#### Return Value

A container that contains the current instance of the Array class.

#### Remarks

The container created by this method contains three elements before the first element from the array:

-   A version number for the container.
-   An integer that identifies the data type of the array elements.
-   The number of elements in the array.

If the values of the array are objects, the pack method is called on each object to yield a subcontainer.

#### Examples

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

### Method toString

Returns a string that describes the contents of the array.

    public str toString()

#### Return Value

A string that describes the contents of the array.

#### Examples

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

### Method typeId

Returns the data type of the values in the array.

    public Types typeId()

#### Return Value

The data type of the elements in the array.

#### Remarks

The type remains the same throughout the life of the array. The type is specified when the array is created.

#### Examples

The following example tests whether a particular array element exists. If it does not exist, the typeId method is used to specify the type of the new value that should be added to the array.

    public anytype getArrayValue(Array a, int _index) 
    { 
        if (! a.exists(_index)) 
        { 
            a.value(_index,nullValueFromType(a.typeId())); 
        } 
      
        return a.value(_index); 
    }

### Method value

Gets or sets the value of the array element that is stored at the specified index.

    public AnyType value(int index, [AnyType arg])

#### Parameters

index  
The value to assign to the array element at the specified offset; optional.

<!-- -->

arg  
The value to assign to the array element at the specified offset; optional.

#### Return Value

The value that is stored at the specified offset.

#### Remarks

The return type is the same as the type of the array. If an attempt is made to read a value at an index that is beyond the last index that has a value, an exception is thrown. If a value is written to a nonexistent location, all locations between the previous element and the nonexistent location are filled with default values, and the array is expanded.

#### Examples

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

### Method xml

Returns an XML string that represents the current object.

    public str xml([int indent])

#### Parameters

indent  
The amount of indentation of the returned XML string; optional.

#### Return Value

An XML string that represents the current object.

#### Remarks

This method can be overridden to return values that are meaningful for a particular type.

### Method create

Creates an array from the container that is obtained from a previous call to the Array.pack method.

    public static Array create(container container)

#### Parameters

container  
A container that is created by using the Array.pack method. The container is unpacked to create an array.

#### Return Value

An array that holds the contents of the specified container.

#### Remarks

If the values in the array are objects, the objects must have an Array.unpack method that is called to reestablish their internal state from a container.

#### Examples

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

### Method createFromXML

    public static Array createFromXML(Object xmlnode)

#### Parameters

xmlnode  

#### Return Value

### Method new

Creates an array in which each element has the specified type.

    public void new(Types Type)

#### Parameters

Type  
The data type of the array elements.

#### Remarks

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

#### Examples

The following example creates an array of integers.

    Array intArray = new Array(Types::Integer);

## Class AsciiIo
    class AsciiIo extends CommaIo

The AsciiIo class provides functionality for reading and writing ASCII files.

### Remarks

The TextIo class provides functionality for reading and writing files that use various code pages. The AsciiIO class supports only ANSI code page (ACP) characters. Existing code that uses the AsciiIO class must be converted to use the TextIO class if the file contains non-ACP characters, or if it is a file that is used only in Microsoft Dynamics AX, such as an .xpo file.

### Examples

### Methods

| Method                                       | Description                                                                                                                      |
|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| public str inFieldDelimiter(\[str value\])   | Sets or retrieves the character that is used as the field delimiter of an input file that is represented by an AsciiIO object.   |
| public str inRecordDelimiter(\[str value\])  | Sets or retrieves the character that is used as the record delimiter of an input file that is represented by an AsciiIO object.  |
| public int inRecordLength(\[int value\])     | Sets or retrieves the record length for an input file.                                                                           |
| public str outFieldDelimiter(\[str value\])  | Sets or retrieves the character that is used as the field delimiter of an output file that is represented by an AsciiIO object.  |
| public str outRecordDelimiter(\[str value\]) | Sets or retrieves the character that is used as the record delimiter of an output file that is represented by an AsciiIO object. |
| public container read()                      | Reads the next full record from the Io object.                                                                                   |
| public IO\_Status status()                   | Returns the status of the last operation on the file.                                                                            |
| public boolean write(VarArg values)          | Writes values of a simple type.                                                                                                  |
| public boolean writeChar(int int)            |                                                                                                                                  |
| public boolean writeExp(container data)      | Writes the content of a container to a file.                                                                                     |
| public boolean writeRaw(str data)            |                                                                                                                                  |
| public void finalize()                       | Closes the file and then flushes the file buffers to disk.                                                                       |
| public void new(str filename, str mode)      | Creates an instance of the AsciiIo class.                                                                                        |

### Method inFieldDelimiter

Sets or retrieves the character that is used as the field delimiter of an input file that is represented by an AsciiIO object.

    public str inFieldDelimiter([str value])

#### Parameters

value  
The character to assign as the field delimiter.

#### Return Value

The character that is used as the field delimiter.

### Method inRecordDelimiter

Sets or retrieves the character that is used as the record delimiter of an input file that is represented by an AsciiIO object.

    public str inRecordDelimiter([str value])

#### Parameters

value  
The character to assign as the record delimiter.

#### Return Value

The character that is used as the record delimiter.

#### Remarks

For standard text, the delimiter is a newline character.

### Method inRecordLength

Sets or retrieves the record length for an input file.

    public int inRecordLength([int value])

#### Parameters

value  
The value to assign as the record length for the input file.

#### Return Value

The record length for the input file.

#### Remarks

For files that have a fixed-length format, use the inRecordLength property to guarantee that no more than the specified number of characters is read for each record. If the record format is overruled by a specified inRecordDelimiter property value (in other words, if the inRecordDelimiter value is met before the fixed length is read), the record is accepted, and no more data is read. To make sure that a fixed number of characters is read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to 0 (zero) to disable the check of the record length.

### Method outFieldDelimiter

Sets or retrieves the character that is used as the field delimiter of an output file that is represented by an AsciiIO object.

    public str outFieldDelimiter([str value])

#### Parameters

value  
The character to assign as the field delimiter.

#### Return Value

The character that is used as the field delimiter.

### Method outRecordDelimiter

Sets or retrieves the character that is used as the record delimiter of an output file that is represented by an AsciiIO object.

    public str outRecordDelimiter([str value])

#### Parameters

value  
The character to assign as the record delimiter.

#### Return Value

The character that is used as the record delimiter.

#### Remarks

For standard text files, the delimiter is a newline character.

### Method read

Reads the next full record from the Io object.

    public container read()

#### Return Value

The next full record from the Io object.

#### Remarks

The definition of the next full record is controlled by the following properties: inFieldDelimiter, inRecordDelimiter, and inRecordLength. The record is returned as a container. Each entry in the container represents one field in the record. Each of the specialized Io classes has default settings for inFieldDelimiter, inRecordDelimiter, and inRecordLength. These settings allow for input and output of the most common formats. However, you might have to adjust these settings to support the desired format.

### Method status

Returns the status of the last operation on the file.

    public IO_Status status()

#### Return Value

The status of the last file operation.

### Method write

Writes values of a simple type.

    public boolean write(VarArg values)

#### Parameters

values  
One or more values, each of a simple type, separated by a field delimiter. The simple types are string, integer, real, enum, and date.

#### Return Value

true if the write operation succeeds; otherwise, false. If the write operation fails, you can check the status to learn the cause.

#### Remarks

The method accepts a variable number of arguments. Each value that is specified is put into the output record as a field: the first argument as the first field, the second argument as the second field, and so on. Fields are separated by the delimiter that is specified in the outFieldDelimiter method. Records are separated by the delimiter that is specified in the outRecordDelimiter method. To write complete containers, use the writeExp method.

### Method writeChar

    public boolean writeChar(int int)

#### Parameters

int  

#### Return Value

### Method writeExp

Writes the content of a container to a file.

    public boolean writeExp(container data)

#### Parameters

data  
The container that holds data for the record.

#### Return Value

true if the operation succeeds; otherwise, false. If the operation fails, check the status to learn the cause.

#### Remarks

The entries in the container are treated as fields. The container is treated as a full record. Fields are separated by the delimiter that is specified in the outFieldDelimiter method. Records are separated by the delimiter that is specified in the outRecordDelimiter method.

### Method writeRaw

    public boolean writeRaw(str data)

#### Parameters

data  

#### Return Value

### Method finalize

Closes the file and then flushes the file buffers to disk.

    public void finalize()

#### Remarks

An AsciiIo object is usually finalized after its scope has ended. This method is not usually called directly. Output that is written to the file is not valid until the AsciiIo object is finalized.

### Method new

Creates an instance of the AsciiIo class.

    public void new(str filename, str mode)

#### Parameters

filename  
The mode to use to create this instance of the AsciiIo class.

<!-- -->

mode  
The mode to use to create this instance of the AsciiIo class.

#### Remarks

If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the FileIOPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

The following example uses the AsciiIo class to read from a text file.

    void AsciiIoExample() 
    { 
        AsciiIo asciiIo; 
        container con; 
        FileIoPermission perm; 
      
        #define.ExampleFile(@"c:\test.txt") 
        #define.ExampleOpenMode("r") 
         
        // The AsciiIo.new method runs under code access permission. 
        perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
        if (perm == null) 
        { 
            return; 
        } 
      
        // Code access permission scope starts here. 
         perm.assert(); 
      
         asciiIo = new AsciiIo(#ExampleFile, #ExampleOpenMode); 
        if (asciiIo != null) 
        { 
              con = asciiIo.read(); 
        } 
        // Closes the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

## Class AssemblyDeployManager
    class AssemblyDeployManager extends Object

The AssemblyDeployManager class lets you deploy the assemblies that are stored in the AOT Visual Studio Projects to the AOS VSAssemblies folder that can be used by the X++ runtime during .NET calls.

### Remarks

### Examples

### Methods

| Method                                                        | Description                                                                                             |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| ::public static boolean isHotswappingEnabled()                | Returns a Boolean value that indicates whether hot swapping is enabled.                                 |
| ::public static void deployAssemblyFromPath(str assemblyPath) |                                                                                                         |
| ::public static void removeAssemblyFromPath(str assemblyPath) | Removes one specific assembly that is marked for deployment to the server from the VSAssemblies folder. |
| ::public static void deployAssemblies()                       | Deploys one specific assembly that is marked for deployment to server to the VSAssemblies folder.       |

### Method isHotswappingEnabled

Returns a Boolean value that indicates whether hot swapping is enabled.

    public static boolean isHotswappingEnabled()

#### Return Value

A Boolean value that indicates whether hot swapping is enabled.

### Method deployAssemblyFromPath

    public static void deployAssemblyFromPath(str assemblyPath)

#### Parameters

assemblyPath  

### Method removeAssemblyFromPath

Removes one specific assembly that is marked for deployment to the server from the VSAssemblies folder.

    public static void removeAssemblyFromPath(str assemblyPath)

#### Parameters

assemblyPath  
The Visual Studio Project path where the assembly is stored.

### Method deployAssemblies

Deploys one specific assembly that is marked for deployment to server to the VSAssemblies folder.

    public static void deployAssemblies()

## Class AsyncTaskResult
    class AsyncTaskResult extends Object

### Remarks

### Examples

### Methods

| Method                                                                               | Description |
|--------------------------------------------------------------------------------------|-------------|
| public container getResult()                                                         |             |
| public System.Exception getException()                                               |             |
| public container getInfologData()                                                    |             |
| public container getAsyncState()                                                     |             |
| ::public static AsyncTaskResult getAsyncTaskResult(System.Threading.Tasks.Task task) |             |

### Method getResult

    public container getResult()

#### Return Value

### Method getException

    public System.Exception getException()

#### Return Value

### Method getInfologData

    public container getInfologData()

#### Return Value

### Method getAsyncState

    public container getAsyncState()

#### Return Value

### Method getAsyncTaskResult

    public static AsyncTaskResult getAsyncTaskResult(System.Threading.Tasks.Task task)

#### Parameters

task  

#### Return Value

## Class AxaptaCOMConnectorMonitor
    class AxaptaCOMConnectorMonitor extends Object

Microsoft internal use only.

### Remarks

### Examples

### Methods

| Method                                     | Description                                                        |
|--------------------------------------------|--------------------------------------------------------------------|
| public int getBufferCount()                |                                                                    |
| public str getCOMRegistration()            |                                                                    |
| public int getContainerCount()             |                                                                    |
| public int getLoggedOnAxaptaObjectCount()  |                                                                    |
| public int getObjectCount()                |                                                                    |
| public int getRecordCount()                |                                                                    |
| public int getReferenceCount()             |                                                                    |
| public boolean isAxaptaCOMConnector()      |                                                                    |
| public boolean isAxaptaInternetConnector() |                                                                    |
| public void finalize()                     | Microsoftinternal use only.                                        |
| public void new()                          | Initializes a new instance of the AxaptaCOMConnectorMonitor class. |

### Method getBufferCount

    public int getBufferCount()

#### Return Value

### Method getCOMRegistration

    public str getCOMRegistration()

#### Return Value

### Method getContainerCount

    public int getContainerCount()

#### Return Value

### Method getLoggedOnAxaptaObjectCount

    public int getLoggedOnAxaptaObjectCount()

#### Return Value

### Method getObjectCount

    public int getObjectCount()

#### Return Value

### Method getRecordCount

    public int getRecordCount()

#### Return Value

### Method getReferenceCount

    public int getReferenceCount()

#### Return Value

### Method isAxaptaCOMConnector

    public boolean isAxaptaCOMConnector()

#### Return Value

### Method isAxaptaInternetConnector

    public boolean isAxaptaInternetConnector()

#### Return Value

### Method finalize

Microsoftinternal use only.

    public void finalize()

### Method new

Initializes a new instance of the AxaptaCOMConnectorMonitor class.

    public void new()

