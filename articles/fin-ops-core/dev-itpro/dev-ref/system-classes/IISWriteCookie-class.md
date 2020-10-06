---
title: IISWriteCookie class
description: This topic describes the IISWriteCookie class.
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

# Class IISWriteCookie

[!include [banner](../../includes/banner.md)]

```xpp
class IISWriteCookie extends Object
```

The IISWriteCookie class wraps the WriteCookie object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one connection between the methods of the IISWriteCookie class and the methods of the WriteCookie object that is offered by IIS. Therefore, for more information about the methods of the IISWriteCookie class, see the Microsoft documentation for IIS. Use of the IISWriteCookie class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                                  | Description                                     |
|-----------------------------------------|-------------------------------------------------|
| public COMEnum2Variant getEnum()        |                                                 |
| public boolean hasKeys()                |                                                 |
| public ComInterface interface()         |                                                 |
| public void new(COM writeCookie)        | Initializes a new instance of the Object class. |
| public void secure(boolean secure)      |                                                 |
| public void path(str path)              |                                                 |
| public void finalize()                  |                                                 |
| public void domain(str domain)          |                                                 |
| public void expires(COMVariant expires) |                                                 |
| public void item(str item, str value)   |                                                 |

## Method getEnum

```xpp
public COMEnum2Variant getEnum()
```

### Return Value - getEnum

## Method hasKeys

```xpp
public boolean hasKeys()
```

### Return Value - hasKeys

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(COM writeCookie)
```

### Parameters - new

writeCookie  

## Method secure

```xpp
public void secure(boolean secure)
```

### Parameters - secure

secure  

## Method path

```xpp
public void path(str path)
```

### Parameters - path

path  

## Method finalize

```xpp
public void finalize()
```

## Method domain

```xpp
public void domain(str domain)
```

### Parameters - domain

domain  

## Method expires

```xpp
public void expires(COMVariant expires)
```

### Parameters - expires

expires  

## Method item

```xpp
public void item(str item, str value)
```

### Parameters - item

item  

<!-- -->

value  

