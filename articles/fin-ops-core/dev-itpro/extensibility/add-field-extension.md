---
title: Add fields to tables through extension
description: Learn how to use a table extension to add a field to a table by creating an extension for the InventTable table in your model.
author: ivanv-microsoft
ms.author: ivanv
ms.topic: article
ms.date: 03/06/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-06-01
ms.dyn365.ops.version: Platform update 4
---

# Add fields to tables through extension

[!INCLUDE [banner](../includes/banner.md)]

To add a new field to an existing table, first create a table extension. For example, to add a field that holds the radius of the released product, create an extension for the `InventTable` table in your model, as shown in the following illustration.

:::image type="content" source="media/TableNewField01.jpg" alt-text="Screenshot of creating a table extension for the InventTable table.":::

Add the field to the extension, just as you would add a field to a table in your model. Use one of the following methods:

+ In the designer, right-click the **Fields** node, select **New**, and then select the type of field to add.
+ Drag an existing Extended Data Type or Base Enumeration from your project onto the **Fields** node.

When you finish, modify the properties of the new field. In the following illustration, only the **Label** property was modified.

:::image type="content" source="media/TableNewField02.jpg" alt-text="Screenshot of modifying properties of the new field in the designer.":::

Optionally, add the new field either to one of the existing field groups or to a new field group that you create. In the following illustration, the `Radius` field was added to the `PhysicalDimensions` field group.

:::image type="content" source="media/TableNewField03.jpg" alt-text="Screenshot of adding the new Radius field to the PhysicalDimensions field group.":::

After compilation and synchronization of the database, you can see and edit the new field in the user interface.

:::image type="content" source="media/TableNewField04.jpg" alt-text="Screenshot of the new field displayed in the user interface.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
