---
title: FormsPreloadingManager class
description: This topic describes the FormsPreloadingManager class.
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

# Class FormsPreloadingManager

[!include [banner](../../includes/banner.md)]

```xpp
class FormsPreloadingManager extends Object
```

The FormsPreloadingManager class manages the preloading of forms, including workspace association and resource pressure management.

## Remarks

## Examples

## Methods

| Method                                              | Description                                                                                  |
|-----------------------------------------------------|----------------------------------------------------------------------------------------------|
| ::private static FormsPreloadingManager construct() |                                                                                              |
| public void workspaceActivated()                    | Sets the preloading workspace affinity to the last activated workspace.                      |
| private void new()                                  | Initializes a new instance of the FormsPreloadingManager class.                              |
| public void updateState()                           | Queues forms for loading, handles high resource pressure, and updates other internal states. |

## Method construct

```xpp
private static FormsPreloadingManager construct()
```

### Return Value - construct

## Method workspaceActivated

Sets the preloading workspace affinity to the last activated workspace.

```xpp
public void workspaceActivated()
```

### Remarks - workspaceActivated

This method is typically called on a timer after a workspace has been activated. Call this method directly to force the workspace affinity to change immediately.

## Method new

Initializes a new instance of the FormsPreloadingManager class.

```xpp
private void new()
```

## Method updateState

Queues forms for loading, handles high resource pressure, and updates other internal states.

```xpp
public void updateState()
```

### Remarks - updateState

This method is typically called on a timer during idle periods. Call this method directly to force a state update during non-idle periods, such as when long-running X++ code is running.

