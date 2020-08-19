---
title: XppPrePostArgs class
description: This topic describes the XppPrePostArgs class.
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

# Class XppPrePostArgs

[!include [banner](../../includes/banner.md)]

```xpp
class XppPrePostArgs extends XppEventArgs
```

The XppPrePostArgs class provides information about a publisher's arguments and return values for pre-handlers and post-handlers.

## Remarks

A publisher is a method that exposes pre-events and post-events.

## Examples

## Methods

| Method                                                                                       | Description                                                                                                 |
|----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public boolean wrapper(str fieldName, AnyType value)                                         |                                                                                                             |
| public struct args()                                                                         |                                                                                                             |
| public boolean existsArg(str fieldName)                                                      | Checks the existence of the publisher's argument by name.                                                   |
| public AnyType getArgNum(int argIndex)                                                       | Retrieves the ;publisher's argument by index.                                                               |
| public int setArgNum(int argIndex, AnyType value)                                            | Sets the publisher's argument by index.                                                                     |
| public AnyType value(str fieldName)                                                          |                                                                                                             |
| public XppEventHandlerCalledWhen getCalledWhen()                                             | Retrieves a value that indicates whether the instance is currently serving a pre-handler or a post-handler. |
| public AnyType getReturnValue()                                                              | Gets the publisher's return value.                                                                          |
| public AnyType getThis()                                                                     | Gets the publisher's "this" reference.                                                                      |
| public boolean removeArg(str fieldName)                                                      |                                                                                                             |
| public int wrapper(str fieldName, AnyType value)                                             |                                                                                                             |
| public int setReturnValue(AnyType retval)                                                    | Sets the publisher's return value.                                                                          |
| public str isFirst()                                                                         |                                                                                                             |
| public void setCalledWhen(XppEventHandlerCalledWhen calledWhen)                              | Sets whether the instance is currently serving a pre-handler or a post-handler.                             |
| ::public static void setReturnValueEx(AnyType retval, XppPrePostArgs args)                   |                                                                                                             |
| public void new(\[AnyType thisPtr\], \[str args\], \[XppEventHandlerCalledWhen calledWhen\]) | Initializes a new instance of the Object class.                                                             |

## Method wrapper

```xpp
public boolean wrapper(str fieldName, AnyType value)
```

### Parameters - wrapper

fieldName  

<!-- -->

value  

### Return Value - wrapper

## Method args

```xpp
public struct args()
```

### Return Value - args

## Method existsArg

Checks the existence of the publisher's argument by name.

```xpp
public boolean existsArg(str fieldName)
```

### Parameters - existsArg

fieldName  

### Return Value - existsArg

A Boolean data type value that indicates whether the specified argument exists.

### Remarks - existsArg

Argument names are case insensitive.

## Method getArgNum

Retrieves the ;publisher's argument by index.

```xpp
public AnyType getArgNum(int argIndex)
```

### Parameters - getArgNum

argIndex  
An int index of the target argument.

### Return Value - getArgNum

An anytype value of the specified argument.

### Remarks - getArgNum

The index range is 0-based for static publishers but 1-based for instance publishers.

## Method setArgNum

Sets the publisher's argument by index.

```xpp
public int setArgNum(int argIndex, AnyType value)
```

### Parameters - setArgNum

argIndex  
An anytype value to assign to the specified argument.

<!-- -->

value  
An anytype value to assign to the specified argument.

### Return Value - setArgNum

An int data type value of 1.

### Remarks - setArgNum

The index range is 0-based for static publishers but 1-based for instance publishers.

## Method value

```xpp
public AnyType value(str fieldName)
```

### Parameters - value

fieldName  

### Return Value - value

## Method getCalledWhen

Retrieves a value that indicates whether the instance is currently serving a pre-handler or a post-handler.

```xpp
public XppEventHandlerCalledWhen getCalledWhen()
```

### Return Value - getCalledWhen

An XppEventHandlerCalledWhen data type value that indicates whether the XppPrePostArgs instance is serving the pre-handlers or the post-handlers.

## Method getReturnValue

Gets the publisher's return value.

```xpp
public AnyType getReturnValue()
```

### Return Value - getReturnValue

An anytype data type value that represents the publisher's return value.

### Remarks - getReturnValue

This method is not intended for pre-handlers.

## Method getThis

Gets the publisher's "this" reference.

```xpp
public AnyType getThis()
```

### Return Value - getThis

An anytype data type value that represents the publisher's "this" reference.

### Remarks - getThis

Returns a nullNothingnullptrunita null reference (Nothing in Visual Basic) reference if the publisher is static.

## Method removeArg

```xpp
public boolean removeArg(str fieldName)
```

### Parameters - removeArg

fieldName  

### Return Value - removeArg

## Method wrapper

```xpp
public int wrapper(str fieldName, AnyType value)
```

### Parameters - wrapper

fieldName  

<!-- -->

value  

### Return Value - wrapper

## Method setReturnValue

Sets the publisher's return value.

```xpp
public int setReturnValue(AnyType retval)
```

### Parameters - setReturnValue

retval  

### Return Value - setReturnValue

An int data type value of 1.

### Remarks - setReturnValue

This method is not intended for pre-handlers or for publishers that return void.

## Method isFirst

```xpp
public str isFirst()
```

### Return Value - isFirst

## Method setCalledWhen

Sets whether the instance is currently serving a pre-handler or a post-handler.

```xpp
public void setCalledWhen(XppEventHandlerCalledWhen calledWhen)
```

### Parameters - setCalledWhen

calledWhen  

### Remarks - setCalledWhen

This method must never be called explicitly from the pre-handler or post-handler code. This method is reserved for unit testing and auto-generated code only.

## Method setReturnValueEx

```xpp
public static void setReturnValueEx(AnyType retval, XppPrePostArgs args)
```

### Parameters - setReturnValueEx

retval  

<!-- -->

args  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([AnyType thisPtr], [str args], [XppEventHandlerCalledWhen calledWhen])
```

### Parameters - new

thisPtr  

<!-- -->

args  

<!-- -->

calledWhen  

