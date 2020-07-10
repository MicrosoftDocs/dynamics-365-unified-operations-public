---
title: VSSItem class
description: This topic describes the VSSItem class.
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

# Class VSSItem

[!include [banner](../../includes/banner.md)]

```xpp
class VSSItem extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                               | Description                                      |
|--------------------------------------------------------------------------------------|--------------------------------------------------|
| public boolean add(\[boolean keepCheckedout\], \[str comment\])                      |                                                  |
| public boolean checkin(\[str comment\])                                              |                                                  |
| public boolean checkout(\[boolean allowMultipleCheckout\], \[boolean replaceLocal\]) |                                                  |
| public boolean delete()                                                              |                                                  |
| public boolean destroy()                                                             |                                                  |
| public Map get(\[boolean force\], \[int version\], \[str label\], \[str localFile\]) |                                                  |
| public str getActionText()                                                           |                                                  |
| public container getCheckedOutTo()                                                   |                                                  |
| public int getCheckoutVersion()                                                      |                                                  |
| public container getHistory()                                                        |                                                  |
| public ComInterface getIUnknown()                                                    |                                                  |
| public int getVersionNo()                                                            |                                                  |
| public str getVSSPath()                                                              |                                                  |
| public boolean isCheckedOut()                                                        |                                                  |
| public boolean isRenamed()                                                           |                                                  |
| public str name(str newName)                                                         |                                                  |
| public boolean rename(str newName)                                                   |                                                  |
| public boolean undoCheckout()                                                        |                                                  |
| private void new()                                                                   | Initializes a new instance of the VSSItem class. |

## Method add

```xpp
public boolean add([boolean keepCheckedout], [str comment])
```

### Parameters - add

keepCheckedout  

<!-- -->

comment  

### Return Value - add

## Method checkin

```xpp
public boolean checkin([str comment])
```

### Parameters - checkin

comment  

### Return Value - checkin

## Method checkout

```xpp
public boolean checkout([boolean allowMultipleCheckout], [boolean replaceLocal])
```

### Parameters - checkout

allowMultipleCheckout  

<!-- -->

replaceLocal  

### Return Value - checkout

## Method delete

```xpp
public boolean delete()
```

### Return Value - delete

## Method destroy

```xpp
public boolean destroy()
```

### Return Value - destroy

## Method get

```xpp
public Map get([boolean force], [int version], [str label], [str localFile])
```

### Parameters - get

force  

<!-- -->

version  

<!-- -->

label  

<!-- -->

localFile  

### Return Value - get

## Method getActionText

```xpp
public str getActionText()
```

### Return Value - getActionText

## Method getCheckedOutTo

```xpp
public container getCheckedOutTo()
```

### Return Value - getCheckedOutTo

## Method getCheckoutVersion

```xpp
public int getCheckoutVersion()
```

### Return Value - getCheckoutVersion

## Method getHistory

```xpp
public container getHistory()
```

### Return Value - getHistory

## Method getIUnknown

```xpp
public ComInterface getIUnknown()
```

### Return Value - getIUnknown

## Method getVersionNo

```xpp
public int getVersionNo()
```

### Return Value - getVersionNo

## Method getVSSPath

```xpp
public str getVSSPath()
```

### Return Value - getVSSPath

## Method isCheckedOut

```xpp
public boolean isCheckedOut()
```

### Return Value - isCheckedOut

## Method isRenamed

```xpp
public boolean isRenamed()
```

### Return Value - isRenamed

## Method name

```xpp
public str name(str newName)
```

### Parameters - name

newName  

### Return Value - name

## Method rename

```xpp
public boolean rename(str newName)
```

### Parameters - rename

newName  

### Return Value - rename

## Method undoCheckout

```xpp
public boolean undoCheckout()
```

### Return Value - undoCheckout

## Method new

Initializes a new instance of the VSSItem class.

```xpp
private void new()
```


