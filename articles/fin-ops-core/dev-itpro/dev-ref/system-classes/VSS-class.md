---
title: VSS class
description: This topic describes the VSS class.
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

# Class VSS

[!include [banner](../../includes/banner.md)]

```xpp
class VSS extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                        | Description                               |
|---------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| public boolean connect()                                                                                      |                                           |
| public boolean connected()                                                                                    |                                           |
| public boolean disconnect()                                                                                   |                                           |
| public container getCheckedoutFiles()                                                                         |                                           |
| public container getConnectionInfo()                                                                          |                                           |
| public VSSItem getVSSItem(str vssItemPath, str localFilePath, \[boolean completePath\], \[int version\])      |                                           |
| public boolean init(str vssIni, str vssPrjRoot, str vssWorkingFolder, str vssUser, str vssPwd)                |                                           |
| public VSSItem newSubProject(str name, str localPath)                                                         |                                           |
| public Map synchronizeProjects(\[Set projects\], \[boolean force\], \[boolean delLocalFiles\], \[str label\]) |                                           |
| public void new()                                                                                             | Initializes an instance of the VSS class. |

## Method connect

```xpp
public boolean connect()
```

### Return Value - connect

## Method connected

```xpp
public boolean connected()
```

### Return Value - connected

## Method disconnect

```xpp
public boolean disconnect()
```

### Return Value - disconnect

## Method getCheckedoutFiles

```xpp
public container getCheckedoutFiles()
```

### Return Value - getCheckedoutFiles

## Method getConnectionInfo

```xpp
public container getConnectionInfo()
```

### Return Value - getConnectionInfo

## Method getVSSItem

```xpp
public VSSItem getVSSItem(str vssItemPath, str localFilePath, [boolean completePath], [int version])
```

### Parameters - getVSSItem

vssItemPath  

<!-- -->

localFilePath  

<!-- -->

completePath  

<!-- -->

version  

### Return Value - getVSSItem

## Method init

```xpp
public boolean init(str vssIni, str vssPrjRoot, str vssWorkingFolder, str vssUser, str vssPwd)
```

### Parameters - init

vssIni  

<!-- -->

vssPrjRoot  

<!-- -->

vssWorkingFolder  

<!-- -->

vssUser  

<!-- -->

vssPwd  

### Return Value - init

## Method newSubProject

```xpp
public VSSItem newSubProject(str name, str localPath)
```

### Parameters - newSubProject

name  

<!-- -->

localPath  

### Return Value - newSubProject

## Method synchronizeProjects

```xpp
public Map synchronizeProjects([Set projects], [boolean force], [boolean delLocalFiles], [str label])
```

### Parameters - synchronizeProjects

projects  

<!-- -->

force  

<!-- -->

delLocalFiles  

<!-- -->

label  

### Return Value - synchronizeProjects

## Method new

Initializes an instance of the VSS class.

```xpp
public void new()
```

