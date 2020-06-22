---
title: WebMenuItem class
description: This topic describes the WebMenuItem class.
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

# Class WebMenuItem

[!include [banner](../../includes/banner.md)]

```xpp
class WebMenuItem extends TreeNode
```

The WebMenuItem class enables you to create, read, update, and delete X++ code and metadata.

## Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before you call this API.

## Examples

## Methods

| Method                                                         | Description                                                                                                                               |
|----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str label()                                             |                                                                                                                                           |
| public str menuItemName(\[str value\])                         |                                                                                                                                           |
| public WebMenuItemType menuItemType(\[WebMenuItemType value\]) |                                                                                                                                           |
| public str name(\[str value\])                                 | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public str parameters(\[str value\])                           | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.                                    |
| public boolean showParentModule(\[boolean value\])             |                                                                                                                                           |

## Method label

```xpp
public str label()
```

### Return Value - label

## Method menuItemName

```xpp
public str menuItemName([str value])
```

### Parameters - menuItemName

value  

### Return Value - menuItemName

## Method menuItemType

```xpp
public WebMenuItemType menuItemType([WebMenuItemType value])
```

### Parameters - menuItemType

value  

### Return Value - menuItemType

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

```xpp
public str parameters([str value])
```

### Parameters - parameters

value  

### Return Value - parameters

The list of parameters that are passed to the object.

### Remarks - parameters

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. Objects ignore passed, unrecognized parameters.

## Method showParentModule

```xpp
public boolean showParentModule([boolean value])
```

### Parameters - showParentModule

value  

### Return Value - showParentModule

