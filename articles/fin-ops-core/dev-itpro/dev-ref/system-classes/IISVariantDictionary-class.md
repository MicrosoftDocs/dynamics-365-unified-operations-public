---
title: IISVariantDictionary class
description: This topic describes the IISVariantDictionary class.
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

# Class IISVariantDictionary

[!include [banner](../../includes/banner.md)]

```xpp
class IISVariantDictionary extends Object
```

The IISVariantDictionary class wraps the VariantDictionary object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one connection between the methods of the IISVariantDictionary class and the methods of the VariantDictionary object that is offered by IIS. Therefore, for more information about the methods of the IISVariantDictionary class, see the Microsoft documentation for IIS. Use of the IISVariantDictionary class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                                                      | Description                                     |
|-------------------------------------------------------------|-------------------------------------------------|
| public int count()                                          |                                                 |
| public COMEnum2Variant getEnum()                            |                                                 |
| public ComInterface interface()                             |                                                 |
| public COMVariant item(COMVariant item, \[COMVariant var\]) |                                                 |
| public COM itemObj(str item, \[COM var\])                   |                                                 |
| public str itemTxt(str item, \[str var\])                   |                                                 |
| public str key(str key)                                     |                                                 |
| public void finalize()                                      |                                                 |
| public void remove(str key)                                 |                                                 |
| public void removeAll()                                     |                                                 |
| public void new(COM variantDictionary)                      | Initializes a new instance of the Object class. |

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
public COMVariant item(COMVariant item, [COMVariant var])
```

### Parameters - item

item  

<!-- -->

var  

### Return Value - item

## Method itemObj

```xpp
public COM itemObj(str item, [COM var])
```

### Parameters - itemObj

item  

<!-- -->

var  

### Return Value - itemObj

## Method itemTxt

```xpp
public str itemTxt(str item, [str var])
```

### Parameters - itemTxt

item  

<!-- -->

var  

### Return Value - itemTxt

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

## Method remove

```xpp
public void remove(str key)
```

### Parameters - remove

key  

## Method removeAll

```xpp
public void removeAll()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(COM variantDictionary)
```

### Parameters - new

variantDictionary  

