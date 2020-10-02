---
title: AOSSessionInfo class
description: This topic describes the AOSSessionInfo class.
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

# Class AOSSessionInfo

[!include [banner](../../includes/banner.md)]

```xpp
class AOSSessionInfo extends Object
```

The AOSSessionInfo class is used to provide information about a session for the Application Object Server (AOS).

## Remarks

## Examples

## Methods

| Method                             | Description                                                               |
|------------------------------------|---------------------------------------------------------------------------|
| public AOSClientMode clientMode()  | Returns the client mode for the AOS session.                              |
| public int cpuTime()               | Returns the number of milliseconds that the CPU uses for the AOS session. |
| public int idleTicks()             | Returns the number of milliseconds since the last communication with AOS. |
| public int sessionId()             | Returns the ID of the AOS session.                                        |
| public void new(\[int sessionId\]) | Creates an instance of the AOSSessionInfo class.                          |

## Method clientMode

Returns the client mode for the AOS session.

```xpp
public AOSClientMode clientMode()
```

### Return Value - clientMode

The client mode for the AOS session.

## Method cpuTime

Returns the number of milliseconds that the CPU uses for the AOS session.

```xpp
public int cpuTime()
```

### Return Value - cpuTime

The number of milliseconds that the CPU uses for the AOS session.

## Method idleTicks

Returns the number of milliseconds since the last communication with AOS.

```xpp
public int idleTicks()
```

### Return Value - idleTicks

The number of milliseconds since the last communication with AOS.

## Method sessionId

Returns the ID of the AOS session.

```xpp
public int sessionId()
```

### Return Value - sessionId

The ID of the AOS session.

## Method new

Creates an instance of the AOSSessionInfo class.

```xpp
public void new([int sessionId])
```

### Parameters - new

sessionId  
The session ID that is used to create the instance of the AOSSessionInfo class. If a session ID is not specified, the current session is used; optional.

