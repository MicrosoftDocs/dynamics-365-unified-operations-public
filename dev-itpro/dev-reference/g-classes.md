---
# required metadata

title: G Classes | Microsoft Docs
description: System API classes that start with the letter G.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-24 14:31:40
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 52381
ms.assetid: 8cb9bd5d-433e-432d-8c1a-9aebcdb4ba07
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# G Classes

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

