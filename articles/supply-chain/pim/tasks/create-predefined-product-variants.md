--- 
# required metadata 
 
title: Create predefined product variants
description: This procedure walks through creating product variants for a product master using the combinations of product dimensions. 
author: ShylaThompson
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductListPage, EcoResProductCreate, EcoResProductDetails, EcoResProductMasterDimension, EcoResProductVariants, EcoResProductVariantSuggestions   
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
# Create predefined product variants

[!include [banner](../../includes/banner.md)]

This procedure walks through creating product variants for a product master using the combinations of product dimensions. The demo company used to create this procedure is USMF.


## Create a product master
1. Go to Product information management > Products > Product masters.
2. Click New.
3. In the Product number field, type a value.
    * Entering a product number manually is only required if no number sequence has been set for the product number field. In other words, skip the step if number sequence has been set for the field.  
4. In the Product name field, type a value.
5. In the Product dimension group field, enter or select a value.
    * Select the product dimension group SizeCol (Size and Color).  
6. Click OK.

## Add product dimensions
1. Click Product dimensions.
    * This example shows how to manually enter product dimensions. You can also choose to select a size, color or style group that includes the product dimension values you want to use.  
2. Click New.
3. In the list, mark the selected row.
4. In the Size field, enter or select a value.
5. In the Name field, type a value.
6. Click New.
7. In the list, mark the selected row.
8. In the Size field, enter or select a value.
9. In the Name field, type a value.
10. Click the Colors tab.
11. Click New.
12. In the list, mark the selected row.
13. In the Color field, enter or select a value.
14. In the Name field, type a value.
15. Click New.
16. In the list, mark the selected row.
17. In the Color field, enter or select a value.
18. In the Name field, type a value.
19. Click Save.
20. Close the page.

## Generate product variants
1. Click Product variants.
2. Click Variant suggestions.
3. Click Select all.
    * In this example, all possible variants are selected. If only a subset of the possible product dimension combinations will be used to create variants, you can select the individual entries.  
4. Click Create.
    * You can generate descriptions for all your variants based on the combination of product dimension values. The descriptions are optional.  
5. Click Save.

