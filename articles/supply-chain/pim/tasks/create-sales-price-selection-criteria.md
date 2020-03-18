--- 
# required metadata 
 
title: Create sales price selection criteria
description: This procedure shows how to create a sales price selection criterion for attribute-based sales price models. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCPriceModelSelectionCriteria, SysQueryForm, SysQueryTableLookUp, SysQueryFieldLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create sales price selection criteria

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a sales price selection criterion for attribute-based sales price models. This procedure requires that at least one sales price model be available. This example uses the price model for the Speaker solution sales price model in the USMF demo data company. Typically, a product manager uses this procedure.


## Add a new criterion for an existing sales price model
1. Click Product variant model definition.
2. Click Product configuration models.
3. In the list, select the row for the Speaker solution product model, but don't click the link for the model name.
4. On the Action Pane, click Model.
5. Click Price model criteria.
6. Click New.
7. In the Name field, type 'Customer group 10'.
    * The name of the price model criterion is used to help identify the underlying selection criteria.  
8. In the Price model field, enter or select a value.
9. In the Order type field, select Sales order.
    * The order type determines the database fields that will be available for the selection query.  
10. In the Valid from field, enter a date.
11. In the Expire by field, enter a date.
12. Click Save.

## Create the query for the selection criteria
1. Click Edit.
2. In the Table field, select Customers. 
3. In the Field field, select Customer group.
    * In this example, we will use a specific customer group for the selection criteria.  
4. In the Criteria field, select Customer group 10. 
5. Click OK.

