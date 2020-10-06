---
title: xVersionControl class
description: This topic describes the xVersionControl class.
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

# Class xVersionControl

[!include [banner](../../includes/banner.md)]

```xpp
class xVersionControl extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                            | Description                                              |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| public boolean allowCreate(TreeNode node)                                                                                                                         |                                                          |
| public boolean allowDelete(TreeNode node)                                                                                                                         |                                                          |
| public boolean allowEdit(TreeNode node)                                                                                                                           |                                                          |
| public boolean allowRename(TreeNode node)                                                                                                                         |                                                          |
| public boolean checkOut(TreeNode node)                                                                                                                            |                                                          |
| public boolean create(TreeNode node)                                                                                                                              |                                                          |
| public boolean delete(TreeNode node)                                                                                                                              |                                                          |
| public int getAvailableId(UtilElementType objectType, UtilEntryLevel layer, \[int parentId\], \[IdAllocationSchema idAllocationSchema\], \[boolean inheritance\]) |                                                          |
| public int getAvailableLabelId(str labelFile, str language, \[IdAllocationSchema idAllocationSchema\])                                                            |                                                          |
| public boolean ideIntegration()                                                                                                                                   |                                                          |
| public boolean moveToModel(TreeNode node, int modelId)                                                                                                            |                                                          |
| public boolean rename(TreeNode node, str newname)                                                                                                                 |                                                          |
| public boolean undoCheckOut(TreeNode node, \[boolean showDialog\])                                                                                                |                                                          |
| public Set unwantedObjectTypes()                                                                                                                                  |                                                          |
| public void colorAOT()                                                                                                                                            |                                                          |
| public void save(TreeNode node)                                                                                                                                   |                                                          |
| public void showHistory(TreeNode node)                                                                                                                            |                                                          |
| public void updateCheckedOutList(Set checkedOutObjects)                                                                                                           |                                                          |
| public void getLatestVersion(\[TreeNode node\], \[boolean delLocalFiles\])                                                                                        |                                                          |
| public void checkIn(TreeNode node)                                                                                                                                |                                                          |
| public void new()                                                                                                                                                 | Initializes a new instance of the xVersionControl class. |
| public void reload()                                                                                                                                              |                                                          |
| public void getLabelVersion(\[TreeNode node\], \[str label\])                                                                                                     |                                                          |

## Method allowCreate

```xpp
public boolean allowCreate(TreeNode node)
```

### Parameters - allowCreate

node  

### Return Value - allowCreate

## Method allowDelete

```xpp
public boolean allowDelete(TreeNode node)
```

### Parameters - allowDelete

node  

### Return Value - allowDelete

## Method allowEdit

```xpp
public boolean allowEdit(TreeNode node)
```

### Parameters - allowEdit

node  

### Return Value - allowEdit

## Method allowRename

```xpp
public boolean allowRename(TreeNode node)
```

### Parameters - allowRename

node  

### Return Value - allowRename

## Method checkOut

```xpp
public boolean checkOut(TreeNode node)
```

### Parameters - checkOut

node  

### Return Value - checkOut

## Method create

```xpp
public boolean create(TreeNode node)
```

### Parameters - create

node  

### Return Value - create

## Method delete

```xpp
public boolean delete(TreeNode node)
```

### Parameters - delete

node  

### Return Value - delete

## Method getAvailableId

```xpp
public int getAvailableId(UtilElementType objectType, UtilEntryLevel layer, [int parentId], [IdAllocationSchema idAllocationSchema], [boolean inheritance])
```

### Parameters - getAvailableId

objectType  

<!-- -->

layer  

<!-- -->

parentId  

<!-- -->

idAllocationSchema  

<!-- -->

inheritance  

### Return Value - getAvailableId

## Method getAvailableLabelId

```xpp
public int getAvailableLabelId(str labelFile, str language, [IdAllocationSchema idAllocationSchema])
```

### Parameters - getAvailableLabelId

labelFile  

<!-- -->

language  

<!-- -->

idAllocationSchema  

### Return Value - getAvailableLabelId

## Method ideIntegration

```xpp
public boolean ideIntegration()
```

### Return Value - ideIntegration

## Method moveToModel

```xpp
public boolean moveToModel(TreeNode node, int modelId)
```

### Parameters - moveToModel

node  

<!-- -->

modelId  

### Return Value - moveToModel

## Method rename

```xpp
public boolean rename(TreeNode node, str newname)
```

### Parameters - rename

node  

<!-- -->

newname  

### Return Value - rename

## Method undoCheckOut

```xpp
public boolean undoCheckOut(TreeNode node, [boolean showDialog])
```

### Parameters - undoCheckOut

node  

<!-- -->

showDialog  

### Return Value - undoCheckOut

## Method unwantedObjectTypes

```xpp
public Set unwantedObjectTypes()
```

### Return Value - unwantedObjectTypes

## Method colorAOT

```xpp
public void colorAOT()
```

## Method save

```xpp
public void save(TreeNode node)
```

### Parameters - save

node  

## Method showHistory

```xpp
public void showHistory(TreeNode node)
```

### Parameters - showHistory

node  

## Method updateCheckedOutList

```xpp
public void updateCheckedOutList(Set checkedOutObjects)
```

### Parameters - updateCheckedOutList

checkedOutObjects  

## Method getLatestVersion

```xpp
public void getLatestVersion([TreeNode node], [boolean delLocalFiles])
```

### Parameters - getLatestVersion

node  

<!-- -->

delLocalFiles  

## Method checkIn

```xpp
public void checkIn(TreeNode node)
```

### Parameters - checkIn

node  

## Method new

Initializes a new instance of the xVersionControl class.

```xpp
public void new()
```

## Method reload

```xpp
public void reload()
```

## Method getLabelVersion

```xpp
public void getLabelVersion([TreeNode node], [str label])
```

### Parameters - getLabelVersion

node  

<!-- -->

label  



