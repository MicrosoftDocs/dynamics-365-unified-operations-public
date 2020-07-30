---
title: IISServer class
description: This topic describes the IISServer class.
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

# Class IISServer

[!include [banner](../../includes/banner.md)]

```xpp
class IISServer extends Object
```

The IISServer class wraps the Server object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one connection between the methods of the IISServer class and the methods of the Server object that is offered by IIS. Therefore, for more information about the methods of the IISServer class, see the Microsoft documentation for IIS. Use of the IISServer class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                                           | Description                                        |
|--------------------------------------------------|----------------------------------------------------|
| public COM createObject(str progID)              |                                                    |
| public str htmlEncode(str txt)                   |                                                    |
| public ComInterface interface()                  |                                                    |
| public str mapPath(str logicalPath)              |                                                    |
| public int scriptTimeout(\[int timeoutSeconds\]) |                                                    |
| public str urlEncode(str txt)                    |                                                    |
| public str urlPathEncode(str txt)                |                                                    |
| public void execute(str logicalPath)             |                                                    |
| public void transfer(str logicalPath)            |                                                    |
| public void new()                                | Initializes a new instance of the IISServer class. |
| public void finalize()                           |                                                    |

## Method createObject

```xpp
public COM createObject(str progID)
```

### Parameters - createObject

progID  

### Return Value - createObject

## Method htmlEncode

```xpp
public str htmlEncode(str txt)
```

### Parameters - htmlEncode

txt  

### Return Value - htmlEncode

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method mapPath

```xpp
public str mapPath(str logicalPath)
```

### Parameters - mapPath

logicalPath  

### Return Value - mapPath

## Method scriptTimeout

```xpp
public int scriptTimeout([int timeoutSeconds])
```

### Parameters - scriptTimeout

timeoutSeconds  

### Return Value - scriptTimeout

## Method urlEncode

```xpp
public str urlEncode(str txt)
```

### Parameters - urlEncode

txt  

### Return Value - urlEncode

## Method urlPathEncode

```xpp
public str urlPathEncode(str txt)
```

### Parameters - urlPathEncode

txt  

### Return Value - urlPathEncode

## Method execute

```xpp
public void execute(str logicalPath)
```

### Parameters - execute

logicalPath  

## Method transfer

```xpp
public void transfer(str logicalPath)
```

### Parameters - transfer

logicalPath  

## Method new

Initializes a new instance of the IISServer class.

```xpp
public void new()
```

## Method finalize

```xpp
public void finalize()
```

