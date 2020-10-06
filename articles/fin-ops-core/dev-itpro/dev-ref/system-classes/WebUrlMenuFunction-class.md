---
title: WebUrlMenuFunction class
description: This topic describes the WebUrlMenuFunction class.
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

# Class WebUrlMenuFunction

[!include [banner](../../includes/banner.md)]

```xpp
class WebUrlMenuFunction extends WebMenuFunction
```

The WebUrlMenuFunction class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                | Description                                                                                            |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| public boolean big(\[boolean value\])                 |                                                                                                        |
| public int closeDialogBehavior(\[int value\])         |                                                                                                        |
| public int correctPermissions(\[int value\])          |                                                                                                        |
| public int createPermissions(\[int value\])           |                                                                                                        |
| public int deletePermissions(\[int value\])           |                                                                                                        |
| public boolean hideActionPane(\[boolean value\])      |                                                                                                        |
| public boolean homePage(\[boolean value\])            |                                                                                                        |
| public int imageLocation(\[int value\])               |                                                                                                        |
| public str linkedPermissionObject(\[str value\])      |                                                                                                        |
| public str linkedPermissionObjectChild(\[str value\]) |                                                                                                        |
| public int linkedPermissionType(\[int value\])        |                                                                                                        |
| public int maintainUserLicense(\[int value\])         | Microsoft internal use only.                                                                           |
| public boolean multiSelect(\[boolean value\])         |                                                                                                        |
| public boolean needsRecord(\[boolean value\])         |                                                                                                        |
| public str normalImage(\[str value\])                 |                                                                                                        |
| public int normalResource(\[int value\])              |                                                                                                        |
| public Guid origin(\[Guid value\])                    |                                                                                                        |
| public str pageDefinition(\[str value\])              |                                                                                                        |
| public str parameters(\[str value\])                  | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class. |
| public int readPermissions(\[int value\])             |                                                                                                        |
| public int updatePermissions(\[int value\])           |                                                                                                        |
| public str uRL(\[str value\])                         |                                                                                                        |
| public int viewUserLicense(\[int value\])             | Microsoft internal use only.                                                                           |
| public int windowMode(\[int value\])                  |                                                                                                        |
| public str windowParameters(\[str value\])            |                                                                                                        |
| public int windowSize(\[int value\])                  |                                                                                                        |
| public void new(str name)                             | Initializes a new instance of the TreeNode class.                                                      |

## Method big

```xpp
public boolean big([boolean value])
```

### Parameters - big

value  

### Return Value - big

## Method closeDialogBehavior

```xpp
public int closeDialogBehavior([int value])
```

### Parameters - closeDialogBehavior

value  

### Return Value - closeDialogBehavior

## Method correctPermissions

```xpp
public int correctPermissions([int value])
```

### Parameters - correctPermissions

value  

### Return Value - correctPermissions

## Method createPermissions

```xpp
public int createPermissions([int value])
```

### Parameters - createPermissions

value  

### Return Value - createPermissions

## Method deletePermissions

```xpp
public int deletePermissions([int value])
```

### Parameters - deletePermissions

value  

### Return Value - deletePermissions

## Method hideActionPane

```xpp
public boolean hideActionPane([boolean value])
```

### Parameters - hideActionPane

value  

### Return Value - hideActionPane

## Method homePage

```xpp
public boolean homePage([boolean value])
```

### Parameters - homePage

value  

### Return Value - homePage

## Method imageLocation

```xpp
public int imageLocation([int value])
```

### Parameters - imageLocation

value  

### Return Value - imageLocation

## Method linkedPermissionObject

```xpp
public str linkedPermissionObject([str value])
```

### Parameters - linkedPermissionObject

value  

### Return Value - linkedPermissionObject

## Method linkedPermissionObjectChild

```xpp
public str linkedPermissionObjectChild([str value])
```

### Parameters - linkedPermissionObjectChild

value  

### Return Value - linkedPermissionObjectChild

## Method linkedPermissionType

```xpp
public int linkedPermissionType([int value])
```

### Parameters - linkedPermissionType

value  

### Return Value - linkedPermissionType

## Method maintainUserLicense

Microsoft internal use only.

```xpp
public int maintainUserLicense([int value])
```

### Parameters - maintainUserLicense

value  
The new user license.

### Return Value - maintainUserLicense

The user license.

## Method multiSelect

```xpp
public boolean multiSelect([boolean value])
```

### Parameters - multiSelect

value  

### Return Value - multiSelect

## Method needsRecord

```xpp
public boolean needsRecord([boolean value])
```

### Parameters - needsRecord

value  

### Return Value - needsRecord

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

## Method pageDefinition

```xpp
public str pageDefinition([str value])
```

### Parameters - pageDefinition

value  

### Return Value - pageDefinition

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

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. Objects will ignore passed, unrecognized parameters.

## Method readPermissions

```xpp
public int readPermissions([int value])
```

### Parameters - readPermissions

value  

### Return Value - readPermissions

## Method updatePermissions

```xpp
public int updatePermissions([int value])
```

### Parameters - updatePermissions

value  

### Return Value - updatePermissions

## Method uRL

```xpp
public str uRL([str value])
```

### Parameters - uRL

value  

### Return Value - uRL

## Method viewUserLicense

Microsoft internal use only.

```xpp
public int viewUserLicense([int value])
```

### Parameters - viewUserLicense

value  
A user license to view.

### Return Value - viewUserLicense

The user license.

## Method windowMode

```xpp
public int windowMode([int value])
```

### Parameters - windowMode

value  

### Return Value - windowMode

## Method windowParameters

```xpp
public str windowParameters([str value])
```

### Parameters - windowParameters

value  

### Return Value - windowParameters

## Method windowSize

```xpp
public int windowSize([int value])
```

### Parameters - windowSize

value  

### Return Value - windowSize

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new(str name)
```

### Parameters - new

name  

