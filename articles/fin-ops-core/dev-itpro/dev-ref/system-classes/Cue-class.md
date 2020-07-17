---
title: Cue class
description: This topic describes the Cue class.
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

# Class Cue

[!include [banner](../../includes/banner.md)]

```xpp
class Cue extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                         | Description                                                                                                                               |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])            | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])        | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])          | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])            | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])       | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])         |                                                                                                                                           |
| public int cueMax(\[int value\])               |                                                                                                                                           |
| public str dataField(\[str value\])            |                                                                                                                                           |
| public str label(\[str value\])                | Gets or sets the label for a control.                                                                                                     |
| public str LabelId()                           |                                                                                                                                           |
| public str menuItemName(\[str value\])         |                                                                                                                                           |
| public str name(\[str value\])                 | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public Guid origin(\[Guid value\])             |                                                                                                                                           |
| public str previewPartReference(\[str value\]) |                                                                                                                                           |
| public boolean showAlert(\[boolean value\])    |                                                                                                                                           |
| public int showAlertValue(\[int value\])       |                                                                                                                                           |
| public int showAlertWhen(\[int value\])        |                                                                                                                                           |
| public boolean showSum(\[boolean value\])      |                                                                                                                                           |
| public str table(\[str value\])                | Gets or sets the table ID associated with the object.                                                                                     |
| public void new(str cueName)                   | Initializes a new instance of the TreeNode class.                                                                                         |

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

## Method cueMax

```xpp
public int cueMax([int value])
```

### Parameters - cueMax

value  

### Return Value - cueMax

## Method dataField

```xpp
public str dataField([str value])
```

### Parameters - dataField

value  

### Return Value - dataField

## Method label

Gets or sets the label for a control.

```xpp
public str label([str value])
```

### Parameters - label

value  

### Return Value - label

The current value of the label string.

### Remarks - label

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

## Method LabelId

```xpp
public str LabelId()
```

### Return Value - LabelId

## Method menuItemName

```xpp
public str menuItemName([str value])
```

### Parameters - menuItemName

value  

### Return Value - menuItemName

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, and classes.

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method previewPartReference

```xpp
public str previewPartReference([str value])
```

### Parameters - previewPartReference

value  

### Return Value - previewPartReference

## Method showAlert

```xpp
public boolean showAlert([boolean value])
```

### Parameters - showAlert

value  

### Return Value - showAlert

## Method showAlertValue

```xpp
public int showAlertValue([int value])
```

### Parameters - showAlertValue

value  

### Return Value - showAlertValue

## Method showAlertWhen

```xpp
public int showAlertWhen([int value])
```

### Parameters - showAlertWhen

value  

### Return Value - showAlertWhen

## Method showSum

```xpp
public boolean showSum([boolean value])
```

### Parameters - showSum

value  

### Return Value - showSum

## Method table

Gets or sets the table ID associated with the object.

```xpp
public str table([str value])
```

### Parameters - table

value  

### Return Value - table

The current value of the table ID associated with the object.

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new(str cueName)
```

### Parameters - new

cueName  

