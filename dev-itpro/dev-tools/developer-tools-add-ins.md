---
# required metadata

title: Tools add-ins for Visual Studio
description: This topic reviews the Add-ins infrastructure that has been added to Microsoft Visual Studio, so that developers can more easily add tools for development.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 27521
ms.assetid: a73c64e1-7e24-4845-b5da-35b1678ddb60
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Tools add-ins for Visual Studio

[!include[banner](../includes/banner.md)]


This topic reviews the Add-ins infrastructure that has been added to Microsoft Visual Studio, so that developers can more easily add tools for development.

A lot of great tools have been added to Microsoft Visual Studio to support development. However, there will always be additional tools to meet specific requirements. To make it easier to add these additional tools, an **Add-ins** infrastructure has been provided for developers. The additional tools are available in two places:

-   The **Add-ins** submenu on the **Dynamics 365 **menu
-   The **Add-ins** submenu on the shortcut menu in the element designer

Dynamics 365 for Operations ships with the **Form statistics** add-in, which provides a summary of the pattern usage for forms. When you access the **Form statistics** add-in from the **Dynamics 365 **menu, it displays statistics for all forms. When you access the add-in from the shortcut menu for a form that is open in the form designer, it displays statistics for that form only. 

[![37\_DevoToolsConcept](./media/37_devotoolsconcept.png)](./media/37_devotoolsconcept.png) 

To make it easier to create your own add-ins, you can select the **Dynamics Developer Tools Add-in** project type when you create a new project in Visual Studio. This project type has the infrastructure that is required to implement an add-in.

See also
--------

[Developer home page](developer-home-page.md)

[Development tools overview](development-tools-overview.md)



