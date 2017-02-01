---
# required metadata

title: Tools add-ins for Visual Studio | Microsoft Docs
description: This topic reviews the Add-ins infrastructure that has been added to Microsoft Visual Studio, so that developers can more easily add tools for development.
author: RobinARH
manager: AnnBe
ms.date: 2015-12-13 21:59:05
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 27521
ms.assetid: 69d20edc-54ad-490f-bcb7-5745c2b9c31e
ms.region: Global
# ms.industry: 
ms.author: robadawy

---

# Tools add-ins for Visual Studio

This topic reviews the Add-ins infrastructure that has been added to Microsoft Visual Studio, so that developers can more easily add tools for development.

A lot of great tools have been added to Microsoft Visual Studio to support development. However, there will always be additional tools to meet specific requirements. To make it easier to add these additional tools, an **Add-ins** infrastructure has been provided for developers. The additional tools are available in two places:

-   The **Add-ins** submenu on the **Dynamics 365 **menu
-   The **Add-ins** submenu on the shortcut menu in the element designer

Dynamics 365 for Operations ships with the **Form statistics** add-in, which provides a summary of the pattern usage for forms. When you access the **Form statistics** add-in from the **Dynamics 365 **menu, it displays statistics for all forms. When you access the add-in from the shortcut menu for a form that is open in the form designer, it displays statistics for that form only. [![37\_DevoToolsConcept](./media/37_devotoolsconcept.png)](./media/37_devotoolsconcept.png) To make it easier to create your own add-ins, you can select the **Dynamics Developer Tools Add-in** project type when you create a new project in Visual Studio. This project type has the infrastructure that is required to implement an add-in.

See also
--------

[Developer home page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/get-started/technical-concepts-guide)

[Development tools](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-tools/dynamics-ax7-technical-preview-development-tools)

