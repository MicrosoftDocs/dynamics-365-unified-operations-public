---
title: Workflow FAQ
description: Access frequently asked questions about the workflow system, including questions about notifications and workflow approval.
author: ChrisGarty
ms.author: cgarty
ms.topic: faq
ms.date: 03/10/2026
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

## Why do I receive multiple notifications when a work item is rejected?

When you reject a work item, the system completes that work item as rejected. It also creates and assigns a new work item to the originator. The system sends a notification to the originator for the rejected work item, and it sends a separate notification to the user assigned to the new "change requested" work item.

Each notification corresponds to a different work item, but their similarity can cause confusion.

## Why are my workflow exports failing?

The workflow export feature currently doesn't support workflow names longer than 48 characters. If you use a name that's longer than 48 characters, you might see a "Server failed to authenticate the request" error. You might also be unable to export a file with a file type. For more information, see [Workflow export troubleshooting](https://community.dynamics.com/365/financeandoperations/b/elandaxdynamicsaxupgradesanddevelopment/posts/workflow-export-troubleshooting).

## Can the submitter of a workflow approve the workflow?

Yes, a submitter of a workflow can approve the workflow unless the setting **Disallow approval by submitter** is enabled for the workflow. To enable this setting, go to **System administration** > **Workflow** > **Workflow parameters** > **General** > **Approver**.

## Can I add alerts to workflows to provide notifications to users?

Here are a few key areas to note about adding alerts to workflows to provide notifications:

- Alerts versus workflow notification mechanisms
  - You can set up alerts for record changes. Workflows change records, so you can set up an alert related to a record change caused by a workflow. However, because workflows have different built-in notification options, using alerts isn't ideal.
- Standard notifications from workflows
  - Workflows have built-in email notifications. You can configure the notifications so users are sent emails. Those notifications don't result in Action Center messages for users.
  - In a future update, an Action Center message will be added so a user is assigned a workflow work item.
- Adding notifications to workflows
  - You can create Action Center messages for specific users, such as a message created from a workflow in X++.
  - [Workflows have business events](../../dev-itpro/business-events/business-events-workflow.md) that you can use to trigger Flows have the notifications that they're looking for.

If a user doesn't get the proper notification from the Action Center when they're assigned a workflow work item, [Workflow business events](../../dev-itpro/business-events/business-events-workflow.md) with Microsoft Power Automate can provide additional or different notifications.

There's some overlap between workflow and Microsoft Power Automate.

- Workflows that you create in Dynamics 365 Finance run inside Dynamics 365 Finance.
  - Use Dynamics 365 Finance to set up workflows that are specific to your Dynamics 365 Finance.
- Power Automate allows you to set up workflows that run outside of Dynamics 365 Finance. For more information, see [Power Automate](/power-automate/getting-started).
  - Use Power Automate to set up flows that involve information that flows through your company.

## Why can't the workflow editor start under AD FS?

When running under Active Directory Federation Services (AD FS) in an upgraded environment, the workflow editor might have trouble starting. If it does, make sure that you add the URL '<https://dynamicsaxworkfloweditor/>' to the property **Microsoft Dynamics 365 for Operations On-premises - Workflow - Native application** in the ADFS settings.

## Why am I getting SQL deadlocks on workflow processing?

The default field value for the **Number of workflow items per batch** on the **Workflow parameters** page is 0. A value of 0 sets the default to 20 items per batch. Be careful when adjusting this value because a high number of items per batch (> 40) can cause SQL deadlocks.

## What is the Workflow Enhanced Error feature?

The Workflow Enhanced Error feature in version 10.0.13 adds error codes that differentiate various classes of workflow errors. The feature also provides error messages that are mostly similar but include minor differences to make them clearer.

## What should I do if I encounter error code CAAC000E when signing in to the workflow editor?

You might encounter error code CAAC000E ("**Something went wrong. User is not eligible to enroll a device. Reason: DeviceCapReached**") when you sign in to the workflow editor if your account reaches the Microsoft Intune device registration cap that your organization configured. To ignore this error, select **Continue** to proceed with using the workflow editor to create or edit workflows.

To avoid this error in the future, select **No, sign in to this app only** the next time you sign in to the workflow editor, or contact your IT administrator to raise your device cap.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
