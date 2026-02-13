---
title: AX 2009 migration - Create migration groups
description: Learn about how to create migration groups to upgrade from Microsoft Dynamics AX 2009 to finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Create migration groups

[!include [banner](../includes/banner.md)]

When you create a definition for migration, you determine which entities should be packaged and exported together, and then put all the entities together in a migration group. A migration group is a set of entities that you must process in a sequence or that you can logically group together. You export the entities in a migration group together, either from the source to staging or directly to a file package. In a migration group, you also associate legal entities. You must set up migration groups before you begin the export process.

Follow these steps to create a migration group.

1. In Microsoft Dynamics AX 2009, in the navigation pane, select **Data Migration** \> **Common forms** \> **Create migration group**.
1. In the **Migration group** form, press CTRL+N or select **New** to create a new migration group.
1. Enter a name for the migration group. Then press Tab to move to the **Company** field, and select **Select company**.
1. In the **Select company accounts** form, select one or more companies to add to the migration group, and then select **OK**.
1. In the **Migration group** form, select **Entity**, and select the lines to include in the migration.
1. Fill in any gaps in the field mapping, as required.
1. Select **Apply sequence**, and then close the form.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
