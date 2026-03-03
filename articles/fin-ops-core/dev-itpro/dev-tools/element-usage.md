---
title: Commands for determining how elements are used
description: Learn about the commands that have been added to the Microsoft Visual Studio Tools to help you determine how elements are used in an application.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/03/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: e9590e78-6aae-4c3a-b50b-786351cfc0ff
---

# Commands for determining how elements are used

[!include [banner](../includes/banner.md)]

This article reviews the commands in Microsoft Visual Studio Tools to help you determine how elements are used in an application.  

Because of the large number of elements in a typical application, commands are available in Microsoft Visual Studio Tools that make it easier to determine how an element is used.

## Finding where elements are used

During build operations, the tools generate cross-reference information that you can use to show how elements are used. You can right-click an element and then select **Find References** to display a list of the locations where that element is used. When you select one of the items in the list, the designer for the element opens. 

:::image type="content" source="./media/23_devotoolsconcept.png" alt-text="Screenshot of the Find References results showing where an element is used." lightbox="./media/23_devotoolsconcept.png":::

## Viewing a reference diagram

When you right-click some higher-level elements, such as tables, you see the **View Reference** command. This command produces a graphic that shows the elements that are related to the current element. You can right-click the items in the graphic and then select **Go To Definition** to navigate to those elements. 

:::image type="content" source="./media/24_devotoolsconcept.png" alt-text="Screenshot of the reference diagram showing elements related to the current element." lightbox="./media/24_devotoolsconcept.png":::

## Additional resources

[Development tools in Visual Studio](development-tools-overview.md)

[Element designers](element-designers.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
