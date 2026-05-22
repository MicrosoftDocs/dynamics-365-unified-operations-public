---
title: Modify existing fields in a table through extension
description: Learn about how to modify an existing field in a table, including the process of creating an extension for the table.
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

# Modify existing fields in a table through extension

[!include [banner](../includes/banner.md)]

To modify properties on an existing field in a table, first create an extension for the table. You can modify the following properties:

- **Label**
- **Help text**
- **Country Region Codes**
- **Extended Data Type** – You can select only extended data types (EDTs) that are derived from the currently selected EDT. The lookup in the property sheet is filtered so that only those EDTs are shown. For example, to edit the EDT on the **Width** field in the InventTable table, you can create a derived EDT that is based on **BOMMeasureWidth**, and then modify the **Extended Data Type** property on the **Width** field in the **InventTable** extension. By using this method, you can modify the look and feel of the **Width** field in the user interface when you deploy the new package.

:::image type="content" source="media/modify-table-property.jpg" alt-text="Screenshot of modifying an existing field in a table extension."::: 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
