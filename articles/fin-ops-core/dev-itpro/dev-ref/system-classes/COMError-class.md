---
title: COMError class
description: This topic describes the COMError class.
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

# Class COMError

[!include [banner](../../includes/banner.md)]

```xpp
class COMError extends Object
```

The COMError class wraps any COM errors that occur during a COM method call.

## Remarks

When an error occurs during a COM method call, the error code and the error description are stored in the COMError object. The COMError object that is associated with a COM class is retrieved from the COM class by using the COM.error method.

## Examples

## Methods

| Method                   | Description                                                                                                               |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public str description() | Returns a description of the error that occurred when the COM object was called.                                          |
| public int helpContext() | Returns the Help context ID for the error that occurred when the COM object was called.                                   |
| public str helpFile()    | Returns the name of the Help file that contains information about the error that occurred when the COM object was called. |
| public int number()      | Returns the error code of the error that occurred when the COM object was called.                                         |
| public str source()      | Returns the name of the component that caused the error that occurred when the COM object was called.                     |
| public str toString()    | Returns a string that contains the class handle and name, and sometimes additional information.                           |
| public void clear()      | Clears the properties of the COMError object.                                                                             |
| public void new()        | Initializes an instance of the COMError class.                                                                            |
| public void finalize()   |                                                                                                                           |

## Method description

Returns a description of the error that occurred when the COM object was called.

```xpp
public str description()
```

### Return Value - description

The error description.

### Remarks - description

The description might be empty if the COM object does not support handing out textual error messages. The description property is read-only.

## Method helpContext

Returns the Help context ID for the error that occurred when the COM object was called.

```xpp
public int helpContext()
```

### Return Value - helpContext

The Help context ID.

### Remarks - helpContext

The Help context ID might be 0 (zero) if the COM object does not support Help for its errors. The helpContext property is read-only.

## Method helpFile

Returns the name of the Help file that contains information about the error that occurred when the COM object was called.

```xpp
public str helpFile()
```

### Return Value - helpFile

The name of the Help file.

### Remarks - helpFile

The Help file might be empty if the COM object does not support Help for its errors. The helpFile property is read-only.

## Method number

Returns the error code of the error that occurred when the COM object was called.

```xpp
public int number()
```

### Return Value - number

The error code; 0 (zero) if no error occurred when the COM object was called.

### Remarks - number

The number property is read-only.

## Method source

Returns the name of the component that caused the error that occurred when the COM object was called.

```xpp
public str source()
```

### Return Value - source

The source of the error.

### Remarks - source

The source might be empty if the COM object does not support handing out the source of the error. The source property is read-only.

## Method toString

Returns a string that contains the class handle and name, and sometimes additional information.

```xpp
public str toString()
```

### Return Value - toString

A textual description of the class.

### Remarks - toString

For most classes, the string that is returned contains the class handle and name. However, for some classes, additional information is included in the string.

## Method clear

Clears the properties of the COMError object.

```xpp
public void clear()
```

### Remarks - clear

The properties of the COMError object are usually read-only, but they can be cleared by using this method.

## Method new

Initializes an instance of the COMError class.

```xpp
public void new()
```

## Method finalize

```xpp
public void finalize()
```

