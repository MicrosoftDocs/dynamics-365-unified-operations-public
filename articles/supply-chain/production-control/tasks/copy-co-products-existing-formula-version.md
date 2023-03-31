--- 
# required metadata 
 
title: Copy co-products from an existing formula version
description: This procedure shows how to copy co-products from an existing formula version to a different formula version for a released product. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductDetailsExtended, BOMConsistOf, PmfFormulaCoBy, BOMRouteCopyDialog   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Copy co-products from an existing formula version

[!include [banner](../../includes/banner.md)]

This procedure shows how to copy co-products from an existing formula version to a different formula version for a released product. It is a prerequisite that there is at least one formula version associated with co-products. The demo data company USP2 is used to create this procedure.


## Find a released product
1. Go to Released products.
2. Click Show filters.
    * You are about to add the field Production type in the filter dialog box.  
3. Click Add a filter field to add the field Production type.
    * In the next step, you need to manually enter Formula in the Production type field before you select Apply. This sets the filter on the list of released products.  
4. Manually enter Formula in the Production type field.
5. Click Apply.

## Select a released product
1. In the list, find and select the desired record.
2. Click Formula versions.
    * On the Engineering Action Pane, click Formula versions.  

## Copy co-products
1. On the Action Pane, click Formula version.
2. Click Co-products.
3. Click Copy.
4. In the Item number field, enter or select a value.
5. In the Formula version field, enter or select a value.
6. Click OK.
7. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]