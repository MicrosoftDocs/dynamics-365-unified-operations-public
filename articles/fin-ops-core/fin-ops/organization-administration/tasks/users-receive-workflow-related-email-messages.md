--- 
title: Enable users to receive workflow-related email messages
description: Learn about how to send workflow-related emails and enable users to receive workflow-related email messages, including a step-by-step process.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 03/10/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysUserManagement, SysUserSetup
ms.dyn365.ops.version: Version 7.0.0 
---

# Enable users to receive workflow-related email messages

[!include [banner](../../includes/banner.md)]

You can configure the system to send email messages to users when workflow-related events occur. For example, you can send email messages to users when you assign documents to them for approval. The demo data company used to create this procedure is USMF.

1. Go to **Navigation pane > Modules > System administration > Users > Users**.
1. In the list, find and select the desired record.
1. On the **Action pane**, select **User options**.
1. Select the **Workflow** tab. Make sure that the **Notifications** section is expanded. In the **Notifications** section, specify how you want the user to be notified about workflow-related events.  
1. In the **Line-item workflow notification type** field, select an option.
    - Grouped – Notifications for line items are grouped into a single email message.
    - Individual – An email message is sent for each line item.  
    - If you want the user to receive notifications in the client, select the **Send notifications in email** check box.  
1. Select **Save**.
1. Close the page.

> [!NOTE]
> The workflow email templates come from either system email templates or organization email templates. The source depends on whether the workflow is a system-level (not company specific) or organization-level (company specific) workflow.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
