---
title: UserSetup class
description: This topic describes the UserSetup class.
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

# Class UserSetup

[!include [banner](../../includes/banner.md)]

```xpp
class UserSetup extends TreeNode
```

The UserSetup class provides an interface for setting user parameters.

## Remarks

This class is used mainly in the SysUserSetup form. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                  | Description |
|-----------------------------------------|-------------|
| public boolean xRef(\[boolean enable\]) |             |
| public void setUserSetup(Common cursor) |             |
| public void setDefaults(Common cursor)  |             |

## Method xRef

```xpp
public boolean xRef([boolean enable])
```

### Parameters - xRef

enable  

### Return Value - xRef

## Method setUserSetup

```xpp
public void setUserSetup(Common cursor)
```

### Parameters - setUserSetup

cursor  

## Method setDefaults

```xpp
public void setDefaults(Common cursor)
```

### Parameters - setDefaults

cursor  

