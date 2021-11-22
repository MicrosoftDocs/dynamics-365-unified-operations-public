---
# required metadata

title: AX 2009 migration - Create package templates 
description: This topic explains how to create package templates that you can use to migrate data from Microsoft Dynamics AX 2009 to Finance and Operations.
author: kfend
ms.date: 09/12/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: kfend
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Create package templates

[!include [banner](../includes/banner.md)]

Packages are created by following a predefined sequence. This sequence is based on the dependencies that the data entities have on each another. Because of these dependencies, when you import data entities, you must import the data entities in the defined order. Otherwise, you might encounter issues during import and configuration.

The Data migration tool (DMT) provides twenty predefined templates, as shown in the following illustration.

[![Data entity import template list.](./media/data-entity-templates.png)](./media/data-entity-templates.png)

You can customize an existing template, or you can create your own templates as you require.

Follow these steps to view and select the entity lists that will be used in the templates for migration.

1. In Microsoft Dynamics AX 2009, click **Data migration** \> **Common forms** \> **Entity list**, and then click **Apply sequence**. Close the message box.
2. Verify that the correct legal entity is selected, and then, in the **Show** field, select to view either all entities or only those entities that should be considered for migration.
3. In the **Template name** field, select a template.
4. In the **Module selected** pane, select the module that contains the data entities to migrate.
5. On the **Entity details** tab, select the **Select for migration** check box for every entity line that you want to migrate.
6. Click **Apply sequence**.
7. To create a customized template, in the Application Object Tree, go to **Resources**, and create a new template in XML format.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]