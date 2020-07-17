---
title: CommaTextIo class
description: This topic describes the CommaTextIo class.
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

# Class CommaTextIo

[!include [banner](../../includes/banner.md)]

```xpp
class CommaTextIo extends Io
```

## Remarks

## Examples

## Methods

| Method                                                    | Description                                                                                                                  |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| public int filePosition()                                 |                                                                                                                              |
| public str inFieldDelimiter(\[str value\])                | Determines the delimiter used to separate fields in records accessed by the \*Io classes.                                    |
| public str inRecordDelimiter(\[str value\])               | Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.  |
| public int inRecordLength(\[int value\])                  | Gets or sets the number of characters to read for each record in a file.                                                     |
| public str outFieldDelimiter(\[str value\])               | Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.          |
| public str outRecordDelimiter(\[str value\])              | Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files. |
| public container read()                                   | Reads the next full record from the Io object.                                                                               |
| public IO\_Status status()                                | Retrieves the status of the last operation that was performed on the Io object.                                              |
| public boolean write(VarArg values)                       | Writes values of a simple type.                                                                                              |
| public boolean writeExp(container data)                   | Writes the content of a container to a file.                                                                                 |
| public void finalize()                                    | Closes the file and, if data was written, flushes the file buffers to disk.                                                  |
| public void new(str filename, str mode, \[int codepage\]) | Initializes a new instance of the Object class.                                                                              |

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

The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength method properties. The record is returned as a container. Each entry in the container equals one field in the record. Each specialized Io class has default settings for the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties. These default settings enable input and output in the most common formats. However, you might have to adjust these settings to support the desired format.

## Method status

Retrieves the status of the last operation that was performed on the Io object.

```xpp
public IO_Status status()
```

### Return Value - status

The status of the last operation, as an IO\_Status system enumeration value.

### Remarks - status

The range of IO\_Status values that can be returned varies, depending on the Io class.

## Method write

Writes values of a simple type.

```xpp
public boolean write(VarArg values)
```

### Parameters - write

values  
A value of a simple type. The simple types are string, integer, real, enum, and date.

### Return Value - write

true if the write operation is successful; otherwise, false. If the write operation fails, you can use the status method to determine the cause.

### Remarks - write

The method accepts a variable number of arguments. Each value that is specified is put into the output record as a field. The first argument is the first field, the second argument is the second field, and so on. Fields are separated by the delimiter that is specified in the outFieldDelimiter method. Records are separated by the delimiter that is specified in the outRecordDelimiter method. To write complete containers, use the writeExp method.

## Method writeExp

Writes the content of a container to a file.

```xpp
public boolean writeExp(container data)
```

### Parameters - writeExp

data  
The container that holds data for the record.

### Return Value - writeExp

true if the operation is successful; otherwise, false.

### Remarks - writeExp

If this method returns false, check the status method for the cause. The entries in the container are treated as fields, and the container is treated as a full record. The field separator is defined in the outFieldDelimiter method. The record separator is defined in the outRecordDelimiter method.

## Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

```xpp
public void finalize()
```

### Remarks - finalize

This method is not usually called directly. Instead, the object is usually finalized by leaving the scope. Written output is not valid until the object is finalized.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(str filename, str mode, [int codepage])
```

### Parameters - new

filename  

<!-- -->

mode  

<!-- -->

codepage  

### Remarks - new

If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the FileIOPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

