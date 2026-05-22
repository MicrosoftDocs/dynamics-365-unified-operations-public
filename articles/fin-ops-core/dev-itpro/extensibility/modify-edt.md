---
title: Modify extended data types (EDTs) through extension
description: Learn about how you can customize several properties on extended data types (EDTs) by using extensions, including using property sheets.
author: ivanv-microsoft
ms.author: ivanv
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Modify extended data types (EDTs) through extension

[!include [banner](../includes/banner.md)]

You can customize several properties on existing extended data types (EDTs) through extension:

- Label
- Help text
- Form help
- Country region codes
- String size
  - You can only modify the value if the EDT doesn't extend from another EDT.
  - You can only set the new string size to a value equal to or larger than the base EDT value.
- Decimals (NoOfDecimals property)
  - For more information, see [Extending decimal point precision for selected data types](decimal-point-precision.md).

Modify the properties as you would for newly added elements, using the property sheet.

:::image type="content" source="media/EDT01.jpg" alt-text="Screenshot of extension properties.":::

After compiling the code, you can see the changes in the application.

:::image type="content" source="media/EDT02.jpg" alt-text="Screenshot of test form.":::

You can view the created extensions in the Application Explorer in Visual Studio.

:::image type="content" source="media/EDT03.jpg" alt-text="Screenshot of Application Explorer.":::

## If you modify the EDT in more than one model

If multiple ISVs extend the same extended data type, the properties of the EDT from the model with the highest Model ID (closest to USR) take precedence. If multiple models contain changes in the same layer, the changes from the model with the highest Model ID take precedence. For example, if ISV 1 modifies the label of `ItemId` to **Awesome item number** in model `AwesomeModel` (USR layer) with ID 15, and ISV 2 modifies the label of `ItemId` to **Super item number** in model `SuperModel` (USR layer) with ID 12, the end user sees **Awesome item number** in the user interface instead of **Item number**.

> [!NOTE]
> Instead of extending an existing EDT, you can create a new one by deriving it from the existing EDT. This approach allows you to edit more properties than you can edit by using the extension approach. To use your new EDT, you need to modify the fields that use the existing EDT.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
