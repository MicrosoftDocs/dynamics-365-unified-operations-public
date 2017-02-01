---
# required metadata

title: Workflow system overview | Microsoft Docs
description: This article describes the workflow system in Microsoft Dynamics 365 for Operations.
author: sericks007
manager: AnnBe
ms.date: 2016-02-29 15:10:28
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: 71
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 56381
ms.assetid: 2cf54a5a-9c18-48db-acdb-b79b8850ae2a
ms.region: Global
# ms.industry: 
ms.author: tjvass

---

# Workflow system overview

This article describes the workflow system in Microsoft Dynamics 365 for Operations.

What is workflow?
-----------------

The term *workflow* can be defined in two ways: as a system and as a business process.
### Workflow is a system

Workflow is a system that is installed with Dynamics 365 for Operations and that runs on the Application Object Server (AOS). The workflow system provides functionality that you can use to create individual workflows, or business processes.

### Workflow is a business process

A workflow represents a business process. It defines how a document flows, or moves, through the system by showing who must complete a task, make a decision, or approve a document. For example, the following figure shows a workflow for expense reports. ![Workflow with elements that are assigned to users](./media/workflow_user.gif) To better understand this workflow, suppose that Sam submits an expense report for USD 7,000. In this scenario, Ivan must review the receipts that Sam routes to him. Then Frank and Sue must approve the expense report. Now suppose that Sam submits an expense report for USD 11,000. In this scenario, Ivan must review the receipts, and Frank, Sue, and Ann must approve the expense report.
Benefits of using the workflow system
-------------------------------------

There are several benefits of using the workflow system in your organization:
-   **Consistent processes** – You can define how specific documents, such as purchase requisitions and expense reports, are processed. By using the workflow system, you ensure that documents are processed and approved in a consistent and efficient manner.
-   **Process visibility** – You can track the status, history, and performance metrics of workflow instances. This helps you determine whether changes should be made to the workflow to improve efficiency.
-   **Centralized work list** – Users can view a centralized work list that displays the workflow tasks and approvals that are assigned to them.



