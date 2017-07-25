---
# required metadata

title: Expense reports and mutiple approvers
description: Depending on the expense approval policies of your organization, more than one person may be required to 
approve an expense report that is submitted by an employee.
author: saraschi2
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer:  twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: saraschi2
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: AX 7.0.0
---

# Expense reports and mutiple approvers

[!include[banner](../includes/banner.md)]

Depending on the expense approval policies of your organization, more than one person may be required to approve an expense report 
that is submitted by an employee. When you are setting up the workflow process for expense report approval, you can add workflow 
elements that include tasks or steps for one or more expense report approvers. For example, you might require that all expense reports
be approved first by the manager of the employee who submitted the report, and then by the accounts payable coordinator.

If you decide to require multiple expense report approvers, you can add the workflow elements in any of the following ways:

 - One approval element that contains one step. For example, the step might require that an expense report be assigned to a user group 
and that it be approved by 50% of the user group members.

 - One approval element that contains multiple steps. For example, the steps in the approval element are as follows: 
1. The manager of the employee who submitted the expense report approves it. 
2. The accounts payable clerk verifies the receipts and expense report items. 
3. The budget owner approves the expense report. 

 - Multiple approval elements, where each element contains one step. For example, the approval elements are as follows: 
1. The employee’s manager approves the expense report. 
2. The budget owner approves the expense report. 
