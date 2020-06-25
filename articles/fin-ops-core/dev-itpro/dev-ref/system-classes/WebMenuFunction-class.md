---
title: WebMenuFunction class
description: This topic describes the WebMenuFunction class.
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

# Class WebMenuFunction

[!include [banner](../../includes/banner.md)]

```xpp
class WebMenuFunction extends SecureNode
```

The WebMenuFunction class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                                           | Description                                                                                                                                   |
|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                                              | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                                                          | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])                                                            | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])                                                              | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                                                         | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])                                                           |                                                                                                                                               |
| public str helpText(\[str value\])                                                               | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public str label(\[str value\])                                                                  | Gets or sets the label for a control.                                                                                                         |
| public str name(\[str value\])                                                                   | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public Guid origin(\[Guid value\])                                                               |                                                                                                                                               |
| ::public static WebMenuFunction createWebMenuFunction(str name, WebMenuItemType webMenuItemType) |                                                                                                                                               |

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

## Method createWebMenuFunction

```xpp
public static WebMenuFunction createWebMenuFunction(str name, WebMenuItemType webMenuItemType)
```

### Parameters - createWebMenuFunction

name  

<!-- -->

webMenuItemType  

### Return Value - createWebMenuFunction

