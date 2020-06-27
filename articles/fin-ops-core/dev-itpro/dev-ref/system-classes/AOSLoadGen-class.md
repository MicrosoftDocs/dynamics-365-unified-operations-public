---
title: AOSLoadGen class
description: This topic describes the AOSLoadGen class.
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

# Class AOSLoadGen

[!include [banner](../../includes/banner.md)]

```xpp
class AOSLoadGen extends Object
```

## Remarks

## Examples

## Methods

| Method                                                     | Description                                  |
|------------------------------------------------------------|----------------------------------------------|
| public boolean spawnClass(ClassId classId, str parm)       |                                              |
| public boolean spawnJob(UtilElementName jobName, str parm) |                                              |
| public void new(\[UserId user\], \[ClassId infoClass\])    | Creates an instance of the AOSLoadGen class. |

## Method spawnClass

```xpp
public boolean spawnClass(ClassId classId, str parm)
```

### Parameters - spawnClass

classId  

<!-- -->

parm  

### Return Value - spawnClass

## Method spawnJob

```xpp
public boolean spawnJob(UtilElementName jobName, str parm)
```

### Parameters - spawnJob

jobName  

<!-- -->

parm  

### Return Value - spawnJob

## Method new

Creates an instance of the AOSLoadGen class.

```xpp
public void new([UserId user], [ClassId infoClass])
```

### Parameters - new

user  
The information class that is used to create the instance of the AOSLoadGen class. The default value is info.

<!-- -->

infoClass  
The information class that is used to create the instance of the AOSLoadGen class. The default value is info.

### Remarks - new

Control of the input to the new method could be a security risk. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.
