---
# required metadata

title: Expense reports and multiple approvers
description: This topic provides information about expense reports that require approval by more than one person. 
author: saraschi2
manager: AnnBe
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  TrvExpensesReportList
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Expense reports and multiple approvers

[!include [banner](../includes/banner.md)]

Depending on your organization's expense approval policies, more than one person might have to approve an expense report that is submitted by an employee. When you set up the workflow process for expense report approval, you can add workflow elements that include tasks or steps for one or more expense report approvers. For example, you might require that all expense reports be approved first by the manager of the employee who submitted the report and then by the Accounts payable coordinator.

If you decide to require multiple expense report approvers, you can add the workflow elements in any of the following ways:

- Add one approval element that has one step. For example, the step might require that an expense report be assigned to a user group, and that it be approved by 50 percent of the user group's members.
- Add one approval element that has multiple steps. For example, the approval element might have the following steps:

    1. The manager of the employee who submitted the expense report approves it.
    2. The Accounts payable clerk verifies the receipts and the expense report items.
    3. The budget owner approves the expense report.

- Add multiple approval elements, each of which has one step. For example, you might add a separate approval element for each of the following steps:

    1. The employee's manager approves the expense report.
    2. The budget owner approves the expense report.
