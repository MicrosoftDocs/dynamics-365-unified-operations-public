--- 
# required metadata 
 
title: Maintain BOM for a product configuration model
description: Running this procedure requires an existing product configuration model. 
author: ShylaThompson
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCProductConfigurationModelDetails, PCBOMLineDetails, InventItemIdLookupSimple   
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
# Maintain BOM for a product configuration model

[!include [banner](../../includes/banner.md)]

Running this procedure requires an existing product configuration model. The High end speaker model in the demo company USMF is used to create this procedure.


## Add a BOM line
1. Click Product variant model definition.
2. Click Product configuration models.
3. In the list, find and select the desired record.
    * Select the High end speaker for this procedure.  
4. In the list, click the link in the selected row.
5. Expand the BOM lines section.
6. Click Add.
7. In the Name field, type a value.
8. In the Description field, type a value.
9. Click Save.

## Add BOM line details
1. Click BOM line details.
2. In the Item number field, enter or select a value.
    * For example, you can select the item M0055.  
    * For each BOM line property, you can select if it takes a fixed value or is mapped to an attribute.  
3. Select the Set check box.
4. Select Yes in the Calculation field.
    * Setting the Calculation property to Yes ensures that the BOM line is included in cost calculations.  
5. Click the Setup tab.
6. Select the Set check box.
7. In the Quantity field, enter a number.
    * The quantity field determines how much of the item that will be included in the BOM. This could be an obvious candidate for an attribute mapping.  
8. Click the Dimension tab.
    * Verify if any of the product dimensions are active,  and therefore must have a value or attribute assigned.  
9. Click OK.

