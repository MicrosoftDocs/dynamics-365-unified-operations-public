---
# required metadata

title: Associate a workflow document class with a workflow type
description: The topic describes how to associate a workflow document class with a workflow type.
author: RobinARH
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Associate a workflow document class with a workflow type 

[!include [banner](../includes/banner.md)]

To create a workflow, you must bind a workflow document class to the workflow type. The workflow document class contains references to the table data fields that the workflow uses. This topic describes how to bind a workflow document class to a workflow type.

> [!NOTE]
> If you used the **Workflow** wizard to create the workflow type, the wizard has already bound the workflow document class to the workflow type.

Before you begin the following procedure, you must create a workflow document class to expose the table fields that are used for conditions in the configuration user interface (UI). For more information, see [Create a workflow document class](workflow-type-document-create.md).

## Bind a workflow document class to a workflow type

1. In Application Explorer, expand the **Workflow** node.
2. In the **Workflow Types** node, right-click the workflow type that you want to bind a workflow document class to, and then select **Properties**.
3. On the **Properties** sheet, set the **Document** property to the workflow document class that defines the workflow document.

## See also

[Create a new workflow type](workflow-type-create-new.md)

[Create a workflow document class](workflow-type-document-create.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]