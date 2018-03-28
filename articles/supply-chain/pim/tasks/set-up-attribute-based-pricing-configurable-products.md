--- 
# required metadata 
 
title: Set up attribute-based pricing for configurable products
description: This procedure shows how to set up attribute-based pricing. 
author: YuyuScheller
manager: AnnBe 
ms.date: 10/12/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: bis
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up attribute-based pricing for configurable products

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to set up attribute-based pricing. As a prerequisite, you must have a product configuration model that has one or more components and attributes. This example uses the High End Speaker product model in the USMF demo data company. Typically, a product manager uses this procedure.


## Create a new price model
1. Click Product variant model definition.
2. Click Product configuration models.
3. In the list, select the High End Speaker line, but don’t click the link for the name.
4. On the Action Pane, click Model.
5. Click Price models.
6. Click New.
7. In the Price model name field, type a value.
    * Use a name that makes the model easy to identify.  
8. In the Description field, type a value.
9. Click Save.

## Add price elements
1. Click Edit.
    * Each component in a product model can have a base price element and any number of price expression rules. You can also add prices in different currencies.  
2. In the Base price expression field, type a value.
    * For example, type 100.   A base price expression can be a numerical value, or it can consist of an arithmetic calculation that involves one or more attributes.  
3. Click Add.
4. In the Name field, type ‘Rosewood’.
    * The price expression name helps identify what the price element represents. In this example, we are creating a price element for the Rosewood speaker cabinet finish option.  
5. Click Edit condition.
    * A price condition helps guarantee that a price expression element is included in the sales price only if a specific combination of attributes is present.  
6. In the ConstraintBody field, enter 'CabinetFinish=="Rosewood"'.
7. Click OK.
8. In the Expression field, type a value.
    * For example, type 50.  
9. Close the page.
10. Close the page.

