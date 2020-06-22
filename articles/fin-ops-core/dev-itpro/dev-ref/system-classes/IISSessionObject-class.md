---
title: IISSessionObject class
description: This topic describes the IISSessionObject class.
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

# Class IISSessionObject

[!include [banner](../../includes/banner.md)]

```xpp
class IISSessionObject extends Object
```

The IISSessionObject class wraps the Session object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one connection between the methods of the IISSessionObject class and the methods of the Session object that is offered by IIS. Therefore, for more information about the methods of the IISSessionObject class, see the Microsoft documentation for IIS. Use of the IISSessionObject class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                                                 | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| public int codePage(\[int codePage\])                  |                                                           |
| public IISVariantDictionary contents()                 |                                                           |
| public str getSessionID()                              |                                                           |
| public ComInterface interface()                        |                                                           |
| public int lcid(\[int lcid\])                          |                                                           |
| public IISVariantDictionary staticObjects()            |                                                           |
| public int timeout(\[int timeout\])                    |                                                           |
| public COMVariant value(str value, \[COMVariant var\]) |                                                           |
| public str valueTxt(str value, \[str var\])            |                                                           |
| public void new()                                      | Initializes a new instance of the IISSessionObject class. |
| public void abandon()                                  |                                                           |
| public void finalize()                                 |                                                           |

## Method codePage

```xpp
public int codePage([int codePage])
```

### Parameters - codePage

codePage  

### Return Value - codePage

## Method contents

```xpp
public IISVariantDictionary contents()
```

### Return Value - contents

## Method getSessionID

```xpp
public str getSessionID()
```

### Return Value - getSessionID

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method lcid

```xpp
public int lcid([int lcid])
```

### Parameters - lcid

lcid  

### Return Value - lcid

## Method staticObjects

```xpp
public IISVariantDictionary staticObjects()
```

### Return Value - staticObjects

## Method timeout

```xpp
public int timeout([int timeout])
```

### Parameters - timeout

timeout  

### Return Value - timeout

## Method value

```xpp
public COMVariant value(str value, [COMVariant var])
```

### Parameters - value

value  

<!-- -->

var  

### Return Value - value

## Method valueTxt

```xpp
public str valueTxt(str value, [str var])
```

### Parameters - valueTxt

value  

<!-- -->

var  

### Return Value - valueTxt

## Method new

Initializes a new instance of the IISSessionObject class.

```xpp
public void new()
```

## Method abandon

```xpp
public void abandon()
```

## Method finalize

```xpp
public void finalize()
```

