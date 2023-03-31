--- 
# required metadata 
 
title: Create sales price selection criteria
description: This procedure shows how to create a sales price selection criterion for attribute-based sales price models. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCPriceModelSelectionCriteria, SysQueryForm, SysQueryTableLookUp, SysQueryFieldLookUp   
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
# Create sales price selection criteria

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a sales price selection criterion for attribute-based sales price models. This procedure requires that at least one sales price model be available. This example uses the price model for the Speaker solution sales price model in the USMF demo data company. Typically, a product manager uses this procedure.

## Add a new criterion for an existing sales price model

1. Go to **Product information management \> Products \> Product configuration models**.
1. In the list, select the row for the Speaker solution product model, but don't select the link for the model name.
1. On the Action Pane, select **Model**.
1. Select **Price model criteria**.
1. Select **New**.
1. In the **Name** field, type 'Customer group 10'.
    * The name of the price model criterion is used to help identify the underlying selection criteria.  
1. In the **Price model** field, enter or select a value.
1. In the **Order type** field, select *Sales order*.
    * The order type determines the database fields that will be available for the selection query.  
1. In the **Valid from** field, enter a date.
1. In the **Expire by** field, enter a date.
1. Select **Save**.

## Create the query for the selection criteria

1. Select **Edit**.
2. In the **Table** field, select *Customers*.
3. In the **Field** field, select *Customer group*.
    * In this example, we will use a specific customer group for the selection criteria.  
4. In the **Criteria** field, select *Customer group 10*.
5. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]