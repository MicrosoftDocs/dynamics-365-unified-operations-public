---
title: AsciiIo class
description: This topic describes the AsciiIo class.
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

# Class AsciiIo

[!include [banner](../../includes/banner.md)]

```xpp
class AsciiIo extends CommaIo
```

The AsciiIo class provides functionality for reading and writing ASCII files.

## Remarks

The TextIo class provides functionality for reading and writing files that use various code pages. The AsciiIO class supports only ANSI code page (ACP) characters. Existing code that uses the AsciiIO class must be converted to use the TextIO class if the file contains non-ACP characters, or if it is a file that is used only in a Finance and Operations application, such as an .xpo file.

## Examples

## Methods

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

## Method inFieldDelimiter

Sets or retrieves the character that is used as the field delimiter of an input file that is represented by an AsciiIO object.

```xpp
public str inFieldDelimiter([str value])
```

### Parameters - inFieldDelimiter

value  
The character to assign as the field delimiter.

### Return Value - inFieldDelimiter

The character that is used as the field delimiter.

## Method inRecordDelimiter

Sets or retrieves the character that is used as the record delimiter of an input file that is represented by an AsciiIO object.

```xpp
public str inRecordDelimiter([str value])
```

### Parameters - inRecordDelimiter

value  
The character to assign as the record delimiter.

### Return Value - inRecordDelimiter

The character that is used as the record delimiter.

### Remarks - inRecordDelimiter

For standard text, the delimiter is a newline character.

## Method inRecordLength

Sets or retrieves the record length for an input file.

```xpp
public int inRecordLength([int value])
```

### Parameters - inRecordLength

value  
The value to assign as the record length for the input file.

### Return Value - inRecordLength

The record length for the input file.

### Remarks - inRecordLength

For files that have a fixed-length format, use the inRecordLength property to guarantee that no more than the specified number of characters is read for each record. If the record format is overruled by a specified inRecordDelimiter property value (in other words, if the inRecordDelimiter value is met before the fixed length is read), the record is accepted, and no more data is read. To make sure that a fixed number of characters is read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to 0 (zero) to disable the check of the record length.

## Method outFieldDelimiter

Sets or retrieves the character that is used as the field delimiter of an output file that is represented by an AsciiIO object.

```xpp
public str outFieldDelimiter([str value])
```

### Parameters - outFieldDelimiter

value  
The character to assign as the field delimiter.

### Return Value - outFieldDelimiter

The character that is used as the field delimiter.

## Method outRecordDelimiter

Sets or retrieves the character that is used as the record delimiter of an output file that is represented by an AsciiIO object.

```xpp
public str outRecordDelimiter([str value])
```

### Parameters - outRecordDelimiter

value  
The character to assign as the record delimiter.

### Return Value - outRecordDelimiter

The character that is used as the record delimiter.

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

The definition of the next full record is controlled by the following properties: inFieldDelimiter, inRecordDelimiter, and inRecordLength. The record is returned as a container. Each entry in the container represents one field in the record. Each of the specialized Io classes has default settings for inFieldDelimiter, inRecordDelimiter, and inRecordLength. These settings allow for input and output of the most common formats. However, you might have to adjust these settings to support the desired format.

## Method status

Returns the status of the last operation on the file.

```xpp
public IO_Status status()
```

### Return Value - status

The status of the last file operation.

## Method write

Writes values of a simple type.

```xpp
public boolean write(VarArg values)
```

### Parameters - write

values  
One or more values, each of a simple type, separated by a field delimiter. The simple types are string, integer, real, enum, and date.

### Return Value - write

true if the write operation succeeds; otherwise, false. If the write operation fails, you can check the status to learn the cause.

### Remarks - write

The method accepts a variable number of arguments. Each value that is specified is put into the output record as a field: the first argument as the first field, the second argument as the second field, and so on. Fields are separated by the delimiter that is specified in the outFieldDelimiter method. Records are separated by the delimiter that is specified in the outRecordDelimiter method. To write complete containers, use the writeExp method.

## Method writeChar

```xpp
public boolean writeChar(int int)
```

### Parameters - writeChar

int  

### Return Value - writeChar

## Method writeExp

Writes the content of a container to a file.

```xpp
public boolean writeExp(container data)
```

### Parameters - writeExp

data  
The container that holds data for the record.

### Return Value - writeExp

true if the operation succeeds; otherwise, false. If the operation fails, check the status to learn the cause.

### Remarks - writeExp

The entries in the container are treated as fields. The container is treated as a full record. Fields are separated by the delimiter that is specified in the outFieldDelimiter method. Records are separated by the delimiter that is specified in the outRecordDelimiter method.

## Method writeRaw

```xpp
public boolean writeRaw(str data)
```

### Parameters - writeRaw

data  

### Return Value - writeRaw

## Method finalize

Closes the file and then flushes the file buffers to disk.

```xpp
public void finalize()
```

### Remarks - finalize

An AsciiIo object is usually finalized after its scope has ended. This method is not usually called directly. Output that is written to the file is not valid until the AsciiIo object is finalized.

## Method new

Creates an instance of the AsciiIo class.

```xpp
public void new(str filename, str mode)
```

### Parameters - new

filename  
The mode to use to create this instance of the AsciiIo class.

<!-- -->

mode  
The mode to use to create this instance of the AsciiIo class.

### Remarks - new

If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the FileIOPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - new

The following example uses the AsciiIo class to read from a text file.

```xpp
void AsciiIoExample() 
{ 
    AsciiIo asciiIo; 
    container con; 
    FileIoPermission perm; 
```

```xpp
    #define.ExampleFile(@"c:\test.txt") 
    #define.ExampleOpenMode("r") 
```

```xpp
    // The AsciiIo.new method runs under code access permission. 
    perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
    if (perm == null) 
    { 
        return; 
    } 
```

```xpp
    // Code access permission scope starts here. 
     perm.assert(); 
```

```xpp
     asciiIo = new AsciiIo(#ExampleFile, #ExampleOpenMode); 
    if (asciiIo != null) 
    { 
          con = asciiIo.read(); 
    } 
    // Closes the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```

