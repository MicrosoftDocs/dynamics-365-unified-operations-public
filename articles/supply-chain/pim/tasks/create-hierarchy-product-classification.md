--- 
# required metadata 
 
title: Create a hierarchy of product classification
description: This procedure shows how to create a new category hierarchy and assign a commodity code hierarchy type. 
author: t-benebo
ms.date: 07/11/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResCategoryHierarchyListPage, EcoResCategoryHierarchyCreate, EcoResCategory, EcoResCategoryHierarchyRole, EcoResProductCategory, EcoResCategorySearchList, EcoResCategoryHierarchyFactbox, EcoResCategoryFriendlyName, EcoResCategoryAddProduct   
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
# Create a hierarchy of product classification

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a new category hierarchy and assign a commodity code hierarchy type. The demo data company used to create this procedure is USMF. This procedure is intended for the category manager.


## Create the new category hierarchy
1. Go to **Product information management > Setup > Categories and attributes > Category hierarchies**.
2. Click **New**.
3. In the **Name** field, type a value.
4. In the **Description** field, type a value.
5. Click **Create**.

## Build the hierarchy
1. Click **New** category node.
2. In the **Name** field, type a value.
3. In the **Code** field, type a value.
4. In the **Friendly name** field, type a value.
5. Click **New** category node.
6. In the **Name** field, type a value.
7. In the **Code** field, type a value.
8. In the **Friendly name** field, type a value.
9. Click **New** category node.
10. In the **Name** field, type a value.
11. In the **Code** field, type a value.
12. In the **Friendly name** field, type a value.
13. Click **New** category node.
14. In the **Name** field, type a value.
15. In the **Code** field, type a value.
16. In the **Friendly name** field, type a value.
17. Close the page.

## Classify the hierarchy
1. In the list, find and select the desired record.
2. On the **Action Pane**, click **Category hierarchy**.
3. Click **Associate hierarchy type**.
4. Click **New**.
5. In the **Category hierarchy type** field, select an option. Select the **Commodity code category hierarchy type for product classification**.  
6. In the **Category hierarchy** field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]