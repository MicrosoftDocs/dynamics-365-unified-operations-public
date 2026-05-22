---
title: Extend table maps that are used for versioning
description: Learn about how to extend table maps that can be used for versioning, including an outline on how to extend PurchLine and PurchLineHistory tables with new fields.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: how-to 
ms.custom: 
  - bap-template
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 11
---

# Extend table maps that are used for versioning

[!include [banner](../includes/banner.md)]

## PurchLineMap table map logic

When you add new fields to the **PurchLine** and **PurchLineHistory** tables by using table extensions, you must copy the new fields between the tables when you version a purchase order. The **PurchLineMap** table map specifies the fields that you must copy between the **PurchLine** table and the **PurchLineHistory** table when you create or edit a new purchase order version. To accomplish this goal, extend the **PurchLineMap** map table to include the additional fields. Additionally, the **VersioningPurchaseOrder** class uses the **PurchLineMap** when archiving purchase order lines. The following diagram shows the model.

:::image type="content" source="media/MapsWithVersioning1.png" alt-text="Screenshot of the VersioningPurchaseOrder model diagram.":::

To specify new fields to copy, the **PurchLineMap** table map logic and its usage are refactored. The copy logic moves to the **PurchLineVersioning** class, so the **VersioningPurchaseOrder** class references the **PurchLineVersioning** class instead of the **PurchLineMap** table map. The **PurchLineVersioning** class delegates the logic to copy the fields and the logic to determine whether a confirmation is required to the classes that implement the **PurchLineIVersioningFieldSet** interface. Each class that implements the interface is associated with a table map that specifies the fields to copy.

The **PurchLineDictVersioning** class instantiates the **PurchLineIVersioningFieldSet** object by using reflection. The **PurchLineDictVersioning** class collects the entire set of fields that need to be copied. It collects the field data based on all the table maps associated with a class that implements **PurchLineIVersioningFieldSet**. The following diagram displays the new classes and their dependencies.

:::image type="content" source="media/MapsWithVersioning2.png" alt-text="Screenshot of the new classes and their dependencies diagram.":::

## How to extend PurchLine and PurchLineHistory tables with new fields

Suppose that you want the ISVModule2 model to extend the **PurchLine** and **PurchLineHistory** tables with new fields that you must copy when creating a new version of a purchase order.

> [!NOTE]
> You must have developer access to the ISVModule2 model.

To complete this task, perform the following steps:

1. Add fields by using table extensions to the **PurchLine** and **PurchLineHistory** tables.
1. Create a new table map containing the fields that you must copy, and implement the new table map on the two new table extensions.
1. Create a new class to implement the **PurchLineIVersioningFieldSet** interface and implement the following required methods.
    - **copyVersion** method - Copies data between two records of the new table map type.
    - **fieldSetTableMapId** method - Returns the ID of the new table map.
    - **isChangeConfirmationRequired** method - Returns true or false based on whether the change to the newly added field values requires a confirmation to be created.

The following diagram shows the classes, interfaces, and extensions described in these steps.

:::image type="content" source="media/TableMaps.png" alt-text="Screenshot of the classes, interfaces, and extensions diagram.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
