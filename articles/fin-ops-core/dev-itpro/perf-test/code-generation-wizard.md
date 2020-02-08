---
# required metadata

title: Acceptance test library Code generation wizard
description: This topic provides information about the Code generation wizard for the Acceptance test library.
author: MichaelFruergaardPontoppidan
manager: AnnBe
ms.date: 03/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: MichaelFruergaardPontoppidan
ms.search.validFrom: 2018-XX-XX
ms.dyn365.ops.version: App Update 10.0.2

---

# Acceptance test library Code generation wizard

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

The Acceptance test library (ATL) code generator quickly generates and updates new ATL entities, queries, and specifications, based on tables and data entities.

## Create the AtlEntity class by using the wizard

Follow these steps to create the `AtlEntity` class by using the **Code generation** wizard.

1. In Microsoft Visual Studio, open the table in the designer window.
2. Right-click the name of the table, and then, on the **Add-ins** menu, select **Generate ATL Entity**.
3. Select the fields that should be included in the `AtlEntity` class, and then select **Add**.
4. Rename the entity and the fields as you require.
5. Select **Generate** to create the class.

### Additional optional steps

When you create the `AtlEntity` class, you can also complete these tasks:

- Add required actions for the scenario.
- Add a `default` method to `AtlData` classes.
- Override the `setMainRecordField` method to call the `modifiedField(_fieldId)` method on the table.

    ```xpp
    protected void setMainRecordField(FieldId _fieldId, anytype _value)
    {
        super(_fieldId, _value);
        common.modifiedField(_fieldId);
    }
    ```

## Create the AtlQuery class by using the wizard

Follow these steps to create the `AtlQuery` class by using the **Code generation** wizard.

1. In Visual Studio, open the table in the designer window.
2. Right-click the name of the table, and then, on the **Add-ins** menu, select **Generate ATL Query**.
3. Select the fields and relations that should be included in the `AtlQuery` class, and then select **Add**.
4. Rename the query, the fields, and the relations as you require.
5. Select **Generate** to create the class.

### Additional optional steps

When you create the `AtlQuery` class, you can also add a `query` method to the `AtlData` class that returns an instance of the `AtlQuery` class that you created earlier in this topic.

## Create the AtlSpec class by using the wizard

Follow these steps to create the `AtlSpec` class by using the **Code generation** wizard.

1. In Visual Studio, open the table in the designer window.
2. Right-click the name of the table, and then, on the **Add-ins** menu, select **Generate ATL Specification**.
3. Select the fields that should be included in the `AtlSpec` class, and then select **Add**.
4. Rename the specification and the fields as you require.
5. Select **Generate** to create the class.

### Additional optional steps

Add a `spec` method to the data class that returns an instance of the `AtlSpec` class that you created earlier in this topic.
