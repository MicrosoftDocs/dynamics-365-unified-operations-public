--- 
# required metadata 
 
title: Enable users to receive workflow-related email messages
description: You can configure the system to send email messages to users when workflow-related events occur. 
author: jasongre
manager: AnnBe 
ms.date: 02/21/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Enable users to receive workflow-related email messages

[!include[task guide banner](../../includes/task-guide-banner.md)]

You can configure the system to send email messages to users when workflow-related events occur. For example, email messages can be sent to users when documents are assigned to them for approval. The demo data company used to create this procedure is USMF.

1. Go to System administration > Users > Users.
2. In the list, find and select the desired record.
3. Click User options.
4. Click the Workflow tab.
    * Make sure that the Notifications section is expanded.     In the Notifications section, you can specify how you want the user to be notified about workflow-related events.  
5. In the Line-item workflow notification type field, select an option.
    * Grouped – Notifications for line items are grouped into a single email message.    Individual – An email message is sent for each line item.  
    * If you want the user to receive notifications in the client, select the Send notifications in email check box.  
6. Click Save.
7. Close the page.

