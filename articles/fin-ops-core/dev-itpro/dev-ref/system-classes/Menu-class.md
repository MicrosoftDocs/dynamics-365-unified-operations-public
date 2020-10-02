---
title: Menu class
description: This topic describes the Menu class.
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

# Class Menu

[!include [banner](../../includes/banner.md)]

```xpp
class Menu extends TreeNode
```

The Menu system class lets you configure and run any of the menu objects from code.

## Remarks

The TreeNode system class serves as a more general approach to the menus in the Application Object Tree (AOT). You use the Menu class to create or manipulate the menus contents, such as submenus and menu items. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                   | Description                                                                                                               |
|--------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                      | Gets or sets the name of the user who last changed the application object.                                                |
| public Date changedDate(\[Date value\])                                  | Gets or sets the date an application object was last changed.                                                             |
| public str changedTime(\[str value\])                                    | Gets or sets the time an application object was last changed.                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                       |
| public str countryRegionCodes(\[str value\])                             |                                                                                                                           |
| public str createdBy(\[str value\])                                      | Gets or sets the name of the user who created the application object.                                                     |
| public Date creationDate(\[Date value\])                                 | Gets or sets the date an application object was created.                                                                  |
| public str creationTime(\[str value\])                                   |                                                                                                                           |
| public str disabledImage(\[str value\])                                  | Gets or sets the disabled image of the button.                                                                            |
| public int disabledImageLocation(\[int value\])                          |                                                                                                                           |
| public int disabledResource(\[int value\])                               | Gets or sets the resource ID of the image to use as the disabled button image.                                            |
| public int imageLocation(\[int value\])                                  |                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                     |
| public str menuFunctionName(\[str name\])                                |                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                           |
| public str menuName()                                                    |                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object. |
| public int neededAccessLevel(\[int value\])                              | Gets or sets the neededAccessLevel property for the MenuFunction class.                                                   |
| public str normalImage(\[str value\])                                    |                                                                                                                           |
| public int normalResource(\[int value\])                                 |                                                                                                                           |
| public Guid origin(\[Guid value\])                                       |                                                                                                                           |
| public str parameter(\[str parameter\])                                  |                                                                                                                           |
| public str parameters(\[str value\])                                     | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.                    |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                           |
| public boolean setCompany(\[boolean value\])                             |                                                                                                                           |
| public str shortCut(\[str value\])                                       |                                                                                                                           |
| public boolean showParentModule(\[boolean value\])                       |                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                           |
| public void save()                                                       |                                                                                                                           |
| public void new(str Name)                                                | Initializes a new instance of the TreeNode class.                                                                         |
| public void makeWebMenu(Object outputClass)                              |                                                                                                                           |
| public void addMenuitem(xMenuFunction menuFunction)                      | Adds a menu item to the menu.                                                                                             |
| public void setTreeNodeName(str name)                                    |                                                                                                                           |
| public void addMenuReference(Menu menu)                                  |                                                                                                                           |
| public void addSubmenu(str name)                                         | Adds a submenu to the menu.                                                                                               |
| public void addSeparator()                                               | Adds a menu separator to the menu.                                                                                        |

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

## Method countryRegionCodes

```xpp
public str countryRegionCodes([str value])
```

### Parameters - countryRegionCodes

value  

### Return Value - countryRegionCodes

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

## Method disabledImage

Gets or sets the disabled image of the button.

```xpp
public str disabledImage([str value])
```

### Parameters - disabledImage

value  

### Return Value - disabledImage

The full name of an image file. The system supports all of the GDI-supported image formats.

### Remarks - disabledImage

This property has precedence over the disabledResource property . It is used if both of these properties are set.

## Method disabledImageLocation

```xpp
public int disabledImageLocation([int value])
```

### Parameters - disabledImageLocation

value  

### Return Value - disabledImageLocation

## Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

```xpp
public int disabledResource([int value])
```

### Parameters - disabledResource

value  

### Return Value - disabledResource

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

## Method imageLocation

```xpp
public int imageLocation([int value])
```

### Parameters - imageLocation

value  

### Return Value - imageLocation

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

## Method menuName

```xpp
public str menuName()
```

### Return Value - menuName

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

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

-   AccessType::NoAccess.
-   AccessType::View.
-   AccessType::Edit.
-   AccessType::Add.
-   AccessType::Delete.

## Method normalImage

```xpp
public str normalImage([str value])
```

### Parameters - normalImage

value  

### Return Value - normalImage

## Method normalResource

```xpp
public int normalResource([int value])
```

### Parameters - normalResource

value  

### Return Value - normalResource

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

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

## Method save

```xpp
public void save()
```

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new(str Name)
```

### Parameters - new

Name  

## Method makeWebMenu

```xpp
public void makeWebMenu(Object outputClass)
```

### Parameters - makeWebMenu

outputClass  

## Method addMenuitem

Adds a menu item to the menu.

```xpp
public void addMenuitem(xMenuFunction menuFunction)
```

### Parameters - addMenuitem

menuFunction  
The menu item to add.

## Method setTreeNodeName

```xpp
public void setTreeNodeName(str name)
```

### Parameters - setTreeNodeName

name  

## Method addMenuReference

```xpp
public void addMenuReference(Menu menu)
```

### Parameters - addMenuReference

menu  

## Method addSubmenu

Adds a submenu to the menu.

```xpp
public void addSubmenu(str name)
```

### Parameters - addSubmenu

name  
A string expression that evaluates to the name of the submenu to add to the menu.

## Method addSeparator

Adds a menu separator to the menu.

```xpp
public void addSeparator()
```

