---
title: Business events in financial period close
description: This article explains how to use business events in the financial period close business process to gain insights and provide internal controls.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 03/09/2026
ms.reviewer: johnmichalak
ms.search.region: Global 
ms.search.validFrom: Platform update 26
# ms.search.form: [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 2019-6-30 
---

# Business events in financial period close

[!include [banner](../../includes/banner.md)]

This article explains how to use business events in the financial period close business process to gain insights and provide internal controls.

To complete this article, you must be running version 10.0.2 (May 2019) with Platform update 26 or later.

## Scenario overview

Task management is fundamental to managing business processes across industries. Out-of-the-box capabilities let users manage business process tasks in a structured manner. The **Financial period close** workspace illustrates these capabilities by offering a central location for managing tasks in a company's accounting period close process.

This article looks at an organization that recently decided to explore how it can use the **Financial period close** workspace to track and report tasks that are associated with every period close. Performance management and traceability are some of the challenges that this organization faces in the current setup. Therefore, the organization undertook an exercise in business process transformation to identify the capabilities of the **Financial period close** workspace. This exercise revealed the following business requirements:

1. The ability to be notified when tasks must be started
1. The ability to attach documents
1. Record management and disposition capabilities for attachments
1. The ability for multiple approvers to approve tasks, based on predefined logic
1. Task questionnaires for audits
1. Reporting capabilities to track the current status of the period close process and do performance analysis for insights into efficiency

## High-level design

To achieve the previously mentioned requirements, the organization used out-of-the-box capabilities of the **Financial period close** workspace. A gap analysis revealed that by doing minor extensions to the workspace and the underlying data entities, the organization could achieve requirements 2, 5, and 6, and could partially achieve requirement 4. To achieve requirements 1 and 3, and parts of requirement 4, the organization chose to use Power Automate. The following illustration shows an architectural overview of the solution.

:::image type="content" source="../../media/Image1.PNG" alt-text="Screenshot of the high-level architectural overview of the solution.":::

## Managing attachments by using Microsoft Power Automate and SharePoint Online

Accountants view their tasks in the **Financial period close** workspace and start working on them. They add attachments to the task by using a SharePoint Online document type. You can use SharePoint triggers in Microsoft Power Automate to trigger the Power Automate flow shown in the following illustration. This Power Automate flow updates the SharePoint metadata with metadata from the task in the **Financial period close** workspace. You create SharePoint columns for this purpose in the document library. You create a separate attachment data entity to hold the attachment metadata for every attachment that you add to the **Financial period close** workspace. You map fields from the custom entity to the SharePoint Online columns in the Power Automate flow. When you create documents that use the specified document type in the predefined SharePoint Online library, Power Automate is triggered, obtains the metadata from the custom data entity, and updates the document's metadata columns in SharePoint Online.

:::image type="content" source="../../media/Image2.png" alt-text="Screenshot of the Power Automate flow for managing attachments.":::

## Enabling internal controls by using business events and Power Automate

As accountants complete their tasks and the tasks become ready for review, they update the value of the **Review status** custom field to **Ready for review**. The **When the change-based alert is triggered** business event triggers the Power Automate flow when you make this update. The payload of this business event contains the task name and the area name. The Power Automate flow uses the combination of the task name and area name, together with the value of the **Review status** field, to route the task through an email-based workflow that Power Automate orchestrates. The Power Automate flow waits for approval, adds new comments to the task log, and updates the task in the **Financial period close** workspace, based on both the outcome of the approval process and related metadata. You build custom data entities to query and update the **Financial period close** workspace by using Power Automate.

### Subscribing to the business event

The following example describes the general steps for subscribing to a change-based alert business event.

1. Add the connector trigger to the Power Automate app, and subscribe to the change-based alert business event.

   :::image type="content" source="../../media/Image3.png" alt-text="Screenshot of subscribing to the business event in Power Automate.":::

1. Parse the business event payload.

   When the business event is triggered, it triggers Power Automate. This business event contains a payload. In this step, you parse the payload and initialize the required variables.

   :::image type="content" source="../../media/Image4.PNG" alt-text="Screenshot of parsing the business event payload in Power Automate.":::

1. Retrieve the task, based on the values from the payload.

   When you update the task, the business event triggers Power Automate. At that point, after you parse the payload, you know basic information about the task. In this step, use the custom data entity to retrieve more information about the task.

1. Retrieve approvers from the Microsoft Excel file, based on the criteria.

   Next, you must determine the list of approvers, so that you can send the approval request in the appropriate manner. This list is a custom Excel file in a SharePoint Online library. In this step, you query the Excel file to get the list of approvers. You also get the links to the attachments for each task, so that you can send the attachments to the approvers.

1. Prepare to send the request for approval.

   In this step, you prepare Power Automate to send the approval request by using all the information that you gathered and assembled in the previous step.

   :::image type="content" source="../../media/Image7.png" alt-text="Screenshot of preparing to send the request for approval, part 1.":::

   :::image type="content" source="../../media/Image8.png" alt-text="Screenshot of preparing to send the request for approval, part 2.":::

1. Start the approval process.

   In this step, you send the approval request from Power Automate.

   :::image type="content" source="../../media/Image10.png" alt-text="Screenshot of starting the approval process in Power Automate.":::

1. Process the approval action that approvers take.

   After the approvers receive the approval request and take action, they notify Power Automate, and it does additional processing.

   :::image type="content" source="../../media/Image11.png" alt-text="Screenshot of processing the approval action taken by approvers in Power Automate.":::

1. Update the task with the approval outcome.

   Based on the outcome of the approval process, update the task with the result.

## Conclusion

For the business requirements of the organization described in this article, this solution involves minimal development and relies mostly on the **Financial period close** workspace, business events, SharePoint Online, and Power Automate to drive functionality. Development is restricted to the addition of fields to pages, the creation of custom data entities, and changes to page labels. Power Automate also provides greater flexibility in the approval process. Because the solution takes advantage of the various applications in the Microsoft 365 suite, internal users can use applications they're already familiar with. Therefore, the amount of change management that's required is limited.

In conclusion, business events offer unique opportunities for extending functionality but also let you avoid extensive in-app customizations. Here are some things to consider before you start to use business events:

- Establish the security requirements of your solution. Business events honor role-based security. This behavior can be beneficial in some use cases.
- Business events functionality continues to get enhanced. Be on the lookout for new capabilities.

Business events and Power Automate offer great opportunities for implementing low-code or no-code extensions. The important thing is that you identify opportunities where this framework can help, but also understand some of the limitations.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
