---
title: Development tools in Visual Studio
description: Visual Studio is the exclusive integrated development environment (IDE) for development. Learn about development tools used for Visual Studio.
author: josaw1
ms.author: josaw
ms.topic: overview
ms.date: 03/30/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Development tools in Visual Studio

[!include [banner](../includes/banner.md)]

## What are the development tools?

You carry out application development in Visual Studio. The development tools support all of the development tasks, including debugging and local testing scenarios. Visual Studio is the exclusive integrated development environment (IDE) for development. You perform all of your application development work with it. This section provides an overview of the main features that are added to Visual Studio when you install the development tools.

Starting with platform updates for version 10.0.21 of finance and operations apps, Visual Studio 2019 is supported.

While you work in Visual Studio, you receive recurring feedback requests regarding new features.
To prevent the feedback requests from appearing in Visual Studio, run the following PowerShell command from a developer’s machine:
Set-ItemProperty HKCU:\Software\Microsoft\Dynamics\AX7\Development\Configurations  -Name ProvideFeedback  -Value "No"

### Application Explorer

In Visual Studio, the Application Explorer represents the model store. On the **View** menu, select **Application Explorer** to open it. Use the Application Explorer to browse and interact with the elements in the model store that define the applications. The following illustration shows the Application Explorer. For more information, see [Application Explorer](application-explorer.md).

:::image type="content" source="media/1_devotoolsconcept.png" alt-text="Screenshot of the Application Explorer.":::

### The project template

Even a simple application can have a large number of elements in its model. The **Operations Project** template was added to Visual Studio to help you organize and manage the elements that you're working with for a model. Use the project to design, build, and test model elements. It's common to have several projects within a single Visual Studio solution. The following illustration shows three projects in a Visual Studio solution. For more information, see [finance and operations project type in Visual Studio](projects.md).

:::image type="content" source="media/2_devotoolsconcept.png" alt-text="Screenshot of three projects in a Visual Studio solution in Solution Explorer.":::

### Element designers

The Visual Studio tools include designers for each kind of element in the application. Use these designers when you create or modify elements. The following illustration shows the element designer for a form element. For more information, see [Element designers](element-designers.md).

:::image type="content" source="media/3_devotoolsconcept.png" alt-text="Screenshot of the element designer for a form element.":::

### Code editor

You write X++ code in the code editor for Visual Studio. The code editor supports the standard features that a developer expects. For example, you can collapse sections of code. IntelliSense provides guidance as you write or modify code. For more information, see [Code editor features](code-editor.md).

:::image type="content" source="media/4_devotoolsconcept.png" alt-text="Screenshot of the code editor in Visual Studio.":::

### Dynamics 365 menu

The tools add the **Dynamics 365** menu to Visual Studio. This menu contains several tools that you use during the development process. For example, you access the tools for managing models from this menu.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
