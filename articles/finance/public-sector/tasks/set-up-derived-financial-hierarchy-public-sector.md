--- 
# required metadata 
 
title: Set up a derived financial hierarchy in the public sector
description: This article provides information about using derived financial hierarchies to work with posted transaction data for main and full account numbers and financial dimension values. 
author: twheeloc
ms.date: 02/14/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResCategoryHierarchyListPage, EcoResCategoryHierarchyCreate, EcoResCategory, EcoResCategoryHierarchyRole, LedgerDerivedFinHierarchyLegalEntities, LedgerDerivedFinHierarchies   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up a derived financial hierarchy in the public sector

[!include [banner](../../includes/banner.md)]

To meet Common Government-wide Accounting Classification (CGAC) requirements, public sector organizations can use derived financial hierarchies to collect and analyze posted transaction data for specific main account numbers, full account numbers, and financial dimension values. This procedure was created using the PSUS demo company data in the public sector partition.


## Create a category hierarchy
1. Go to **Product information management > Setup > Categories and attributes > Category hierarchies**.
2. Click **New**.
3. In the **Name** field, type a value.
4. In the **Description** field, type a value.
5. Click **Create**.
6. Click **New category** node.
7. In the **Name** field, type a value.
8. In the **Code** field, type a value.
9. Click **New category** node.
10. In the **Name** field, type a value.
11. In the **Code** field, type a value.
    * (Optional) Add additional child nodes, or set additional options for the nodes that you have created.  
12. Click **Save**.

## Assign the Derived financial hierarchy category type
1. Go to **Product information management > Setup > Categories and attributes > Category hierarchy role associations**.
2. Click **New**.
3. In the **Category hierarchy type** field, select 'Derived financial hierarchy'.
4. In the **Category hierarchy** field, click the drop-down button to open the lookup.
5. In the list, click the **Category hierarchy** to associate with the **Derived financial hierarchy** type.
6. Click **Save**.

## Associate the derived financial hierarchy with a legal entity
1. Go to **General ledger > Chart of accounts > Dimensions > Associate financial hierarchies**.
2. Click **New**.
3. In the **Legal entity** field, click the drop-down button to open the lookup.
4. In the list, select the legal entity to associate with the derived financial hierarchy.
5. In the **Derived financial hierarchy** field, click the drop-down button to open the lookup.
6. In the list, select the derived financial hierarchy to associate with the legal entity.
7. Click **Save**.

## Create filter rules for the derived financial hierarchy
1. Go to **General ledger > Chart of accounts > Dimensions > Derived financial hierarchies**.
2. In the **Derived financial hierarchy** field, click the drop-down button to open the lookup.
3. In the list, click the hierarchy to create filter rules for.
4. In the tree, select 'In the tree, select a child node.'.
5. Click **Edit** filter.
    * Click **Add new criteria** to begin adding rules to the filter. After you've added all of the criteria, click **Activate filter**.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
