---
title: Create a workflow type
description: This article describes how to create workflow types.
author: josaw1
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
---

# Create a workflow type

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

To add workflow support for a document, you must create a workflow type. After you create a workflow type, it can be used to create workflow configurations for the document. This article provides links to the procedures for creating a workflow type.

You create workflow types to define the following elements:

- The workflow document to assign the workflow to
- A category that defines the module that the workflow type is available in
- Tasks, automated tasks, and approvals that are supported for the workflow
- The workflow started, completed, configuration data change, and canceled event handlers
- A **SubmitToWorkflowMenuItem** menu item

## In this section

- [Workflow type checklist](workflow-type-checklist.md)
- [Create a workflow category](workflow-type-category.md)
- [Create a query for a workflow type](workflow-type-query.md)
- [Create a new workflow type](workflow-type-create-new.md)
- [Create a workflow document class](workflow-type-document-create.md)
- [Create a SubmitToWorkflow class](workflow-type-submit-to-workflow.md)
- [Associate a workflow document class with a workflow type](workflow-type-associate-document.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
