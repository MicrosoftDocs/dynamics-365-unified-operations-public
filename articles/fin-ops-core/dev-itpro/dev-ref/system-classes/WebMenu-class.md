---
title: WebMenu class
description: This topic describes the WebMenu class.
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

# Class WebMenu

[!include [banner](../../includes/banner.md)]

```xpp
class WebMenu extends TreeNode
```

The WebMenu class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                   | Description                                                                                                                                   |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                      | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                                  | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])                                    | Gets or sets the time an application object was last changed.                                                                                 |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public str createdBy(\[str value\])                                      | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                                 | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])                                   |                                                                                                                                               |
| public boolean highlightSelected(\[boolean value\])                      |                                                                                                                                               |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                         |
| public str menuItemName(\[str value\])                                   |                                                                                                                                               |
| public WebMenuItemType menuItemType(\[WebMenuItemType value\])           |                                                                                                                                               |
| public str menuName()                                                    |                                                                                                                                               |
| public str name(\[str value\])                                           | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public int neededAccessLevel(\[int value\])                              | Gets or sets the neededAccessLevel property for the MenuFunction class.                                                                       |
| public Guid origin(\[Guid value\])                                       |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                               |
| public boolean setCompany(\[boolean value\])                             |                                                                                                                                               |
| public boolean showParentModule(\[boolean value\])                       |                                                                                                                                               |
| public str webTarget(\[str value\])                                      |                                                                                                                                               |
| public void addSeparator()                                               |                                                                                                                                               |
| public void makeMenu(Object outputClass)                                 |                                                                                                                                               |
| public void addSubmenu(str name)                                         |                                                                                                                                               |
| public void new(str Name)                                                | Initializes a new instance of the TreeNode class.                                                                                             |
| public void addMenuitem(WebMenuFunction webMenuFunction)                 |                                                                                                                                               |

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

## Method configurationKey

Gets or sets the configuration key that is assigned to the control.

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  

### Return Value - configurationKey

The identifier of the configuration key that is assigned to the control.

### Remarks - configurationKey

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

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

## Method highlightSelected

```xpp
public boolean highlightSelected([boolean value])
```

### Parameters - highlightSelected

value  

### Return Value - highlightSelected

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

## Method menuName

```xpp
public str menuName()
```

### Return Value - menuName

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, or classes.

## Method neededAccessLevel

Gets or sets the neededAccessLevel property for the MenuFunction class.

```xpp
public int neededAccessLevel([int value])
```

### Parameters - neededAccessLevel

value  

### Return Value - neededAccessLevel

The current value of the neededAccessLevel property.

### Remarks - neededAccessLevel

The possible values for the AccessType system enumeration value are as follows:

-   AccessType::NoAccess
-   AccessType::View
-   AccessType::Edit
-   AccessType::Add
-   AccessType::Delete

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method securityKey

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  

### Return Value - securityKey

## Method setCompany

```xpp
public boolean setCompany([boolean value])
```

### Parameters - setCompany

value  

### Return Value - setCompany

## Method showParentModule

```xpp
public boolean showParentModule([boolean value])
```

### Parameters - showParentModule

value  

### Return Value - showParentModule

## Method webTarget

```xpp
public str webTarget([str value])
```

### Parameters - webTarget

value  

### Return Value - webTarget

## Method addSeparator

```xpp
public void addSeparator()
```

## Method makeMenu

```xpp
public void makeMenu(Object outputClass)
```

### Parameters - makeMenu

outputClass  

## Method addSubmenu

```xpp
public void addSubmenu(str name)
```

### Parameters - addSubmenu

name  

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new(str Name)
```

### Parameters - new

Name  

## Method addMenuitem

```xpp
public void addMenuitem(WebMenuFunction webMenuFunction)
```

### Parameters - addMenuitem

webMenuFunction  

