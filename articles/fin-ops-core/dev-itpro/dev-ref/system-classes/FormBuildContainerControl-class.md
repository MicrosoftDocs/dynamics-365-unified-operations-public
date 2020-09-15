---
title: FormBuildContainerControl class
description: This topic describes the FormBuildContainerControl class.
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

# Class FormBuildContainerControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormBuildContainerControl extends FormBuildControl
```

## Remarks

## Examples

## Methods

| Method                                                                                                      | Description |
|-------------------------------------------------------------------------------------------------------------|-------------|
| public boolean alignControl(\[boolean value\])                                                              |             |
| public boolean allowEdit(\[boolean value\])                                                                 |             |
| public boolean autoDeclaration(\[boolean value\])                                                           |             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    |             |
| public int containerId()                                                                                    |             |
| public str countryRegionCodes(\[str value\])                                                                |             |
| public str dataRelationPath(\[str value\])                                                                  |             |
| public int displayTarget(\[int value\])                                                                     |             |
| public int dragDrop(\[int value\])                                                                          |             |
| public boolean enabled(\[boolean value\])                                                                   |             |
| public int height(int value, \[int mode\])                                                                  |             |
| public int heightMode(\[int value\])                                                                        |             |
| public int heightValue(\[int value\])                                                                       |             |
| public str helpText(\[str value\])                                                                          |             |
| public str hierarchyParent(\[str value\])                                                                   |             |
| public int id()                                                                                             |             |
| public boolean isContainer()                                                                                |             |
| public int left(int value, \[int mode\])                                                                    |             |
| public int leftMode(\[int value\])                                                                          |             |
| public int leftValue(\[int value\])                                                                         |             |
| public int moveControl(int controlId, \[int insertAfterControlId\])                                         |             |
| public str name(\[str value\])                                                                              |             |
| public int neededPermission(\[int value\])                                                                  |             |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   |             |
| public boolean skip(\[boolean value\])                                                                      |             |
| public int top(int value, \[int mode\])                                                                     |             |
| public int topMode(\[int value\])                                                                           |             |
| public int topValue(\[int value\])                                                                          |             |
| public int type(\[int value\])                                                                              |             |
| public int userData(\[int value\])                                                                          |             |
| public int userDataItem(\[int value\])                                                                      |             |
| public int userDataItems(\[int value\])                                                                     |             |
| public boolean useUserLayout(\[boolean value\])                                                             |             |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                |             |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      |             |
| public int verticalSpacingValue(\[int value\])                                                              |             |
| public boolean visible(\[boolean value\])                                                                   |             |
| public int width(int value, \[int mode\])                                                                   |             |
| public int widthMode(\[int value\])                                                                         |             |
| public int widthValue(\[int value\])                                                                        |             |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |             |

## Method alignControl

```xpp
public boolean alignControl([boolean value])
```

### Parameters - alignControl

value  

### Return Value - alignControl

## Method allowEdit

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

## Method autoDeclaration

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  

### Return Value - autoDeclaration

## Method configurationKey

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  

### Return Value - configurationKey

## Method containerId

```xpp
public int containerId()
```

### Return Value - containerId

## Method countryRegionCodes

```xpp
public str countryRegionCodes([str value])
```

### Parameters - countryRegionCodes

value  

### Return Value - countryRegionCodes

## Method dataRelationPath

```xpp
public str dataRelationPath([str value])
```

### Parameters - dataRelationPath

value  

### Return Value - dataRelationPath

## Method displayTarget

```xpp
public int displayTarget([int value])
```

### Parameters - displayTarget

value  

### Return Value - displayTarget

## Method dragDrop

```xpp
public int dragDrop([int value])
```

### Parameters - dragDrop

value  

### Return Value - dragDrop

## Method enabled

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

## Method height

```xpp
public int height(int value, [int mode])
```

### Parameters - height

value  

<!-- -->

mode  

### Return Value - height

## Method heightMode

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  

### Return Value - heightMode

## Method heightValue

```xpp
public int heightValue([int value])
```

### Parameters - heightValue

value  

### Return Value - heightValue

## Method helpText

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  

### Return Value - helpText

## Method hierarchyParent

```xpp
public str hierarchyParent([str value])
```

### Parameters - hierarchyParent

value  

### Return Value - hierarchyParent

## Method id

```xpp
public int id()
```

### Return Value - id

## Method isContainer

```xpp
public boolean isContainer()
```

### Return Value - isContainer

## Method left

```xpp
public int left(int value, [int mode])
```

### Parameters - left

value  

<!-- -->

mode  

### Return Value - left

## Method leftMode

```xpp
public int leftMode([int value])
```

### Parameters - leftMode

value  

### Return Value - leftMode

## Method leftValue

```xpp
public int leftValue([int value])
```

### Parameters - leftValue

value  

### Return Value - leftValue

## Method moveControl

```xpp
public int moveControl(int controlId, [int insertAfterControlId])
```

### Parameters - moveControl

controlId  

<!-- -->

insertAfterControlId  

### Return Value - moveControl

## Method name

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

## Method neededPermission

```xpp
public int neededPermission([int value])
```

### Parameters - neededPermission

value  

### Return Value - neededPermission

## Method securityKey

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  

### Return Value - securityKey

## Method skip

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  

### Return Value - skip

## Method top

```xpp
public int top(int value, [int mode])
```

### Parameters - top

value  

<!-- -->

mode  

### Return Value - top

## Method topMode

```xpp
public int topMode([int value])
```

### Parameters - topMode

value  

### Return Value - topMode

## Method topValue

```xpp
public int topValue([int value])
```

### Parameters - topValue

value  

### Return Value - topValue

## Method type

```xpp
public int type([int value])
```

### Parameters - type

value  

### Return Value - type

## Method userData

```xpp
public int userData([int value])
```

### Parameters - userData

value  

### Return Value - userData

## Method userDataItem

```xpp
public int userDataItem([int value])
```

### Parameters - userDataItem

value  

### Return Value - userDataItem

## Method userDataItems

```xpp
public int userDataItems([int value])
```

### Parameters - userDataItems

value  

### Return Value - userDataItems

## Method useUserLayout

```xpp
public boolean useUserLayout([boolean value])
```

### Parameters - useUserLayout

value  

### Return Value - useUserLayout

## Method verticalSpacing

```xpp
public int verticalSpacing([int value], [AutoMode mode])
```

### Parameters - verticalSpacing

value  

<!-- -->

mode  

### Return Value - verticalSpacing

## Method verticalSpacingMode

```xpp
public AutoMode verticalSpacingMode([AutoMode mode])
```

### Parameters - verticalSpacingMode

mode  

### Return Value - verticalSpacingMode

## Method verticalSpacingValue

```xpp
public int verticalSpacingValue([int value])
```

### Parameters - verticalSpacingValue

value  

### Return Value - verticalSpacingValue

## Method visible

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  

### Return Value - visible

## Method width

```xpp
public int width(int value, [int mode])
```

### Parameters - width

value  

<!-- -->

mode  

### Return Value - width

## Method widthMode

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  

### Return Value - widthMode

## Method widthValue

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  

### Return Value - widthValue

## Method registerOverrideMethod

```xpp
public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])
```

### Parameters - registerOverrideMethod

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

