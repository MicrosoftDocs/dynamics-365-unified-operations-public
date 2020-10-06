---
title: PresenceInfo class
description: This topic describes the PresenceInfo class.
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

# Class PresenceInfo

[!include [banner](../../includes/banner.md)]

```xpp
class PresenceInfo extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                | Description                                           |
|-----------------------------------------------------------------------|-------------------------------------------------------|
| public str contactName(\[str contactName\])                           |                                                       |
| public str emailAddress(int index)                                    |                                                       |
| public str emailAlias(int index)                                      |                                                       |
| public int emailCount()                                               |                                                       |
| public str phoneAlias(int index)                                      |                                                       |
| public int phoneCount()                                               |                                                       |
| public str phoneNumber(int index)                                     |                                                       |
| public str sipAddress(\[str sipAddress\])                             |                                                       |
| public void finalize()                                                |                                                       |
| public void new()                                                     | Initializes a new instance of the PresenceInfo class. |
| public void addEmailAddress(\[str emailAlias\], \[str emailAddress\]) |                                                       |
| public void addPhoneNumber(\[str phoneAlias\], \[str phoneNumber\])   |                                                       |

## Method contactName

```xpp
public str contactName([str contactName])
```

### Parameters - contactName

contactName  

### Return Value - contactName

## Method emailAddress

```xpp
public str emailAddress(int index)
```

### Parameters - emailAddress

index  

### Return Value - emailAddress

## Method emailAlias

```xpp
public str emailAlias(int index)
```

### Parameters - emailAlias

index  

### Return Value - emailAlias

## Method emailCount

```xpp
public int emailCount()
```

### Return Value - emailCount

## Method phoneAlias

```xpp
public str phoneAlias(int index)
```

### Parameters - phoneAlias

index  

### Return Value - phoneAlias

## Method phoneCount

```xpp
public int phoneCount()
```

### Return Value - phoneCount

## Method phoneNumber

```xpp
public str phoneNumber(int index)
```

### Parameters - phoneNumber

index  

### Return Value - phoneNumber

## Method sipAddress

```xpp
public str sipAddress([str sipAddress])
```

### Parameters - sipAddress

sipAddress  

### Return Value - sipAddress

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the PresenceInfo class.

```xpp
public void new()
```

## Method addEmailAddress

```xpp
public void addEmailAddress([str emailAlias], [str emailAddress])
```

### Parameters - addEmailAddress

emailAlias  

<!-- -->

emailAddress  

## Method addPhoneNumber

```xpp
public void addPhoneNumber([str phoneAlias], [str phoneNumber])
```

### Parameters - addPhoneNumber

phoneAlias  

<!-- -->

phoneNumber  

