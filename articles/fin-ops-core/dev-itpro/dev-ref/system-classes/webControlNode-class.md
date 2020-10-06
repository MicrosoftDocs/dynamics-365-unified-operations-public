---
title: webControlNode class
description: This topic describes the webControlNode class.
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

# Class webControlNode

[!include [banner](../../includes/banner.md)]

```xpp
class webControlNode extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                                        | Description                                                                                                                                   |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                     | Returns the source code of this node.                                                                                                         |
| public str changedBy(\[str value\])                           | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                       | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])                         | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])                           | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                      | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])                        |                                                                                                                                               |
| public str filename(\[str value\])                            |                                                                                                                                               |
| public List getRelatedWebControls(\[boolean firstLevelOnly\]) | Get a list of web controls that are related to this web control.                                                                              |
| public str helpText(\[str value\])                            | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public str name(\[str value\])                                | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public Guid origin(\[Guid value\])                            |                                                                                                                                               |
| public str relativePath(\[str value\])                        |                                                                                                                                               |
| public str version(\[str value\])                             |                                                                                                                                               |
| ::public static webControlNode createFromFile(str fileName)   |                                                                                                                                               |
| public void AOTsetSource(str source, \[boolean isStatic\])    | Sets the source code of this node.                                                                                                            |

## Method AOTgetSource

Returns the source code of this node.

```xpp
public str AOTgetSource()
```

### Return Value - AOTgetSource

The string that contains source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - AOTgetSource

This function is overridden by nodes that have source code.

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

## Method filename

```xpp
public str filename([str value])
```

### Parameters - filename

value  

### Return Value - filename

## Method getRelatedWebControls

Get a list of web controls that are related to this web control.

```xpp
public List getRelatedWebControls([boolean firstLevelOnly])
```

### Parameters - getRelatedWebControls

firstLevelOnly  
A value that indicates whether only the first level of web controls is checked.

### Return Value - getRelatedWebControls

A list of related web controls.

## Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  

### Return Value - helpText

The string to be displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property dialog box. The help text must not exceed 250 characters.

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method relativePath

```xpp
public str relativePath([str value])
```

### Parameters - relativePath

value  

### Return Value - relativePath

## Method version

```xpp
public str version([str value])
```

### Parameters - version

value  

### Return Value - version

## Method createFromFile

```xpp
public static webControlNode createFromFile(str fileName)
```

### Parameters - createFromFile

fileName  

### Return Value - createFromFile

## Method AOTsetSource

Sets the source code of this node.

```xpp
public void AOTsetSource(str source, [boolean isStatic])
```

### Parameters - AOTsetSource

source  
The value that specifies whether the method is static; optional.

<!-- -->

isStatic  
The value that specifies whether the method is static; optional.

### Remarks - AOTsetSource

This method is overridden by nodes that have source code.

