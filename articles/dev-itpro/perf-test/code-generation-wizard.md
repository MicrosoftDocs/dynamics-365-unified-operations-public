---
# required metadata

title: Acceptance test library code generation wizard
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
ms.reviewer: RobinARH
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

# Acceptance test library code generation wizard

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

The Acceptance test library (ATL) code generator quickly generates and updates new ATL entities, queries, and specification based on tables and data entities.

## Create `AtlEntity` class 
Complete the following steps to create the `AtlEntity` class by using the Code generation wizard.

1. Open the table in the designer window in Visual Studio.
2. Right-click the name of the table and on the **Add-ins** menu, select **Generate ATL Entity**.
3. Select the fields that should be included in the `AtlEntity` and click **Add**.
4. If necessary, rename the entity and the fields.
5. Click **Generate** to create the class.
	
	
### Additional optional steps 
When you create the `AltEntity` class, you can also:

- Add required actions for the scenario.
- Add a `default` method to `AtlData` classes.
- Override the `setMainRecordField` method in order to call the "modifiedField(_fieldId)" method on the table.

    ```
    protected void setMainRecordField(FieldId _fieldId, anytype _value)
    {
        super(_fieldId, _value);
        common.modifiedField(_fieldId);
    }
    ```

## Create `AtlQuery` 
Complete the following steps to create the `AtlQuery` class by using the Code generation wizard. 

1. Open the table in the designer window in Visual Studio.
2. Right-click the name of the table and on the **Add-ins** menu, click **Generate ATL Query**.
3. Select the fields and relations that should be included in the `AtlQuery`, and then click **Add**.
4. If needed, rename the query, the fields, and the relations.
6. Click **Generate** to create the class.
	
	
### Additional optional steps
When you create the `AltQuery` class, you can also add a `query` method to the `AtlData` class that returns an instance of the `AtlQuery` class created in the procedure earlier in this topic.

## Create `AtlSpec` class using the wizard
Complete the following steps to create the `AtlSpec` class by using the Code generation wizard.

1. Open the table in the designer window in Visual Studio.
2. Right-click the name of the table and on the **Add-ins** menu, select **Generate ATL Specification**.
3. Select the fields that should be included in the `AtlSpec`, and click **Add**.
4. If needed, rename the specification and the fields.
5. Click **Generate** to create the class.
	
	
### Additional optional steps 

Add a `spec` method to the data class which will return an instance of the `AtlSpec` class created in the procedure earlier in this topic.
