---
title: DynamicPropertyManager class
description: This topic describes the DynamicPropertyManager class.
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

# Class DynamicPropertyManager

[!include [banner](../../includes/banner.md)]

```xpp
class DynamicPropertyManager extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                                      | Description                                                     |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| public DynamicPropertyCallback callbackObject()                                                                                                                                             |                                                                 |
| public str getConfigString()                                                                                                                                                                | Microsoft internal use only.                                    |
| public int hasSheetChanged()                                                                                                                                                                | Microsoft internal use only.                                    |
| public Struct propertyValues()                                                                                                                                                              |                                                                 |
| public void allowEdit(str name, boolean allow)                                                                                                                                              |                                                                 |
| public void updateValue(str propertyname, str value)                                                                                                                                        |                                                                 |
| public void new()                                                                                                                                                                           | Initializes a new instance of the DynamicPropertyManager class. |
| public void getPropertySheet(str configString, boolean canWebletTypeChange)                                                                                                                 | Microsoft internal use only.                                    |
| public void noProperties()                                                                                                                                                                  |                                                                 |
| public void allowDisplay(str name, boolean allow)                                                                                                                                           |                                                                 |
| public void refresh()                                                                                                                                                                       |                                                                 |
| public void setProperties(int propertySetId, str caption, Struct values, \[Struct defaultValues\], \[Struct categories\], \[DynamicPropertyCallback callbackObject\], \[boolean setFocus\]) |                                                                 |

## Method callbackObject

```xpp
public DynamicPropertyCallback callbackObject()
```

### Return Value - callbackObject

## Method getConfigString

Microsoft internal use only.

```xpp
public str getConfigString()
```

### Return Value - getConfigString

A configuration string.

## Method hasSheetChanged

Microsoft internal use only.

```xpp
public int hasSheetChanged()
```

### Return Value - hasSheetChanged

A value that indicates whether the sheet has changed.

## Method propertyValues

```xpp
public Struct propertyValues()
```

### Return Value - propertyValues

## Method allowEdit

```xpp
public void allowEdit(str name, boolean allow)
```

### Parameters - allowEdit

name  

<!-- -->

allow  

## Method updateValue

```xpp
public void updateValue(str propertyname, str value)
```

### Parameters - updateValue

propertyname  

<!-- -->

value  

## Method new

Initializes a new instance of the DynamicPropertyManager class.

```xpp
public void new()
```

## Method getPropertySheet

Microsoft internal use only.

```xpp
public void getPropertySheet(str configString, boolean canWebletTypeChange)
```

### Parameters - getPropertySheet

configString  
A value that indicates whether the weblet type can change.

<!-- -->

canWebletTypeChange  
A value that indicates whether the weblet type can change.

## Method noProperties

```xpp
public void noProperties()
```

## Method allowDisplay

```xpp
public void allowDisplay(str name, boolean allow)
```

### Parameters - allowDisplay

name  

<!-- -->

allow  

## Method refresh

```xpp
public void refresh()
```

## Method setProperties

```xpp
public void setProperties(int propertySetId, str caption, Struct values, [Struct defaultValues], [Struct categories], [DynamicPropertyCallback callbackObject], [boolean setFocus])
```

### Parameters - setProperties

propertySetId  

<!-- -->

caption  

<!-- -->

values  

<!-- -->

defaultValues  

<!-- -->

categories  

<!-- -->

callbackObject  

<!-- -->

setFocus  



