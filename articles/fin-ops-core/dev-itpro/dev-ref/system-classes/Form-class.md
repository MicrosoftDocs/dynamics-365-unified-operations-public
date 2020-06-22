---
title: Form class
description: This topic describes the Form class.
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

# Class Form

[!include [banner](../../includes/banner.md)]

```xpp
class Form extends TreeNode
```

The Form class represents an instance of a design-time form.

## Remarks

## Examples

## Methods

| Method                                                                                                                           | Description                                                                                                               |
|----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public FormBuildControl addControl(FormControlType controlType, str controlName)                                                 |                                                                                                                           |
| public FormBuildControl addControlEx(str controlClass, str controlName, \[FormBuildControl insertAfter\], \[boolean pushFront\]) |                                                                                                                           |
| public FormBuildDataSource addDataSource(str name, \[str tableName\])                                                            |                                                                                                                           |
| public List rootFormDataSources()                                                                                                |                                                                                                                           |
| public FormBuildDesign addDesign(str name)                                                                                       |                                                                                                                           |
| public Query query(str queryName)                                                                                                |                                                                                                                           |
| public boolean allowPreLoading(\[boolean value\])                                                                                | A Boolean value that determines whether a preloaded instance can be used when the associated FormRun instance is created. |
| public boolean autoCacheUpdate(\[boolean value\])                                                                                |                                                                                                                           |
| public str changedBy(\[str value\])                                                                                              | Gets or sets the name of the user who last changed the application object.                                                |
| public Date changedDate(\[Date value\])                                                                                          | Gets or sets the date an application object was last changed.                                                             |
| public str changedTime(\[str value\])                                                                                            | Gets or sets the time an application object was last changed.                                                             |
| public ChangeGroupMode changeGroupMode(\[ChangeGroupMode value\])                                                                |                                                                                                                           |
| public str createdBy(\[str value\])                                                                                              | Gets or sets the name of the user who created the application object.                                                     |
| public Date creationDate(\[Date value\])                                                                                         | Gets or sets the date an application object was created.                                                                  |
| public str creationTime(\[str value\])                                                                                           |                                                                                                                           |
| public FormBuildDataSource dataSource(AnyType objectSet)                                                                         |                                                                                                                           |
| public int dataSourceCount()                                                                                                     |                                                                                                                           |
| public FormBuildDesign design(\[int designNo\])                                                                                  |                                                                                                                           |
| public int formTemplate(\[int value\])                                                                                           |                                                                                                                           |
| public str interactionClass(\[str value\])                                                                                       |                                                                                                                           |
| public boolean isLoadedForInference()                                                                                            |                                                                                                                           |
| public str name(\[str value\])                                                                                                   | Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object. |
| public Guid origin(\[Guid value\])                                                                                               |                                                                                                                           |
| ::public static boolean formKernelObjectHasMethod(Object kernelObject, str methodName)                                           |                                                                                                                           |
| ::public static boolean formObjectSetHasMethod(FormObjectSet formObjectSet, str methodName)                                      |                                                                                                                           |
| ::public static boolean formRunHasMethod(xFormRun formRun, str methodName)                                                       |                                                                                                                           |
| ::public static str getSetupUserQueryElementName(MenuItemType menuItemType, str menuItemName)                                    |                                                                                                                           |
| public void new(\[str name\], \[boolean buildMode\])                                                                             | Initializes a new instance of the Form class.                                                                             |
| public void inInitializeDesign(\[boolean value\])                                                                                |                                                                                                                           |
| public void save()                                                                                                               |                                                                                                                           |
| public void load(str name, \[boolean buildMode\])                                                                                |                                                                                                                           |
| public void finalize()                                                                                                           |                                                                                                                           |

## Method addControl

```xpp
public FormBuildControl addControl(FormControlType controlType, str controlName)
```

### Parameters - addControl

controlType  

<!-- -->

controlName  

### Return Value - addControl

