--- 
# required metadata 
 
title: Create a product number nomenclature for predefined product variants
description: This topic explains how to set up a product number nomenclature for predefined product variants, and how you assign it to the appropriate product dimension group. 
author: ShylaThompson
manager: tfehr 
ms.date: 08/20/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, EcoResNomenclature, EcoResProductDimensionGroup   
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
# Create a product number nomenclature for predefined product variants

[!include [banner](../../includes/banner.md)]

This topic explains how to set up a product number nomenclature for predefined product variants, and how you assign it to the appropriate product dimension group. The demo data company used to create this procedure is USMF. The new product number nomenclature is assigned to the Color and Size product dimension group. This task would typically be done by a product designer.


## Create a product number nomenclature
1. Select **Product variant model definition**.
2. Select **Product nomenclature**.
3. Select **New**.
4. In the **Name** field, enter a nomenclature name that helps to identify the target product dimension group, for example, `ColorSize`.
5. In the **Description** field, type a value.
6. Select **Add**.
7. Select **Product master** number.
8. Select **Add**.
9. Select **Text constant**.
10. In the **Text** field, type a value.
11. Select **Add**.
12. Select **Color**.
13. Select **Add**.
14. Select **Text constant**.
15. In the **Text** field, type a value.
16. Select **Add**.
17. Select **Size**.
18. Close the page.

## Assign the nomenclature to a product master
1. Select **Product dimension groups**.
2. Select the **SizeCol product dimension** group.
3. Select **Edit**.
4. Select **Yes** in the **Use nomenclature** field.
5. In the **Product variant number nomenclature** field, enter or select a value.
6. Close the page.

