--- 
title: Set up rules and parameters for cross docking and buyer's push
description: Learn how to set up rules and parameters for cross docking and buyer's push in Microsoft Dynamics 365 Commerce. 
author: josaw1
ms.date: 02/11/2026
ms.topic: how-to 
ms.search.form: RetailReplenishmentRuleTable, RetailReplenishmentTreeLookup   
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Set up rules and parameters for cross docking and buyer's push

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to set up rules and parameters for cross docking and buyer's push in Microsoft Dynamics 365 Commerce.

The following procedure demonstrates the steps to create replenishment rules. 

You use replenishment rules to control how products are distributed to stores when using cross-docking and buyer's push. Set up replenishment rules for stores or store groups. The weight you define for each line in a rule controls how the quantities of products get distributed between the stores when using replenishment rules as the distribution method in Cross-docking or Buyer's push.

This procedure uses the USRT demo company.

To set up rules and parameters for cross docking and buyer's push, follow these steps.

1. In Commerce headquarters, go to **Replenishment rules**.
1. Select **New**.
1. In the **Replenishment rule** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Save**.
1. Select **Add**.
1. In the list, select the row. You can choose **Replenishment hierarchy** or **Channel** for the type. The value controls whether the selection in **Name** is a hierarchy of channels or a specific channel. For this example, leave it set as **Replenishment hierarchy**.  
1. In the **Name** field, select a value. The default weight value comes from the weight defined on the warehouse. Use this weight for the **Replenishment rule** or enter a new weight in the **Weight** field.  
1. In the **Weight** field, enter a number.
1. Select **Add**.
1. In the list, select the row.
1. In the **Type** field, select **Channel**.
1. In the **Name** field, enter or select a value.
1. In the **Weight** field, enter a number.
1. Select **Save**.

[!INCLUDE [footer-include](../../includes/footer-banner.md)]