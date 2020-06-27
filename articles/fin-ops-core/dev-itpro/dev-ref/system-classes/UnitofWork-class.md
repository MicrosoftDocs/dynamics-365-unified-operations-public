---
title: UnitofWork class
description: This topic describes the UnitofWork class.
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

# Class UnitofWork

[!include [banner](../../includes/banner.md)]


```xpp
class UnitofWork extends Object
```

## Remarks

## Examples

## Methods

| Method                                                       | Description                                         |
|--------------------------------------------------------------|-----------------------------------------------------|
| public boolean getByKey(Common record)                       |                                                     |
| public void updateonSaveChanges(Common record)               |                                                     |
| public void saveChanges(\[UserConnection user\_connection\]) |                                                     |
| public void deleteonSaveChanges(Common record)               |                                                     |
| public void insertonSaveChanges(Common record)               |                                                     |
| public void finalize()                                       |                                                     |
| public void new()                                            | Initializes a new instance of the UnitofWork class. |
| public void clear()                                          |                                                     |

## Method getByKey

```xpp
public boolean getByKey(Common record)
```

### Parameters - getByKey

record  

### Return Value - getByKey

## Method updateonSaveChanges

```xpp
public void updateonSaveChanges(Common record)
```

### Parameters - updateonSaveChanges

record  

## Method saveChanges

```xpp
public void saveChanges([UserConnection user_connection])
```

### Parameters - saveChanges

user\_connection  

## Method deleteonSaveChanges

```xpp
public void deleteonSaveChanges(Common record)
```

### Parameters - deleteonSaveChanges

record  

## Method insertonSaveChanges

```xpp
public void insertonSaveChanges(Common record)
```

### Parameters - insertonSaveChanges

record  

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the UnitofWork class.

```xpp
public void new()
```

## Method clear

```xpp
public void clear()
```

