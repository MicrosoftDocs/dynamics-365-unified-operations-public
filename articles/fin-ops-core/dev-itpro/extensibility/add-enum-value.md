---
title: Add values to enums through extension
description: Learn about how to add new values to an enum by extending the enum, including an outline on extending an enum value.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/05/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Add values to enums through extension

[!include [banner](../includes/banner.md)]

To add new values to an enum, extend the enum. You can extend any enum that's marked as **Extensible** (**IsExtensible = true**). You can find the extensibility information in the **Properties** window in Visual Studio, as shown in the following illustration.

:::image type="content" source="media/AddEnum01.png" alt-text="Screenshot of the Properties window showing the IsExtensible property set to true for an enum.":::

When enum values of extensible enums are synchronized, the integer values of the baseline enum are deterministic. However, the integer values of the extension enum values are non-deterministic. The values are generated during synchronization. Therefore, you can't have logic that depends on the integer value of the enum values. Here are some examples:

- Range comparisons, such as `<`, `>`, and `..`
- Modeled ranges in views and queries
- Query ranges that are created from code

Usually, an extended enum must have its own implementation wherever it's used. Look for all uses of the enum, and add the implementation where it's required. Here are some significant places to look for:

- Switch blocks:

  - If the switch block doesn't have a default case block or has a default case block that doesn't throw an exception, handle the extended enum value by subscribing to a delegate, if a delegate is provided. Otherwise, add a post-event handler to the method.
  - If the enum is used in a switch that has a default case block that throws an exception, contact Microsoft to request a delegate.

- If the enum has an associated class hierarchy that handles the enum, create a subclass for the extended enum–specific implementation, and add the construct on the base class as required. For more information, see [Register subclasses for factory methods](register-subclass-factory-methods.md).
 
## Extend an enum

There are two ways to extend an enum:

- Create a project with a model reference where you want the new enum extension. Right-click the enum to extend, and then select **Create extension**.

    :::image type="content" source="media/AddEnum02.png" alt-text="Screenshot of the context menu showing the Create extension option for an enum.":::

- Right-click the enum to extend, and then select **Create extension in new project**. Select the model for the extension enum.
  
    :::image type="content" source="media/AddEnum03.png" alt-text="Screenshot of the context menu showing the Create extension in new project option for an enum.":::
  
The enum extension is created in the selected model. You can add new enum values to this extension.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
