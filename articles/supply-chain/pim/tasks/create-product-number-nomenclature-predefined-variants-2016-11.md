--- 
# required metadata 
 
title: Create a product number nomenclature for predefined product variants
description: This article explains how to set up a product number nomenclature for predefined product variants, and how you assign it to the appropriate product dimension group. 
author: t-benebo
ms.date: 08/20/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, EcoResNomenclature, EcoResProductDimensionGroup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a product number nomenclature for predefined product variants

[!include [banner](../../includes/banner.md)]

This article explains how to set up a product number nomenclature for predefined product variants, and how you assign it to the appropriate product dimension group. The demo data company used to create this procedure is USMF. The new product number nomenclature is assigned to the Color and Size product dimension group. This task would typically be done by a product designer.


## Create a product number nomenclature

1. Go to **Product information management \> Setup \> Product nomenclature**.
1. Select **New**.
1. In the **Name** field, enter a nomenclature name that helps to identify the target product dimension group, for example, `ColorSize`.
1. In the **Description** field, type a value.
1. Select **Add**.
1. Select **Product master** number.
1. Select **Add**.
1. Select **Text constant**.
1. In the **Text** field, type a value.
1. Select **Add**.
1. Select **Color**.
1. Select **Add**.
1. Select **Text constant**.
1. In the **Text** field, type a value.
1. Select **Add**.
1. Select **Size**.
1. Close the page.

## Assign the nomenclature to a product master

1. Select **Product dimension groups**.
2. Select the **SizeCol product dimension** group.
3. Select **Edit**.
4. Select **Yes** in the **Use nomenclature** field.
5. In the **Product variant number nomenclature** field, enter or select a value.
6. Close the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]