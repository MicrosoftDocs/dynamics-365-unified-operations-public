---
title: FormObject class
description: This topic describes the FormObject class.
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

# Class FormObject

[!include [banner](../../includes/banner.md)]


```xpp
class FormObject extends Object
```

## Remarks

## Examples

## Methods

| Method                                        | Description                             |
|-----------------------------------------------|-----------------------------------------|
| public boolean getAllowEdit(\[int rowIndex\]) |                                         |
| public AnyType getValue(\[int rowIndex\])     |                                         |
| public boolean getVisible()                   |                                         |
| public str helpField()                        | Returns the Help text for the control.  |
| public str labelText()                        | Returns the label text for the control. |
| public boolean setValue(AnyType value)        |                                         |
| public str toolTip()                          |                                         |
| public boolean validate()                     |                                         |
| public void jumpRef()                         |                                         |
| public void modified()                        |                                         |
| public void restore()                         |                                         |
| public void find()                            |                                         |
| public void context()                         |                                         |

## Method getAllowEdit

```xpp
public boolean getAllowEdit([int rowIndex])
```

### Parameters - getAllowEdit

rowIndex  

### Return Value - getAllowEdit

## Method getValue

```xpp
public AnyType getValue([int rowIndex])
```

### Parameters - getValue

rowIndex  

### Return Value - getValue

## Method getVisible

```xpp
public boolean getVisible()
```

### Return Value - getVisible

## Method helpField

Returns the Help text for the control.

```xpp
public str helpField()
```

### Return Value - helpField

The Help text for the control; an empty string if there is no Help text.

### Examples - helpField

The following example shows how to use the helpField method.

```xpp
str strHelp;
strHelp = this.helpField();
```

## Method labelText

Returns the label text for the control.

```xpp
public str labelText()
```

### Return Value - labelText

The label text for the control; an empty string if there is no label text for the control.

## Method setValue

```xpp
public boolean setValue(AnyType value)
```

### Parameters - setValue

value  

### Return Value - setValue

## Method toolTip

```xpp
public str toolTip()
```

### Return Value - toolTip

## Method validate

```xpp
public boolean validate()
```

### Return Value - validate

## Method jumpRef

```xpp
public void jumpRef()
```

## Method modified

```xpp
public void modified()
```

## Method restore

```xpp
public void restore()
```

## Method find

```xpp
public void find()
```

## Method context

```xpp
public void context()
```

