---
title: FileIOPermission class
description: This topic describes the FileIOPermission class.
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

# Class FileIOPermission

[!include [banner](../../includes/banner.md)]

```xpp
class FileIOPermission extends CodeAccessPermission
```

The FileIOPermission class controls the ability to access files and folders.

## Remarks

The FileIoPermission class is designed to check permissions for specific APIs. For a list of all APIs that are protected by permissions, see Secured APIs. Before the protected API is run, you must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission::demand method is called on. Call a method on the server tier from one of the following:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property

## Examples

The following code example shows a new instance of the FileIoPermission class that specifies read access for the File.txt file. The assert method is called to declare that the code can then call the AsciiIo.new method.

```xpp
server static void main(Args args) 
{ 
    FileIoPermission _perm; 
    AsciiIo a; 
    _perm = new FileIoPermission("c:\\File.txt",'r'); 
    _perm.assert(); 
    // Invoke the protected API. 
    a = new AsciiIo("c:\\File.txt",'r'); 
}
```

## Methods

| Method                                                 | Description                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.               |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether the current permission is a subset of a specified permission. |
| public void new(str filename, str mode)                | Initializes a new instance of the CodeAccessPermission class.                    |

## Method copy

Creates and returns a copy of the current permission class object.

```xpp
public CodeAccessPermission copy()
```

### Return Value - copy

A copy of the current permission object.

### Remarks - copy

You override this method when you derive a class from the CodeAccessPermission class. For more information, see copy.

## Method isSubsetOf

Determines whether the current permission is a subset of a specified permission.

```xpp
public boolean isSubsetOf(CodeAccessPermission target)
```

### Parameters - isSubsetOf

target  
A CodeAccessPermission class object.

### Return Value - isSubsetOf

true if the current permission is a subset of the specified permission; otherwise, false.

### Remarks - isSubsetOf

You override this method when you derive a class from the CodeAccessPermission class. For more information, see M: CodeAccessPermission.isSubsetOf.

## Method new

Initializes a new instance of the CodeAccessPermission class.

```xpp
public void new(str filename, str mode)
```

### Parameters - new

filename  
A String data type that specifies the type of access.

<!-- -->

mode  
A String data type that specifies the type of access.

### Remarks - new

The following table lists the possible values for the \_mode parameter.

|     |                |
|-----|----------------|
| R   | Read           |
| W   | Write          |
| RW  | Read and write |

### Examples - new

The following code example shows a new instance of the FileIoPermission class that specifies read access for the File.txt file.

```xpp
server static void main(Args args) 
{ 
    FileIoPermission _perm; 
    _perm = new FileIoPermission("c:\\File.txt",'r'); 
}
```

