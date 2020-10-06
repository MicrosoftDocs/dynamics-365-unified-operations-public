---
title: WebActionMenuFunction class
description: This topic describes the WebActionMenuFunction class.
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

# Class WebActionMenuFunction

[!include [banner](../../includes/banner.md)]


```xpp
class WebActionMenuFunction extends WebMenuFunction
```

The WebActionMenuFunction class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                   | Description                                                                                                 |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public boolean big(\[boolean value\])                    |                                                                                                             |
| public int correctPermissions(\[int value\])             |                                                                                                             |
| public int createPermissions(\[int value\])              |                                                                                                             |
| public int deletePermissions(\[int value\])              |                                                                                                             |
| public int enumParameter(\[int value\])                  | Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class. |
| public EnumId enumTypeParameter(\[EnumId value\])        | Gets or sets the enumTypeParameter property for the MenuFunction class.                                     |
| public int imageLocation(\[int value\])                  |                                                                                                             |
| public str linkedPermissionObject(\[str value\])         |                                                                                                             |
| public str linkedPermissionObjectChild(\[str value\])    |                                                                                                             |
| public int linkedPermissionType(\[int value\])           |                                                                                                             |
| public int maintainUserLicense(\[int value\])            | Microsoft internal use only.                                                                                |
| public boolean multiSelect(\[boolean value\])            |                                                                                                             |
| public boolean needsRecord(\[boolean value\])            |                                                                                                             |
| public str normalImage(\[str value\])                    |                                                                                                             |
| public int normalResource(\[int value\])                 |                                                                                                             |
| public str object(\[str value\])                         | Gets or sets the object that the MenuFunction class runs.                                                   |
| public int objectType(\[int value\])                     |                                                                                                             |
| public Guid origin(\[Guid value\])                       |                                                                                                             |
| public str parameters(\[str value\])                     | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.      |
| public int readPermissions(\[int value\])                |                                                                                                             |
| public str reportDesign(\[str value\])                   |                                                                                                             |
| public int runOn(\[int value\])                          |                                                                                                             |
| public int updatePermissions(\[int value\])              |                                                                                                             |
| public int viewUserLicense(\[int value\])                | Microsoft internal use only.                                                                                |
| ::public static void runCalled(str name, \[xArgs args\]) |                                                                                                             |
| public void AOTrun(\[xArgs args\])                       | Compiles this node and its sub-tree in the Application Object Tree (AOT).             |
| ::public static void runClient(str name, \[xArgs args\]) |                                                                                                             |
| public void run(\[xArgs args\])                          |                                                                                                             |
| public void new(str name)                                | Initializes a new instance of the TreeNode class.                                                           |
| ::public static void runServer(str name, \[xArgs args\]) |                                                                                                             |

## Method big

```xpp
public boolean big([boolean value])
```

### Parameters - big

value  

### Return Value - big

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

## Method enumParameter

Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.

```xpp
public int enumParameter([int value])
```

### Parameters - enumParameter

value  

### Return Value - enumParameter

The enumParameter property that is passed to the object that is run by the MenuFunction class.

## Method enumTypeParameter

Gets or sets the enumTypeParameter property for the MenuFunction class.

```xpp
public EnumId enumTypeParameter([EnumId value])
```

### Parameters - enumTypeParameter

value  

### Return Value - enumTypeParameter

The enumTypeParameter property for the MenuFunction class.

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

## Method object

Gets or sets the object that the MenuFunction class runs.

```xpp
public str object([str value])
```

### Parameters - object

value  

### Return Value - object

The object that the MenuFunction class runs.

### Remarks - object

property value may be one of the following objects:

-   Form
-   Report
-   Job
-   Class
-   Query

## Method objectType

```xpp
public int objectType([int value])
```

### Parameters - objectType

value  

### Return Value - objectType

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

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

## Method readPermissions

```xpp
public int readPermissions([int value])
```

### Parameters - readPermissions

value  

### Return Value - readPermissions

## Method reportDesign

```xpp
public str reportDesign([str value])
```

### Parameters - reportDesign

value  

### Return Value - reportDesign

## Method runOn

```xpp
public int runOn([int value])
```

### Parameters - runOn

value  

### Return Value - runOn

## Method updatePermissions

```xpp
public int updatePermissions([int value])
```

### Parameters - updatePermissions

value  

### Return Value - updatePermissions

## Method viewUserLicense

Microsoft internal use only.

```xpp
public int viewUserLicense([int value])
```

### Parameters - viewUserLicense

value  
The user license to view.

### Return Value - viewUserLicense

The user license.

## Method runCalled

```xpp
public static void runCalled(str name, [xArgs args])
```

### Parameters - runCalled

name  

<!-- -->

args  

## Method AOTrun

Compiles this node and its sub-tree in the Application Object Tree (AOT).

```xpp
public void AOTrun([xArgs args])
```

### Parameters - AOTrun

args  

## Method runClient

```xpp
public static void runClient(str name, [xArgs args])
```

### Parameters - runClient

name  

<!-- -->

args  

## Method run

```xpp
public void run([xArgs args])
```

### Parameters - run

args  

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new(str name)
```

### Parameters - new

name  

## Method runServer

```xpp
public static void runServer(str name, [xArgs args])
```

### Parameters - runServer

name  

<!-- -->

args  

