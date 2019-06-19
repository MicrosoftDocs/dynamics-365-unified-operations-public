---
# required metadata

title: How to associate a workflow document class with a workflow type
description: The topic describes how to associate a workflow document class with a workflow type in Dynamics 365 for Finance and Operations.
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

# How to associate a workflow document class with a workflow type 

To create a workflow in Dynamics 365 for Finance and Operations, you must bind a workflow document class to the workflow type. The workflow document class contains references to the table data fields used by the workflow. This topic describes how to bind the workflow document class to a workflow type.


> [!NOTE]
> <P>If you used the Workflow Wizard to create the workflow type, the workflow document class will have already been bound to the workflow type by the wizard.</P>



Before you begin this procedure, you must create a workflow document class to expose table fields used for conditions in the configuration user interface. For more information, see [How to create a workflow document class](workflow-document-create.md).

### To bind a workflow document class to a workflow type

1.  In the AOT, expand the **Workflow** node.

2.  In the **Workflow Types** node, right-click the workflow type that you want to bind a workflow document class to, and then click **Properties**.

3.  In the **Properties** sheet, set the **Document** property to the workflow document class that defines the workflow document.

## See also

[How to create a new workflow type](new-workflow-type.md)

[How to create a workflow document class](workflow-document-create.md)
