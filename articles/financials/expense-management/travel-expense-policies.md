---
# required metadata

title: Define expense policies
description: You can define expense policies that your workers must follow when entering and submitting expense reports and travel requisitions in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 
author: saraschi2
manager: AnnBe
ms.date: 01/12/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SysPolicyListPage 
audience: Application User
# ms.devlang: 
ms.reviewer:  twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: AX 7.0.0
---

# Expense policies

[!include[banner](../includes/banner.md)]

You can define policies that your workers must follow when entering and submitting expense reports and travel requisitions. 
Implementing expense policies can help you manage expenses effectively. 

For example, you can set a policy for hotel expenses in New York City, which states that the per night expense cannot exceed USD 250. 
If a worker submits an expense report or a travel requisition in which the room rate exceeds this amount, the system will notify the 
worker that the policy amount for the expense has been exceeded. You can configure the message that the worker will receive when you 
define the policy. 

You can define three types of policies: 

 - Warning – Allows the worker to submit an expense report or travel requisition but the expense will be marked for all approvers and  
 for later reporting. 
 - Error – Requires the worker to revise the expense to comply with the policy before submitting the expense report or travel 
 requisition. 
 - Justification – Requires the worker or a manager to enter a justification for exceeding the policy amount before submitting the
 expense report or travel requisition. 

You can also set up a date range for which expense policies are in effect. For example, airline fares for flights between Denmark 
and New York City can be expensive during the peak holiday travel season. You can define a flight expense rule that restricts the 
cost of flights to New York City to a limit of DKK 5000, and you can specify that this rule be in effect between March 15 and 
September 15. 
