---
title: IISRequest class
description: This topic describes the IISRequest class.
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

# Class IISRequest

[!include [banner](../../includes/banner.md)]

```xpp
class IISRequest extends Object
```

The IISRequest class wraps the Request object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one connection between the methods of the IISRequest class and the methods of the Request object that is offered by IIS. Therefore, for more information about the methods of the IISRequest class, see the Microsoft documentation for IIS. Use of the IISRequest class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                                               | Description                                         |
|------------------------------------------------------|-----------------------------------------------------|
| public COMVariant binaryRead(COMVariant countToRead) |                                                     |
| public IISRequestDictionary clientCertificate()      |                                                     |
| public IISRequestDictionary cookies()                |                                                     |
| public IISPostedFile file(COMVariant index)          |                                                     |
| public int fileCount()                               |                                                     |
| public IISRequestDictionary form()                   |                                                     |
| public ComInterface interface()                      |                                                     |
| public str item(str item)                            |                                                     |
| public IISRequestDictionary queryString()            |                                                     |
| public IISRequestDictionary serverVariables()        |                                                     |
| public int totalBytes()                              |                                                     |
| public void finalize()                               |                                                     |
| public void new()                                    | Initializes a new instance of the IISRequest class. |

## Method binaryRead

```xpp
public COMVariant binaryRead(COMVariant countToRead)
```

### Parameters - binaryRead

countToRead  

### Return Value - binaryRead

## Method clientCertificate

```xpp
public IISRequestDictionary clientCertificate()
```

### Return Value - clientCertificate

## Method cookies

```xpp
public IISRequestDictionary cookies()
```

### Return Value - cookies

## Method file

```xpp
public IISPostedFile file(COMVariant index)
```

### Parameters - file

index  

### Return Value - file

## Method fileCount

```xpp
public int fileCount()
```

### Return Value - fileCount

## Method form

```xpp
public IISRequestDictionary form()
```

### Return Value - form

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method item

```xpp
public str item(str item)
```

### Parameters - item

item  

### Return Value - item

## Method queryString

```xpp
public IISRequestDictionary queryString()
```

### Return Value - queryString

## Method serverVariables

```xpp
public IISRequestDictionary serverVariables()
```

### Return Value - serverVariables

## Method totalBytes

```xpp
public int totalBytes()
```

### Return Value - totalBytes

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the IISRequest class.

```xpp
public void new()
```

