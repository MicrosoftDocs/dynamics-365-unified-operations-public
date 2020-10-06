---
# required metadata

title: Define expense policies
description: You can define expense policies that your workers must follow when entering and submitting expense reports and travel requisitions in Microsoft Dynamics 365 Finance. 
author: suvaidya
manager: AnnBe
ms.date: 05/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  SysPolicyListPage, TrvPolicyRule
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ryansand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Define expense policies

[!include [banner](../includes/banner.md)]

You can define policies that your workers must follow when entering and submitting expense reports and travel requisitions. 		
Implementing expense policies can help you manage expenses effectively. 		

For example, you can set a policy for hotel expenses in New York City, which states that the per night expense cannot exceed USD 250. 		
If a worker submits an expense report or a travel requisition in which the room rate exceeds this amount, the system will notify the 		
worker that the policy amount for the expense has been exceeded. You can configure the message that the worker will receive when you 		
define the policy. 		
		
You can define three types of policies: 		
		
- Warning – Allows the worker to submit an expense report or travel requisition but the expense will be marked for all approvers and 		
  for later reporting.        

- Error – Requires the worker to revise the expense to comply with the policy before submitting the expense report or travel requisition. 		
 
 - Justification – Requires the worker or a manager to enter a justification for exceeding the policy amount before submitting the expense report or travel requisition.        

## Policy tips
Here are a few suggestions that can assist you when creating new policies for expense management. 
* Policies are date effective and won't take effect if the policy is created with a date after the date that the expense occurred. For example, if you are creating a new policy today to enforce a maximum meal expense of $50, then any existing expenses entered as of yesterday won't be checked against this policy.
* When creating a policy for an expense category that can be itemized, consider adding a condition for expense line type. Some policies such as requiring a receipt may not make sense for itemized lines and should only be applied to the header line or a non-itemized line. 
* Expense management policies are evaluated against the source entity by default. For intercompany scenarios, you can set the policy to be evaluated against the destination entity (borrowing entity) instead. To run the policies against the destination entity, turn on the "Evaluate Expense policy against borrowing legal entity" feature in the **Feature Management** workspace.

## When to evaluate policies

In expense management parameters, there is an option to either evaluate expense management policies when a line is saved or when an expense report is submitted. If you choose to evaluate when a line is saved this ensures that users have earlier visibility into what they need to do to complete their expense report all at once. Otherwise, you can delay policy evaluation and save time if you have validation occur at the end, during submission to workflow.
