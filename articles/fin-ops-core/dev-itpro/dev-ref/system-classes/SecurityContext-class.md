---
title: SecurityContext class
description: This topic describes the SecurityContext class.
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

# Class SecurityContext

[!include [banner](../../includes/banner.md)]

```xpp
class SecurityContext extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                | Description |
|-------------------------------------------------------------------------------------------------------|-------------|
| public boolean isTableOperationAllowed(int tableId, StatementType operation, \[DataAreaId dataArea\]) |             |
| ::public static SecurityContext current()                                                             |             |
| ::public static SecurityContext constructFromEntryPoint(SecurableType type, str name, str childName)  |             |
| public boolean equal(SecurityContext context)                                                         |             |
| public SecurableType securableType()                                                                  |             |
| public str securableName()                                                                            |             |
| public str securableChildName()                                                                       |             |
| public void push()                                                                                    |             |
| ::public static void pop()                                                                            |             |
| private void new()                                                                                    |             |

## Method isTableOperationAllowed

```xpp
public boolean isTableOperationAllowed(int tableId, StatementType operation, [DataAreaId dataArea])
```

### Parameters - isTableOperationAllowed

tableId  

<!-- -->

operation  

<!-- -->

dataArea  

### Return Value - isTableOperationAllowed

## Method current

```xpp
public static SecurityContext current()
```

### Return Value - current

## Method constructFromEntryPoint

```xpp
public static SecurityContext constructFromEntryPoint(SecurableType type, str name, str childName)
```

### Parameters - constructFromEntryPoint

type  

<!-- -->

name  

<!-- -->

childName  

### Return Value - constructFromEntryPoint

## Method equal

```xpp
public boolean equal(SecurityContext context)
```

### Parameters - equal

context  

### Return Value - equal

## Method securableType

```xpp
public SecurableType securableType()
```

### Return Value - securableType

## Method securableName

```xpp
public str securableName()
```

### Return Value - securableName

## Method securableChildName

```xpp
public str securableChildName()
```

### Return Value - securableChildName

## Method push

```xpp
public void push()
```

## Method pop

```xpp
public static void pop()
```

## Method new

```xpp
private void new()
```

