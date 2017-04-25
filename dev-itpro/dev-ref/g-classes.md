---
# required metadata

title: G Classes
description: System API classes that start with the letter G.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 52381
ms.assetid: 6d4b3577-f254-4702-9878-ec3863c033fa
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# G Classes

[!include[banner](../includes/banner.md)]


System API classes that start with the letter G.

Class Gac
---------

    class Gac extends Object

The Gac class lets you enumerate the assemblies of the global assembly cache (GAC).

### Remarks

### Examples

### Methods

| Method                                 | Description                                                   |
|----------------------------------------|---------------------------------------------------------------|
| public container enumerateAssemblies() | Enumerates the assemblies of the global assembly cache (GAC). |
| public void new()                      | Initializes a new instance of the Gac class.                  |

### Method enumerateAssemblies

Enumerates the assemblies of the global assembly cache (GAC).

    public container enumerateAssemblies()

#### Return Value

A container that represents the assemblies of the GAC.

### Method new

Initializes a new instance of the Gac class.

    public void new()


