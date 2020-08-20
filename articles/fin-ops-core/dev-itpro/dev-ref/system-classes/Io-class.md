---
title: Io class
description: This topic describes the Io class.
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

# Class Io

[!include [banner](../../includes/banner.md)]

```xpp
class Io extends Object
```

The Io class serves as the base class for the format-specific Io classes, which are used to access external files.

## Remarks

The basic Io class features no actual data I/O but works as base class for the format-specific Io classes. The methods that are common to all Io classes are described here. For format-specific features and behavior of the member functions, refer to the documentation for each of the I/O classes. To support reading and writing of different formats of external files, MorphX features a range of different Io classes for comma-separated files, for comma-separated 7 bit files, for binary files, and for plain-text files.

## Examples

## Methods

| Method                                       | Description                                                                                                                  |
|----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| public str inFieldDelimiter(\[str value\])   | Determines the delimiter used to separate fields in records accessed by the \*Io classes.                                    |
| public str inRecordDelimiter(\[str value\])  | Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.  |
| public int inRecordLength(\[int value\])     | Gets or sets the number of characters to read for each record in a file.                                                     |
| public str outFieldDelimiter(\[str value\])  | Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.          |
| public str outRecordDelimiter(\[str value\]) | Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files. |
| public container read()                      | Reads the next full record from the Io object.                                                                               |
| public IO\_Status status()                   | Retrieves the status of the last operation performed on the Io object.                                                       |
| public boolean write(VarArg values)          | Writes values of a simple type.                                                                                              |
| public boolean writeExp(container data)      | Writes the content of a container to the file.                                                                               |
| public void finalize()                       | Closes the file and, if data was written, flushes the file buffers to disk.                                                  |
| public void new(str filename, str mode)      | Creates a new instance of the Io class.                                                                                      |

## Method inFieldDelimiter

Determines the delimiter used to separate fields in records accessed by the \*Io classes.

```xpp
public str inFieldDelimiter([str value])
```

### Parameters - inFieldDelimiter

value  

### Return Value - inFieldDelimiter

The delimiter used to separate fields in records accessed by the \*Io classes.

## Method inRecordDelimiter

Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.

```xpp
public str inRecordDelimiter([str value])
```

### Parameters - inRecordDelimiter

value  

### Return Value - inRecordDelimiter

The character or characters that indicate whether a full record has been read.

### Remarks - inRecordDelimiter

For standard text, the delimiter is a newline character.

## Method inRecordLength

Gets or sets the number of characters to read for each record in a file.

```xpp
public int inRecordLength([int value])
```

### Parameters - inRecordLength

value  

### Return Value - inRecordLength

The number of characters to read for each record in the file.

### Remarks - inRecordLength

For files that have a fixed-length format, use the inRecordLength property to guarantee that no more than the specified number of characters are read for each record. If the record format is overruled by a specified inRecordDelimiter property value , that is the inRecordDelimiter value is met before the fixed length is read, the record is accepted, and no additional data is read. To guarantee that a fixed number of characters are read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to zero to disable the record length check.

## Method outFieldDelimiter

Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.

```xpp
public str outFieldDelimiter([str value])
```

### Parameters - outFieldDelimiter

value  

### Return Value - outFieldDelimiter

The sequence of characters that are written to a file that is used to separate the fields of a record.

## Method outRecordDelimiter

Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files.

```xpp
public str outRecordDelimiter([str value])
```

### Parameters - outRecordDelimiter

value  

### Return Value - outRecordDelimiter

The sequence of characters that is written to the output files.

### Remarks - outRecordDelimiter

For standard text files, the delimiter is a newline character.

## Method read

Reads the next full record from the Io object.

```xpp
public container read()
```

### Return Value - read

A container that holds the next full record from the Io object.

### Remarks - read

The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength method properties. The record is returned as a container. Each entry in the container equals one field in the record. Each of the specialized Io classes has default settings for inFieldDelimiter, inRecordDelimiter, and inRecordLength enabling input and output of the most common formats. You might have to adjust these to support the wanted format.

