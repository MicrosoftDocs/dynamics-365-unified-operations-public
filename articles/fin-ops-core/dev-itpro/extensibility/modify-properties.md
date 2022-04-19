---
title: Modify table properties through extension
description: This topic describes how to modify properties on a table by using an extension.
author: ivanv-microsoft
ms.date: 08/20/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: ivanv
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4
---

# Modify table properties through extension

[!include [banner](../includes/banner.md)]

To modify properties on a table, you must create an extension of that table. In Application Explorer, right-click the table, and then select **Create extension**. A new table extension is created in the selected project, as shown in the following illustration.

![Create a table extension.](media/ModifyPropertiesOnTable.jpg) 

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

By setting the **Created By**, **Created Date Time**, **Modified By**, or **Modified Date Time** property to **Yes**, you help guarantee that a corresponding field is added to the table. Corresponding tracking information about the user is then stored in the table when records are created or updated. You can't set these properties to **No** if they are set to **Yes** on the base table.

By adding country or region codes to the list, you help guarantee that the corresponding table is also applicable when the system runs in the context of the specified country or region.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
