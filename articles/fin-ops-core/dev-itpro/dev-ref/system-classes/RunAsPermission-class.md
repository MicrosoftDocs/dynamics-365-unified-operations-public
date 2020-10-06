---
title: RunAsPermission class
description: This topic describes the RunAsPermission class.
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

# Class RunAsPermission

[!include [banner](../../includes/banner.md)]

```xpp
class RunAsPermission extends CodeAccessPermission
```

The RunAsPermssion class controls the execution of code in the security context of another user.

## Remarks

You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission.demand method is called on before the protected API is executed. Call a method on the server tier from one of the following: The RunAsPermission class is designed to check permissions for the runAs function. For a list of all APIs protected by permissions, see Secured APIs.

-   A server static method �or�
-   A class instance method that is set to run on the server by using the RunOn class property

## Examples

The following code example shows a new instance of the RunAsPermission class. The assert method is called to declare that the code can then call the runAs function to run the EventJobDueDate.:runDueDateEventsForUser method in the security context of another user.

```xpp
server static void main(Args args) 
{ 
    RunAsPermission _perm; 
    UserId          _runAsUser; 
    SysUserInfo     _userInfo; 
    _userInfo = SysUserInfo::find(); 
    _runAsUser = _userInfo.Id; 
    _perm = new RunAsPermission(_runAsUser); 
    _perm.assert(); 
    // Invoke the protected API. 
    RunAs(_runAsUser, classnum(EventJobDueDate), "runDueDateEventsForUser"); 
    // Optionally, call revertAssert() to limit the scope of assert. 
    CodeAccessPermission::revertAssert(); 
}
```

## Methods

| Method                                                 | Description                                                                                                         |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                            |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when overridden by a derived class. |
| public void new(UserId userId)                         | Initializes a new instance of the CodeAccessPermission class.                                                       |

## Method copy

Creates and returns a copy of a permission class object.

```xpp
public CodeAccessPermission copy()
```

### Return Value - copy

A copy of the derived class object.

### Remarks - copy

You can override this method as part of the process of making an API more secure.

## Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when overridden by a derived class.

```xpp
public boolean isSubsetOf(CodeAccessPermission target)
```

### Parameters - isSubsetOf

target  
A CodeAccessPermission class object.

### Return Value - isSubsetOf

true if a current permission is a subset of a specified permission; otherwise, false.

### Remarks - isSubsetOf

You can override the method as part of the process of making an API more secure.

## Method new

Initializes a new instance of the CodeAccessPermission class.

```xpp
public void new(UserId userId)
```

### Parameters - new

userId  
A userId system data type that specifies a user.

### Examples - new

The following example shows a new instance of the RunAsPermission class. The SysUserInfo table is used to initialize the userId parameter.

```xpp
server static void main(Args args) 
{ 
    RunAsPermission _perm; 
    UserId          _userId; 
    SysUserInfo     _userInfo; 
    _userInfo = SysUserInfo::find(); 
    _userId = _userInfo.Id; 
    _perm = new RunAsPermission(_userId); 
```

```xpp
}
```

### Remarks - new

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

## Method rightMargin

```xpp
public void rightMargin(Real value, Units unit)
```

### Parameters - rightMargin

value  

<!-- -->

unit  

## Method left

```xpp
public void left(Real value, Units unit)
```

### Parameters - left

value  

<!-- -->

unit  

## Method width

Gets or sets the width of the control.

```xpp
public void width(Real value, Units unit)
```

### Parameters - width

value  

<!-- -->

unit  

### Remarks - width

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

## Method extraSumWidth

```xpp
public void extraSumWidth(Real value, Units unit)
```

### Parameters - extraSumWidth

value  

<!-- -->

unit  

## Method topMargin

```xpp
public void topMargin(Real value, Units unit)
```

### Parameters - topMargin

value  

<!-- -->

unit  

## Method leftMargin

```xpp
public void leftMargin(Real value, Units unit)
```

### Parameters - leftMargin

value  

<!-- -->

unit  

## Method labelWidth

```xpp
public void labelWidth(Real value, Units unit)
```

### Parameters - labelWidth

value  

<!-- -->

unit  

## Method top

```xpp
public void top(Real value, Units unit)
```

### Parameters - top

value  

<!-- -->

unit  

## Method bottomMargin

```xpp
public void bottomMargin(Real value, Units unit)
```

### Parameters - bottomMargin

value  

<!-- -->

unit  

