---
title: IISStringList class
description: This topic describes the IISStringList class.
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

# Class IISStringList

[!include [banner](../../includes/banner.md)]

```xpp
class IISStringList extends Object
```

The IISStringList class wraps the StringList object that is offered by Internet Information Services (IIS).

## Remarks

There is a one-to-one connection between the methods of the IISStringList class and the methods of the StringList object that is offered by IIS. Therefore, for more information about the methods of the IISStringList class, see the Microsoft documentation for IIS. Use of the IISStringList class is valid only when code is run by the Internet Connector under IIS.

## Examples

## Methods

| Method                           | Description                                     |
|----------------------------------|-------------------------------------------------|
| public int count()               |                                                 |
| public COMEnum2Variant getEnum() |                                                 |
| public ComInterface interface()  |                                                 |
| public str item(\[str item\])    |                                                 |
| public void finalize()           |                                                 |
| public void new(COM stringList)  | Initializes a new instance of the Object class. |

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
public str item([str item])
```

### Parameters - item

item  

### Return Value - item

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(COM stringList)
```

### Parameters - new

stringList  

