---
title: XDSServices class
description: This topic describes the XDSServices class.
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

# Class XDSServices

[!include [banner](../../includes/banner.md)]

```xpp
class XDSServices extends Object
```

The XDSServices class provides APIs to manage the extensible data security (XDS) behavior.

## Remarks

## Examples

## Methods

| Method                                                                 | Description                                                                                                                       |
|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public int flushXDSMyConstructs(int reserved, str tablename)           | Flushes the MyConstruct table that is used with XDS.                                                                              |
| public str getQuerySQL(str queryname)                                  |                                                                                                                                   |
| public str getTableSQL(str tablename, \[str policyname\])              |                                                                                                                                   |
| public str getXDSBinding(str name)                                     |                                                                                                                                   |
| public str getXDSContext(int reserved)                                 |                                                                                                                                   |
| public int getXDSToFlushPerServiceSession(int reserved)                | Checks whether the MyConstruct tables will be flushed when the service session is returned to the pool.                           |
| public void finalize()                                                 |                                                                                                                                   |
| public void new()                                                      | Initializes a new instance of the XDSServices class.                                                                              |
| public void setXDSContext(int reserved, str contextstring)             |                                                                                                                                   |
| public void setXDSBinding(str name, str value)                         |                                                                                                                                   |
| public void setXDSState(int finalState)                                |                                                                                                                                   |
| public void setXDSToFlushPerServiceSession(int reserved, int newstate) | Sets the setting that determines whether the MyConstruct tables will be flushed when the service session is returned to the pool. |
| public void setXDSTrace(int flag, str value)                           |                                                                                                                                   |

## Method flushXDSMyConstructs

Flushes the MyConstruct table that is used with XDS.

```xpp
public int flushXDSMyConstructs(int reserved, str tablename)
```

### Parameters - flushXDSMyConstructs

reserved  
The name of the MyConstruct table to flush. It no value is passed in, or if an empty string is passed in, all MyConstruct tables are flushed.

<!-- -->

tablename  
The name of the MyConstruct table to flush. It no value is passed in, or if an empty string is passed in, all MyConstruct tables are flushed.

### Return Value - flushXDSMyConstructs

## Method getQuerySQL

```xpp
public str getQuerySQL(str queryname)
```

### Parameters - getQuerySQL

queryname  

### Return Value - getQuerySQL

## Method getTableSQL

```xpp
public str getTableSQL(str tablename, [str policyname])
```

### Parameters - getTableSQL

tablename  

<!-- -->

policyname  

### Return Value - getTableSQL

## Method getXDSBinding

```xpp
public str getXDSBinding(str name)
```

### Parameters - getXDSBinding

name  

### Return Value - getXDSBinding

## Method getXDSContext

```xpp
public str getXDSContext(int reserved)
```

### Parameters - getXDSContext

reserved  

### Return Value - getXDSContext

## Method getXDSToFlushPerServiceSession

Checks whether the MyConstruct tables will be flushed when the service session is returned to the pool.

```xpp
public int getXDSToFlushPerServiceSession(int reserved)
```

### Parameters - getXDSToFlushPerServiceSession

reserved  
A reserved flag; not currently used.

### Return Value - getXDSToFlushPerServiceSession

1 if the MyConstruct tables will be flushed when the service session is returned to the pool; otherwise, 0.

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the XDSServices class.

```xpp
public void new()
```

## Method setXDSContext

```xpp
public void setXDSContext(int reserved, str contextstring)
```

### Parameters - setXDSContext

reserved  

<!-- -->

contextstring  

## Method setXDSBinding

```xpp
public void setXDSBinding(str name, str value)
```

### Parameters - setXDSBinding

name  

<!-- -->

value  

## Method setXDSState

```xpp
public void setXDSState(int finalState)
```

### Parameters - setXDSState

finalState  

## Method setXDSToFlushPerServiceSession

Sets the setting that determines whether the MyConstruct tables will be flushed when the service session is returned to the pool.

```xpp
public void setXDSToFlushPerServiceSession(int reserved, int newstate)
```

### Parameters - setXDSToFlushPerServiceSession

reserved  
A value that indicates whether to flush the MyConstruct tables when the service session is returned to the pool. Pass 1 to flush the tables and 0 not to flush them.

<!-- -->

newstate  
A value that indicates whether to flush the MyConstruct tables when the service session is returned to the pool. Pass 1 to flush the tables and 0 not to flush them.

## Method setXDSTrace

```xpp
public void setXDSTrace(int flag, str value)
```

### Parameters - setXDSTrace

flag  

<!-- -->

value  

