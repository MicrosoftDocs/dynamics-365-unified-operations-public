---
title: Change the captions of forms through extension
description: Learn about how to change the form caption that helps the user identify the current page in a web browser, with an example of what the form caption should appear.
author: ivanv-microsoft
ms.author: ivanv
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4
---

# Change the captions of forms through extension

[!include [banner](../includes/banner.md)]

The form caption appears in the page tab next to the web browser's Address bar and helps the user identify the page that is currently open. In metadata, the form caption is represented by a property on the form design. To change the caption, modify the **Caption** property on the form design. You can make this change through extension. Create an extension of the selected form in the extension model, and then change the **Caption** property as usual.

:::image type="content" source="media/ChangeCaption01.jpg" alt-text="Screenshot of modifying the Caption property.":::

The following illustration shows what the form caption looks like in a browser.

:::image type="content" source="media/ChangeCaption02.jpg" alt-text="Screenshot of the form caption displayed in a browser.":::

> [!NOTE]
> You can't change any other properties on the form design.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
