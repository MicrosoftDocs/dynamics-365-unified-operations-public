---
title: Page class
description: This topic describes the Page class.
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

# Class Page

[!include [banner](../../includes/banner.md)]


```xpp
class Page extends Object
```

This Page class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                        | Description                                                              |
|-------------------------------------------------------------------------------|--------------------------------------------------------------------------|
| public boolean actionPaneControlEnabled(str controlName, \[boolean enabled\]) | Sets or gets the enabled property value of a control on the Action Pane. |
| public boolean actionPaneControlVisible(str controlName, \[boolean visible\]) | Sets or gets the visible property value of a control on the Action Pane. |
| public Array activeActionPaneTabNames()                                       |                                                                          |
| public Common activeRecord(str dataSourceName)                                | Gets the active record for the given data source name.                   |
| public str name()                                                             | Gets the name of the page.                                               |
| public PageArgs pageArgs()                                                    | Gets the page arguments.                                                 |
| public xFormRun formRun()                                                     |                                                                          |

## Method actionPaneControlEnabled

Sets or gets the enabled property value of a control on the Action Pane.

```xpp
public boolean actionPaneControlEnabled(str controlName, [boolean enabled])
```

### Parameters - actionPaneControlEnabled

controlName  
A value that specifies whether the Action Pane control is enabled; optional.

<!-- -->

enabled  
A value that specifies whether the Action Pane control is enabled; optional.

### Return Value - actionPaneControlEnabled

A Boolean value that indicates whether the Action Pane control is enabled.

## Method actionPaneControlVisible

Sets or gets the visible property value of a control on the Action Pane.

```xpp
public boolean actionPaneControlVisible(str controlName, [boolean visible])
```

### Parameters - actionPaneControlVisible

controlName  
A value that specifies whether the Action Pane control is visible; optional.

<!-- -->

visible  
A value that specifies whether the Action Pane control is visible; optional.

### Return Value - actionPaneControlVisible

A Boolean value that indicates whether the Action Pane control is visible.

## Method activeActionPaneTabNames

```xpp
public Array activeActionPaneTabNames()
```

### Return Value - activeActionPaneTabNames

## Method activeRecord

Gets the active record for the given data source name.

```xpp
public Common activeRecord(str dataSourceName)
```

### Parameters - activeRecord

dataSourceName  
The name of the data source to search on.

### Return Value - activeRecord

The active record for the given data source.

## Method name

Gets the name of the page.

```xpp
public str name()
```

### Return Value - name

The page name.

## Method pageArgs

Gets the page arguments.

```xpp
public PageArgs pageArgs()
```

### Return Value - pageArgs

The page arguments.

## Method formRun

```xpp
public xFormRun formRun()
```

### Return Value - formRun

