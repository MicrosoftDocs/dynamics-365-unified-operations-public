--- 
# required metadata 
 
title: Add an expression constraint to a product configuration model
description: This procedure shows how you can add a new constraint expression to a product configuration model. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCProductConfigurationModelDetails, SysClientPolymorphicCreateSelector, PCConstraintEditor, PCRuntimeConfiguratorValidate   
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
# Add an expression constraint to a product configuration model

[!include [banner](../../includes/banner.md)]

This procedure shows how you can add a new constraint expression to a product configuration model. It shows how you can mandate that corner protection must be applied to a speaker if the user has selected a front grill in metal. The procedure uses the High end speaker component in the demo company USMF.


## Create an expression constraint
1. Click Product variant model definition.
2. Click Product configuration models.
3. In the list, find and select the desired record.
    * This example uses the high end speaker model.  
4. In the list, click the link in the selected row.
5. Expand the Constraints section.
6. Click Add.
7. Click Create.
8. In the Name field, type a value.

## Enter expression
1. Click Edit expression.
    * If you unlock the user interface in the task recording at this stage, you can use IntelliSense and the list of symbols to build the constraint expression .  
2. In the ConstraintBody field, enter 'Implies[FrontGrill=="Metal", CornerProtection] '.
    * This expression logic states: If the Front grill is  metal, then the corner protection option must be selected.  
3. Click Validate.
    * The validate function runs through the constraint expression and checks for syntax errors.  
4. Click Close.
5. Click OK.

