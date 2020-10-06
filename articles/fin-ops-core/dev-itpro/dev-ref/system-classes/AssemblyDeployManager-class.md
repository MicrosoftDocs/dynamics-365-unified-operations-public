---
title: AssemblyDeployManager class
description: This topic describes the AssemblyDeployManager class.
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

# Class AssemblyDeployManager

[!include [banner](../../includes/banner.md)]

```xpp
class AssemblyDeployManager extends Object
```

The AssemblyDeployManager class lets you deploy the assemblies that are stored in the AOT Visual Studio Projects to the AOS VSAssemblies folder that can be used by the X++ runtime during .NET calls.

## Remarks

## Examples

## Methods

| Method                                                        | Description                                                                                             |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| ::public static boolean isHotswappingEnabled()                | Returns a Boolean value that indicates whether hot swapping is enabled.                                 |
| ::public static void deployAssemblyFromPath(str assemblyPath) |                                                                                                         |
| ::public static void removeAssemblyFromPath(str assemblyPath) | Removes one specific assembly that is marked for deployment to the server from the VSAssemblies folder. |
| ::public static void deployAssemblies()                       | Deploys one specific assembly that is marked for deployment to server to the VSAssemblies folder.       |

## Method isHotswappingEnabled

Returns a Boolean value that indicates whether hot swapping is enabled.

```xpp
public static boolean isHotswappingEnabled()
```

### Return Value - isHotswappingEnabled

A Boolean value that indicates whether hot swapping is enabled.

## Method deployAssemblyFromPath

```xpp
public static void deployAssemblyFromPath(str assemblyPath)
```

### Parameters - deployAssemblyFromPath

assemblyPath  

## Method removeAssemblyFromPath

Removes one specific assembly that is marked for deployment to the server from the VSAssemblies folder.

```xpp
public static void removeAssemblyFromPath(str assemblyPath)
```

### Parameters - removeAssemblyFromPath

assemblyPath  
The Visual Studio Project path where the assembly is stored.

## Method deployAssemblies

Deploys one specific assembly that is marked for deployment to server to the VSAssemblies folder.

```xpp
public static void deployAssemblies()
```

