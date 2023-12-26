--- 
# required metadata 
 
title: Maintain BOM for a product configuration model
description: Running this procedure requires an existing product configuration model. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCProductConfigurationModelDetails, PCBOMLineDetails, InventItemIdLookupSimple   
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
# Maintain BOM for a product configuration model

[!include [banner](../../includes/banner.md)]

Running this procedure requires an existing product configuration model. The High end speaker model in the demo company USMF is used to create this procedure.

## Add a BOM line

1. Go to **Product information management \> Products \> Product configuration models**.
1. In the list, find and select the desired record.
    * Select the High end speaker for this procedure.  
1. In the list, select the link in the selected row.
1. Expand the **BOM lines** section.
1. Select **Add**.
1. In the **Name** field, type a value.
1. In the **Description** field, type a value.
1. Select **Save**.

## Add BOM line details

1. Select **BOM line details**.
2. In the **Item number** field, enter or select a value.
    * For example, you can select the item M0055.  
    * For each BOM line property, you can select if it takes a fixed value or is mapped to an attribute.  
3. Select the **Set** check box.
4. Select *Yes* in the **Calculation** field.
    * Setting the **Calculation** property to *Yes* ensures that the BOM line is included in cost calculations.  
5. Select the **Setup** tab.
6. Select the **Set** check box.
7. In the **Quantity** field, enter a number.
    * The quantity field determines how much of the item that will be included in the BOM. This could be an obvious candidate for an attribute mapping.  
8. Select the **Dimension** tab.
    * Verify if any of the product dimensions are active,  and therefore must have a value or attribute assigned.  
9. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]