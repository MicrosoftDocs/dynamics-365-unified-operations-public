---
# required metadata

title: Creating a workflow type
description: This topic describes how to create a workflow type in Dynamics 365 for Finance and Operations.
author: RobinARH
manager: AnnBe
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
ms.search.region: Global
# ms.search.industry: 
ms.author: RobinARH
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Creating a workflow type 

To add workflow support for a document in Finance and Operations, you must create a workflow type. This topic describes the procedures to create a workflow type. The workflow type can then be used to create workflow configurations for the document in Finance and Operations.

You create workflow types to define:

  - The workflow document to assign the workflow to.

  - A category that defines the module that the workflow type is available in.

  - Tasks, automated tasks, and approvals supported for the workflow.

  - The workflow started, completed, configuration data change, and canceled event handlers.

  - A SubmitToWorkflowMenuItem.

## In this section

  - [Workflow type checklist](workflow-type-checklist.md)  

  - [How to create a workflow category](how-to-create-a-workflow-category.md)  

  - [How to create a query for a workflow type](how-to-create-a-query-for-a-workflow-type.md)  

  - [How to create a new workflow type](how-to-create-a-new-workflow-type.md)  

  - [How to create a workflow document class](how-to-create-a-workflow-document-class.md)  

  - [How to create a SubmitToWorkflow class](how-to-create-a-submittoworkflow-class.md)  

  - [How to associate a workflow document class with a workflow type](how-to-associate-a-workflow-document-class-with-a-workflow-type.md)  

## See also

[Walkthrough: creating a workflow type](walkthrough-creating-a-workflow-type.md)
