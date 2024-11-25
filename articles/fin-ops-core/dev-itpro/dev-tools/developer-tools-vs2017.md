---
title: Visual Studio requirements for X++
description: Learn about the Visual Studio components that are required to run the Visual Studio extension for X++ with tables that outline requirement statuses for components.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 06/26/2024
ms.reviewer: johnmichalak
audience: Developer
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: AX 7.0.0
---

# Visual Studio requirements for X++

[!include [banner](../includes/banner.md)]

This article lists the Visual Studio components that are required to run the **Visual Studio** extension for X++.

> [!NOTE]
> We don't recommend installing Visual Studio manually on the downloadable virtual hard drive (VHD) or virtual machines deployed from Lifecycle Services (LCS). Instead, we strongly recommend that you download or deploy a new virtual machine. Virtual machines deployed with versions 10.0.13 or later all have Visual Studio and its prerequisites installed, and come with other updates outside of Visual Studio to help keep the machines compatible and secure.

## Visual Studio editions

The supported editions of Visual Studio include:

- Visual Studio 2022 Professional
- Visual Studio 2022 Enterprise


> [!NOTE]
> Different Visual Studio editions have different licensing requirements and costs. For more information, see [Visual Studio](https://visualstudio.microsoft.com).

## Required Visual Studio components

The following table lists the required Visual Studio components.

| Type | Name | Required | Notes |
| --- | --- | --- | --- |
| Workload | .NET desktop development | Yes | |
| Individual component | Modeling SDK | Yes | |
| Individual component | DGML editor | No | This component is used for dependency graph features using the Directed Graph Markup Language. |
| Visual Studio Marketplace | Microsoft Reporting Services Projects | Yes | This component is needed for report development. If the component isn't installed, Visual Studio will prompt you when you try to open report designs. |

## Dynamics 365 Commerce

For more information on Commerce and Visual Studio, see these topics.

- [Migrate the Retail SDK from Visual Studio 2015 to Visual Studio 2017](../../../commerce/dev-itpro/retail-sdk/migrate-sdk.md)

