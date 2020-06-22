---
title: SecurityTableRights class
description: This topic describes the SecurityTableRights class.
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

# Class SecurityTableRights

[!include [banner](../../includes/banner.md)]

```xpp
class SecurityTableRights extends Object
```

The SecurityTableRights class holds the information about the table security rights.

## Remarks

## Examples

## Methods

| Method                                                   | Description                                               |
|----------------------------------------------------------|-----------------------------------------------------------|
| public AccessRight fieldAccessRight(FieldName fieldName) | Gets the access rights for the field of the table.        |
| public AccessRight tableAccessRight()                    | Gets the access rights for the table.                     |
| private void new()                                       | Initializes an instance of the SecurityTableRights class. |

## Method fieldAccessRight

Gets the access rights for the field of the table.

```xpp
public AccessRight fieldAccessRight(FieldName fieldName)
```

### Parameters - fieldAccessRight

fieldName  

### Return Value - fieldAccessRight

The AccesRight instance for the field.

## Method tableAccessRight

Gets the access rights for the table.

```xpp
public AccessRight tableAccessRight()
```

### Return Value - tableAccessRight

The AccesRight instance for the table.

## Method new

Initializes an instance of the SecurityTableRights class.

```xpp
private void new()
```

