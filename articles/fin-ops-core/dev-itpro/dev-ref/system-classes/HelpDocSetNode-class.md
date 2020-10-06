---
title: HelpDocSetNode class
description: This topic describes the HelpDocSetNode class.
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

# Class HelpDocSetNode

[!include [banner](../../includes/banner.md)]

```xpp
class HelpDocSetNode extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                                     | Description                                                                |
|------------------------------------------------------------|----------------------------------------------------------------------------|
| public boolean addToApplicationHelpMenu(\[boolean value\]) |                                                                            |
| public boolean addToDeveloperHelpMenu(\[boolean value\])   |                                                                            |
| public str changedBy(\[str value\])                        | Gets or sets the name of the user who last changed the application object. |
| public Date changedDate(\[Date value\])                    | Gets or sets the date an application object was last changed.              |
| public str changedTime(\[str value\])                      | Gets or sets the time an application object was last changed.              |
| public int contentLocation(\[int value\])                  |                                                                            |
| public str createdBy(\[str value\])                        | Gets or sets the name of the user who created the application object.      |
| public Date creationDate(\[Date value\])                   | Gets or sets the date an application object was created.                   |
| public str creationTime(\[str value\])                     |                                                                            |
| public boolean developerDocumentSet(\[boolean value\])     |                                                                            |
| public str documentSetDescription(\[str value\])           |                                                                            |
| public str documentSetName(\[str value\])                  |                                                                            |
| public str helpProviderClass(\[str value\])                |                                                                            |
| public Guid origin(\[Guid value\])                         |                                                                            |
| public boolean userDocumentSet(\[boolean value\])          |                                                                            |
| public void new(str DocSetName)                            | Initializes a new instance of the TreeNode class.                          |

## Method addToApplicationHelpMenu

```xpp
public boolean addToApplicationHelpMenu([boolean value])
```

### Parameters - addToApplicationHelpMenu

value  

### Return Value - addToApplicationHelpMenu

## Method addToDeveloperHelpMenu

```xpp
public boolean addToDeveloperHelpMenu([boolean value])
```

### Parameters - addToDeveloperHelpMenu

value  

### Return Value - addToDeveloperHelpMenu

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

## Method contentLocation

```xpp
public int contentLocation([int value])
```

### Parameters - contentLocation

value  

### Return Value - contentLocation

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

## Method developerDocumentSet

```xpp
public boolean developerDocumentSet([boolean value])
```

### Parameters - developerDocumentSet

value  

### Return Value - developerDocumentSet

## Method documentSetDescription

```xpp
public str documentSetDescription([str value])
```

### Parameters - documentSetDescription

value  

### Return Value - documentSetDescription

## Method documentSetName

```xpp
public str documentSetName([str value])
```

### Parameters - documentSetName

value  

### Return Value - documentSetName

## Method helpProviderClass

```xpp
public str helpProviderClass([str value])
```

### Parameters - helpProviderClass

value  

### Return Value - helpProviderClass

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method userDocumentSet

```xpp
public boolean userDocumentSet([boolean value])
```

### Parameters - userDocumentSet

value  

### Return Value - userDocumentSet

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new(str DocSetName)
```

### Parameters - new

DocSetName  

