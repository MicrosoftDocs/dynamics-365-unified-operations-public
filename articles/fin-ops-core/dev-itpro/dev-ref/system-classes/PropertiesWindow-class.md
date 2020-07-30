---
title: PropertiesWindow class
description: This topic describes the PropertiesWindow class.
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

# Class PropertiesWindow

[!include [banner](../../includes/banner.md)]

```xpp
class PropertiesWindow extends Object
```

## Remarks

## Examples

## Methods

| Method                                                   | Description |
|----------------------------------------------------------|-------------|
| public int Activate(PropWindowDisplayState displaystate) |             |
| public boolean DockFrame(PropWindowDockState dockstate)  |             |
| public str GetSelectedPropertyName()                     |             |
| public boolean IsVisible()                               |             |
| public boolean SelectPropertyByName(str propname)        |             |
| public boolean SelectTab(PropWindowSelectTab selecttab)  |             |

## Method Activate

```xpp
public int Activate(PropWindowDisplayState displaystate)
```

### Parameters - Activate

displaystate  

### Return Value - Activate

## Method DockFrame

```xpp
public boolean DockFrame(PropWindowDockState dockstate)
```

### Parameters - DockFrame

dockstate  

### Return Value - DockFrame

## Method GetSelectedPropertyName

```xpp
public str GetSelectedPropertyName()
```

### Return Value - GetSelectedPropertyName

## Method IsVisible

```xpp
public boolean IsVisible()
```

### Return Value - IsVisible

## Method SelectPropertyByName

```xpp
public boolean SelectPropertyByName(str propname)
```

### Parameters - SelectPropertyByName

propname  

### Return Value - SelectPropertyByName

## Method SelectTab

```xpp
public boolean SelectTab(PropWindowSelectTab selecttab)
```

### Parameters - SelectTab

selecttab  

### Return Value - SelectTab