### Examples - read

This method demonstrates the use of the run method. However, the following example will not compile in a job as it must be run in the context of a class, form, or other object.

```xpp
static void Job1(Args _args) 
{ 
    FileIoPermission _perm; 
    AsciiIo myfileio; 
    Container c; 
    _perm = new FileIoPermission("myfile.txt","r"); 
    myfileio = new AsciiIo("myfile.txt","r"); 
    while(myfileio.status()==IO_Status::OK) 
    { 
        c = myfileio.read(); 
        // ...do something with the container 
    } 
}
```

## Method status

Retrieves the status of the last operation performed on the Io object.

```xpp
public IO_Status status()
```

### Return Value - status

The status of the last operation, as an IO\_Status system enumeration value.

### Remarks - status

The range of possible IO\_Status values returned varies among Io Classes.

### Examples - status

```xpp
static void myExample(Args _args) 
{ 
    Io myIo; 
    //.. create io object and perform some operations 
    if (myIo.status()==IO_Status::OK) 
    { 
        // ...go ahead - last operation was successful 
    } 
}
```

## Method write

Writes values of a simple type.

```xpp
public boolean write(VarArg values)
```

### Parameters - write

values  
The simple types are string, integer, real, enum, and date.

### Return Value - write

true if the write operation succeeds; otherwise false. If the write failed, the status method could be checked for the cause.

### Remarks - write

The method accepts a variable number of arguments. Each value specified is put into the output record as a field. The first argument as the first field, the second argument as the second field, and so on. The fields are separated with the field delimiter that is specified in the outFieldDelimiter method. Each record is separated by the outRecordDelimiter method. To write complete containers, use the writeExp method.

## Method writeExp

Writes the content of a container to the file.

```xpp
public boolean writeExp(container data)
```

### Parameters - writeExp

data  
The container with data for the record.

### Return Value - writeExp

true if the operation succeeded; otherwise false.

### Remarks - writeExp

If this method returns false, check the status method for the cause. The entries in the container are treated as fields, and the container is treated as a full record. The field separator is defined in the outFieldDelimiter method. The record separator is defined in the outRecordDelimiter method.

### Examples - writeExp

```xpp
static void testMethod(Args _args) 
{ 
    FileIOPermission _perm; 
    container c; 
    CommaIo myfile; 
    _perm = new FileIOPermission("myfile.txt","w"); 
    _perm.assert(); 
    myfile = new CommaIo("myfile.txt","w"); 
    // Assign the entries in the container according to record layout. 
    c = [1,"MyText",1.324,"Last field"]; 
    // write this record according to file format (record/field delimiters). 
    myfile.writeExp(c); 
}
```

## Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

```xpp
public void finalize()
```

### Remarks - finalize

The object is typically finalized by leaving the scope, so finalize is typically not called directly. Written output will not be valid before the object is finalized.

## Method new

Creates a new instance of the Io class.

```xpp
public void new(str filename, str mode)
```

### Parameters - new

filename  
The mode in which the file should be opened.

<!-- -->

mode  
The mode in which the file should be opened.

### Remarks - new

The mode parameter can be one of the following modes:

-   R � read
-   W � write
-   A � append (implies W)
-   T � translate (text)
-   B � binary

A run-time error occurs if the file is accessed with a method that does not correspond to the current opened mode (for example, if an attempt is made to write to a read-mode file). If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. . Ensure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - new

This example uses the Io class to write to ExampleFile.

```xpp
void IoExample() 
{ 
    Io io; 
    container con; 
    FileIoPermission perm; 
    #define.ExampleFile(@"c:\test.txt") 
    #define.ExampleOpenMode("w") 
    // Grants permission to execute the 
    // Io.new method. 
    // Io.new runs under code access security. 
    perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
    if (perm == null) 
    { 
        return; 
    } 
    perm.assert(); 
    io = new Io(#ExampleFile, #ExampleOpenMode); 
    if (io != null) 
    { 
        io.write("Test"); 
    } 
    // Close the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```


