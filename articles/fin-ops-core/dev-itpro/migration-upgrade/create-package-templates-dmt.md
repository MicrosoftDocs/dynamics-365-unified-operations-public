---
title: AX 2009 migration - Create package templates
description: Learn about how to create package templates that you can use to migrate data from Microsoft Dynamics AX 2009 to finance and operations.
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

# AX 2009 migration – Create package templates

[!include [banner](../includes/banner.md)]

Create packages by following a predefined sequence. This sequence is based on the dependencies that the data entities have on each other. Because of these dependencies, you must import data entities in the defined order. Otherwise, you might encounter issues during import and configuration.

The Data migration tool (DMT) provides 20 predefined templates, as shown in the following illustration.

:::image type="content" source="./media/data-entity-templates.png" alt-text="Screenshot of Data entity import template list.":::

You can customize an existing template, or you can create your own templates as needed.

Follow these steps to view and select the entity lists that the templates use for migration.

1. In Microsoft Dynamics AX 2009, select **Data migration** \> **Common forms** \> **Entity list**, then select **Apply sequence**. Close the message box.
1. Verify that the correct legal entity is selected then in the **Show** field, select to view either all entities or only those entities that you should consider for migration.
1. In the **Template name** field, select a template.
1. In the **Module selected** pane, select the module that contains the data entities to migrate.
1. On the **Entity details** tab, select the **Select for migration** check box for every entity line that you want to migrate.
1. Select **Apply sequence**.
1. To create a customized template, in the Application Object Tree, go to **Resources**, and create a new template in XML format.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
