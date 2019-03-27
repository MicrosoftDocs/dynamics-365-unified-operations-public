---
# required metadata

title: Acceptance test library code generation wizard
description: This topic provides information about the Code genration wizard for the Acceptance test library.
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

The ATL Code Generator is the swiss-army knife that generates/update quickly new ATL entities, queries and specification based on tables and data entities.

## Create `AtlEntity` class using the wizard

1. Open the table in the designer window in Visual Studio.
2. Right click the name of the table and select 'Generate ATL Entity' from the Add-ins menu.
3. Select the fields that should be included in the `AtlEntity` and press the 'Add' button
4. Rename the name of entity if a different name if required.
5. Rename the name of the fields if required
6. Press the 'Generate' button to create the class.
	
	
### Additional steps to consider

1. Add actions required for the scenario.
2. Add a `default` method to `AtlData` classes.
3. Override the `setMainRecordField` method in order to call the "modifiedField(_fieldId)" method on the table.

    ```
    protected void setMainRecordField(FieldId _fieldId, anytype _value)
    {
        super(_fieldId, _value);
        common.modifiedField(_fieldId);
    }
    ```

## Create `AtlQuery` class using the wizard

1. Open the table in the designer window in Visual Studio.
2. Right click the name of the table and select 'Generate ATL Query' from the Add-ins menu
3. Select the fields and relations that should be included in the `AtlQuery` and press the 'Add' button
4. Rename the name of query if a different name if required.
5. Rename the name of the fields and relations if required
6. Press the 'Generate' button to create the class.
	
	
### Additional steps to consider

1. Add a `query` method to the `AtlData` class returning an instance of the `AtlQuery` class created above.

## Create `AtlSpec` class using the wizard

1. Open the table in the designer window in Visual Studio.
2. Right click the name of the table and select 'Generate ATL Specification' from the Add-ins menu.
3. Select the fields that should be included in the `AtlSpec` and press the 'Add' button.
4. Rename the name of specification if a different name is required.
5. Rename the name of the fields if required.
6. Press the 'Generate' button to create the class.
	
	
### Additional steps to consider

1. Add a `spec` method to the data class returning an instance of the `AtlSpec` class created above.