## Method addControlEx

```xpp
public FormBuildControl addControlEx(str controlClass, str controlName, [FormBuildControl insertAfter], [boolean pushFront])
```

### Parameters - addControlEx

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

<!-- -->

pushFront  

### Return Value - addControlEx

## Method addDataSource

```xpp
public FormBuildDataSource addDataSource(str name, [str tableName])
```

### Parameters - addDataSource

name  

<!-- -->

tableName  

### Return Value - addDataSource

## Method rootFormDataSources

```xpp
public List rootFormDataSources()
```

### Return Value - rootFormDataSources

## Method addDesign

```xpp
public FormBuildDesign addDesign(str name)
```

### Parameters - addDesign

name  

### Return Value - addDesign

## Method query

```xpp
public Query query(str queryName)
```

### Parameters - query

queryName  

### Return Value - query

## Method allowPreLoading

A Boolean value that determines whether a preloaded instance can be used when the associated FormRun instance is created.

```xpp
public boolean allowPreLoading([boolean value])
```

### Parameters - allowPreLoading

value  
true if a preloaded instance can be used when the associated FormRun instance is created; otherwise, false.

### Return Value - allowPreLoading

true if a preloaded instance can be used when the associated FormRun instance is created; otherwise, false.

## Method autoCacheUpdate

```xpp
public boolean autoCacheUpdate([boolean value])
```

### Parameters - autoCacheUpdate

value  

### Return Value - autoCacheUpdate

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

## Method changeGroupMode

```xpp
public ChangeGroupMode changeGroupMode([ChangeGroupMode value])
```

### Parameters - changeGroupMode

value  

### Return Value - changeGroupMode

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
public FormBuildDataSource dataSource(AnyType objectSet)
```

### Parameters - dataSource

objectSet  

### Return Value - dataSource

## Method dataSourceCount

```xpp
public int dataSourceCount()
```

### Return Value - dataSourceCount

## Method design

```xpp
public FormBuildDesign design([int designNo])
```

### Parameters - design

designNo  

### Return Value - design

## Method formTemplate

```xpp
public int formTemplate([int value])
```

### Parameters - formTemplate

value  

### Return Value - formTemplate

## Method interactionClass

```xpp
public str interactionClass([str value])
```

### Parameters - interactionClass

value  

### Return Value - interactionClass

## Method isLoadedForInference

```xpp
public boolean isLoadedForInference()
```

### Return Value - isLoadedForInference

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

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method formKernelObjectHasMethod

```xpp
public static boolean formKernelObjectHasMethod(Object kernelObject, str methodName)
```

### Parameters - formKernelObjectHasMethod

kernelObject  

<!-- -->

methodName  

### Return Value - formKernelObjectHasMethod

## Method formObjectSetHasMethod

```xpp
public static boolean formObjectSetHasMethod(FormObjectSet formObjectSet, str methodName)
```

### Parameters - formObjectSetHasMethod

formObjectSet  

<!-- -->

methodName  

### Return Value - formObjectSetHasMethod

## Method formRunHasMethod

```xpp
public static boolean formRunHasMethod(xFormRun formRun, str methodName)
```

### Parameters - formRunHasMethod

formRun  

<!-- -->

methodName  

### Return Value - formRunHasMethod

## Method getSetupUserQueryElementName

```xpp
public static str getSetupUserQueryElementName(MenuItemType menuItemType, str menuItemName)
```

### Parameters - getSetupUserQueryElementName

menuItemType  

<!-- -->

menuItemName  

### Return Value - getSetupUserQueryElementName

## Method new

Initializes a new instance of the Form class.

```xpp
public void new([str name], [boolean buildMode])
```

### Parameters - new

name  

<!-- -->

buildMode  

## Method inInitializeDesign

```xpp
public void inInitializeDesign([boolean value])
```

### Parameters - inInitializeDesign

value  

## Method save

```xpp
public void save()
```

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

