---
# required metadata

title: Expense workflow
description: You can use the workflow system in Microsoft Dynamics AX to set up a review process for expense reports in expense.
author: saraschi2
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer:  twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi2
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: AX 7.0.0
---

# Expense workflow

[!include[banner](../includes/banner.md)]

You can use the workflow system in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition to set up a review process for 
expense reports in expense. You can set up a work flow to determine who approves expense reports based on any of the following criteria: 

- The employee reporting hierarchy and predefined approval limits 
- Financial dimensions and project responsibility 
- Assignment to specific users or user groups 

Workflow approvals can be created for expense reports, travel requisitions, cash advances, credit card disputes, and value-added tax (VAT) recovery. 

**Example** 

The following process is an example of the expense management workflow for an expense report. 

1. An employee creates and saves an expense report. 

2. The employee submits the expense report for approval. The approver is identified based on the rules that were defined when the 
workflow was set up. 

3. The approver receives notification that an expense report is ready for approval. The approver reviews the expense report and verifies
that the following conditions are met: 
 - The expenses do not violate any expense policies. If an expense does violate a policy, the approver verifies that a valid business 
 justification is included in the report. 
 - Electronic receipts are attached to the expense report. 

4. The approver approves the expense report. 

5. The expense report is assigned to the accounts payable coordinator for posting. 

- If automatic posting is configured, the expense report is processed for payment and the status of the expense report is updated. 
- If automatic posting is not configured, the accounts payable coordinator verifies that all original receipts have been submitted, and 
that the receipts align with the expenses on the expense report. All tax codes entered on the expense report must also be verified as 
correct. 

After these requirements are verified, the expense report is posted. 
After the expense report is posted, payment is authorized for the expense report and the employee is reimbursed. 
