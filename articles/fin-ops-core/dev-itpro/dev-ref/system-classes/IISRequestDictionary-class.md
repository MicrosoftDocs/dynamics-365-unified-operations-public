---
title: IISRequestDictionary class
description: This topic describes the IISRequestDictionary class.
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

# Class IISRequestDictionary

[!include [banner](../../includes/banner.md)]

```xpp
class IISRequestDictionary extends Object
```

The IISRequestDictionary class wraps the RequestDictionary object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one relationship between the methods of the IISRequestDictionary class and the methods of the RequestDictionary object that is offered by IIS. Therefore, for more information about the methods of the IISRequestDictionary class, see the Microsoft documentation for IIS. Use of the IISRequestDictionary class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                                              | Description                                     |
|-----------------------------------------------------|-------------------------------------------------|
| public int count()                                  |                                                 |
| public COMEnum2Variant getEnum()                    |                                                 |
| public ComInterface interface()                     |                                                 |
| public COMVariant item(COMVariant item)             |                                                 |
| public IISReadCookie itemReadCookie(\[str item\])   |                                                 |
| public IISStringList itemStringList(\[str item\])   |                                                 |
| public str itemTxt(str item)                        |                                                 |
| public IISWriteCookie itemWriteCookie(\[str item\]) |                                                 |
| public str key(str key)                             |                                                 |
| public void finalize()                              |                                                 |
| public void new(COM requestDictionary)              | Initializes a new instance of the Object class. |

## Method count

```xpp
public int count()
```

### Return Value - count

## Method getEnum

```xpp
public COMEnum2Variant getEnum()
```

### Return Value - getEnum

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method item

```xpp
public COMVariant item(COMVariant item)
```

### Parameters - item

item  

### Return Value - item

## Method itemReadCookie

```xpp
public IISReadCookie itemReadCookie([str item])
```

### Parameters - itemReadCookie

item  

### Return Value - itemReadCookie

## Method itemStringList

```xpp
public IISStringList itemStringList([str item])
```

### Parameters - itemStringList

item  

### Return Value - itemStringList

## Method itemTxt

```xpp
public str itemTxt(str item)
```

### Parameters - itemTxt

item  

### Return Value - itemTxt

## Method itemWriteCookie

```xpp
public IISWriteCookie itemWriteCookie([str item])
```

### Parameters - itemWriteCookie

item  

### Return Value - itemWriteCookie

## Method key

```xpp
public str key(str key)
```

### Parameters - key

key  

### Return Value - key

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(COM requestDictionary)
```

### Parameters - new

requestDictionary  

