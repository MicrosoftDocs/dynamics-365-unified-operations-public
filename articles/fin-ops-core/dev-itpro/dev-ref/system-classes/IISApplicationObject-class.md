---
title: IISApplicationObject class
description: This topic describes the IISApplicationObject class.
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

# Class IISApplicationObject

[!include [banner](../../includes/banner.md)]

```xpp
class IISApplicationObject extends Object
```

The IISApplicationObject class wraps the Application object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one connection between the methods of the IISApplicationObject class and the methods of the Application object that is offered by IIS. Therefore, for more information about the methods of the IISApplicationObject class, see the Microsoft documentation for IIS. Use of the IISApplicationObject class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                                                 | Description                                                   |
|--------------------------------------------------------|---------------------------------------------------------------|
| public IISVariantDictionary contents()                 |                                                               |
| public ComInterface interface()                        |                                                               |
| public IISVariantDictionary staticObjects()            |                                                               |
| public COMVariant value(str value, \[COMVariant var\]) |                                                               |
| public str valueTxt(str value, \[str var\])            |                                                               |
| public void new()                                      | Initializes a new instance of the IISApplicationObject class. |
| public void finalize()                                 |                                                               |
| public void lock()                                     |                                                               |
| public void unLock()                                   |                                                               |

## Method contents

```xpp
public IISVariantDictionary contents()
```

### Return Value - contents

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method staticObjects

```xpp
public IISVariantDictionary staticObjects()
```

### Return Value - staticObjects

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

Initializes a new instance of the IISApplicationObject class.

```xpp
public void new()
```

## Method finalize

```xpp
public void finalize()
```

## Method lock

```xpp
public void lock()
```

## Method unLock

```xpp
public void unLock()
```

