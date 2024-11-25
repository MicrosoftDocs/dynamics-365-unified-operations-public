---
title: AX 2009 migration - Create migration groups
description: Learn about how to create migration groups to upgrade from Microsoft Dynamics AX 2009 to finance and operations apps.
author: sericks007
ms.author: sericks
ms.topic: article
ms.date: 09/13/2018
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Create migration groups

[!include [banner](../includes/banner.md)]

When you create a definition for migration, you determine which entities should be packaged and exported together, and then put all the entities together in a migration group. A migration group is a set of entities that must be processed in a sequence, or that can logically be grouped together. The entities in a migration group are exported together, either from the source to staging or directly to a file package. In a migration group, you also associate legal entities. Migration groups must be set up before you begin the export process.

Follow these steps to create a migration group.

1. In Microsoft Dynamics AX 2009, in the navigation pane, click **Data Migration** \> **Common forms** \> **Create migration group**.
2. In the **Migration group** form, press CTRL+N or click **New** to create a new migration group.
3. Enter a name for the migration group. Then press Tab to move to the **Company** field, and click **Select company**.
4. In the **Select company accounts** form, select one or more companies to add to the migration group, and then click **OK**.
5. In the **Migration group** form, click **Entity**, and select the lines to include in the migration.
6. Fill in any gaps in the field mapping, as required.
7. Click **Apply sequence**, and then close the form.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
