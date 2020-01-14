---
# required metadata

title: Workflow FAQ
description: This topic answers frequently asked questions about the workflow system.
author: ChrisGarty 
manager: AnnBe
ms.date: 01/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Workflow FAQ

[!include [banner](../includes/banner.md)]

This topic answers frequently asked questions about the workflow system.

## Why are multiple notifications received when a work item is rejected?
When a work item is rejected, that work item is completed as rejected. Another work item is created and assigned to the originator. This means that there is a notification to the originator for the rejected work item, and a separate notification to the user assigned to the new "change requested" work item. 

Each notification is for a different work item, but the similarity can cause confusion. We are looking at ways to improve this in a future release.

## Why are my workflow exports failing?
There is currently a limitation in the workflow export feature that prevents workflow names from exceeding 48 characters. Using a name that is longer than 48 characters can result in a "Server failed to authenticate the request" error and/or prevent a file to be exported  without a file type. The following blog post provides more details [Workflow Export Troubleshooting](https://community.dynamics.com/ax/b/elandaxdynamicsaxupgradesanddevelopment/archive/2019/04/10/workflow-export-troubleshooting).

## Can the submitter of a workflow also approve the workflow?
Yes, a submitter of a workflow can also approve the workflow if it is configured that way. To prevent this behavior, set **System administration > Workflow > Workflow parameters > General > Approver > Disallow approval by submitter** to **Yes**.

## Can I add alerts to workflows to provide notifications to users?
Here are a few key areas to note about adding alerts to workflows to provide notifications:
- Alerts versus workflow notification mechanisms
    - Alerts can be set up for record changes. Workflows change records, so it's possible to set up an alert related to a record change caused by a workflow. However, because workflows have different built-in notification options, using alerts isn’t ideal.
- Standard notifications from workflows 
    - Workflows have built in email notifications. A customer can configure the notifications so that the users are sent emails. Those notifications don’t result in Action Center messages for users.
    - In a future update we will be adding an Action Center message so a user is assigned a workflow work item. 
- Adding notifications to workflows
    - Action Center messages can be created for specific users, such as a message created from a workflow in X++.
    - [Workflows have Business Events](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/business-events/business-events-workflow) that the customer could use to trigger Flows have the notifications that they are looking for.   

In summary, if a user does not get the proper notification from the Action Center when they are assigned a workflow work item, then leverage [Workflow Business Events](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/business-events/business-events-workflow) with Microsoft Power Automate to provide additional or different notifications.

## Workflow editor has trouble starting under ADFS 
When running under Active Directory Federation Services (AD FS) in an upgraded environment, the workflow editor may have trouble starting. If it does, make sure that the URL "https://dynamicsaxworkfloweditor/" is added to the property **Microsoft Dynamics 365 for Operations On-premises - Workflow - Native application** in the ADFS settings.
