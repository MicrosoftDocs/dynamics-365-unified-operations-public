--- 
title: Create and assign advanced rule structures
description: Learn how to create and assign an advanced rule structure to an account structure with an outline on applying advanced rule structures to account structures. 
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 07/10/2026 
ms.custom:
ms.reviewer: twheeloc
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: DimensionConfigureAccountRuleStructure, DimensionCreateAccountRuleStructure, DimensionHierarchyAddLevel, DimensionHierarchyConstraintActivate, DimensionConfigureAccountStructure, DimensionConfigureAccountRule, DimensionCreateAccountRule, DimensionSelectAccountRuleStructure 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and assign advanced rule structures

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to create and assign an advanced rule structure to an account structure. This guide uses the USMF demo company.

> [!NOTE]
> Advanced rule structures apply only to the Ledger account type (the main account). They don't validate financial dimensions for non-ledger accounts like Vendor, Customer, or Bank account types. For more information, see [Account structures overview](../configure-account-structures.md).

## Create an advanced rule structure

1. Go to **General ledger > Chart of accounts > Structures > Advanced rule structures**.
1. Select **New**.
1. In the **Advanced rule structure** field, enter a name to describe the rule structure.
1. Select **OK**.
1. Select **Add segment**.
1. In the list of segments, select a financial dimension. For example, **Store**.  
1. Select **Add segment**.
1. Select **Activate**.

## Apply an advanced rule structure to an account structure

1. Go to **General ledger > Chart of accounts > Structures > Configure account structures**.
1. In the list, find and select the account structure you want to apply the advanced rule to.
1. Select **Edit**. You can also select **Advanced rules** and you'll be prompted to put the account structure in **Draft mode**.  
1. Select **Advanced rules**.
1. Select **New** to open the drop dialog.
1. In the **Advanced rule** field, type a value.
1. In the **Name** field, type a value.
1. Select **Create**.
1. Select **Add new criteria**.
1. In the **Where** field, select main account or a financial dimension.
1. In the **Operator** field, select an option, such as **is between** and **includes**.
1. In the **Value** field, type a value.
1. In the **through** field, type a value.
1. Select **Add** to open the drop dialog.
1. In the list, find the advanced rule structure you want to use when the criteria you entered is met.
1. Select **Add**.
1. Close the page.
1. Select **Activate**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
