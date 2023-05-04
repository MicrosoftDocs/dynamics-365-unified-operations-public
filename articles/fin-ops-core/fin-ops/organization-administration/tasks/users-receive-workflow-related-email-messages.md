--- 
# required metadata 
 
title: Enable users to receive workflow-related email messages
description: You can configure the system to send email messages to users when workflow-related events occur. 
author: jasongre
ms.date: 06/01/2020
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysUserManagement, SysUserSetup   
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
# Enable users to receive workflow-related email messages

[!include [banner](../../includes/banner.md)]


[!INCLUDE [PEAP](../../../../includes/peap-1.md)]

You can configure the system to send email messages to users when workflow-related events occur. For example, email messages can be sent to users when documents are assigned to them for approval. The demo data company used to create this procedure is USMF.

1. Go to **Navigation pane > Modules > System administration > Users > Users**.
2. In the list, find and select the desired record.
3. On the **Action pane**, click **User options**.
4. Click the **Workflow** tab. Make sure that the **Notifications** section is expanded. In the **Notifications** section, you can specify how you want the user to be notified about workflow-related events.  
5. In the **Line-item workflow notification type** field, select an option.
    - Grouped – Notifications for line items are grouped into a single email message.
    - Individual – An email message is sent for each line item.  
    - If you want the user to receive notifications in the client, select the **Send notifications in email** check box.  
6. Click **Save**.
7. Close the page.

> [!NOTE]
> The workflow email templates will be sourced from either system email templates or organization email templates depending on whether the workflow is a system-level (not company specific) or organization-level (company specific) workflow.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]