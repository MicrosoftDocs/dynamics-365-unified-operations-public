---
title: Commands for determining how elements are used
description: This article reviews the commands that have been added to the Microsoft Visual studio Tools to help you determine how elements are used in an application. 
author: RobinARH
ms.date: 06/20/2017
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.custom: 4984
ms.assetid: e9590e78-6aae-4c3a-b50b-786351cfc0ff
ms.search.region: Global
ms.author: jorisde
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Commands for determining how elements are used

[!include [banner](../includes/banner.md)]

This article reviews the commands that have been added to the Microsoft Visual studio Tools to help you determine how elements are used in an application. 

Because of the large number of elements in a typical application, commands have been added to the Microsoft Visual Studio Tools to make it easier to determine how an element is used.

## Finding where elements are used

During build operations, cross-reference information is generated that can be used to show how elements are used. You can right-click an element and then click **Find References** to display a list of the locations where that element is used. When you click one of the items in the list, the designer for the element opens. 

[![23\_DevoToolsConcept.](./media/23_devotoolsconcept.png)](./media/23_devotoolsconcept.png)

## Viewing a reference diagram

When you right-click some higher-level elements, such as tables, the **View Reference** command is available. This command produces a graphic that shows the elements that are related to the current element. You can right-click the items in the graphic and then click **Go To Definition** to navigate to those elements. 

[![24\_DevoToolsConcept.](./media/24_devotoolsconcept.png)](./media/24_devotoolsconcept.png)

## Additional resources

[Development tools in Visual Studio](development-tools-overview.md)

[Element designers](element-designers.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]