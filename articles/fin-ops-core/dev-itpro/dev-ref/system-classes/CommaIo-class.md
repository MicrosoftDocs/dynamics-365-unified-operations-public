---
title: CommaIo class
description: This topic describes the CommaIo class.
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

# Class CommaIo

[!include [banner](../../includes/banner.md)]

```xpp
class CommaIo extends Io
```

The CommaIo class provides functionality for reading and writing comma-separated files.

## Remarks

This class has been replaced by the CommaTextIo class.

## Examples

## Methods

| Method                                       | Description                                                                                                                  |
|----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| public int filePosition()                    |                                                                                                                              |
| public str inFieldDelimiter(\[str value\])   | Determines the delimiter used to separate fields in records accessed by the \*Io classes.                                    |
| public str inRecordDelimiter(\[str value\])  | Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.  |
| public int inRecordLength(\[int value\])     | Gets or sets the number of characters to read for each record in a file.                                                     |
| public str outFieldDelimiter(\[str value\])  | Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.          |
| public str outRecordDelimiter(\[str value\]) | Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files. |
| public container read()                      | Reads the next full record from the Io object.                                                                               |
| public IO\_Status status()                   | Retrieves the status of the last operation that was performed on the Io object.                                              |
| public boolean write(VarArg values)          | Writes values of a simple type.                                                                                              |
| public boolean writeExp(container data)      | Writes the content of a container to a file.                                                                                 |
| public void new(str filename, str mode)      | Creates a new object of the CommaIo class.                                                                                   |
| public void finalize()                       | Closes the file and, if data was written, flushes the file buffers to disk.                                                  |

## Method filePosition

```xpp
public int filePosition()
```

### Return Value - filePosition

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

For files that have a fixed-length format, use the inRecordLength property to guarantee that no more than the specified number of characters are read for each record. If the record format is overruled by a specified inRecordDelimiter property value , that is the inRecordDelimiter value is met before the fixed length is read, the record is accepted, and no additional data is read. To ensure that a fixed number of characters are read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to zero to disable the record length check.

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

The next full record from the Io object.

### Remarks - read

The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties. The record is returned as a container. Each entry in the container equals one field in the record. Each specialized Io class has default settings for the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties to enable input and output in the most common formats. However, you might have to adjust these settings to support the desired format.

## Method status

Retrieves the status of the last operation that was performed on the Io object.

```xpp
public IO_Status status()
```

### Return Value - status

The status of the last operation, in the form of a system enumeration.

### Remarks - status

The return value is represented by the IO\_Status system enumeration. The range of possible IO\_Status values varies among Io classes.

### Examples - status

This example shows how to use the status method. However, this example will not compile in a job, because it must be run in the context of a class, form, or other object.

```xpp
{ 
    // Create an Io object and perform some operations. 
    if (myIo.status() == IO_Status::OK) 
    { 
        // Go ahead - the last operation was successful. 
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
One or more values, each of a simple type, separated by a field delimiter. The simple types are string, integer, real, enum, and date.

### Return Value - write

true if the write operation succeeds; otherwise, false. If the operation fails, you can check the status to learn the cause of the failure.

### Remarks - write

The method accepts a variable number of arguments. Each value that is specified is put into the output record as a field. The first argument becomes the first field, the second argument becomes the second field, and so on. Fields are separated by the field delimiter that is specified in the outFieldDelimiter method. Records are separated by the delimiter that is specified by using the outRecordDelimiter method. To write complete containers, use the writeExp method.

## Method writeExp

Writes the content of a container to a file.

```xpp
public boolean writeExp(container data)
```

### Parameters - writeExp

data  
The container that holds data for the record.

### Return Value - writeExp

true if the operation succeeds; otherwise, false. If the operation fails, you can check the status to learn the cause of the failure.

### Remarks - writeExp

The entries in the container are treated as fields. The container itself is treated as a full record. Fields are separated by the delimiter that is specified by using the outFieldDelimiter method. Records are separated by the delimiter that is specified by using the outRecordDelimiter method.

### Examples - writeExp

This example uses a CommaIO object to read from the example file.

```xpp
{ 
    container c; 
    CommaIo myfile; 
    FileIoPermission perm; 
```

```xpp
    #define.ExampleFile(@"c:\myfile.txt") 
    #define.ExampleOpenMode("w") 
```

```xpp
    // Set code access permission to help protect the use 
    // of CommaIO.new 
    perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
    perm.assert(); 
```

```xpp
    myfile = new CommaIo(#ExampleFile, #ExampleOpenMode); 
```

```xpp
    // Assign the entries in the container according to record layout. 
    c = [1,"MyText",1.324,"Last field"]; 
    // Write this record according to file format  
    // (record/field delimiters). 
    myfile.writeExp(c); 
```

```xpp
    // Close the code access permission. 
    CodeAccessPermission::revertAssert(); 
}
```

## Method new

Creates a new object of the CommaIo class.

```xpp
public void new(str filename, str mode)
```

### Parameters - new

filename  
The mode that the file should be opened in. Specify the mode as follows:

<!-- -->

mode  
The mode that the file should be opened in. Specify the mode as follows:

### Remarks - new

A run-time error occurs if the file is accessed by using a method that does not correspond to the current mode. For example, an error occurs if a user tries to write to a file that is opened in read mode. If an attacker can control input to this method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the FileIOPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - new

The following example uses a CommaIO object to read from the ExampleFile file.

```xpp
{ 
    CommaIo         io; 
    container       con; 
    FileIoPermission perm; 
```

```xpp
    #define.ExampleFile(@"c:\test.txt") 
    #define.ExampleOpenMode("r") 
```

```xpp
    perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
    if (perm == null) 
    { 
        return; 
    } 
    // Grants permission to execute the CommaIo.new method. 
    // CommaIo.new runs under code access security. 
    perm.assert(); 
```

```xpp
    io = new CommaIo(#ExampleFile, #ExampleOpenMode); 
    if (io != null) 
    { 
        con = io.read(); 
    } 
```

```xpp
    // Close the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```

## Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

```xpp
public void finalize()
```

### Remarks - finalize

This method is not usually called directly; instead, the object is finalized by leaving the scope. The written output is not valid until the object is finalized.

