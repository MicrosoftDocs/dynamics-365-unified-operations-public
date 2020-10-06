---
title: MenuItem class
description: This topic describes the MenuItem class.
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

# Class MenuItem

[!include [banner](../../includes/banner.md)]

```xpp
class MenuItem extends TreeNode
```

The MenuItem class lets you create, read, update, and delete X++ code and metadata.

## Remarks

A menu item represents the user interface of a menu function. Menu items are linked to a MenuFunction object, which runs when the user selects the menu item. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                     | Description                                                                                                                                   |
|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str allowRootNavigation(\[str value\])              |                                                                                                                                               |
| public boolean isDisplayedInContentArea(\[boolean value\]) |                                                                                                                                               |
| public str label(\[str name\])                             |                                                                                                                                               |
| public str menuFunctionName(\[str name\])                  |                                                                                                                                               |
| public str menuItemName(\[str value\])                     |                                                                                                                                               |
| public MenuItemType menuItemType(\[MenuItemType value\])   |                                                                                                                                               |
| public str name(\[str value\])                             | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public str parameter(\[str parameter\])                    |                                                                                                                                               |
| public str parameters(\[str value\])                       | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.                                        |
| public str shortCut(\[str value\])                         |                                                                                                                                               |
| public boolean showParentModule(\[boolean value\])         |                                                                                                                                               |
| public boolean visible(\[boolean value\])                  |                                                                                                                                               |
| public str webTarget(\[str value\])                        |                                                                                                                                               |

## Method allowRootNavigation

```xpp
public str allowRootNavigation([str value])
```

### Parameters - allowRootNavigation

value  

### Return Value - allowRootNavigation

## Method isDisplayedInContentArea

```xpp
public boolean isDisplayedInContentArea([boolean value])
```

### Parameters - isDisplayedInContentArea

value  

### Return Value - isDisplayedInContentArea

## Method label

```xpp
public str label([str name])
```

### Parameters - label

name  

### Return Value - label

## Method menuFunctionName

```xpp
public str menuFunctionName([str name])
```

### Parameters - menuFunctionName

name  

### Return Value - menuFunctionName

## Method menuItemName

```xpp
public str menuItemName([str value])
```

### Parameters - menuItemName

value  

### Return Value - menuItemName

## Method menuItemType

```xpp
public MenuItemType menuItemType([MenuItemType value])
```

### Parameters - menuItemType

value  

### Return Value - menuItemType

## Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in the code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method parameter

```xpp
public str parameter([str parameter])
```

### Parameters - parameter

parameter  

### Return Value - parameter

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

## Method shortCut

```xpp
public str shortCut([str value])
```

### Parameters - shortCut

value  

### Return Value - shortCut

## Method showParentModule

```xpp
public boolean showParentModule([boolean value])
```

### Parameters - showParentModule

value  

### Return Value - showParentModule

## Method visible

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  

### Return Value - visible

## Method webTarget

```xpp
public str webTarget([str value])
```

### Parameters - webTarget

value  

### Return Value - webTarget

