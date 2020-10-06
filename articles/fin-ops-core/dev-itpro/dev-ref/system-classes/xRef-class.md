---
title: xRef class
description: This topic describes the xRef class.
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

# Class xRef

[!include [banner](../../includes/banner.md)]

```xpp
class xRef extends Object
```

## Remarks

## Examples

## Methods

| Method                                         | Description                                     |
|------------------------------------------------|-------------------------------------------------|
| public AccessLevel accessLevel()               |                                                 |
| public int column()                            |                                                 |
| public container contents()                    |                                                 |
| public xRefKind kind()                         |                                                 |
| public int line()                              |                                                 |
| public XRefMode mode()                         |                                                 |
| public str name()                              |                                                 |
| public str path()                              |                                                 |
| public XRefReference reference()               |                                                 |
| public int typeHandle()                        |                                                 |
| public str typeName(xRefKind kind, int handle) |                                                 |
| public void new(container data)                | Initializes a new instance of the Object class. |
| public void init()                             |                                                 |
| public void finalize()                         |                                                 |
| public void next()                             |                                                 |

## Method accessLevel

```xpp
public AccessLevel accessLevel()
```

### Return Value - accessLevel

## Method column

```xpp
public int column()
```

### Return Value - column

## Method contents

```xpp
public container contents()
```

### Return Value - contents

## Method kind

```xpp
public xRefKind kind()
```

### Return Value - kind

## Method line

```xpp
public int line()
```

### Return Value - line

## Method mode

```xpp
public XRefMode mode()
```

### Return Value - mode

## Method name

```xpp
public str name()
```

### Return Value - name

## Method path

```xpp
public str path()
```

### Return Value - path

## Method reference

```xpp
public XRefReference reference()
```

### Return Value - reference

## Method typeHandle

```xpp
public int typeHandle()
```

### Return Value - typeHandle

## Method typeName

```xpp
public str typeName(xRefKind kind, int handle)
```

### Parameters - typeName

kind  

<!-- -->

handle  

### Return Value - typeName

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(container data)
```

### Parameters - new

data  

## Method init

```xpp
public void init()
```

## Method finalize

```xpp
public void finalize()
```

## Method next

```xpp
public void next()
```

