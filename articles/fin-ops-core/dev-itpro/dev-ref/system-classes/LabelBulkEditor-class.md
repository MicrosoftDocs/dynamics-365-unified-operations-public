---
title: LabelBulkEditor class
description: This topic describes the LabelBulkEditor class.
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

# Class LabelBulkEditor

[!include [banner](../../includes/banner.md)]

```xpp
class LabelBulkEditor extends Object
```

The LabelBulkEditor class is used to quickly modify label files.

## Remarks

The LabelBulkEditor class is instantiated through the Label.bulkEditor() method. The label file is opened for modification when the instance of the class is created, and the label file is closed when the instance has garbage collected.

## Examples

## Methods

| Method                                                      | Description                                                                  |
|-------------------------------------------------------------|------------------------------------------------------------------------------|
| public boolean delete(str label)                            | Deletes a specified label.                                                   |
| public boolean modify(str label, str text, \[str comment\]) | Modifies the text and comment that are associated with a specified label ID. |
| public void new()                                           | Initializes an instance of the LabelBulkEditor class.                        |

## Method delete

Deletes a specified label.

```xpp
public boolean delete(str label)
```

### Parameters - delete

label  
A string that specifies the label ID. The string must include an at sign (@) followed by a label file ID and a number.

### Return Value - delete

true if the label is deleted; otherwise, false.

## Method modify

Modifies the text and comment that are associated with a specified label ID.

```xpp
public boolean modify(str label, str text, [str comment])
```

### Parameters - modify

label  
A string that specifies the comment that is associated with the label ID.

<!-- -->

text  
A string that specifies the comment that is associated with the label ID.

<!-- -->

comment  
A string that specifies the comment that is associated with the label ID.

### Return Value - modify

true if the label is modified; otherwise, false.

## Method new

Initializes an instance of the LabelBulkEditor class.

```xpp
public void new()
```

