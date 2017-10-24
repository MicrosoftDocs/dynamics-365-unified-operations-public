---

# required metadata

title: Add a method to a table
description: This topic describes how to add a method to a table by using an extension.
author: ivanv-microsoft
manager: AnnBe
ms.date: 07/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ivanv
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4

---

# Add a method to a table

When you extend the business logic that is related to a table, the general coding principles that help keep your code clean still apply. Therefore, you must eventually encapsulate actions in separate methods on the table. In Microsoft Dynamics AX 2012, you completed that task by adding the method directly on the table through overlayering. To complete the same task through extension, you use a different approach. Specifically, you create an augmentation class.

For example, a new field that is named **MyInventLocationId** was added to the InventTable table through extension. A data event handler was also created for the **Inserting** event, and you must implement the logic of filling the new field there. To encapsulate that action, you will create a new method on InventTable and name that method **defaultMyInventLocationId**.

You first create a new class in the extension model. This class will augment the InventTable table, and enable access to the table's fields and methods in a manner that is easy to read and understand. It's important that you choose the correct name for your augmentation class. This name must be unique across all types in all models that are deployed. For more information, see [Naming guidelines for model extensions](naming-guidelines-extensions.md).

```
[ExtensionOf(tableStr(InventTable))]
final class MyInventTable_Extension
{
    [DataEventHandler(tableStr(InventTable), DataEventType::Inserting)]
    public static void InventTable_onInserting(Common sender, DataEventArgs e)
    {
        InventTable inventTable = sender as InventTable;
        // Call the method as if it was defined directly on InventTable.
        inventTable.defaultMyInventLocationId();
    }
    public void defaultMyInventLocationId()
    {
        // This would have partner specific logic to initialize the new field.
        this.MyInventLocationId = this.inventLocationId();
    }
}
```

You can now add new methods to the augmentation class. These methods will then appear in IntelliSense for variables of the **InventTable** type, just as if they were defined directly on the table. This behavior applies to both static methods and instance methods.

There are a few rules for augmentation classes:

+ They must be final.
+ They must be suffixed by **\_Extension**.
+ They must be decorated with the **[ExtensionOf()]** attribute.

> [!NOTE]
> In this example, the data event handling method is also defined on the augmentation class. In a real implementation, you might want to move the data event handling method into a separate class that contains the event handlers for the InventTable table.
