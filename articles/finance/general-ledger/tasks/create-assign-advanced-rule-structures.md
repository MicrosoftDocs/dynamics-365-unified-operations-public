--- 
# required metadata 
 
title: Create and assign advanced rule structures
description: This article explains how to create and assign an advanced rule structure to an account structure. 
author: aprilolson
ms.date: 07/19/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DimensionConfigureAccountRuleStructure, DimensionCreateAccountRuleStructure, DimensionHierarchyAddLevel, DimensionHierarchyConstraintActivate, DimensionConfigureAccountStructure, DimensionConfigureAccountRule, DimensionCreateAccountRule, DimensionSelectAccountRuleStructure   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and assign advanced rule structures

[!include [banner](../../includes/banner.md)]

This article explains how to create and assign an advanced rule structure to an account structure. This guide uses the USMF demo company.

## Create an advanced rule structure
1. Go to **Navigation pane > Modules > General ledger > Chart of accounts > Structures > Advanced rule structures**.
2. Select **New** to open the drop dialog.
3. In the **Advanced rule structure** field, type a name to describe the rule structure.
4. Select **OK**.
5. Select **Add segment**.
6. In the list of segments, select a financial dimension. For example, **Store**.  
7. Select **Add segment**.
8. Select **Activate**.

## Apply an advanced rule structure to an account structure
1. Go to **navigation pane > Modules > General ledger > Chart of accounts > Structures > Configure account structures**.
2. In the list, find and select the account structure you want to apply the advanced rule to.
3. Select **Edit**. You can also select **Advanced rules** and you will be prompted to put the account structure in **Draft mode**.  
4. Select **Advanced rules**.
5. Select **New** to open the drop dialog.
6. In the **Advanced rule** field, type a value.
7. In the **Name** field, type a value.
8. Select **Create**.
9. Select **Add new criteria**.
10. In the **Where** field, select main account or a financial dimension.
11. In the **Operator** field, select an option, such as **is between** and **includes**.
12. In the **Value** field, type a value.
13. In the **through** field, type a value.
14. Select **Add** to open the drop dialog.
15. In the list, find the advanced rule structure you want to use when the criteria you entered is met.
16. Select **Add**.
17. Close the page.
18. Select **Activate**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
