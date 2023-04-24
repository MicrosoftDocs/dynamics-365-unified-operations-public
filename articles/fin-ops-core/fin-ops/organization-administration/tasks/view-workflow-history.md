--- 
# required metadata 
 
title: View workflow history
description: This article describes the steps to view the status of a document that was submitted to the workflow system for processing and approval.  
author: jasongre
ms.date: 07/09/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WorkflowStatus   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# View workflow history

[!include [banner](../../includes/banner.md)]


[!INCLUDE [PEAP](../../../../includes/peap-1.md)]

This article describes the steps to view the status of a document that was submitted to the workflow system for processing and approval. The demo data company used to create this procedure is USMF.

1. Go to **Navigation pane > Modules > Common > Inquiries > Workflow > Workflow history**.
    - Use this form to view the status of a document that was submitted to the workflow system for processing and approval.  
    - The **Instance ID** is the identification code of the workflow instance that is processing, or has processed the document.  
    - The **Status** is the workflow status of the document.  
    - The **Workflow ID** is the identification code of the workflow that is processing, or has processed the document.  
    - The **Document** is the identification code of the document.  
    - The **Document type** is the type of document that was submitted for processing.  
    - The **Workflow** is the name of the workflow that is processing, or has processed the document.  
    - The **Version** is the version number of the workflow that is processing, or has processed the document.  
    - The **Created date and time** is the date and time that the document was submitted.  
    - The **Elapsed time** is the time that has passed since the document was submitted.  
    - The **Resume** button allows you to resume the workflow process for the selected document.  
    - The **Recall** button allows you to recall the selected document so that it is not processed.   
2. In the list, select the link in the desired row.
    - Make sure the **Work items** section is expanded. In this section you can view the work items that are associated with the selected document. For example, a task may have to be completed, or the document may have to be approved.  
    - The **Reassign** button will open a dialog box where you can reassign a work item to another user.  
    - Make sure the **Tracking details** section is expanded. In this section you can view the workflow history of the selected document.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]