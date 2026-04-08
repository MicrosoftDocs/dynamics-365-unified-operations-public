---
title: Add methods to tables through extension
description: Learn how to add a method to a table by using an extension, including code examples for adding methods to tables.
author: ivanv-microsoft
ms.author: ivanv
ms.topic: how-to
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4
---

# Add methods to tables through extension

[!include [banner](../includes/banner.md)]

When you extend the business logic related to a table, follow general coding principles to keep your code clean. Encapsulate actions in separate methods on the table. In Microsoft Dynamics AX 2012, you add the method directly on the table through overlayering. To complete the same task through extension, use a different approach. Specifically, create an augmentation class.

For example, you add a new field named **MyInventLocationId** to the `InventTable` table through extension. You also create a data event handler for the **Inserting** event, and you implement the logic for filling the new field. To encapsulate that action, you create a new method on `InventTable` and name that method **myDefaultInventLocationId**.

First, create a new class in the extension model. This class augments the `InventTable` table and enables access to the table's fields and methods in a manner that's easy to read and understand. Choose the correct name for your augmentation class. This name must be unique across all types in all models that are deployed. For more information, see [Naming guidelines for extensions](naming-guidelines-extensions.md).

```xpp
[ExtensionOf(tableStr(InventTable))]
final class InventTableMy_Extension
{
    public void myDefaultInventLocationId()
    {
        // This would have partner specific logic to initialize the new field.
        this.MyInventLocationId = this.inventLocationId();
    }
}
```

You can now add new methods to the augmentation class. These methods then appear in IntelliSense for variables of the **InventTable** type, just as if they were defined directly on the table. This behavior applies to both static methods and instance methods.

Follow these rules for augmentation classes:

- They must be final.
- They must be suffixed by **\_Extension**.
- They must be decorated with the **[ExtensionOf()]** attribute.

Now you can use your new method, for example, from an event handler:

```xpp
class InventTableMy_EventHandler
{
    [DataEventHandler(tableStr(InventTable), DataEventType::Inserting)]
    public static void InventTable_onInserting(Common sender, DataEventArgs e)
    {
        InventTable inventTable = sender as InventTable;
        // Call the method as if it was defined directly on InventTable.
        inventTable.myDefaultInventLocationId();
    }
}

```

> [!NOTE]
> It's common for event handler classes to contain handlers for any number of events. However, it's **not** good practice to put event handlers in augmentation classes. Doing so makes the event handler methods available as methods on the augmented type. This is incorrect because the event handler is intended to be called through the event, not explicitly as a method on the type.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
