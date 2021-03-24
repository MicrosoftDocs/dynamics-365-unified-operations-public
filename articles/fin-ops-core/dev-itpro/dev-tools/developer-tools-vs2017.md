---
# required metadata

title: Visual Studio 2017 Requirements for X++
description: This topic reviews the required components for Visual Studio 2017 to support the X++ tooling.
author: RobinARH
manager: AnnBe
ms.date: 08/17/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.author: jorisde
ms.search.validFrom: 2020-03-24
ms.dyn365.ops.version: AX 7.0.0

---

# Visual Studio 2017 Requirements for X++

[!include [banner](../includes/banner.md)]

This topic reviews the required Visual Studio 2017 components to run the **Visual Studio** extension for X++.

> [!NOTE]
> We do not recommend installing Visual Studio manually on the downloadable VHD or virtual machines deployed from LCS. Instead, it is strongly encouraged to download or deploy a new virtual machine. Virtual machines deployed with versions 10.0.13 or newer all have Visual Studio 2017 and its prerequisites installed, and come with other updates outside of Visual Studio to keep the machines compatible and secure.

## Visual Studio Editions

The support editions are Visual Studio 2017 Professional or Enterprise.

> [!NOTE]
> Different Visual Studio editions have different licensing requirements and costs. Consult the [Visual Studio website](https://visualstudio.microsoft.com) for more information.

## Required Visual Studio Components

The following tables lists the required components for Visual Studio that have to be enabled.

| Type | Name | Required | |
| --- | --- | --- | --- |
| Workload | .NET desktop development | Yes | |
| Individual Component | Modeling SDK | Yes | |
| Individual Component | DGML editor | No | This component is used for dependency graph features. |
| Marketplace | Microsoft Reporting Services Projects | Yes (for report development) | This component is needed for report development. If the component is not installed, Visual Studio will prompt you when trying to open report designs. |
