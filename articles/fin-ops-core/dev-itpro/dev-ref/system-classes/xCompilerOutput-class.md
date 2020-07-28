---
title: xCompilerOutput class
description: This topic describes the xCompilerOutput class.
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

# Class xCompilerOutput

[!include [banner](../../includes/banner.md)]

```xpp
class xCompilerOutput extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                         | Description                                              |
|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| public str getErrorMessage(int errorCode, int severity, str errorString)                                                       |                                                          |
| public container getSquiggleInfo(str treeNodePath)                                                                             |                                                          |
| public void compilerStatus(UtilElementType utilElementType, str utilElementName)                                               |                                                          |
| public void setActiveTab(int tab)                                                                                              |                                                          |
| public void startCompilationObject(str path)                                                                                   |                                                          |
| public void endCompilation()                                                                                                   |                                                          |
| public void startExport()                                                                                                      |                                                          |
| public void startCompilation(int flag, str path, int activeWindowHandle)                                                       |                                                          |
| public void importOutput(str buffer)                                                                                           |                                                          |
| public void endExport()                                                                                                        |                                                          |
| public void endCompilationObject(str path)                                                                                     |                                                          |
| public void startImport()                                                                                                      |                                                          |
| public void new()                                                                                                              | Initializes a new instance of the xCompilerOutput class. |
| public void compilerOutputMessage(str path, int errorCode, int line, int col, int severity, str errorString, str propertyName) |                                                          |
| public void exportOutput(str buffer)                                                                                           |                                                          |
| public void endCILGenerationOutput()                                                                                           |                                                          |
| public void cilGenerationOutput(str msg, str path, int severity, int line, int col)                                            |                                                          |
| public void endImport()                                                                                                        |                                                          |
| public void nextError()                                                                                                        |                                                          |
| public void startCILGenerationOutput()                                                                                         |                                                          |

## Method getErrorMessage

```xpp
public str getErrorMessage(int errorCode, int severity, str errorString)
```

### Parameters - getErrorMessage

errorCode  

<!-- -->

severity  

<!-- -->

errorString  

### Return Value - getErrorMessage

## Method getSquiggleInfo

```xpp
public container getSquiggleInfo(str treeNodePath)
```

### Parameters - getSquiggleInfo

treeNodePath  

### Return Value - getSquiggleInfo

## Method compilerStatus

```xpp
public void compilerStatus(UtilElementType utilElementType, str utilElementName)
```

### Parameters - compilerStatus

utilElementType  

<!-- -->

utilElementName  

## Method setActiveTab

```xpp
public void setActiveTab(int tab)
```

### Parameters - setActiveTab

tab  

## Method startCompilationObject

```xpp
public void startCompilationObject(str path)
```

### Parameters - startCompilationObject

path  

## Method endCompilation

```xpp
public void endCompilation()
```

## Method startExport

```xpp
public void startExport()
```

## Method startCompilation

```xpp
public void startCompilation(int flag, str path, int activeWindowHandle)
```

### Parameters - startCompilation

flag  

<!-- -->

path  

<!-- -->

activeWindowHandle  

## Method importOutput

```xpp
public void importOutput(str buffer)
```

### Parameters - importOutput

buffer  

## Method endExport

```xpp
public void endExport()
```

## Method endCompilationObject

```xpp
public void endCompilationObject(str path)
```

### Parameters - endCompilationObject

path  

## Method startImport

```xpp
public void startImport()
```

## Method new

Initializes a new instance of the xCompilerOutput class.

```xpp
public void new()
```

## Method compilerOutputMessage

```xpp
public void compilerOutputMessage(str path, int errorCode, int line, int col, int severity, str errorString, str propertyName)
```

### Parameters - compilerOutputMessage

path  

<!-- -->

errorCode  

<!-- -->

line  

<!-- -->

col  

<!-- -->

severity  

<!-- -->

errorString  

<!-- -->

propertyName  

## Method exportOutput

```xpp
public void exportOutput(str buffer)
```

### Parameters - exportOutput

buffer  

## Method endCILGenerationOutput

```xpp
public void endCILGenerationOutput()
```

## Method cilGenerationOutput

```xpp
public void cilGenerationOutput(str msg, str path, int severity, int line, int col)
```

### Parameters - cilGenerationOutput

msg  

<!-- -->

path  

<!-- -->

severity  

<!-- -->

line  

<!-- -->

col  

## Method endImport

```xpp
public void endImport()
```

## Method nextError

```xpp
public void nextError()
```

## Method startCILGenerationOutput

```xpp
public void startCILGenerationOutput()
```

