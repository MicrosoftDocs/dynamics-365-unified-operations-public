---
# required metadata

title: Element usage
description: This article reviews the commands that have been added to the Microsoft Visual studio Tools to help you determine how elements are used in an application. 
author: RobinARH
manager: AnnBe
ms.date: 2015-09-14 08 - 50 - 13
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 4984
ms.assetid: d2447385-6a0b-40dd-bc94-55999e477b41
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Element usage

This article reviews the commands that have been added to the Microsoft Visual studio Tools to help you determine how elements are used in an application. 

Because of the large number of elements in a typical application, commands have been added to the Microsoft Visual Studio Tools to make it easier to determine how an element is used.

### Finding where elements are used

During build operations, cross-reference information is generated that can be used to show how elements are used. You can right-click an element and then click **Find References** to display a list of the locations where that element is used. When you click one of the items in the list, the designer for the element opens. [![23\_DevoToolsConcept](./media/23_devotoolsconcept.png)](./media/23_devotoolsconcept.png)

### Viewing a reference diagram

When you right-click some higher-level elements, such as tables, the **View Reference** command is available. This command produces a graphic that shows the elements that are related to the current element. You can right-click the items in the graphic and then click **Go To Definition** to navigate to those elements. [![24\_DevoToolsConcept](./media/24_devotoolsconcept.png)](./media/24_devotoolsconcept.png)

See also
--------

[Microsoft Dynamics &#8216;AX 7 &#8216; development tools](development-tools.md)

[Element designers](element-designers.md)

[Technical Concepts Guide](developer-landing-page.md)

