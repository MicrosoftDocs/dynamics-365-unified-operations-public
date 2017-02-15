---
# required metadata

title: Development tools
description: Application development is carried out exclusively in Visual Studio. 
author: RobinARH
manager: AnnBe
ms.date: 2016-02-09 00 - 49 - 35
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31851
ms.assetid: e9e874f9-f285-437c-8578-3937a770eda0
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Development tools

Application development is carried out exclusively in Visual Studio. 

What are the development tools?
-------------------------------

A notable change from Microsoft Dynamics AX 2012 is that Dynamics 365 for Operations does not include a rich-client application (ax32.exe). From a development perspective, this means that the Microsoft Dynamics AX 2012 development environment, MorphX, is no longer used. In its place, the application development is carried out exclusively in Visual Studio. The development tools support all of the development tasks, including debugging and local testing scenarios. A primary goal of the development experience is to keep familiar Microsoft Dynamics AX 2012 concepts, and seamlessly adapt them to the Visual Studio framework and paradigms.

## What are the Visual Studio tools?
Visual Studio 2015 is the exclusive integrated development environment (IDE) for development. All of your application development work will be performed with it. This section is an overview of the main features that are added to Visual Studio when the development tools are installed.

### Application Explorer

In Visual Studio, the model store is represented by the Application Explorer. On the **View** menu, click **Application** **Explorer** to open it. The Application Explorer corresponds to the Application Object Tree (AOT) that you may be familiar with in Microsoft Dynamics AX 2012. Use the Application Explorer to browse and interact with the elements in the model store that define the applications. The following illustration shows the Application Explorer. For more details, see [Application Explorer](application-explorer.md). [![1\_DevoToolsConcept](./media/1_devotoolsconcept.png)](./media/1_devotoolsconcept.png)

### The project template

Even a simple application can have a large number of elements in its model. The **Operations Project** template has been added to Visual Studio to help you organize and manage the elements that you are working with for a model. You will use the project to design, build, and test model elements. It’s common to have several projects within a single Visual Studio solution. The following illustration shows three projects in a Visual Studio solution. For more details, see [Projects](projects.md). [![2\_DevoToolsConcept](./media/2_devotoolsconcept.png)](./media/2_devotoolsconcept.png)

### Element designers

The Visual Studio tools contain designers for each kind of element in the application. You will use these designers when you create or modify elements. The following illustration shows the element designer for a form element. For more details, see [Element designers](element-designers.md). [![3\_DevoToolsConcept](./media/3_devotoolsconcept.png)](./media/3_devotoolsconcept.png)

### Code editor

The X++ code is written in the code editor for Visual Studio. The standard features that a developer expects from the code editor are supported. For example, sections of code are collapsible. IntelliSense provides guidance as you write or modify code. For more details, see [Code editor](code-editor.md). [![4\_DevoToolsConcept](./media/4_devotoolsconcept.png)](./media/4_devotoolsconcept.png)

### Dynamics 365 menu

The tools add the **Dynamics 365** menu to Visual Studio. Several tools that you will use during the development process are found here. For example, the tools for managing models are accessed from the menu. [![5\_DevoToolsConcept](./media/5_devotoolsconcept.png)](./media/5_devotoolsconcept.png)

