--- 
# required metadata 
 
title: Create a product number nomenclature for configured product variants
description: This procedure shows you how to set up a product number nomenclature for configured product variants, and how it can be attached to a configurable product master. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, EcoResNomenclature, EcoResProductListPage, EcoResProductDetails, PCProductConfigurationModelListPage, PCProductConfigurationModelDetails   
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
# Create a product number nomenclature for configured product variants

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up a product number nomenclature for configured product variants, and how it can be attached to a configurable product master. This procedure also demonstrates how you can build a configuration nomenclature for a product configuration model component. The demo data company used to create this procedure is USMF. The new product number nomenclature is assigned to the D0004 product master. This task would typically be done by a product designer.

## Create a product number nomenclature

1. Go to **Product information management \> Setup \> Product nomenclature**.
1. Select **New**.
1. In the **Name** field, type a value.
1. In the **Description** field, type a value.
1. Select **Add**.
1. Select **Product master number**.
1. Select **Add**.
1. Select **Text constant**.
1. In the list, mark the selected row.
1. In the **Text** field, type a value.
1. Select **Add**.
1. Select **Configuration**.
1. Close the page.

## Assign the product number nomenclature to a product master

1. Go to **Product information management \> Products \> Product masters**.
1. Use the Quick Filter to find records. For example, filter on the **Product number** field with a value of 'D'.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. Select *Yes* in the **Use nomenclature** field.
1. In the **Product variant number nomenclature** field, enter or select a value.
1. Close the page.
1. Close the page.

## Create nomenclature for a product configuration model component

1. Go to **Product information management \> Products \> Product configuration models**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. Select *Yes* in the **Use configuration nomenclature** field.
1. Select **Add**.
1. Select **Attribute value**.
1. In the list, mark the selected row.
1. In the **Attribute** field, enter or select a value.
1. Select **Add**.
1. Select **Text constant**.
1. In the list, mark the selected row.
1. In the **Text** field, type a value.
1. Select **Add**.
1. Select **Attribute value**.
1. In the list, mark the selected row.
1. In the **Attribute** field, enter or select a value.
1. Select **Add**.
1. Select **Text constant**.
1. In the list, mark the selected row.
1. In the **Text** field, type a value.
1. Select **Add**.
1. Select **Attribute value**.
1. In the list, mark the selected row.
1. In the **Attribute** field, enter or select a value.
1. Select **Add**.
1. Select **Text constant**.
1. In the list, mark the selected row.
1. In the **Text** field, type a value.
1. Select **Add**.
1. Select **Attribute value**.
1. In the list, mark the selected row.
1. In the **Attribute** field, enter or select a value.
1. Select **Add**.
1. Select **Text constant**.
1. In the list, mark the selected row.
1. In the **Text** field, type a value.
1. Select **Add**.
1. Select **Number sequence value**.
1. In the list, mark the selected row.
1. In the **Number sequence** field, enter or select a value.
1. Close the page.
1. Close the page.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]