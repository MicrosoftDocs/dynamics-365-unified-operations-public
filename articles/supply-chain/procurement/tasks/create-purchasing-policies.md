--- 
# required metadata 
 
title: Create purchasing policies
description: This article shows you how to create purchasing policies to align with your business processes for purchasing. 
author: GalynaFedorova
ms.date: 07/31/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysPolicyListPage, SysPolicyParameters, SysPolicy, RequisitionPurposeRule   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create purchasing policies

[!include [banner](../../includes/banner.md)]

This article shows you how to create purchasing policies to align with your business processes for purchasing. Before you can create purchasing policies, you must set up the purchasing policy parameters. It's possible to create, modify, and retire a purchasing policy, but you can't delete a purchasing policy. This procedure would typically be carried out by a purchasing manager. You can use this procedure in demo data company USMF or on your own data.


## Set up policy parameters
1. Go to **Procurement and sourcing > Setup > Policies > Purchasing policies**.
2. On the Action Pane, select **Parameters**.
    - Policy precedence rules apply to different levels in your organization. The organizational units that are shown depend on your organizational hierarchy, and on which levels in the hierarchy have been assigned the purpose of Procurement internal control. For example, your organization might have legal entities, cost centers, regions, and departments, but it may be that only some of these have a hierarchy purpose of Procurement internal control. As a default, the organization of type Company is available.  
3. Select the **Policy rule type parameters** tab.
4. In the tree, go to **Purchasing policy > Purchase requisition control rule**.
    - You define the order of precedence for policy resolution at the policy level. However, for some policy types, you can override the order of precedence for individual policy rule types. For example, you might define the order of precedence for purchasing policies to be: cost center, department, company. For the catalog policy rule, you might want the order of precedence to be: department, cost center, company. You can change the order of precedence for the Catalog policy rule. When a worker creates a requisition, the catalog that is displayed is determined by the policies that are associated with the worker's department, then their cost center, and then their company.  
    - If there's more than one organizational level listed, you can use the Up/Down arrows to set the order of precedence for the Purchase requisition control rule.  
5. Close the page.

## Create a new policy
1. Select **New**.
2. In the **Name** field, type a value.
3. In the **Description** field, type a value.
    - A single purchasing policy can only apply to one organization hierarchy. For example, you could have one hierarchy called "Geographic" and one called "Department", and have a different purchasing policy for each.  
    - Select an organization that the policy should apply to.  
4. Select the arrow to add the selected organization.
    - You can repeat this process to add more organizations.  

## Add a policy rule
1. In the **Policy rule type** list, select **Requisition purpose rule**.
    - You'll create a rule that sets the default requisition purpose to type Consumption but allows the Replenishment type to be selected instead.  
2. Select **Create policy rule**.
3. Select **Yes** in the **Allow manual override** field.
4. Select **Close**.
    - Now you can set up other policy rules for the purchasing policy. Note that a Policy rule type cannot have overlapping rules that are active at the same time within a single procurement policy.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
