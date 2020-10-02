---
title: ObjectRun class
description: This topic describes the ObjectRun class.
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

# Class ObjectRun

[!include [banner](../../includes/banner.md)]

```xpp
class ObjectRun extends Object
```

Used as the base class for the FormRun and ReportRun classes.

## Remarks

## Examples

## Methods

| Method                      | Description                                                                                                                                                             |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public xArgs args()         | Returns the arguments that the object was constructed with.                                                                                                             |
| public boolean isDetached() | Communicates whether an ObjectRun.detach method call has been made on this object.                                                                                      |
| public void attach()        | Reverses a call to the method. This is the reverse of calling the ObjectRun.detach method. Reversing the call disallows any further switching of focus between windows. |
| public void detach()        | Allows focus to be switched between windows.                                                                                                                            |

## Method args

Returns the arguments that the object was constructed with.

```xpp
public xArgs args()
```

### Return Value - args

An Args Class object that contains the arguments for the object.

## Method isDetached

Communicates whether an ObjectRun.detach method call has been made on this object.

```xpp
public boolean isDetached()
```

### Return Value - isDetached

true if detach has been called; otherwise, false.

## Method attach

Reverses a call to the method. This is the reverse of calling the ObjectRun.detach method. Reversing the call disallows any further switching of focus between windows.

```xpp
public void attach()
```

## Method detach

Allows focus to be switched between windows.

```xpp
public void detach()
```

### Remarks - detach

For example, a new form is created from an existing form by calling the new form's run method. Calling a run method changes the focus to the new form. Calling the detach method allows the user to return to the first form without closing the second form. Calling the ObjectRun.attach Method method reverses the effects of the detach method.

