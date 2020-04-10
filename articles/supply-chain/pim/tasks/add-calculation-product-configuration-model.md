--- 
# required metadata 
 
title: Add a calculation to a product configuration model
description: This procedure shows how to add a new calculation to a product configuration model. 
author: ShylaThompson
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCProductConfigurationModelDetails, PCConstraintEditor, PCRuntimeConfiguratorValidate   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Add a calculation to a product configuration model

[!include [banner](../../includes/banner.md)]

This procedure shows how to add a new calculation to a product configuration model. It shows how you can create a logical expression using the "If" operator to set a speaker height to 10 for white speakers and 15 for all other cabinet finishes. The procedure uses the High end speaker component in the demo company USMF.


## Add a calculation

## Create calculation expression
1. Click Edit expression.
2. In the ConstraintBody field, enter 'If[CabinetFinish=="White", 10, 15]'.
3. Click Validate.
4. Click Close.
5. Click OK.

