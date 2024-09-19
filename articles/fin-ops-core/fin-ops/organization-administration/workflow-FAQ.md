---
title: Workflow FAQ
description: Access frequently asked questions about the workflow system, including questions about notifications and workflow approval.
author: ChrisGarty
ms.author: cgarty
ms.topic: article 
ms.date: 02/08/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Workflow FAQ

[!include [banner](../includes/banner.md)]

This article answers frequently asked questions about the workflow system.

## Why are multiple notifications received when a work item is rejected?
When a work item is rejected, that work item is completed as rejected. Another work item is created and assigned to the originator. There will be a notification to the originator for the rejected work item, and a separate notification to the user assigned to the new "change requested" work item. 

Each notification is for a different work item, but the similarity can cause confusion. 

## Why are my workflow exports failing?
There's currently a limitation in the workflow export feature that prevents workflow names longer than 48 characters. Using a name that is longer than 48 characters can result in a "Server failed to authenticate the request" error or prevent a file to be exported without a file type. For more information, see [Workflow export troubleshooting](https://community.dynamics.com/365/financeandoperations/b/elandaxdynamicsaxupgradesanddevelopment/posts/workflow-export-troubleshooting).

## Can the submitter of a workflow approve the workflow?
Yes, a submitter of a workflow can approve the workflow unless the setting **Disallow approval by submitter** is enabled for the workflow under **System administration > Workflow > Workflow parameters > General > Approver**.

## Can I add alerts to workflows to provide notifications to users?
Here are a few key areas to note about adding alerts to workflows to provide notifications:
- Alerts versus workflow notification mechanisms
    - Alerts can be set up for record changes. Workflows change records, so it's possible to set up an alert related to a record change caused by a workflow. However, because workflows have different built-in notification options, using alerts isn’t ideal.
- Standard notifications from workflows 
    - Workflows have built-in email notifications. A customer can configure the notifications so users are sent emails. Those notifications don’t result in Action Center messages for users.
    - In a future update, an Action Center message will be added so a user is assigned a workflow work item. 
- Adding notifications to workflows
    - Action Center messages can be created for specific users, such as a message created from a workflow in X++.
    - [Workflows have business events](../../dev-itpro/business-events/business-events-workflow.md) that the customer could use to trigger Flows have the notifications that they're looking for.   

If a user doesn't get the proper notification from the Action Center when they're assigned a workflow work item, [Workflow business events](../../dev-itpro/business-events/business-events-workflow.md) with Microsoft Power Automate can provide additional or different notifications.

There's some overlap between workflow and Microsoft Power Automate. 
 - Workflows that are created in Dynamics 365 Finance are restricted to run inside Dynamics 365 Finance. 
     - Use Dynamics 365 Finance to set up workflows that are specific to your Dynamics 365 Finance.
 - Power Automate allows users to set up workflows that run outside of Dynamics 365 Finance. For more information, see [Power Automate](/power-automate/getting-started)
    - Use Power Automate to set up flows that involve information that flows through your company. 

## Why is workflow editor not able to start under AD FS?
When running under Active Directory Federation Services (AD FS) in an upgraded environment, the workflow editor may have trouble starting. If it does, make sure that the URL "https://dynamicsaxworkfloweditor/" is added to the property **Microsoft Dynamics 365 for Operations On-premises - Workflow - Native application** in the ADFS settings.

## Why am I getting SQL deadlocks on workflow processing? 
The default field value for the **Number of workflow items per batch** on the **Workflow parameters** page is 0. A value of 0 causes the  default to change to 20 items per batch. Be careful when adjusting this value because a high number of items per batch (> 40) can cause SQL deadlocks.

## What is the Workflow Enhanced Error feature?
The Workflow Enhanced Error feature in version 10.0.13 adds error codes to differentiate different classes of workflow errors. The error messages reported will be mostly similar with minor differences to make them clearer.

## What should I do if I encounter error code CAAC000E when signing in to the workflow editor? 
The error with code CAAC000E, **Something went wrong. User is not eligible to enroll a device. Reason: DeviceCapReached**, can appear when signing in to the workflow editor if your account has reached the Microsoft Intune device registration cap configured for your organization. You can click **Continue** to proceed to use the workflow editor to create or edit workflows despite this error. 

To avoid this error, choose the **No, sign in to this app only** the next time you sign in to the workflow editor, or contact your IT administrator to raise your device cap. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
