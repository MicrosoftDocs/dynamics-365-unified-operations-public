---
# required metadata

title: Expense management workflow
description: This topic explains how you can use the workflow system in Microsoft Dynamics 365 Finance, to set up a review process for expense reports in Expense management.
author: ShylaThompson
manager: AnnBe
ms.date: 09/13/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  WorkflowtableListPageRnr
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Expense management workflow

[!include [banner](../includes/banner.md)]

You can use the workflow system to set up a review process for expense reports in Expense management. You can set up a workflow that uses the following criteria to determine who approves expense reports:

- The employee reporting hierarchy and predefined approval limits
- Multi-level approval that supports interim approvers and a final approver
- Financial dimensions and project responsibility
- Assignment to specific users or user groups

Workflow approvals can be created for expense reports, travel requisitions, cash advances, and value-added tax (VAT) recovery.

**Example**

The following process is an example of the expense management workflow for an expense report.

1. An employee creates and saves an expense report.
2. The employee submits the expense report for approval. The approver is identified based on the rules that were defined when the workflow was set up.
3. The approver receives a notification that an expense report is ready for approval. The approver reviews the expense report and verifies that the following conditions are met:

    - The expenses don't violate any expense policies. If an expense violates a policy, the approver verifies that the expense report includes a valid business justification.
    - Electronic receipts are attached to the expense report.

4. The approver approves the expense report.
5. The expense report is assigned to the Accounts payable coordinator for posting.
6. One of the following steps occurs, depending on whether automatic posting is configured:

    - If automatic posting is configured, the expense report is processed for payment, and the status of the expense report is updated.
    - If automatic posting isn't configured, the Accounts payable coordinator verifies that all original receipts have been submitted, and that the receipts are aligned with the expenses on the expense report. All tax codes that are entered on the expense report must also be verified as correct.

After these requirements are verified, the expense report is posted.

After the expense report is posted, payment is authorized for the expense report, and the employee is reimbursed.
