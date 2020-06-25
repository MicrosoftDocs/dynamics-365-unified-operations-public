---
title: DataSet class
description: This topic describes the DataSet class.
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

# Class DataSet

[!include [banner](../../includes/banner.md)]

```xpp
class DataSet extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                                  | Description                                                                                                                       |
|---------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public FormBuildDataSource addDataSource(str name)      |                                                                                                                                   |
| public str changedBy(\[str value\])                     | Gets or sets the name of the user who last changed the application object.                                                        |
| public Date changedDate(\[Date value\])                 | Gets or sets the date an application object was last changed.                                                                     |
| public str changedTime(\[str value\])                   | Gets or sets the time an application object was last changed.                                                                     |
| public str createdBy(\[str value\])                     | Gets or sets the name of the user who created the application object.                                                             |
| public Date creationDate(\[Date value\])                | Gets or sets the date an application object was created.                                                                          |
| public str creationTime(\[str value\])                  |                                                                                                                                   |
| public FormBuildDataSource dataSource(int dataSourceNo) |                                                                                                                                   |
| public int dataSourceCount()                            |                                                                                                                                   |
| public str name(\[str value\])                          | Gets or sets the name used in code to identify a form, report, table, query, or other application object. |
| public Guid origin(\[Guid value\])                      |                                                                                                                                   |
| public void load(str name, \[boolean buildMode\])       |                                                                                                                                   |
| public void finalize()                                  |                                                                                                                                   |
| public void new(\[str name\], \[boolean buildMode\])    | Initializes a new instance of the TreeNode class.                                                                                 |
| public void save()                                      |                                                                                                                                   |

## Method addDataSource

```xpp
public FormBuildDataSource addDataSource(str name)
```

### Parameters - addDataSource

name  

### Return Value - addDataSource

## Method changedBy

Gets or sets the name of the user who last changed the application object.

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  

### Return Value - changedBy

The name of the user.

## Method changedDate

Gets or sets the date an application object was last changed.

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  

### Return Value - changedDate

The date an application object was last changed.

## Method changedTime

Gets or sets the time an application object was last changed.

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  

### Return Value - changedTime

The time an application object was last changed.

## Method createdBy

Gets or sets the name of the user who created the application object.

```xpp
public str createdBy([str value])
```

### Parameters - createdBy

value  

### Return Value - createdBy

The name of the user.

## Method creationDate

Gets or sets the date an application object was created.

```xpp
public Date creationDate([Date value])
```

### Parameters - creationDate

value  

### Return Value - creationDate

The date an application object was created.

## Method creationTime

```xpp
public str creationTime([str value])
```

### Parameters - creationTime

value  

### Return Value - creationTime

## Method dataSource

```xpp
public FormBuildDataSource dataSource(int dataSourceNo)
```

### Parameters - dataSource

dataSourceNo  

### Return Value - dataSource

## Method dataSourceCount

```xpp
public int dataSourceCount()
```

### Return Value - dataSourceCount

## Method name

Gets or sets the name used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, classes, and so on.

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method load

```xpp
public void load(str name, [boolean buildMode])
```

### Parameters - load

name  

<!-- -->

buildMode  

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new([str name], [boolean buildMode])
```

### Parameters - new

name  

<!-- -->

buildMode  

## Method save

```xpp
public void save()
```

