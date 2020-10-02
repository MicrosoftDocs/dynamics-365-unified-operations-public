---
title: BinaryIo class
description: This topic describes the BinaryIo class.
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

# Class BinaryIo

[!include [banner](../../includes/banner.md)]

```xpp
class BinaryIo extends Io
```

## Remarks

## Examples

## Methods

| Method                                  | Description                                                                     |
|-----------------------------------------|---------------------------------------------------------------------------------|
| public container read()                 | Reads the next full record from the Io object.                                  |
| public IO\_Status status()              | Retrieves the status of the last operation that was performed on the Io object. |
| public boolean write(VarArg values)     | Writes values of a simple type.                                                 |
| public boolean writeExp(container data) | Writes the content of a container to a file.                                    |
| public void new(str filename, str mode) | Creates an instance of the BinaryIo class.                                      |
| public void finalize()                  | Closes the file and, if data was written, flushes the file buffers to disk.     |

## Method read

Reads the next full record from the Io object.

```xpp
public container read()
```

### Return Value - read

A container that holds the next full record from the Io object.

### Remarks - read

The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength method properties. The record is returned as a container. Each entry in the container equals one field in the record. Every specialized Io class has default settings for the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties. These default settings enable input and output of the most common formats. You might have to adjust these settings to support the format that you want to use.

## Method status

Retrieves the status of the last operation that was performed on the Io object.

```xpp
public IO_Status status()
```

### Return Value - status

The status of the last operation as an IO\_Status system enumeration value.

### Remarks - status

The range of possible IO\_Status values that are returned varies, depending on the Io class.

## Method write

Writes values of a simple type.

```xpp
public boolean write(VarArg values)
```

### Parameters - write

values  
The simple type. The simple types are string, integer, real, enum, and date.

### Return Value - write

true if the write operation succeeds; otherwise, false. If the write operation is unsuccessful, you can check the status method for the cause.

### Remarks - write

This method accepts a variable number of arguments. Each value that is specified is put into the output record as a field. The first argument is the first field, the second argument is the second field, and so on. The fields are separated by the field delimiter that is specified in the outFieldDelimiter method. Each record is separated by the record delimiter that is specified in the outRecordDelimiter method. To write complete containers, use the writeExp method.

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

## Method new

Creates an instance of the BinaryIo class.

```xpp
public void new(str filename, str mode)
```

### Parameters - new

filename  
The mode to use to create the instance of the BinaryIo class.

<!-- -->

mode  
The mode to use to create the instance of the BinaryIo class.

### Remarks - new

If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - new

This example uses the BinaryIo class to read data from the ExampleFile text file.

```xpp
static void BinaryIoExampleW2(Args _args)
{     
    #define.ExampleFile(@"D:\Writers\GeneMi\_Junk\TestW.BinaryIo")
    #define.ExampleOpenModeW("w")
    #define.ExampleOpenModeR("r")
    BinaryIo binaryIoObject;
    container con1;
    str sConRecs;
    FileIoPermission perm;
```

```xpp
    // Set the code access permission to help protect the use of
    // the BinaryIo.new method.
    perm = new FileIoPermission(#ExampleFile, #ExampleOpenModeW);
    if (perm == null)
    {
        return;
    }
    perm.assert();
```

```xpp
    // Overwrites the file if it already exists; restarts it as empty.
    binaryIoObject = new BinaryIo(#ExampleFile, #ExampleOpenModeW);
    if (binaryIoObject != null)
    {
        info("w binaryIoObject is NOT null, Good.");
        binaryIoObject.write("hello world");
        binaryIoObject.write("goodbye solar system");
    }
    else
    {
        warning("w binaryIoObject is NULL, Bad.");
    }
```

```xpp
    binaryIoObject.finalize();
    binaryIoObject = null;
    // Close the file, w?
    // BinaryIo instance can only read files in that
    // are in the exact same esoteric format that BinaryIo
    // writes files to.
    // binaryIoObject = new BinaryIo(#ExampleFile, #ExampleOpenModeR);
    if (binaryIoObject != null)
    {
         info("r binaryIoObject is NOT null, Good.");
         while (true)
        {
            con1 = binaryIoObject.read();
            if (con1 == conNull())
            {
                info("r, no more records.");
                break;
            }
            sConRecs = con2Str(con1);
            info(sConRecs);
        }
    }
    else
    {
         warning("r binaryIoObject is NULL, Bad.");
    }
    binaryIoObject.finalize();
    binaryIoObject = null;
    WINAPI::deleteFile(#ExampleFile);
     // Clean up after the job.
    CodeAccessPermission::revertAssert();
 }
/*** Output copied from Infolog:Message (11:22:16 am)w binaryIoObject is NOT null, Good.r binaryIoObject is NOT null, Good.hello worldgoodbye solar systemr, no more records.***/
```

## Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

```xpp
public void finalize()
```

### Remarks - finalize

Typically, you finalize the object by leaving the scope. Therefore, the finalize method is not usually called directly. Written output is not valid until the object is finalized.

