---
title: MessageWin class
description: This topic describes the MessageWin class.
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

# Class MessageWin

[!include [banner](../../includes/banner.md)]

```xpp
class MessageWin extends Object
```

The MessageWin class gives access to the messageWindow class development environment.

## Remarks

Although you can instantiate more MessageWin objects, they will all refer to the same message window on the screen.

## Examples

## Methods

| Method                        | Description                                           |
|-------------------------------|-------------------------------------------------------|
| public void clear()           | Clears the message window.                            |
| public void activate()        | Makes the message window the currently active window. |
| public void addLine(str line) | Writes a line to the message window.                  |

## Method clear

Clears the message window.

```xpp
public void clear()
```

## Method activate

Makes the message window the currently active window.

```xpp
public void activate()
```

### Remarks - activate

Before version 2.11, the message window would get focus when lines were added or contents were cleared. Starting in version 2.11, the developer must call this method to make the message window the top window.

## Method addLine

Writes a line to the message window.

```xpp
public void addLine(str line)
```

### Parameters - addLine

line  
A string that contains the line to write to the message window.

