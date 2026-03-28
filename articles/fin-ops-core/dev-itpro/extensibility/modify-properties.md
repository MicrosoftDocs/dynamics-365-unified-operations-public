---
title: Modify table properties through extension
description: Learn about how to modify properties on a table by using an extension, illustrating how to modify various properties.
author: ivanv-microsoft
ms.author: ivanv
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4
---

# Modify table properties through extension

[!include [banner](../includes/banner.md)]

To modify properties on a table, you must create an extension of that table. In Application Explorer, right-click the table, and then select **Create extension**. The following illustration shows a new table extension created in the selected project.

:::image type="content" source="media/ModifyPropertiesOnTable.jpg" alt-text="Screenshot of a new table extension created in the selected project.":::

You can now modify the following properties through the property sheet:

+ Country Region Codes
+ Created By
+ Created Date Time
+ Form Ref
+ Modified By
+ Modified Date Time
+ Preview Part Ref
+ Tags
+ Title Field1
+ Title Field2

When you set the **Created By**, **Created Date Time**, **Modified By**, or **Modified Date Time** property to **Yes**, you add a corresponding field to the table. The table stores tracking information about the user when it creates or updates records. You can't set these properties to **No** if they're set to **Yes** on the base table.

When you add country or region codes to the list, you make sure that the corresponding table is also applicable when the system runs in the context of the specified country or region.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
