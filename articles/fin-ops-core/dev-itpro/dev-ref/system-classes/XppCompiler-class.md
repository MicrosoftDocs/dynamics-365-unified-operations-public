---
title: XppCompiler class
description: This topic describes the XppCompiler class.
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

# Class XppCompiler

[!include [banner](../../includes/banner.md)]

```xpp
class XppCompiler extends Object
```

## Remarks

## Examples

## Methods

| Method                                 | Description                                                                                                       |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| public boolean compile(str source)     |                                                                                                                   |
| public boolean compileExpr(str source) |                                                                                                                   |
| public str dumpClass(str className)    | Creates an XML string that contains the X++ compiler information for a class.                                     |
| public str dumpEnums()                 | Creates an XML string that contains the X++ compiler information for all enumerations in the current application. |
| public str dumpTable(str tableName)    | Creates an XML string that contains the X++ compiler information for a table.                                     |
| public str errorText()                 |                                                                                                                   |
| public AnyType execute(VarArg )        |                                                                                                                   |
| public AnyType executeEx()             |                                                                                                                   |
| public void setGuidArg(Guid arg)       |                                                                                                                   |
| public void setInt64Arg(Int64 arg)     |                                                                                                                   |
| public void setDateArg(Date arg)       |                                                                                                                   |
| public void new()                      | Initializes a new instance of the XppCompiler class.                                                              |
| public void endArgs()                  |                                                                                                                   |
| public void startArgs()                |                                                                                                                   |
| public void setRealArg(Real arg)       |                                                                                                                   |
| public void setIntArg(int arg)         |                                                                                                                   |
| public void setStrArg(str arg)         |                                                                                                                   |

## Method compile

```xpp
public boolean compile(str source)
```

### Parameters - compile

source  

### Return Value - compile

## Method compileExpr

```xpp
public boolean compileExpr(str source)
```

### Parameters - compileExpr

source  

### Return Value - compileExpr

## Method dumpClass

Creates an XML string that contains the X++ compiler information for a class.

```xpp
public str dumpClass(str className)
```

### Parameters - dumpClass

className  

### Return Value - dumpClass

The X++ compiler information for the specified class

### Remarks - dumpClass

General use of this method is discouraged, because the output format might change without warning from version to version.

## Method dumpEnums

Creates an XML string that contains the X++ compiler information for all enumerations in the current application.

```xpp
public str dumpEnums()
```

### Return Value - dumpEnums

The X++ compiler information for all enumerations in the current application

### Remarks - dumpEnums

General use of this method is discouraged, because the output format might change without warning from version to version.

## Method dumpTable

Creates an XML string that contains the X++ compiler information for a table.

```xpp
public str dumpTable(str tableName)
```

### Parameters - dumpTable

tableName  

### Return Value - dumpTable

The X++ compiler information for the specified table

### Remarks - dumpTable

General use of this method is discouraged, because the output format might change without warning from version to version.

## Method errorText

```xpp
public str errorText()
```

### Return Value - errorText

## Method execute

```xpp
public AnyType execute(VarArg )
```

### Parameters - execute


### Return Value - execute

### Remarks - execute

XppCompiler objects can compile code at run time. This presents a security risk. Therefore, execute method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - execute

The following example calls the execute method to compile and execute the supplied buffer.

```xpp
void XppCompilerExecuteExample(Common _buf) 
{ 
    XppCompiler       xpp; 
    ExecutePermission perm; 
    perm = new ExecutePermission(); 
    if (perm == null) 
    { 
        return; 
    } 
    perm.assert(); 
    xpp = new XppCompiler(); 
    if (xpp != null) 
    { 
        xpp.execute(_buf); 
    } 
    CodeAccessPermission::revertAssert(); 
}
```

## Method executeEx

```xpp
public AnyType executeEx()
```

### Return Value - executeEx

### Remarks - executeEx

XppCompiler objects can compile code at run time. This presents a security risk. Therefore, the executeEx method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - executeEx

```xpp
void XppCompilerExecuteExExample() 
{ 
    XppCompiler       xpp; 
    ExecutePermission perm; 
    perm = new ExecutePermission(); 
    if (perm == null) 
    { 
        return; 
    } 
    perm.assert(); 
    xpp = new XppCompiler(); 
    if (xpp != null) 
    { 
        xpp.executeEx(); 
    } 
    CodeAccessPermission::revertAssert(); 
}
```

## Method setGuidArg

```xpp
public void setGuidArg(Guid arg)
```

### Parameters - setGuidArg

arg  

## Method setInt64Arg

```xpp
public void setInt64Arg(Int64 arg)
```

### Parameters - setInt64Arg

arg  

## Method setDateArg

```xpp
public void setDateArg(Date arg)
```

### Parameters - setDateArg

arg  

## Method new

Initializes a new instance of the XppCompiler class.

```xpp
public void new()
```

### Remarks - new

Instances of the XppCompiler class can compile code at run time. Because this presents a security risk, the new method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission Class.

## Method endArgs

```xpp
public void endArgs()
```

## Method startArgs

```xpp
public void startArgs()
```

## Method setRealArg

```xpp
public void setRealArg(Real arg)
```

### Parameters - setRealArg

arg  

## Method setIntArg

```xpp
public void setIntArg(int arg)
```

### Parameters - setIntArg

arg  

## Method setStrArg

```xpp
public void setStrArg(str arg)
```

### Parameters - setStrArg

arg  

